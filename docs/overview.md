# PredictionSwap  

## The Problem

Prediction markets today are built as vertically integrated platforms.

Settlement may be on-chain, but live trading still relies on off-chain centralisation because on-chain designs fragment liquidity:

- Economically identical actions become different transactions  
- Economically identical positions become different token states  
- Capital gets trapped in representations  
- Deep liquidity requires pre-funded inventory  

### Read
- [Why Is Polymarket Centralised?](./Centralisation.md)  
- [Additional Structural Inefficiencies in Polymarket](./Inefficiencies.md)  

---

## The Shift

PredictionSwap changes what the system records.

Traditional systems: token balances first, economics inferred.  
PredictionSwap: **exposure first**, recorded directly as on-chain state.

When exposure is the primitive:

- Equivalent transactions collapse into the same state update  
- Equivalent positions collapse into the same representation  
- Netting happens automatically at the ledger level  
- Execution no longer depends on holding the “right” token inventory  

### Read
- [Exposure Execution](./ExposureExecution.md)  
- [Why Intents Are Simpler](./SimplifiedIntents.md)  

---

## What This Unlocks

Once execution is expressed as exposure updates rather than inventory swaps:

- Liquidity no longer requires pools of outcome tokens  
- A single capital base can support many markets  
- Execution systems can compete against the same shared market state  
- New market-making designs become possible  

### Read
- [Open Prediction Markets: A New Landscape](./NewLandscape.md)  
- [ZAMMs: Automated Market Makers Without Pools](./ZAMMs.md)  

---

## About This Archive

This site is a curated set of conceptual articles explaining the structural foundations of PredictionSwap.  

For the full narrative in one document:

- [PredictionSwap Protocol Litepaper (PDF)](./assets/litepaper.pdf)