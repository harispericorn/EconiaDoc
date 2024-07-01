Econia - Order Book

https://blog.cow.fi/what-is-backrunning-mev-attacks-explained-38692250690c

Arbitrage describes the act of buying a security in one market and simultaneously selling it in another market at a higher price, thereby enabling investors to profit from the temporary difference in cost per share.

MEV attack - (Maximal Extractable Value) / miner extractable value

frontrunning, sandwich attacks, and backrunning)

Backrunning = capturing arbitrage left over after a large trade

When a trader places a large trade that artificially inflates the price of an asset on an AMM, an MEV bot can backrun the trade and profit from the arbitrage

In practice, backrunning involves strategically executing a transaction immediately after another, high-value transaction. By doing this, the backrunning transaction capitalizes on the arbitrage opportunity left over from the price impact of the initial transaction.

Backrunning is only harmful to the user when combined with a frontrunning attack, which results in the worst kind of MEV — the sandwich attack.

Frontrunning: In a frontrunning attack, an MEV bot spots a profitable transaction, duplicates it, and offers a higher gas fee so that validators execute the duplicate transaction before the original one. In effect, the MEV bot hijacks the profits of the original transaction and keeps them for itself.

Sandwich Attacks: This tactic combines frontrunning and backrunning. An attacker first executes a frontrunning transaction before a valuable trade, pushing the price of the asset up to the slippage tolerance set by the victim trade. This increases the price of the purchased asset. The victim trade then goes through at this new higher price and its price impact raises the price of the asset even more. Finally, the attacker performs a backrunning attack which captures the newly-created arbitrage, generating a profit in the process.

protect against MEV attacks :
Delegated trade execution
Uniform clearing prices
Uniform Clearing Prices, all token pairs traded in the same batch will clear at the same price

“Coincidences of Wants” (CoWs)

MEV Blocker is a custom RPC endpoint that you add to your crypto wallet which routes all of your transactions through a trusted network of searchers that scan for backrunning opportunities, but cannot frontrun or sandwich your trades. The best part? The RPC passes the profits from backrunning opportunities back to you in the form of rebates. This means you can make money from any backrunning opportunity you create just by routing your transactions through MEV Blocker.

MEV Blocker works on all types of transactions across all of DeFi. Just add the RPC endpoint to your wallet and start trading.

https://medium.com/@mesprotocol/the-future-of-decentralized-exchange-order-book-model-or-automated-market-maker-f9c86a58c6d1

Market maker refers to a firm or individual who actively quotes two-sided markets, providing bids and asks along the order book to take profit by arbitrage.

There are basically two order placements — market order and limit order.

a market order placement is a “taker” which takes away liquidity from the order book; hence they usually pay higher trading fees at centralized exchanges.

================
Econia solves the MEV attack by utilizing an ordered system. transactions gets executed in an order pre-determined

===================

https://medium.com/econialabs/introducing-econias-atomic-matching-engine-a337924b560f

Econia - paraqueues, and an atomic matching engine.

on-chain atomic matching engine
Here, atomicity refers to the compressed nature of Econia’s matching engine, which settles market orders in one execution step: when a user decides they want to buy or sell a digital asset at the best price offered by the market, Econia v1 matches their order against another market participant’s limit order (an ask or a bid), updates positions on the book, and routes assets between counterparties, all within a single transaction.

optimistic concurrency of the Aptos blockchain

Pessimistic Approach: Validate -> Read -> Compute -> Write; complicated & deadlock issue
Optimistic Approach: Read -> Compute -> Validate -> Write; If conflict rollback

Econia isolates different markets into separate regions of computer memory, achieving a condition known as non-overlapping state, so that orders can clear in parallel across separate markets:

Market 1 = token1 USDT
Market 2 / fake = token1 USDT

============================

https://medium.com/aptoslabs/block-stm-how-we-execute-over-160k-transactions-per-second-on-the-aptos-blockchain-3b003657e4ba

in Block-STM, determinism is considered a performance blessing. In fact, the final outcome is guaranteed to match a sequential execution of transactions in a fixed, preset order, and this constraint is used to the system’s advantage. This is possible, as previously noted in the Bohm paper in the context of databases, because agreeing on a specific serialization reduces the amount of synchronization required during execution.

Software Transactional Memory (STM)

AMM => MEV

https://unchainedcrypto.com/uniswapx-launches-with-mev-protection-and-gas-free-swaps/
ecosystem of fillers, who will pay gas on behalf of these users to complete transactions.

https://docs.mountainprotocol.com/reference/usdm-reserves
Instead, the company provides liquidity by securing multiple OTC USDC-denominated lines of credit, collateralized by USDM Reserves. Such facility provides "advances" to users in the form of USDC, which are then re-paid by the USDM Reserves when markets open.

https://thalalabs.medium.com/introducing-thala-v2-60eb5dc45e07
Users can lock either of the two to obtain veTHL, which represents a user’s voting weight.

https://docs.liquidswap.com/v/liquidswap-v1-docs/protocol-overview

https://www.investopedia.com/terms/s/slippage.asp
Slippage refers to all situations in which a market participant receives a different trade execution price than intended.
Slippage occurs when the bid/ask spread changes between the time a market order is requested and the time an exchange or other market maker executes the order.
Slippage occurs in all market venues, including equities, bonds, currencies, and futures.
The final execution price vs. the intended execution price can be categorized as positive slippage, no slippage, or negative slippage.
Slippage can be limited by not executing trades late in the day, investing in calm and liquid markets, and placing limit orders.

While a limit order prevents negative slippage, it carries the inherent risk of the trade not being executed if the price does not return to the limit level. This risk increases in situations where market fluctuations occur more quickly, significantly limiting the amount of time for a trade to be completed at the intended execution price.

With negative slippage, the ask has increased in a long trade or the bid has decreased in a short trade. With positive slippage, the ask has decreased in a long trade or the bid has increased in a short trade. Market participants can protect themselves from slippage by placing limit orders and avoiding market orders.

Slippage usually occurs when markets are volatile or liquidity is lacking

If you want to limit slippage, don't invest around the time of major economic announcements or important updates relating to a security you wish to trade, such as an earnings report. These types of events can move markets significantly and lead prices to jump around.

Market orders are transactions to be executed as quickly as possible, whereas limit orders are orders that will only go through at a specified price or better. If you place a limit order, you can avoid negative slippage. However, there is also the risk that the order doesn’t get executed.

Some platforms allow investors to place an order while specifying the maximum amount of slippage they are willing to accept in percentage terms.

What Is a 2% Slippage?
Some brokers allow investors to specify a maximum slippage tolerance. 2% slippage means an order being executed at 2% more or less than the expected price. For example, if you placed an order for shares in a company when they were trading at $100 and ended up paying $102 per share, you would have 2% negative slippage.

positive slippage is good. It means you got a better price than expected.

A spot market deal is for immediate delivery, which is defined as two business days for most currency pairs. The major exception is the purchase or sale of USD/CAD, which is settled in one business day.

The U.S. dollar is the most actively traded currency. The euro is the most actively traded counter currency, followed by the Japanese yen, British pound, and Chinese renminbi

Currencies are listed in pairs on the forex market. This combination is called a currency pair. The first currency is called the base or transaction currency while the second one is the counter or quote currency. I

https://www.investopedia.com/terms/l/limitorder.asp

What Is a Limit Order?
A limit order in the financial markets is a direction to purchase or sell a stock or other security at a specified price or better. This stipulation allows traders to better control the prices at which they trade. A limit can be placed on either a buy or a sell order:

A buy limit order will be executed only at the limit price or a lower price.
A sell limit order will be executed only at the limit price or a higher one.

The price is guaranteed, but the filling of the order is not. Limit orders will be executed only if the price meets the order qualifications.

The alternative to a limit order is a market order, which calls for a trade to be executed at the prevailing market price without any price limit specified.

What Is a Limit Order?
A limit order is a direction given to a broker to buy or sell a security at a specific price or better. It is a way for traders to execute trades at desired prices without having to constantly monitor markets. It is also a way to hedge risk and ensure losses are minimized by capturing sale prices at certain levels.

What Is a Fill?
A fill is an executed order. It is the action of completing or satisfying an order for a security or commodity. Order execution and reporting fills is a fundamental act in the transacting of stocks, bonds or any other type of securit

How Fills Work
There are several types of ways investors may attempt to fill a securities order. The first and most straightforward approach is the market order. In this scenario, an investor instructs a broker to buy or sell an investment immediately at the best available current price.

This is usually a default option on an investor’s trading platform and highly likely to be executed. A market order is also sometimes called an unrestricted order and on average has low commissions, due to the lack of requirements, logistics, and effort needed to complete it.

A stop order (also called a stop-loss order) is a limit order that becomes a market order once the target price is achieved. For example, if a buy stop order is entered at a price of $20 (above the current market price), and the stock achieves this price, it will automatically purchase specified shares at the next available market price (e.g. $20.05).

https://www.investopedia.com/decentralized-finance-defi-5113835

Total value locked (TVL) is a metric used in the cryptocurrency sector to determine the total U.S. dollar value of digital assets locked, or staked, on a particular blockchain network via decentralized finance (DeFi) platforms or decentralized applications (dApps). The higher the TVL of a project, the more secure and valuable it is perceived to be.

Total value locked (TVL) measures the U.S. dollar value of assets locked on a blockchain.
It is an important indicator of investor and developer interest in a blockchain or decentralized application (dApp).
TVL is similar to bank deposits for decentralized finance (DeFi) projects.

TVL will only provide a snapshot of the total value of assets that are locked in a platform; it doesn’t highlight activity levels. If a platform has a high TVL but low user-activity levels, this may mean that a small number of investors account for the TVL on that platform—generally, this is a red flag and would require more investigation. Investors should also look at the data practices of third-party analytics platforms to ensure that all the TVL figures are up to date.

https://pontem.network/posts/what-is-an-automated-market-maker-amm
function x\*y=k, which establishes a range of prices for two tokens according to the available quantities (liquidity) of each token. When the supply of token X increases, the token supply of Y must decrease, and vice-versa, to maintain the constant product K. When plotted, the result is a hyperbola where liquidity is always available but at increasingly higher prices, which approach infinity at both ends.

According to the AMM principle, the more liquidity in the pool, the less slippage of large orders. And this, in turn, allows you to attract larger volumes to the platform, and so on.

What is impermanent loss?
The risks associated with liquidity pools include impermanent loss. They arise when the price ratio of the combined assets fluctuates. LP will automatically incur losses when the price ratio of the combined asset deviates from the price at which it invested. At the same time, the greater the price change, the higher the losses incurred. Impermanent losses usually affect pools containing volatile digital assets.

However, this loss is impermanent, as there is a possibility that the price ratio will recover. Losses become permanent only if the LP withdraws funds before the price ratio changes to the opposite. In addition, it should be borne in mind that potential revenues from transaction fees and LP rates on tokens can sometimes cover such losses.

https://pontem.network/posts/liquidity-pool-mechanics#what-is-a-liquidity-pool
popular exchanges do not have enough orders to complete every single trade with a live buyer and seller.

This change in price between the quote and the filled order is called slippage. Bob’s trade was quite large compared to the size of the pool. His 10 USDT are 10% of the liquid USDT. While there will always be some price effect from making a swap in the pool, this is far less noticeable with larger pools. Much of the time, the slippage will be negligible or even too small to notice.

Such a discrepancy creates an arbitrage opportunity. Arbitrage means taking advantage of a difference in price in two different places: buy something where it’s cheap, sell it where it’s expensive, and pocket the difference. Liquidity pools use arbitrage to balance themselves and return to equilibrium.

Correlated Pools
That’s why liquidity pools are not a great fit for stablecoin-to-stablecoin swaps. Ihe same goes for correlated pairs like BTC/WBTC and ETH/WETH.
The exchange rate should be extremely consistent. As a solution, Solidly (a DEX on Fantom built by Andre Cronje) introduced an alternative pricing formula:

X3Y + Y3X = K
Impermanent Loss
The other main way liquidity pools can be risky is impermanent loss. Impermanent loss occurs when the price ratio of the combined assets fluctuates, as they do in any uncorrelated pool. Remember, the assets you deposit in the pool have value of their own which changes. If you deposit an asset at a certain price, then the price decreases, you can incur a loss if you withdraw your deposit before the pool has corrected itself. Make no mistake: if you do withdraw under these conditions, the loss is, in fact, permanent.

The loss is called impermanent because it is not realized until you withdraw your funds. If you wait to withdraw until the exchange rate is in your favor, there can be no loss.

Tips to Stay Safe in Liquidity Pools

- Never use a pool with low liquidity.

2. Set your slippage tolerance
   Turn on Frontrunning Protection

https://pontem.network/posts/concentrated-liquidity-beginner-guide-to-uniswap-v3-liquidity-book

Concentrated liquidity maximizes capital efficiency and earnings for liquidity providers. It lets you decide where on the price curve your funds should be traded.

Concentrated liquidity maximizes capital efficiency and earnings for liquidity providers. It lets you decide where on the price curve your funds should be traded.
The best-known Concentrated Liquidity Market Makers (CLMM) are Uniswap V3 and Trader Joe’s Liquidity Book. Concentrated liquidity pools account for 85% of the volume on Uniswap. You can earn up to 320% more this way, as your money constantly works for you instead of lying idly in a pool.
Concentrated liquidity is suitable only for experienced liquidity providers.
CLMMs use different approaches: Uniswap v3 has price ranges, where you pick a section of the price curve from point A to point B. Liquidity Book uses “bins” -- mini-pools within the main pool, where every step of the price corresponds to a new bin.
The advantage of Trader Joe’s approach is that within one bin, swaps happen with zero slippage and zero price impact. Once tokens in a bin are depleted, the contract moves to the next bin.
On the other hand, the Uniswap interface can be easier to use.
Uniswap V3 positions are represented as NFTs, which makes them more expensive to use than Liquidity Book’s fungible LP tokens.
Concentrated liquidity is suitable only for experienced liquidity providers. If the price exits the range, you won’t earn any fees. Because of this, you’ll have to rebalance the range frequently.
Another issue is impermanent loss: it can be several times higher on concentrated liquidity AMMs than on a regular DEX.

Concentrated liquidity is a DEX feature that allows users to allocate liquidity in a custom price range instead of along the whole possible range of prices.

The feature was first introduced by Uniswap V3 in March 2021. In August 2022, Trader Joe, the biggest DEX on Avalanche, introduced its own version, called Liquidity Book (arguably more efficient, but also a bit more complex, so we’ll start with Uniswap V3.)

Less capital for the same gains

Less slippage and price impact for swapper
V3 pools have deeper liquidity where it matters most: around the current price. Deep liquidity means less price impact and less slippage. Your swap will be executed at the price you expect, and even a large transaction won’t move the price by much.

Lower fees

Disadvantages of Concentrated Liquidity
Rebalancing
For maximum earnings, you’ll need to readjust the price range regularly, making sure that the range includes the current price. Every rebalancing is a transaction that costs gas.

Technical complexity
Concentrated liquidity AMMs aren’t designed for newbies, both Uniswap V3 and - especially - Trader Joe’s Liquidity Book with its liquidity bins, radiuses, and strategies.

Time-intensive
You’ll need to spend time monitoring prices, adjusting ranges, studying strategies, etc.

Impermanent loss
The impact of impermanent loss is larger. That is, if the token price rises sharply, you’ll miss out on more gains relative to simply keeping the tokens in a wallet. (More on this below.)

NFTs instead of LP tokens on some platforms

In V3, you don’t always have to deposit equal amounts of both tokens, as you do in V2 (e.g. 100 USDT and 100 USDC). The range and amounts can be asymmetrical relative to the current price. If you set a range that doesn’t include the current price, you’ll need to deposit just one token.

The smallest step between prices is called a tick. The tick size is different for each cryptocurrency. When you drag the range slider, it will move from one tick to the next, so you may not be able to set an exact price.

As the price nears one of the ends of the range, the reserves of one of the tokens will be depleted. When the price moves outside of the range, the whole position will be converted to just one token.

Impermanent loss in CLMM
Impermanent loss (IL) is a decrease in the value of a liquidity position compared to the hypothetical situation where the user holds them in a wallet without depositing them in a pool.
IL is a type of opportunity cost. Ideally, you would earn more from fees than you miss out on from impermanent loss, but this is often not the case.
On AMMs with concentrated liquidity, the impact of IL is several times higher for the same change in prices, depending on the width of the range.
How can you offset impermanent loss? One way is through yield farming. Another way is through variable swap fees that go up when volatility increases. This is implemented in Trader Joe’s Liquidity Book, which also features so-called liquidity bins instead of price ranges.

Liquidity Book: a new solution to slippage, price impact, and IL
Liquidity Book is a concentrated liquidity AMM that powers TraderJoe, the biggest DEX on Avalanche. The new V.2.1 launched in April 2023. It’s also live on Arbitrum and BNB Chain.

Instead of ranges, Liquidity Book uses liquidity bins: a sort of pool within a pool. Every bin corresponds to a specific price level, and the price difference that separates one bin from the next is called the bin step.

At any point, one bin is active: the one that corresponds to the current price. The tokens for the swaps are taken from this bin, and once it’s empty, the smart contract switches to the next one, which becomes active.

You earn LP rewards only when you have money in the active bin. In V.2.1, the rewards are compounded into the active bin.
While trading within the same bin, there is no price impact and no slippage. This is a big advantage of Liquidity Book.

When you deposit liquidity in a bin, you’ll get special fungible tokens (not NFTs like on Uniswap V3).
You can choose a price range or bin radius (the number of bins to be included in a position).

There are several strategies depending on the maximum bin radius and how tokens are distributed among them: Spot, Curve, and Bid-Ask.

V.2.1 will introduce Autopools - dynamic strategies that are automatically rebalanced. There will also be yield farms for Autopools.

Liquidity Book has only one fee tier per pool (compared to Uniswap’s four).

To compensate liquidity providers for impermanent loss, swap fees go up when volatility is high, so that LPs earn more. This is called Surge Pricing.

Advantages of Liquidity Book
Zero slippage or price impact in the active bin
Fungible LP tokens, which are cheaper and easier to transact with than NFTs
Fluctuating swap fees to compensate for impermanent loss
Autopools (coming soon) -- dynamic strategies that don’t need rebalancing
Better control over where your funds are deployed (thanks liquidity tobins)

Disadvantages
More complicated for beginners than Uniswap V3 because of the various strategies and the concept of bins
No Full Range option
Adding liquidity in a wide range requires several transactions, meaning more gas fees

Liquidity Bins in Detail
The whole pool still uses the constant product formula x*y=k, but inside each bin, a different formula is used: P*x+y=k, where P is a price constant that’s unique to each pool. Basically. you add X tokens and take out Y tokens, or vice versa, until there is just one type of token left.

All bins except for the active one contain just one type of token (X or Y), because they’ve either been depleted or are waiting to be used. For example, in the APT-USDT pool, you’ll be able to add only APT or only USDT to inactive bins. You can also deposit just one type of token to the active bin, and part of it will be automatically swapped for the other.

Only the active bin earns trading fees. Your goal as a liquidity provider is to make sure that you have funds in the active bin. You can spread the capital across a number of bins to cover the price range where you expect a pair to trade. If the price goes to a bin where you don’t have any tokens, you won’t earn any fees.

What is Bin Radius?
Bin radius is the number of liquidity bins on either side of your target price. In the Add Liquidity interface, the target price is set to the current market price by default, but you can change it.

Your liquidity position will span 2x of the radius: if you set the radius to 20 bins, the position will cover 40.

To compensate liquidity providers for the high risk of impermanent loss, Liquidswap introduces special variable fees. When volatility is high, the swap fee automatically increases to ramp up liquidity providers’ earnings. And when volatility goes down, so do the fees. Liquidswap measures volatility based on how often the price moves from one liquidity bin to the next.

The variable fee structure is different for different pools. There is also a cap on the total fee to keep it fair for swappers.

you need to always have liquidity in the active bin to earn the full APR, and even then impermanent loss can eat up some of the gains.
Here is an important rule that goes for all DEXs: the current APR is never a guarantee (or even an indication) of future gains. It’s there for information purposes only.

Innovations in Liquidity Book V.2.1
Autopools. These are automated “liquidity-as-a-service” strategies for those who don’t want to spend time on rebalancing. An Autopool rebalances liquidity automatically: when volatility is low, your tokens will be concentrated around the active bin. But when volatility increases, they will be spread wider. Autopools weren’t live yet as of May 4.

Autopool Farms. Autopools will issue special LP tokens that can be easily deposited in yield farms.

Permissionless pools. Users will finally be able to create concentrated liquidity pools for any token in pairs with AVAX, USDC, and a few other whitelisted assets.

Price curve shapes and strategies

When using liquidity bins on TraderJoe, you can choose one of the three options for the price curve shape: Spot, Bid-Ask, and Curve.

https://support.traderjoexyz.com/en/articles/6707938-an-introduction-to-liquidity-shapes

Liquidity Shape
Liquidity Book is distinct in that it allows you to construct varying "shapes" by allocating different amounts of tokens at diverse price points that are referred to as 'bins'. Each bin represents a fixed price pool in a Liquidity Pool and when you deploy your Liquidity, you will be defining your range by selecting bins. This concept is known as building a liquidity shape.

Please note that providing concentrated liquidity can come with large risk of impermanent loss if a position is not monitored closely. No strategy deployed will prevent the possibility of Impermanent Loss. You must monitor your position.

https://pontem.network/posts/concentrated-liquidity-top-clmm-protocols-pontem-survey-insights
Concentrated liquidity is a way to deploy liquidity in a DEX pool in a limited range (usually around the current price) as opposed to uniformly along the whole price curve. You choose the range when you open a position.

This increases capital efficiency, as the funds are constantly used for swaps and generate more fees.

Concentrated liquidity pools can generate up to 320% higher APR than regular pools, but they also have potential limitations:

1. Concentrated liquidity is technically complex and not suited for beginners.

2. Liquidity positions have to be adjusted (rebalanced) often, or the price will move outside your range and you won’t earn any fees. Every adjustment costs a gas fee.

3. Impermanent loss can be higher.

Concentrated liquidity pools work best when liquidity is deep and volatility is moderate, so that a single trade can’t move the price by much. Higher volatility means more frequent rebalancing to ensure your range includes the current price.

Concentrated liquidity on Liquidswap

Trader Joe’s Liquidity Book
You’ll be able to choose between a price range and a bin radius and select among several liquidity shapes (Spot, Curve, Bid-Ask, Wide). Also, you won’t have to bother with Uniswap-style NFT positions; Liquidswap pools issue regular LP tokens.

Concentrated liquidity on Aptos
Cetus Protocol

https://pontem.network/posts/on-chain-order-books-101-econia-more
On-Chain Order Books 101: Econia

Central Limit Order Books (CLOBs) are one of the biggest innovations in decentralized trading. They connect buyers and sellers on a DEX, enabling limit orders and other advantages of the CEX trading experience while keeping it trustless.

What is an order book?

An order book is a list of limit buy orders (bids) and sell orders (asks) for a traded asset, such as a security or cryptocurrency.

Limit orders are bids and asks that specify a certain price; for instance, if bitcoin is trading at $43,000, one might place a limit order to purchase a certain amount if the price falls to $41,000. Sometimes you’ll see an order book called a CLOB (Central Limit Order Book).

Limit orders exist in contrast to market orders, which buy or sell an asset as soon as possible at the current price. Order books are necessary for limit orders, as bids often must be held for some time until an ask of corresponding price and size is made, or vice versa. For swing traders, the wait can take months!

The “top of the book” contains the lowest bids and highest asks, which will be filled first. The “spread” is the difference between those figures, while the average current market price is displayed in the middle.

These limit orders are used to fill market orders - always at the best available price. Once the supply at a certain price level (tick) is exhausted, the price moves to the next tick. This is called slippage. You’ll see the numbers on an order book move really fast as the price slips between ticks.

https://pontem.network/posts/breaking-news-try-concentrated-liquidity-on-liquidswap

Example: the current price is 0.100 APT for 1 USDC and the bin step is X20. If you set the radius to 10, it will cover 2% of the price (10\*0.2%) on either side of the current price, or from 0.098 APT to 0.102 APT for 1 USDC.

Fees on Liquidswap V1
Swapping fees on the CLMM are dynamic: they change depending on volatility. The fee is composed of:

base fee (determined by the parameters set at the moment of pool creation);
dynamic fee (this is the part that adjusts).
The total fee is capped, so no matter how high volatility gets, swappers won’t pay more than the maximum fee.

The point of this system is to protect CLMM liquidity providers. When volatility increases, there is a higher risk that the price will exit the range and the provider will stop earning fees. By increasing the fees during high volatility, we make sure that they at least earn more on each swap, so that the risk is partly compensated for.

ECONIA - Order Book - Limit/market order | Uniswap - CLMM| AMM | LiquidSwap - CLMM - Joe Traders's - pool within a pool

Aptos: ECONIA - Order Book Vs LiquidSwap - CLMM - Joe Traders's - pool within a pool

common: zero slippage
integrations = good
Arbitrage = find arbitrage

How we can utilize them in WG1708|USDC
