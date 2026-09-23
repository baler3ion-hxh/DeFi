# 06 · DeFi Protocols & Trading

## Uniswap: a decentralized exchange (DEX)

Uniswap is a DEX protocol. It allows people to swap crypto tokens directly through smart contracts, without a centralized exchange matching buyers and sellers. It uses a **liquidity pool** protocol.

**Example: you have ETH and want USDC**

On a centralized exchange, you trade through an order book: you place an order to sell ETH, someone else buys it, and the exchange matches the orders.

On Uniswap, you usually interact with a liquidity pool. A pool contains two tokens, such as ETH and USDC. Users can swap one token for the other using the pool's smart contract. Liquidity providers may earn a portion of swap fees in exchange for supplying assets to the pool, subject to the pool's rules.

## Liquidity pool

A liquidity pool is a smart contract that holds two (or more) tokens and allows people to trade between them without a traditional order book.

*Example:* on Uniswap, the ETH/USDC liquidity pool contains both ETH and USDC. You can swap ETH for USDC directly from that pool.

**Who provides this liquidity?**
- Users called **Liquidity Providers (LPs)**.
- They deposit equal values of both tokens into the pool and earn fees from every trade.

**Why is it important?**
- It allows decentralized trading.
- More liquidity = lower slippage = a better trading experience.

## Automated Market Maker (AMM)

An algorithm with a 50:50 standard:

```
x × y = k
```

**Example: x = potatoes, y = apples**

We add 50k potatoes and 50k apples to the liquidity pool, so `k = 50k × 50k = 2.5 billion`. At the beginning, the price of both is the same (1:1).

A trader wants to swap 5k apples for potatoes:
- Apples in the pool: 50k + 5k = **55k**
- Potatoes left in the pool: 2.5 billion ÷ 55k ≈ **45,455**
- Potatoes the trader receives: 50k − 45,455 ≈ **4,545**

So he pays 5k apples for 4,545 potatoes. Because there are now more apples and fewer potatoes in the pool, **potatoes become more expensive and apples cheaper**:
- Potato price: 55k ÷ 45,455 ≈ **1.21 apples**
- Apple price: 45,455 ÷ 55k ≈ **0.83 potatoes**

## Slippage in a DEX

Slippage is the difference between the expected price of a trade and the actual price at which the trade is executed. It usually happens due to price movement between the time the transaction is submitted and when it's confirmed on-chain.

**Why slippage happens in DEXs**
- **Low liquidity**: not enough tokens in the pool to fill your trade at the expected price.
- **High volatility**: token prices change quickly ...between the time you confirm the transaction and when it's included in a block.
- **Large orders**: a big trade may shift the price because of how AMMs (like Uniswap or PancakeSwap) calculate prices using the constant product formula.

*Example:* you're trying to buy 1 ETH for $3,000, but due to slippage the final executed price is $3,050. That extra $50 is the result of slippage.

### Slippage tolerance

Most DEXs let you set a slippage tolerance, like 0.5%, 1%, or even 5%.
-  If the final price stays within your tolerance → the transaction goes through.
-  If the price moves too much beyond your tolerance → the transaction fails ("slippage too high").

## Volume vs. liquidity

**Volume** is the total amount of assets traded over a specific period, usually 24 hours.

*Example:* if 10,000 ETH are swapped for USDC in one day, the 24h volume for the ETH/USDC pair is 10,000 ETH (or its value in USD).

**Why it's important**
- Shows how active a market or token is.
- High volume = easier to trade in/out with minimal price impact.

| | Meaning |
|---|---|
| **Liquidity pool** | How much money is available for trading |
| **Volume** | How much money was traded recently |

## Market orders vs. limit orders

| Order type | How it works | Downside |
|---|---|---|
| **Market order** | A trade made now at the current price | It may not execute at the expected price because the price is changing, especially in low-volume markets |
| **Limit order** | You choose a price, and if the market touches it the trade is done | It may never happen if the market doesn't reach your price |

---

## Aave: lending and borrowing

Aave is a decentralized lending and borrowing protocol in DeFi. It allows users to:
- Deposit crypto and earn interest
- Borrow crypto by providing collateral
- Use smart contracts instead of a traditional bank

**Example: you want to borrow USDC**

Imagine you have ETH and need $1,000 in USDC, but you don't want to sell your ETH.

- Your collateral: $2,000 in ETH
- Your loan: $1,000 in USDC

You now have your ETH locked in Aave as collateral, $1,000 USDC in your wallet, and a debt of $1,000 USDC plus interest. You can use that USDC for other purposes without selling your ETH.

**How does Aave make this possible?** There are three main participants:

1. **Lenders**: deposit assets such as USDC or ETH into Aave's lending pools and can earn interest from borrowers.
2. **Borrowers**: supply collateral and borrow another asset. They pay interest.
3. **Smart contracts**: manage deposits, loans, interest, collateral, and liquidation according to programmed rules.

**What happens if the ETH price falls?**

If ETH falls to $1,200, your collateral is now worth only $1,200, while your debt is still approximately $1,000 plus interest.

Aave lets you borrow only up to a percentage of your collateral value (the exact percentage depends on the asset), so liquidation can start **before** the collateral falls to the value of the debt. In this example, your position could already be liquidated at $1,200.

When that happens, Aave can allow a liquidator to repay part of your debt and receive collateral at a liquidation bonus. This protects the lending pool from bad debt.

## Flash loans

A flash loan is a crypto loan that lets you borrow a large amount of assets without providing traditional collateral, as long as you repay the loan plus the required fee **within the same blockchain transaction**.

The key idea: **Borrow → Use the money → Repay → Transaction succeeds.**

If you cannot repay, the transaction reverts, so the flash loan does not complete.
