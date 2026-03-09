# Loans Without Liquidations

## A Different Kind of DeFi Loan

Most DeFi loans rely on **over-collateralisation and liquidation**.

Borrowers must maintain a collateral buffer above a threshold. If the collateral price falls too far, the position is liquidated and the collateral is sold to repay lenders.

This model protects lenders, but it creates well-known problems:

- forced selling during market stress  
- liquidation cascades  
- loans whose effective terms change continuously as prices move  

But there is another way to structure lending.

Instead of managing collateral risk through liquidations, the risk can be **priced and transferred to a market at the moment the loan is issued**.

This makes it possible to build **fixed-term loans with no liquidation risk**.

---

## Hedging the Loan at the Moment It Is Created

The key idea is **atomic hedging**.

When a loan is issued, the protocol simultaneously buys prediction market positions covering the range of collateral price outcomes that would normally trigger liquidation.

Because both operations occur in the same transaction, the cost of the hedge can be included directly in the loan pricing.

The borrower therefore pays interest on:

- the borrowed amount  
- plus the cost of the hedge that protects lenders from collateral price crashes  

From the borrower’s perspective the loan behaves like a **traditional fixed-term credit instrument**.

There is no liquidation threshold to monitor and no risk of forced collateral sales during the loan.

---

## What Happens if Prices Collapse?

If the collateral price falls below the level that would normally trigger liquidation, the prediction market position pays out.

That payout covers the lender’s exposure.

The collateral itself is **not sold**. It simply remains locked in the protocol until the loan matures.

At maturity the borrower can:

- repay the loan and reclaim the collateral  
- or walk away, allowing the protocol to retain it  

The lender is protected either way.

In effect, **collateral crash risk has been sold to the prediction market**.

---

## A Shift in Where Risk Lives

This structure changes the role of the lending protocol.

In traditional DeFi lending systems the protocol must manage collateral risk itself through:

- liquidation thresholds  
- oracle feeds  
- collateral whitelists  
- conservative risk parameters  

In the hedged model the protocol does not manage that risk.

Instead, the downside exposure is **sold to counterparties in prediction markets** at the moment the loan is created.

As long as a prediction market exists for the asset’s price distribution over the loan horizon, the protocol can hedge the relevant outcomes immediately.

This means almost **any asset with a tradable price distribution could theoretically be used as collateral**.

---

## Oracle and Market Microstructure Risk

This approach also changes who bears operational risk.

In existing lending systems the borrower absorbs many types of market-structure risk:

- delayed oracle updates  
- flash crashes  
- temporary market dislocations  

These events can trigger liquidations even if the underlying price later recovers.

In the hedged model those risks are transferred to the prediction market.

If a flash crash or oracle anomaly pushes the collateral price through the liquidation threshold, the prediction market payout covers the lender’s exposure.

The lending protocol itself remains neutral.

---

## Why This Doesn’t Exist Yet

The reason this type of product has not appeared in DeFi is not economic.

It is **architectural**.

For atomic hedging to work, the prediction market trade must execute in the **same transaction** that creates the loan. The system must know the exact hedge price before issuing the loan.

Today’s prediction markets cannot provide this guarantee.

Most platforms rely on **centralised trade execution**, even when settlement happens on-chain. Orders are matched inside platform-controlled order books or off-chain matching engines.

Because of this, other protocols cannot deterministically execute prediction trades as part of their own transactions.

Without atomic execution, the hedge cannot be reliably priced at the moment the loan is issued.

---

## PredictionSwap

PredictionSwap removes the structural inefficiencies that force prediction markets to rely on centralised execution.

Trading can therefore occur **fully on-chain and atomically**.

Once prediction markets become composable infrastructure rather than standalone platforms, they can be embedded directly into financial products.

Fixed-term loans without liquidation risk are one example of what becomes possible.

For more detail on the structural issues that prevent existing prediction markets from operating this way see:

- [Why Is Polymarket Centralised?](./Centralisation.md)  
- [Additional Structural Inefficiencies in Polymarket](./Inefficiencies.md)