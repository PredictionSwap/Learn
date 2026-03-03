# Representation Of State

## Introduction

### PredictionSwap changes how economic state is recorded on-chain.

Traditional prediction markets record token balances first and economic exposure is then derived from those balances.  

PredictionSwap records economic exposure directly.

---

## The Traditional Representation

### An account’s state is defined by asset balances:

- Cash balance  
- YES tokens  
- NO tokens  

State is a collection of token quantities.

The same economic exposure can arrise from different collections of tokens.

---

## The Exposure Vector Representation

### An account state is defined by a single object:

\[
e = (e_1, e_2, \dots, e_n)
\]

Where:

- \( e_k \) represents the account’s value if outcome \( k \) occurs.

This vector is the account’s complete economic state.

---

## What is an Exposure Vector?

### A payoff function defined over outcome space.

For an event with outcomes:

\[
\Omega = \{ \omega_1, \omega_2, \dots, \omega_n \}
\]

an exposure vector

\[
e = (e_1, e_2, \dots, e_n)
\]

specifies the value of an account in each possible outcome.

Each component \( e_k \) is the account’s value if outcome \( \omega_k \) occurs.

The exposure vectorfully describes economic state.

### An Example
Consider a mutually exclusive outcome space:

\[
\Omega = \{R, G, B\}
\]

Exactly one of these outcomes will occur.

We consider how we represent a positon for Alice within this market under the traditional representation and under a PredictionSwap representation.

---

### Traditional Representation
#### Tokens as the Primitive

- **YES–R** pays \$1 if \( R \) occurs, otherwise \$0  
- **YES–G** pays \$1 if \( G \) occurs, otherwise \$0  
- **NO–G** pays \$1 if \( G \) does not occur (i.e. if \( R \) or \( B \) occurs)

##### Alice holds:

- 3 YES–R  
- 6 NO–G  
- 1 YES–G  
- \$10 cash  

---

#### Payoffs by Outcome

##### If \( R \) occurs:

- \$10  
- +3 from YES–R  
- +6 from NO–G  

###### Total: \$19  

##### If \( G \) occurs:

- \$10  
- +1 from YES–G  

###### Total: \$11  

##### If \( B \) occurs:

- \$10  
- +6 from NO–G  

###### Total: \$16  

---

#### Economic State

##### Alice’s economic state is therefore:

\[
e = (19, 11, 16)
\]

This vector completely describes her economic position.

---

### Exposure Representation

#### PredictionSwap stores:

\[
e = (19, 11, 16)
\]

This is the full unique description of Alice’s position.

---