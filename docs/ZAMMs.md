# ZAMMs: Automated Market Makers Without Pools  

## Zero-Sum Automated Market Makers  

Under PredictionSwap, market makers no longer need to manage pools of outcome tokens or manually split, merge, allocate, and deallocate funds to specific markets.

There are no per-market inventory buckets to maintain.

Each trade only requires that both parties have sufficient economic headroom to take on the resulting change in position.

Within this structure, a new type of market maker becomes possible.

These are **Zero-Sum Automated Market Makers**, or **ZAMMs**.

---

## 1. What a ZAMM Is  

### Core Mechanism  

A ZAMM is a contract that decides whether to accept a proposed trade.

When a trader submits a position change, the ZAMM evaluates it according to its own internal rules.

- If it accepts the trade, the protocol executes it.  
- If it rejects the trade, nothing happens.  

That is the entire mechanism.

### What a ZAMM Does *Not* Do  

A ZAMM:

- Does **not** manage settlement  
- Does **not** manage collateral  
- Does **not** maintain pools per market  

It simply defines which position changes it is willing to take the other side of.

Liquidity becomes a rule over admissible trades.

---

## 2. A Broader Class of Market Maker  

### Traditional AMMs as Special Cases  

Traditional automated market makers can be understood as specific examples of this structure.

- An **LMSR** market maker defines a pricing function.  
- A **constant-product AMM** defines an invariant curve.  

Both determine which trades are allowed and at what price.

Under PredictionSwap, these can be implemented as ZAMMs.

### Beyond Fixed Curves  

But ZAMMs are **not** restricted to fixed curves or symmetric rules.

There is no requirement that liquidity:

- Be symmetric  
- Be reversible  
- Follow a static formula  
- Operate identically in both directions  

---

## 3. Liquidity as Acceptance Rules  

Because the protocol handles netting and collateral automatically, a ZAMM is free to define its own acceptance rules.

### What This Enables  

It can:

- Provide broad two-sided liquidity  
- Concentrate liquidity in specific regions  
- Operate only in one direction  
- Accumulate exposure gradually  
- Adjust behaviour over time  
- React to external information  
- Hedge prices in one market with those in another  
- Target a specific portfolio configuration  

Liquidity is no longer tied to a pool.

It is defined by what position changes the ZAMM is willing to accept.

---

## 4. One ZAMM, Many Markets  

### No Per-Market Pools  

Traditional AMMs require separate pools per market.

A ZAMM does not.

A single ZAMM can provide liquidity across many markets simultaneously using one unified capital base.

It does not need to:

- Pre-allocate inventory per event  
- Open separate pools for each outcome  

### Structural Consequence  

It can quote across thousands of independently resolving zero-sum markets without fragmenting capital.

This is a significant structural difference to existing systems.

---

## 5. Composite ZAMMs  

### Modular Liquidity Policies  

A **Composite ZAMM** is a single capital base that runs multiple liquidity modules.

Each module defines its own rules for which trades it is willing to accept.

For example:

- One module may operate only in election markets.  
- Another may focus on macroeconomic events.  
- Another may provide liquidity only in extreme outcome ranges.  

Each module evaluates trades independently according to its own policy.

### Unified Capital  

But all accepted trades draw from the same underlying capital.

- There are no separate pools to divide.  
- No inventory needs to be pre-allocated per market.  

Different liquidity policies operate across different markets or outcome regions, while sharing one unified pool of funds.

Capital remains unified.

---

## Conclusion  

### The Structural Shift  

ZAMMs generalise automated market making.

They include traditional AMMs, but also allow entirely new types of liquidity engines.

The key shift is simple:

- Liquidity is no longer bound to pools.  
- It is no longer confined to a single market.  
- It is no longer restricted to symmetric curves.  

It becomes programmable.