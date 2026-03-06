# What Is A Trade?

## Introduction

### What is a trade?

#### Traditional Representation
In traditional on-chain prediction markets, a trade is defined as an exchange of tokens. One participant sends cash, the other sends specific outcome tokens. Execution depends on both parties holding the correct inventory in the correct representation.

Under that definition, many economically valid trades fail. Not because they are unsound, but because one side does not hold the required tokens, or because the trade would require intermediate transformations or flash loans to complete. 

Valid trades are defined by representation.

---

#### PredictionSwap Representation
PredictionSwap adopts a different definition.

A trade is not an asset swap.
A trade is a pair of equal and opposite changes to the Conditional Account Value Vectors of two accounts.

Execution depends only on the resulting economic state. If both participants remain solvent in every possible outcome, the trade is valid and executes.

The examples below illustrate the difference between defining a trade as a token exchange and defining a trade as a state transition.

---

## A Simple Structural Example

Consider a mutually exclusive outcome market:

\[
\Omega = \{R, G, B\}
\]

---

## Example 1

### Traditional Systems

Alice holds:

- \$10 only

Bob holds:

- \(5\,\text{YES–R}\) tokens  

Alice wants to buy \(2\,\text{YES–R}\) at price \(0.6\).

- Alice sends \$1.2  
- Bob sends \(2\,\text{YES–R}\)

---

#### After Trade

Alice:

- \$8.8  
- \(2\,\text{YES–R}\)

Bob:

- \$1.2  
- \(3\,\text{YES–R}\)

Execution succeeds, both participants have the correct tokens for the trade.

---

### Account Value Accounting

#### Step 1 — Translate Holdings to Conditional Account Value Vectors

Initial:

We translate all holdings Alice and Bob have into Conditional Account Value Vectors.

\[
e = (e_R, e_G, e_B)
\]

\(e_k\) tells us how much money the user has if outcome \(k\) happens.

Alice has \$10:

\[
e_A = (10,10,10)
\]

Bob has \(5\,\text{YES–R}\) tokens:

\[
e_B = (5,0,0)
\]

---

#### Step 2 — Translate the Trade into an Account Value \(\Delta\)

Alice wants to buy \(2\,\text{YES–R}\) at price \(0.6\).

Translation:

\[
2\,\text{YES–R} \rightarrow (+2,0,0)
\]

\[
\text{Pay }0.6 \rightarrow (-0.6,-0.6,-0.6)
\]

Combined vector change in account value:

\[
\Delta e = (+1.4,-0.6,-0.6)
\]

Bob agrees to take the opposite vector change:

\[
-\Delta e
\]

---

#### Step 3 — Apply Equal and Opposite Updates

Alice:

\[
e_A \rightarrow e_A + \Delta e
\]

\[
(10,10,10) + (+1.4,-0.6,-0.6)
= (11.4,9.4,9.4)
\]

Bob:

\[
e_B \rightarrow e_B - \Delta e
\]

\[
(5,0,0) - (+1.4,-0.6,-0.6)
= (3.6,0.6,0.6)
\]

The trade executes because both accounts still have positive account values in every possible world.
---

## Example 2 — Trade That Fails Under Traditional Token Holdings

### Traditional Model

Now suppose:

Alice holds:
- \$10  

Bob holds:
- \(5\,\text{NO–G}\) tokens  

Alice wants to buy \(2\,\text{YES–R}\) from Bob for \$0.6.

Bob has no \(\text{YES–R}\) to sell.

Therefore the trade fails.

---

### Account Value Model

Alice holds:
- \$10  

\[
e_A = (10,10,10)
\]

Bob holds:
- \(5\,\text{NO–G}\) tokens  

\[
e_B = (5,0,5)
\]

(Bob has \$5 if either \(R\) or \(B\) happens.)

---

#### Step 1 — Translate the Trade into a Vector Change \(\Delta\)

As before Alice wants to buy \(2\,\text{YES–R}\) for \$0.6.

Recap:

\[
2\,\text{YES–R} \rightarrow (+2,0,0)
\]

\[
\text{Pay }0.6 \rightarrow (-0.6,-0.6,-0.6)
\]

Combined vector change:

\[
\Delta e = (+1.4,-0.6,-0.6)
\]

Bob agrees to take the opposite vector change:

\[
-\Delta e
\]

---

#### Step 2 — Apply Equal and Opposite Updates

Alice:

\[
e_A \rightarrow e_A + \Delta e
\]

\[
(10,10,10) + (+1.4,-0.6,-0.6)
= (11.4,9.4,9.4)
\]

Bob:

\[
e_B \rightarrow e_B - \Delta e
\]

\[
(5,0,5) - (+1.4,-0.6,-0.6)
= (3.6,0.6,5.6)
\]

The trade executes because both accounts still have positive account values in every possible world.


---

## Structural Difference

### Traditional model

- Requires specific asset inventory  
- Trades may fail due to token representation  

### Account value model

- Updates payoff vectors directly  
- Trades depend only on economic capacity  
- Representation does not constrain execution  

---

## Significance

### Liquidity without inventory

Because trades are expressed directly as vector changes Δe, execution updates payoff vectors symmetrically:

\[
e_A \rightarrow e_A + \Delta e
\]

\[
e_B \rightarrow e_B - \Delta e
\]

Trading redistributes Conditional Account Value between participants.

The trade executes if and only if the resulting Conditional Account Value Vectors remain solvent:

\[
e_{A,k} > 0
\quad\text{and}\quad
e_{B,k} > 0
\quad
\forall k \in \Omega
\]

Liquidity therefore becomes a rule over admissible conditional account value vector changes, rather than a pool of pre-allocated tokens.

---

### Intents simplify

An intent specifies:

- A desired account value vector change \(\Delta e\)  

Matching simply requires pairing with

- A corresponding vector change \( - \Delta e\)

---

### New Automatic Market Makers

A new powerful class of Zero Sum Automatic Market Makers becomes possible as liquidity providers no longer manage pools of YES and NO tokens.

ZAMMs simply decide whether to accept a proposed change in account value vector \(\Delta e\).

---