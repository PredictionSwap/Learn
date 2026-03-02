# Why Is Polymarket Centralised?

## Introduction

Polymarket settles trades on-chain but centralises its trading layer.

---

### What This Centralisation Achieves

This centralisation solves four structural issues:

- Complement reconciliation across YES and NO tokens  
- Capital-efficient liquidity projection  
- Continuous limit order management  
- Gasless market order execution  

In this article, we explore why these issues arise and why they require coordination above the settlement layer.

---

## A Simple Binary Market

### The Core Primitive

Consider a market:

> **Will Event X happen?**

On Polymarket, **$1 can be split into two tokens:**

- 1 YES  
- 1 NO  

Together they equal **$1**.

---

### Settlement Logic

At resolution:

- YES pays $1  if the event happens, otherwise $0
- NO pays $1  if the event does not happen, otherwise $0

YES and NO are separate tokens.

---

## Four On-Chain Trade Directions

### Mechanical Distinction

Because YES and NO are separate tokens, there are four discrete on-chain trades:

- Buy YES  
- Sell YES  
- Buy NO  
- Sell NO  

These are mechanically distinct.

---

### Economic Overlap

However:

- **Buy YES for _c_** is economically equivalent to **Sell NO for _1 − c_**  
- **Buy NO for _c_** is economically equivalent to **Sell YES for _1 − c_**

Why?

---

## Trade Equivalence

### Starting Portfolio

Start with the portfolio:

<table>
  <thead>
    <tr>
      <th style="width: 220px;">Stage</th>
      <th>Cash</th>
      <th>YES</th>
      <th>NO</th>
      <th>Payout if YES Happens</th>
      <th>Payout if NO Happens</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Initial</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <td>Buy 1 YES for <em>c</em></td>
      <td>1 − c</td>
      <td>2</td>
      <td>1</td>
      <td>3 − c</td>
      <td>2 − c</td>
    </tr>
    <tr>
      <td>Sell 1 NO for <em>1 − c</em></td>
      <td>2 − c</td>
      <td>1</td>
      <td>0</td>
      <td>3 − c</td>
      <td>2 − c</td>
    </tr>
  </tbody>
</table>

---

### Identical Economic Outcome

Both trades produce **identical final payoffs**.

Buying YES for _c_ is economically equivalent to selling NO for _1 − c_.

But they are expressed as trades in different tokens.

That difference matters for matching.

---

## 1. Complement Reconciliation

### The Matching Problem

A naïve token-based orderbook matches identical instruments:

- Buy YES matches Sell YES  
- Buy NO matches Sell NO  

But economic exposure crosses token boundaries.

> **Buy YES at price _c_**  
> **Sell NO at price _1 − c_**

As shown above, these represent the same economic change.

---

### Why This Requires Coordination

Matching therefore requires recognising this symmetry and translating price and direction.

Currently, there is **no on-chain implementation** of this complement reconciliation.

Polymarket’s CLOB performs both matching and exposure normalisation **off-chain**.

---

## 2. Liquidity Projection

### Conditional Liquidity

A market maker with $100 can place limit orders across many binary markets simultaneously, thus supporting far more than $100 of quoted liquidity.

These orders are conditional.

Capital is only consumed if an order is filled.

Until execution, they are signed commitments.

---

### Solvency at Match Time

This allows liquidity to be expressed across multiple markets at once, with solvency enforced at the moment of match.

---

## 3. Gasless Limit Order Management

### Off-Chain Order Lifecycle

Limit orders are signed messages stored off-chain.

They can be:

- Placed  
- Modified  
- Cancelled  

Without sending a transaction.

---

### Execution Boundary

Only executed trades are submitted on-chain.

This enables continuous quoting and active repricing.

---

## 4. Gasless Market Order Execution

### Immediate Matching

Market orders are also submitted gaslessly.

The matching engine pairs them against resting liquidity immediately.

---

### On-Chain Settlement

The resulting trade is then settled on-chain.

---

## Summary

Polymarket’s off-chain trading layer instantiates four capabilities:

- Complement reconciliation  
- Liquidity projection  
- Gasless limit order management  
- Gasless market order execution  

Polymarket achieves these capabilities through **centralised coordination**.

PredictionSwap decentralises them by adjusting the **on-chain representation of state and exposure**.

---