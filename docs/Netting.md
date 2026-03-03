# Automatic Netting

## Overview

Automatic netting is a structural consequence of PredictionSwap's exposure representation.

This section contrasts how offsetting positions are handled under the traditional token model and under the exposure model.

---

## Traditional Token Model

### Outcome Space

Consider a mutually exclusive outcome space:

\[
\Omega = \{R, G, B\}
\]

Exactly one outcome will occur.

---

### Initial Position

Alice holds:

- \$5  
- 2 YES–R  
- 2 YES–B  

---

### Trade

Alice buys:

- 2 YES–G for \$1  

---

### Post-Trade Balances

#### Her balances are now:

- \$4  
- 2 YES–R  
- 2 YES–G  
- 2 YES–B  

#### She now holds one complete set:

- 2 YES–R  
- 2 YES–G  
- 2 YES–B  

Economically, one complete set of YES tokens across all outcomes is equivalent to \$1, because exactly one outcome will occur.

However, the ledger does not recognise this automatically.

---

### Merge Operation

To reconcile her position, Alice must explicitly call a **merge** operation.

After merging 2 complete sets, her balances become:

- \$6  
- 0 YES–R  
- 0 YES–G  
- 0 YES–B  

Netting is procedural.  
It requires a separate action.

---

## PredictionSwap Representation

### Initial Position

State is recorded directly as an exposure vector.

Alice initially holds:

- \$5  
- 2 YES–R  
- 2 YES–B  

Her exposure is:

\[
e = (7,5,7)
\]

This can be written as:

\[
e = 5(1,1,1) + (2,0,2)
\]

#### Interpretation

- Cash = 5  
- Shares = (2,0,2)

---

### After Trade

After buying 2 YES–G for \$1:

\[
e = (6,6,6)
\]

This can be written as:

\[
e = 6(1,1,1) + (0,0,0)
\]

#### Interpretation

- Cash = 6  
- Shares = (0,0,0)

---

### Structural Consequence

No merge operation is required.

The complete set of YES tokens collapses automatically into uniform exposure, which is represented directly as cash.

Netting is not an action.  
It is a property of the representation.