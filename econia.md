# Econia Documentation

Econia is an order book, a fundamental financial tool utilized by financial institutions like stock markets,
except unlike the New York Stock Exchange or the NASDAQ, Econia is open-source, permissionless, and fully on-chain.Econia is an order book,
a fundamental financial tool utilized by financial institutions like stock markets, except unlike the New York Stock Exchange or the NASDAQ,
Econia is open-source, permissionless, and fully on-chain.

Econia is optimized for parallel execution across markets, such that transactions for different trading pairs operate on non-overlapping regions of global state

## Instances

Mainnet
https://explorer.aptoslabs.com/account/0xc0deb00c405f84c85dc13442e305df75d1288100cdd82675695f6148c7ece51c?network=mainnet

Testnet
https://explorer.aptoslabs.com/account/0xc0de11113b427d35ece1d8991865a941c0578b0f349acabbe9753863c24109ff?network=testnet

Implementation in move

```[dependencies.Econia]
git = "https://github.com/econia-labs/econia"
subdir = "src/move/econia"
rev = "mainnet"
```

## Key Elments

### Orders

FOr each markets orders are tracked in 2 places namely global OrderBook for market and a user specific MarketAccount for each user trading on the market

Each OrderBook has an ascending AVL queue for asks, and a descending AVL queue for bids,AVL queue is linked list of order sizes

AVL tree has self balancing results in cost reduction for lookup

### Eviction

For preventing AVL queue to have a very long height it has whereby the AVL queue tail is popped upon insertion of a different order, if one of two conditions are met:

- The tree exceeds a specified critical height, or
- The AVL tree cannot fit any more orders.

Presently, the AVL tree supports up to N_NODES_MAX = 16383 orders at a time, meaning that for a critical height of 18, for example, up to 16383 orders

### Units and market parameters

- Price granularity
  Prices should be in continous manner else users trades are never executed

- Minimum order size
  Market participants should be able to create a limit order as long as it's for a meaningful amount of asset

- Order size granularity
  One increment or decrement in order size should be a meaningful but not overwhelming difference in value

### Adversarial considerations

- Econia has upper bound on the number of possible price levels to prevent attacker cant do DOS attack by filling up orders like 1,2,3,4,,,,
  such that insertion/removal operations would have to access as many as 368 table entries

- Other than just having upper bound and as well as the number of total orders still allows attacker to place maximum orders and lock up the order book hence Econia additionally imposes eviction logic, whereby the order with lowest price-time priority is evicted if the order book fills up Here, orders far away from the spread are subject to cancellation if a better price comes around, Even if attacker placing and cancelling during the same transaction attacker still need to have to pay for n_node_max

## The Registory

The global registory tracks information about markets, coustodians and underwriters all of which can be registed permissionlessly

### Markets

EAch EConia market has unique MarketInfo and corresponding Marketid. It specifies the base and quote asset types for a market and Market parameters(tick size,lot size minimum size)

**Quote asset must be a CoinType**
**Base asset can be CoinTYpe or generic asset and generic asset requires the underwriter required to verify generic asset amounts for the market**

- get_market_account_market_info_custodian()
- get_market_account_market_info_user()

### Custodians

within a market a user may register a MarketAccount with their signature is required to approve order operations and withdrawals
Custodians manage orders and withdrawals on behalf of a user, via a CustodianCapability with a unique serial ID that is assigned upon issuance. Via this custodian ID approach only a single entity (either signing user or a delegated custodian), has authority over a certain market account

### Market uniqueness

Base coin,Quote coin,Lot size,Tick size,Minimum order size make the market unique

In the case of a spot market, where both the base asset and the quote asset are Coin types, a new market can be registered via register_market_base_coin(),

### Incentives

Econia also charges taker fees, denominated in the quote coin for a given market, which are distributed between integrators and Econia. The share of taker fees distributed between an integrator and Econia
The fee, denominated in the utility coin, to register a market.
The fee, denominated in the utility coin, to register an underwriter capability.
The fee, denominated in the utility coin, to register a custodian capability.

## Market accounts

### Collateral

A user's MarketAccount tracks the amount of base and quote assets held, as well as the amount available for withdrawal, but it does not actually store any coins held as collateral. Instead, a separate Collateral resource is maintained for each relevant coin asset. This includes:

- The quote coin type for the market.
- The base coin type for the market, if the base type is not GenericAsset.

when a user deposits assets to Econia for trading, their assets are held locally rather than in a global vault for the entire order book. Through this direct peer-to-peer trading approach, Econia:

Eliminates transaction collisions that would otherwise result from deposits and withdrawals against a global resource.
Reduces the size of a hypothetical economic attack target (a central vault) by distributing its contents across all users.

### Collateralization

every position on an Econia order book is fully backed with an asset that cannot be withdrawn unless the corresponding maker cancels their order.

## Matching

Econia's matching engine is atomic and crankless, which means that taker orders either fill against maker orders during the transaction in which they are placed, or do not fill at all

Econia's matching engine routes assets directly between counterparties, rather than updating units of account within a central vault

Functions

![pic](https://econia.dev/assets/images/matching-1a0cbaa3b8b101b3063a095bfdbf2de6.svg)

### Limit orders

Econia supports limit orders with a side, size, price, and restriction, per place_limit_order() and its associated wrappers. Notably, this include a size in lots and an integer price.

Depending on the price and restriction, a limit order will first match across the spread as a taker, then will post as a maker order.

Flag Meaning
NO_RESTRICTION Optionally fill as a taker, then post to the book as a maker
FILL_OR_ABORT Abort if any size posts as a maker (only fill)
POST_OR_ABORT Abort if any size fills as a taker (only post)
IMMEDIATE_OR_CANCEL Fill as a taker as much as possible, then cancel any remaining size

### Passive advance limit orders

Econia supports a special type of limit order known as a "passive advance limit order", which allows a user to place a passive limit order that advances a specified amount into the spread. As described in place_limit_order_passive_advance(), a user can specify a passive advance amount either in ticks or as a percent of the maximum possible advance into the spread, resulting in a passive advance price that is then input to place_limit_order() as a post-or-abort order.

### Market orders

Per place_market_order() and its associated wrappers, Econia supports taker-only market orders that fill from a user's market account. Like limit orders, market orders specify an integer price and a size in lots.

### Self match behavior

Econia's matching engine supports configurable self match behavior, with a self match defined as a hypothetical fill where taker and maker assets are derived from the same market account. Hence since limit orders and market orders can both fill as a taker, they require one of the following self match behavior flags:
