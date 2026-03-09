# Loans Without Liquidations

## The Current DeFi Lending Model

### Over-Collateralised Borrowing

DeFi loans require borrowers to post collateral worth significantly more than the amount borrowed.

This buffer exists so that if the price of the collateral falls, the protocol still has enough value locked in the system to repay lenders. The collateral therefore acts as the primary protection mechanism for the loan.

### System-Level Risk Management

Liquidations are not the only protection mechanism used by lending protocols.

Systems such as Aave also rely on a wider set of risk management tools and incentives, including:

- conservative collateralisation ratios  
- liquidation bonuses paid to liquidators  
- continuously updated price feeds from oracles  
- protocol reserves designed to absorb losses in extreme situations  
- supply caps
- borrowing limits 

Together, these mechanisms are designed to protect lenders even during volatile market conditions.

### A Loan That Changes With the Market

This architecture protects lenders through a combination of collateral buffers, liquidation incentives, and protocol reserves.

But it also means that DeFi loans do not behave like traditional fixed-term credit instruments. Borrowers must actively manage their positions to avoid liquidation, and the effective terms of the loan change continuously as market prices move.

What follows describes a different type of lending product entirely.

---

## Atomic Hedging

### Prediction Markets as Risk Infrastructure

Prediction markets can act as embedded hedging infrastructure rather than standalone betting platforms.

Consider a system where financial transactions can automatically hedge the price exposure they create, the exposure can be hedged at the same moment the position is created.

Atomic execution makes this possible. Because the transaction and the hedge occur in the same operation, the cost of the hedge can be included directly in the transaction price. The system simply executes the required prediction trades at the same time the financial position is opened.

The result is that price risk can be embedded directly into the structure of financial products, rather than managed separately.

---

## A New Lending Product

### Fixed-Term Loans Without Liquidations

This structure allows a new type of lending product: **fixed-term, fixed-rate loans with no liquidation risk.**

When the loan is issued, the protocol atomically purchases prediction market outcomes covering the range of collateral prices that would normally trigger liquidation during the loan term. The cost of this position is added to the amount being borrowed, and interest is charged on the combined figure.

If the liquidation event occurs during the term, the prediction market payout covers the loan amount owed to lenders.

The collateral itself is not liquidated. It remains locked in the protocol. At maturity the borrower can repay the loan plus interest to reclaim the collateral, or choose not to repay, in which case the protocol retains it.

In effect, the exposure to collateral price crashes is transferred to prediction markets and atomically priced into the loan when it is issued.

The loan itself behaves like a standard fixed-term credit instrument.

---

## A Consequence

### Collateral Risk Moves to the Market

One important consequence of this design is that the lending protocol no longer needs to manage the price risk of the collateral.

As long as a prediction market exists for the asset’s price distribution over the loan horizon, the protocol can hedge the relevant outcomes atomically at issuance.

In principle this means any asset with a tradable prediction market could be used as collateral, because the downside exposure is transferred to counterparties in the prediction market rather than borne by the lending system itself.

This is a significant shift from the current model, where protocols must carefully choose collateral assets and configure conservative risk parameters. And means there is no structural risk in the amount of any one asset which is used as collateral. 

---
### Oracle and Market Microstructure Risk Move to the Market

In existing DeFi lending systems the operational risks of the system are largely borne by the borrower.

Liquidations depend directly on oracle prices, which means events such as delayed oracle updates, flash crashes, or short-term market dislocations can trigger liquidations even if the underlying asset later recovers. When these events occur, the borrower absorbs the loss through forced collateral sales.

In traditional lending the situation is different: lenders typically bear this type of risk. If collateral prices move unexpectedly or markets become temporarily dislocated, the lender is exposed.

The hedged lending structure described above introduces a third model.

Instead of placing this risk on either the borrower or the lender, the risk exposure is sold to the prediction market at the moment the loan is issued. If a flash crash, oracle anomaly, or other market disruption causes the collateral price to cross the liquidation threshold, the prediction market payout covers the lender’s exposure.

---

## Why Existing Prediction Markets Can't Support This

### The Centralised Execution Problem

The main obstacle is that today’s prediction markets rely on centralised trade execution.

Even when positions are ultimately settled on-chain, trading itself typically happens off-chain inside a platform’s matching engine or order book. Because of this, other protocols cannot execute prediction trades as part of their own transactions.

Structures like the lending product described above require the hedge to be executed atomically with the financial transaction that creates the exposure. The loan and the hedge must occur in the same transaction so that the cost of the hedge can be deterministically incorporated into the loan pricing.

When trading occurs off-chain under the control of a platform, this is not possible. A protocol cannot guarantee that the required prediction position will execute at the moment the loan is issued, which prevents prediction markets from being embedded directly into financial products.

---

### The PredictionSwap Difference

The reason prediction platforms rely on centralised execution is that current underlying on-chain infrastrucutre is structurally inefficient to trade directly on-chain.

PredictionSwap removes these inefficiencies at the protocol layer, allowing so trading can therefore occur fully on-chain and atomically.

Once that constraint is removed, prediction markets can become composable financial infrastructure rather than standalone platforms. Products like fixed-term loans without liquidation risk can then be built directly on top.

For a deeper explanation of these structural inefficiencies see:

- [Why Is Polymarket Centralised?](./Centralisation.md)  
- [Additional Structural Inefficiencies in Polymarket](./Inefficiencies.md)  




