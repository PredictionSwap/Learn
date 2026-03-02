# Simplified Intents

## Old Model

### Two Trade Primitives

In the traditional token-based model, there are two distinct trade primitives:

- YES trade
- NO trade

Each primitive has two sides:

- Buy
- Sell

This produces four transaction paths in total.

The YES and NO trades are mechanically distinct.
They are treated as separate execution flows.

Matching must determine which primitive is being used.

---

## New Model
### One Trade Primitive

In PredictionSwap, there is only one trade primitive.

Every trade is a single bet with two sides:

- One participant takes the YES side.
- The other participant takes the NO side.

There are not separate YES and NO trades.
There is only one trade with two opposing sides.

---

## Token Requirements

### Old Model

Each trade primitive has two sides:

- One side sends cash.
- The other side sends tokens.

#### Yes Trade Token Requirements

- If a participant buys YES, they must hold dollars.  
- If a participant sells YES, they must hold YES tokens.

#### No Trade Token Requirements

- If a participant buys NO, they must hold dollars.  
- If a participant sells NO, they must hold NO tokens.


#### Summary
Execution therefore depends on holding the correct asset for the chosen pathway.

The trade functions like a traditional asset swap:
cash on one side, tokens on the other.

---

### New Model

In PredictionSwap two participants agree to equal and opposite changes in exposure.

#### Exposure Requirements

- No specific token inventory is required.
- Each participant must have sufficient economic headroom to absorb the proposed exposure change.
- After applying the exposure update, both accounts must remain solvent.

#### Summary

Execution depends only on post-trade solvency.

The trade functions as a direct exposure update:
equal and opposite exposure changes applied simultaneously.

---


## Why Intents Are Simplified

### In the traditional  model:

- Trades are executed as asset swaps.
- One side must hold cash.
- The other side must hold the specific token being sold.
- An order can fail simply because the required token inventory is not present.

---


### In the new model:

- Trades are exposure updates.
- Both sides take equal and opposite changes in exposure.
- Execution depends only on both participants having sufficient economic headroom.
- There is no requirement to pre-hold YES, NO, or cash.

---

### As a result:

- Intent matching no longer depends on token inventory.
- An intent only needs to specify which side of the exposure change the participant wants.
- Execution succeeds whenever both sides can absorb the exposure.

The simplification comes from removing inventory constraints and reducing trades to symmetric exposure changes.

---
