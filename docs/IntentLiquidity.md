# Intent-Based Liquidity

## Introduction

PredictionSwap removes the token inventory requirement from trade execution. This means liquidity can be expressed directly as exposure delta intents.

This dramatically simplifies matching and filling intents.

---

## Clearing Intents

Once intents exist, trades can clear in two ways.


### Market Taking

#### Example:

##### Alice publishes an intent:

```
Buy 3 YES @ 0.42
```

##### Bob wishes to trade immediately and executes against Alice’s intent:

```
Sell 3 YES @ 0.42
```

##### The exposure and cash changes applied to the ledger are:

```
Alice
+3 YES
-1.26 USD
```

```
Bob
-3 YES
+1.26 USD
```

This is equivalent to taking liquidity from an orderbook.

--- 


### Coincidence of Wants

Intents can also be batched and executed by a matcher.

The matcher does not require any assets or a flash loan.

The trades execute atomically, and the ledger applies the resulting exposure and cash updates directly.


#### Example:

##### Alice publishes an intent:

```
Buy 3 YES @ 0.42
```

##### Bob publishes an intent:

```
Sell 3 YES @ 0.40
```

These intents overlap in price.

##### Mike executes the match:

```
Alice buys 3 YES from Mike @ 0.42
Mike buys 3 YES from Bob @ 0.40
```

##### The exposure and cash changes applied to the ledger are:

```
Alice
+3 YES
-1.26 USD
```

```
Bob
-3 YES
+1.20 USD
```

###### Mike captures the spread between the two prices.

```
Mike
0 YES
+0.06 USD
```


**No capital, tokens, exposure or inventory is required for Mike to perform this match.**

The atomic trade is netted automatically in the ledger and Mike captures the spread.

---

## Gasless Trading

### Limit Orders

Limit orders are published as intents and can be created gaslessly.

### Market Buys

If a participant wishes to execute a market trade gaslessly, they simply publish an intent that slightly crosses the spread.

This creates an immediate opportunity for a matcher to execute the trade and capture the spread.


## Matching Simplicity

### Token Routing

In traditional decentralised matching systems, trades must determine how tokens move between participants.

Execution may require:

- transferring tokens between traders  
- routing through liquidity pools  
- multi-hop swaps between assets  

Matching therefore becomes a token routing and optimisation problem.

### Exposure Settlement

PredictionSwap does not require any token routing.

Trades simply apply equal and opposite exposure updates to the ledger.

Matching only needs to determine whether the exposure changes cancel out.

If they do, the trade can execute.

---


## Decentralised Liquidty

### Orderbooks emerge naturally
Participants publish intents describing the exposure they are willing to take and the price they are willing to accept. These intents sit in the system like limit orders.

### Simplified matching
Matchers scan for overlaps and clear them, capturing the spread between prices. Because execution only requires applying exposure updates, matchers do not need to supply capital or route tokens.

### Liquidity As Intents
Liquidity therefore organises itself as a network of gasless intents, with matchers continuously clearing opportunities as they appear.
