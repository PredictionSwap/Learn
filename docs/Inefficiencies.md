# Structural Inefficiencies in Prediction Markets

<div style="font-size: 1.25rem; font-weight: 600; margin-top: -0.5rem;">
The Representational Duplication Problem
</div>

---

## Introduction

In addition to the structural inefficiencies in on-chain prediction market systems that are mitigated through centralisation (see [Why Is Polymarket Centralised?](./Centralisation.md)), there is a further inefficiency that remains unresolved in current designs.

PredictionSwap addresses this directly at the protocol level.


## 1. Yes/No Markets as the Primitive

### Binary as the Base Unit

Polymarket represents events using binary markets.

Every market is framed as:

- YES
- NO

This binary structure is the foundational primitive.

Even when an event has multiple mutually exclusive outcomes, it is decomposed into separate yes/no questions.

---

### Decomposition of a Multi-Outcome Event

Suppose exactly one of three outcomes can occur:

- Red wins  
- Green wins  
- Blue wins  

Rather than representing this as a single three-outcome market, it is split into three independent binary markets:

- “Red wins?” → YES–Red / NO–Red  
- “Green wins?” → YES–Green / NO–Green  
- “Blue wins?” → YES–Blue / NO–Blue  

Each market has its own pair of tokens.  
Each pair trades independently in its own orderbook.

---

## 2. The Meaning of “NO–Red”

### Economic Interpretation

In a three-outcome world, “not Red” means either Green or Blue.

Economically:

> Holding NO–Red is exposure to (Green ∪ Blue).

---

### Mechanical Reality

Mechanically, NO–Red is simply a token in the Red market.

It cannot automatically function inside the Green or Blue markets, even though its economic meaning spans the same outcome space.

This gap between economic meaning and token representation is the source of structural inefficiency.

---

## 3. The NegRisk Adapter

### What It Does

Polymarket introduces the **NegRisk adapter** to allow users to convert between certain economically equivalent positions.

For example:

A user holding NO–Red can call `convertPositions` to transform that exposure into the corresponding YES–Green and YES–Blue positions.

This conversion is:

- Explicit  
- User-initiated  

It allows a position’s representation to be reshaped.

---

### What It Does Not Do

The orderbook does **not** treat economically equivalent exposures as interchangeable.

It continues to match specific tokens against specific tokens.

The NegRisk adapter allows representation to change.

It does **not** remove the structural separation between markets.

---

## 4. Fragmented Liquidity

### Capital Exists in One Form at a Time

Suppose you hold a large amount of NO–Red.

Economically, that position corresponds to exposure to Green and Blue.

In principle, that capital could support liquidity in:

- The Red market (as NO–Red)  
- The Green market  
- The Blue market  

But in practice, it can only exist in **one token form at a time**.

- If it sits as NO–Red, it supports the Red market.  
- If it is converted into YES–Green and YES–Blue, it leaves the Red market.  

Capital must choose a market context.

It cannot simultaneously reinforce all economically equivalent markets.

---

## 5. The Structural Consequence

### Representational Duplication

Because exposure is encoded separately in each yes/no market, economically equivalent positions exist in multiple representations.

Liquidity becomes distributed across token forms that describe the same underlying outcome space.

This is the **representational duplication problem**.

Economically unified exposure becomes mechanically fragmented.