# PredictionSwap  

## The Problem

Prediction markets today are built as vertically integrated platforms.

Settlement may be on-chain, but live trading still relies on off-chain centralisation.

This centralisation is to addresses the inefficiencies of on-chain representation which fragments liquidity.

### On-Chain Inefficiencies

- Economically identical actions are different transactions  
- Economically identical positions are different token states  
- Capital gets trapped in representations  
- Deep liquidity requires pre-funded inventory  

### Read
- [Why Is Polymarket Centralised?](./Centralisation.md)  
- [Additional Structural Inefficiencies in Polymarket](./Inefficiencies.md)  

---

## The Shift

PredictionSwap changes the on-chain state representation.

Traditional systems record token balances first and from them build exposure.  
PredictionSwap records **exposure first** and builds token balances from exposure.

### When exposure is the primitive

- Equivalent transactions collapse into the same state update  
- Equivalent positions collapse into the same representation  
- Netting happens automatically at the ledger level  
- Execution no longer depends on holding the “right” token inventory  

### Read
- [Better Execution](./ExposureExecution.md)  
- [Why Intents Are Simpler](./SimplifiedIntents.md)  

---

## What This Unlocks

There is a cascade of positive benefits from having a more efficient on-chain representation. 

### When exposure is the primitive

- Liquidity no longer requires pools of outcome tokens  
- A single capital base can support many markets  
- Execution systems can compete against the same shared market state  
- New market-making designs become possible  

### Read
- [Open Prediction Markets: A New Landscape](./NewLandscape.md)  
- [ZAMMs: Automated Market Makers Without Pools](./ZAMMs.md)  

---

## About Foundational Docs

This site is a curated set of conceptual articles explaining the structural foundations of PredictionSwap.  

For the full narrative in one document:

- [PredictionSwap Protocol Litepaper (PDF)](./assets/litepaper.pdf)

---
