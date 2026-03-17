# Loans Without Liquidations

## The DeFi Lending Landscape

Most DeFi lending today is built around **open-ended borrowing positions** rather than fixed-term loans.

In systems such as Aave, a borrower deposits collateral and borrows against it. The position can remain open indefinitely as long as the collateral remains sufficient.

There is no fixed maturity date.

Instead, the protocol continuously monitors the value of the collateral.

If the collateral value falls too far, the protocol liquidates the position to protect lenders.

This architecture can be described as **Continuous Liquidation Loans**.

---

## Continuous Liquidation Loans

In a **Continuous Liquidation Loan**, the protocol protects lenders by:

- holding the collateral asset directly  
- monitoring its price continuously  
- liquidating the position if the collateral value becomes insufficient  

If the borrower repays the loan, the collateral is returned.

If the borrower does not repay and the collateral value falls too far, the protocol liquidates the position before lenders become under-collateralised.

Because of this design:

- the protocol must monitor collateral prices continuously  
- borrowers must monitor the health of their positions  
- liquidation can occur at any time

---

## A Different Type of Loan

This article describes a different lending structure: **Fixed-Rate Maturity Loans**.

A Fixed-Rate Maturity Loan has three defining features:

- the borrower receives a fixed amount today  
- the borrower owes a fixed repayment amount  
- the loan settles at a fixed maturity date
- the borrower is not a risk of liquidation prior to maturity  

Instead of managing risk continuously through liquidation, the system only needs to ensure that the correct obligations can be satisfied **at maturity**.

---

### What Collateral Is Doing

Collateral exists to protect the lender.

When a lender provides USDC today, they expect to receive USDC back later.

If the borrower fails to repay, the system must still produce the funds required to repay lenders.

In Continuous Liquidation Loans this protection comes from the protocol holding the collateral asset and selling it if necessary.

But the essential requirement is simply that the system can fulfil its obligations.

This allows those obligations to be constructed in other ways.

---

### Obligations of a Fixed-Rate Maturity Loan

Consider a loan of **USDC secured by ETH**.

For example:

- borrower supplies **1 ETH**
- borrower receives **$700 USDC**
- borrower must repay **$750 USDC in one month**

### Liquidation Threshold

On Aave there is a threshold where collateral is liquidated to cover the loan amount. For ETH this might be something like 82.5% loan to value ratio. 

That corresponds to a liquidation threshold around ETH = **$850** for this loan.

The threshold is there so that one the position is liquidated it covers the lenders position.

---

### Conditional Liabilities

At maturity the protocol must satisfy two obligations:

- **Return 1 ETH if the borrower repays**
- **Deliver $750 USDC if the borrower defaults**

These obligations depend on the state of the world.

The protocol can therefore hold **conditional financial positions** that pay the required assets in those states.

---

### A Concrete Example

Return to the loan described above.

- borrower supplies **1 ETH**
- borrower receives **$700 USDC**
- borrower must repay **$750 USDC in one month**

Suppose the protocol defines the downside region as:

**ETH settles below $850 at maturity**

To ensure the protocol always has sufficient funds, an **insurance buffer** is created.

---

#### Downside USDC Claim

The protocol holds a conditional claim paying:

**$850 USDC if ETH settles below $850**

This ensures the protocol always has enough USDC to:

- repay lenders if the borrower defaults  
- repurchase ETH if the borrower repays  

---

#### Upside ETH Claim

The protocol also holds a conditional claim paying:

**1 ETH if ETH settles at or above $750**

This ensures ETH exists in the states where the borrower repays.

The overlap between **$750 and $850** creates a safety buffer.

---

### Walking Through the Outcomes

There are **six possible states** at maturity.

These depend on:

- borrower action (repay or default)  
- ETH price region  

The price regions are:

- **ETH < $750**  
- **$750 ≤ ETH < $850**  
- **ETH ≥ $850**

---

### Outcome Table

| Scenario | ETH Price | Borrower Repays | Claims That Pay | Lender Outcome | Borrower Outcome | Protocol Outcome |
|---|---|---|---|---|---|---|
| 1 | ETH < $750 | Yes | $850 USDC | +$50 | 1 ETH returned | >~$100 USDC |
| 2 | $750 ≤ ETH < $850 | Yes | $850 USDC + 1 ETH | +$50 | 1 ETH returned | +$1600 USDC |
| 3 | ETH ≥ $850 | Yes | 1 ETH | +$50 | 1 ETH returned | $0 |
| 4 | ETH < $750 | No | $850 USDC | +$50 | ETH lost | +$100 USDC |
| 5 | $750 ≤ ETH < $850 | No | $850 USDC + 1 ETH | +$50 | ETH lost | +$100 USDC + 1 ETH |
| 6 | ETH ≥ $850 | No | 1 ETH | +$50 | ETH lost | >~$100 USDC |

---

### What the Table Shows

Across all six possible states:

- **Lenders always receive $750 USDC (+$50 interest)**  
- **Borrowers recover 1 ETH only if they repay**  
- **The protocol accumulates surplus capital in several states**

This surplus exists because the insurance buffer and conditional claims overlap in certain price regions.

---

### Continuous Liquidation Loans vs Fixed-Rate Maturity Loans

Both systems guarantee the same economic obligations.

They simply use different mechanisms.

#### Continuous Liquidation Loans

- hold collateral directly  
- monitor prices continuously  
- liquidate if necessary  

Risk is managed through **continuous monitoring and liquidation**.

#### Fixed-Rate Maturity Loans

- hold conditional financial positions  
- require no continuous monitoring  
- settle deterministically at maturity  

Risk is managed through **structured conditional claims**.

---

### Why This Does Not Exist Yet

For Fixed-Rate Maturity Loans to work, the protocol must purchase the conditional claims **atomically when the loan is issued**. So within a single transaction the protocol must

1) Purchase conditional ETH denominated ETH > $750  position
2) Purchase conditional USDC denominated USDC < $850 downside position

Currently the infrastructure is not in place to do that.

---

### Prediction Markets as Financial Infrastructure

Prediction markets create **conditional claims on future states of the world**.

These claims can be used not only for forecasting but also for financial structure.

A Fixed-Rate Maturity Loan requires claims that pay different assets depending on future outcomes.

Prediction markets provide the infrastructure needed to construct these claims.

---

### PredictionSwap

PredictionSwap is designed to make this possible.

By allowing prediction market trades to execute atomically on-chain, PredictionSwap enables protocols to construct conditional claims directly inside financial transactions.

This makes prediction markets **composable financial infrastructure**.

Fixed-Rate Maturity Loans are one example of the financial products that become possible when these claims can be created atomically.