# Prediction Markets Are Core DeFi Infrastructure

## DeFi Is About Trading Risk

At its core, DeFi is a system for trading **financial risk**.

Different protocols allow users to take on or transfer different types of risk.

For example:

- lending protocols manage **collateral risk**
- perpetual futures markets trade **price exposure**
- options markets trade **contracts whose payout depends on future prices**

Each of these systems creates financial positions whose value depends on **future outcomes**.

In other words, DeFi is already a system for **trading uncertainty about the future**.

---

## Prediction Markets Trade Outcomes Directly

Prediction markets approach this problem differently.

Instead of creating financial contracts that indirectly depend on future outcomes, prediction markets trade **conditional claims**.

A conditional claim is simple:

- if a specific event happens → the claim pays  
- if the event does not happen → it does not pay

Examples of events could include:

- ETH settles above $3000 at the end of the month  
- BTC price falls below $40,000  
- a specific election outcome occurs  

Each market creates assets that correspond directly to these outcomes.

---

## Conditional Claims Are Financial Building Blocks

Once conditional claims exist, they can be combined to create many other financial structures.

Traditional finance already uses similar ideas.

Many financial products are simply combinations of payouts that occur in different states of the world.

For example:

- some contracts pay only if an asset price rises above a threshold  
- others pay if a borrower defaults  
- others pay if a market falls below a certain level

All of these are examples of **state-dependent payouts**.

Prediction markets provide a direct way to create and trade these payouts.

---

## DeFi Currently Lacks a General Market for Conditional Claims

Despite the growth of DeFi, most protocols do not operate using conditional claims.

Instead they rely on other mechanisms.

For example, lending protocols protect lenders by:

- requiring excess collateral
- monitoring collateral prices
- liquidating positions if collateral becomes insufficient

This system works, but it requires **continuous monitoring and liquidation** to manage risk.

In many cases these mechanisms exist because the system does not have a simple way to trade the underlying conditional risk directly.

---

## What Happens When Conditional Markets Exist

If conditional claims can be created and traded easily on-chain, new types of financial structures become possible.

Protocols could manage risk by purchasing conditional claims that pay in specific states of the world.

Instead of reacting to price movements after they occur, a protocol could **structure its risk exposure at the moment a position is created**.

This changes how certain financial products can be designed.

---

## Example: Loans Without Liquidations

One example of this idea is a lending system where loans settle at a fixed maturity date rather than relying on liquidation.

When a loan is issued, the protocol could purchase conditional claims that pay in the relevant downside scenarios.

These claims would ensure that the protocol always has sufficient assets to satisfy lender obligations at maturity.

In this structure:

- the borrower receives funds today  
- the borrower repays a fixed amount at maturity  
- the system does not require continuous liquidation

Instead, the protocol holds positions that pay the required assets in the appropriate future states.

*(A detailed explanation of this mechanism is described in the technical note “Loans Without Liquidations”.)*

---

## Prediction Markets as Financial Infrastructure

Prediction markets are often viewed primarily as tools for forecasting.

But they also provide something more fundamental: **markets for conditional financial claims**.

These claims can act as building blocks for other financial products.

Just as automated market makers provide liquidity infrastructure for trading tokens, prediction markets can provide infrastructure for trading **future outcomes**.

---

## The PredictionSwap Thesis

PredictionSwap is designed to make conditional claims composable within on-chain transactions.

This allows protocols to create and trade state-dependent payouts directly inside financial operations.

In this view, prediction markets are not only forecasting tools.

They are a foundational layer of financial infrastructure that allows DeFi systems to price and transfer risk in a more direct way. 