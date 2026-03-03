# Position Tokens

## Preliminaries

This document builds on [Representation Of State](./Representation.md).

PredictionSwap records economic state directly as an exposure vector.  
Position tokens are views of that exposure.

This document describes how exposure maps to token balances.

---

## Uniform and Residual Exposure

### Outcome Space

Consider a mutually exclusive outcome space:

\[
\Omega = \{R, G, B\}
\]

Exactly one of these outcomes will occur.

---

### Exposure Decomposition

Given an exposure vector

\[
e = (e_R, e_G, e_B)
\]

it can be decomposed uniquely into:

\[
e = c(1,1,1) + r
\]

#### Where

- \( c = \min(e_R, e_G, e_B) \)  
- \( r = e - c(1,1,1) \)

By construction:

\[
\min(r_R, r_G, r_B) = 0
\]

---

### Interpretation

- The constant component \( c \) represents uniform exposure across all outcomes — this is **free cash**.  
- The residual vector \( r \) represents outcome-specific exposure — this is **shares**.  

This decomposition is unique.

---

## Example

### Starting Exposure

Alice's holdings are uniquely characterised by the exposure vector:

\[
e = (19, 11, 16)
\]

---

### Alice's Free Cash

\[
c = \min(19,11,16) = 11
\]

---

### Alice's Shares

\[
r = (19,11,16) - (11,11,11)
\]

\[
r = (8,0,5)
\]


---

## YES Tokens

### Definition

YES token balances correspond directly to the residual exposure, or shares Alice has in each outcome.

From:

\[
r = (8,0,5)
\]

### Token Balances

- YES–R = 8  
- YES–G = 0  
- YES–B = 5  

YES tokens are mutually exclusive.  
Each corresponds to exposure in exactly one outcome.

---

## NO Tokens

### Definition

A NO token corresponds to exposure in all outcomes except one.

For example:

- NO–G pays \$1 if either \( R \) or \( B \) occurs.

Economically, one NO–G is equivalent to:

- 1 unit of YES–R  
- 1 unit of YES–B  

---

### Applying to the Example

Alice has:

- YES–R = 8  
- YES–B = 5  

Since each NO–G requires one YES–R and one YES–B,  
she has:

- NO–G = 5  

NO tokens are overlapping views of exposure.  
They are combinations of YES tokens.

---

## Alice’s Token Balance

- YES–R = 8  
- YES–G = 0  
- YES–B = 5  

- (NO–G = 5)

---

## Interpretation

An exposure vector has a single canonical form.

YES tokens provide a unique decomposition of outcome-specific exposure.

NO tokens are derived overlapping views.
