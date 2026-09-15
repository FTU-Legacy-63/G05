# WEEK 4 — FINANCIAL LOGIC, TECHNICAL READINESS & MIDTERM

## 1. Project Logic Chain

```text
Problem
→ Students may understand carry trade conceptually
  but may not understand how asset return, FX risk,
  funding cost, and repayment interact.

Target User
→ Finance students participating in the simulation game.

User Task
→ Borrow JPY
→ Convert JPY into USD
→ Invest in USD assets
→ Manage portfolio and liquidity
→ Manage JPY debt
→ Repay debt
→ Evaluate final performance.

Input
→ Role
→ Borrowing decision
→ Market data
→ Trading decisions
→ Information decision
→ Repayment decision

Financial Logic
→ Borrowing Validation
→ FX Conversion
→ Portfolio Transactions
→ Floating Interest
→ Portfolio Valuation
→ Debt Valuation
→ Repayment
→ P&L Calculation
→ Player Status

Output
→ Free Cash
→ Asset Holdings
→ Portfolio Value
→ JPY Debt
→ USD Debt Value
→ Net Wealth
→ P&L
→ Player Status

User Action
→ BUY / SELL / HOLD
→ DEPOSIT / WITHDRAW
→ BORROW / REPAY
→ Continue to the next round
```

---

## 2. Input–Logic–Output Mapping

| Input | Financial Meaning | Rule / Calculation | Output |
|---|---|---|---|
| Player Role | Determines role-specific limits | Lookup role parameters | Borrowing limit, information cost |
| Borrow Package | JPY funding decision | Borrow % × Max JPY Principal | Requested JPY loan |
| USD/JPY | FX exposure | JPY amount / USDJPY | USD funding and USD debt value |
| BOJ Rate | Floating funding cost | Round-specific interest calculation | Interest expense |
| Quarter Length | Loan duration | Months / 12 | Accrued interest |
| Information Decision | Cost of additional information | Affordability check | Information status and cost |
| Tech / S&P Action | Investment decision | BUY / SELL / HOLD validation | Asset holdings |
| US Cash Action | Defensive allocation | DEPOSIT / WITHDRAW / HOLD | US Cash balance |
| Repayment Decision | Debt management | HOLD or full REPAY | Remaining debt |
| Asset Prices | Market risk | Quantity × Current Price | Asset market value |
| Portfolio + Debt | Financial position | Assets − Debt | Net Wealth |
| End Phase | Final settlement | Liquidation + debt repayment | Final Wealth and Net P&L |

---

## 3. Financial Logic

### 3.1 Borrowing

Players choose a borrowing package:

```text
0% / 25% / 50% / 75% / 100%
```

Requested JPY principal:

```text
Requested JPY
= Borrow % × Role Maximum JPY Principal
```

A new loan is accepted only if both borrowing constraints are satisfied.

#### JPY Principal Cap

```text
Outstanding JPY after new borrowing
≤ Role Maximum JPY Principal
```

#### USD-Equivalent Cap

```text
Outstanding JPY after new borrowing
/ Current USDJPY
≤ Role Maximum USD Equivalent
```

If both conditions are satisfied:

```text
Accepted Principal = Requested Principal
```

Otherwise:

```text
Loan Request = REJECT
```

---

### 3.2 JPY-to-USD Conversion

When a JPY loan is accepted:

```text
Borrowed USD
= Accepted JPY Principal
/ USDJPY at Borrowing
```

The USD proceeds are added to Free Cash.

Example:

```text
JPY Principal = ¥6,000,000
USDJPY = 150

Borrowed USD
= 6,000,000 / 150
= $40,000
```

---

## 4. Floating Interest

The borrowing rate is **floating by round**.

A loan pays the BOJ rate of every round during which it remains outstanding.

```text
Floating Interest
= Σ [
Outstanding Principal
× BOJ Rate of Round
× Round Months / 12
]
```

Example: a loan is opened in R1 and remains outstanding until the end of R4.

```text
Interest
= Principal × (
R1 Rate × R1 Months / 12
+ R2 Rate × R2 Months / 12
+ R3 Rate × R3 Months / 12
+ R4 Rate × R4 Months / 12
)
```

If the loan is repaid at the end of R2:

```text
Interest
= Principal × (
R1 Rate × R1 Months / 12
+ R2 Rate × R2 Months / 12
)
```

R3 interest is not included because the debt has already been settled before R3 begins.

---

## 5. Repayment Timing

Repayment occurs at the **end of the current round**, after the current-round portfolio has been valued and the current-round floating interest has been accrued.

The next round's market data and BOJ rate are revealed only after the repayment decision has been processed.

The round transition is:

```text
Current-Round Actions
→ Current-Round Market Valuation
→ Current-Round Floating Interest
→ HOLD / REPAY Decision
→ Debt Settlement
→ Round Summary
→ Reveal Next-Round Data
```

This prevents players from using future information when deciding whether to repay.

For example:

```text
Loan opened in R1
Repaid at end of R2
```

The repayment includes:

```text
R1 Interest
+ R2 Interest
```

but not R3 interest.

---

## 6. Debt Repayment

Each outstanding loan package can be:

```text
HOLD
or
REPAY
```

Partial repayment is not allowed.

Total JPY due:

```text
Total JPY Due
= JPY Principal
+ Accumulated Floating Interest
```

USD required for repayment:

```text
USD Repayment
= Total JPY Due
/ Current USDJPY
```

After a loan package is fully repaid:

```text
Outstanding Principal decreases
→ Borrowing Capacity is restored
→ The player may borrow again later
```

---

## 7. Trading Logic

### 7.1 BUY

Purchase cost:

```text
Purchase Cost
= Quantity × Current Asset Price
```

A BUY order is accepted only when:

```text
Purchase Cost
≤ Available Free Cash
```

After a valid BUY:

```text
Free Cash decreases
Asset Holdings increase
```

---

### 7.2 SELL

A SELL order is accepted only when:

```text
Sell Quantity
≤ Current Holdings
```

Sale proceeds:

```text
Sale Proceeds
= Sell Quantity × Current Asset Price
```

After a valid SELL:

```text
Asset Holdings decrease
Free Cash increases
```

Overselling is rejected.

---

### 7.3 HOLD

When the player chooses HOLD:

```text
Quantity remains unchanged
```

However, the market value still changes when the asset price changes.

---

## 8. US Cash Logic

Free Cash and US Cash are treated separately.

### DEPOSIT

```text
Free Cash decreases
US Cash increases
```

Deposit amount must not exceed available Free Cash.

### WITHDRAW

```text
US Cash decreases
Free Cash increases
```

Withdrawal amount must not exceed the current US Cash balance.

### US Cash Return

Only explicitly deposited US Cash earns a return.

```text
US Cash Interest
= US Cash Balance
× US Cash Return
```

Idle Free Cash earns no interest.

---

## 9. Information Purchase

Information can only be purchased when:

```text
Beginning Free Cash
≥ Information Cost
```

If the player cannot afford the information:

```text
Information Purchase = REJECT
Information Cost = 0
```

The system must not allow information purchases to create negative Free Cash.

---

## 10. FX Logic

The USD value of JPY debt is:

```text
USD Debt
= JPY Debt / USDJPY
```

### JPY Depreciation

```text
USDJPY increases
→ JPY becomes weaker
→ USD value of JPY debt decreases
→ Positive for carry trade
```

### JPY Appreciation

```text
USDJPY decreases
→ JPY becomes stronger
→ USD value of JPY debt increases
→ Negative for carry trade
```

FX P&L for a loan package:

```text
FX P&L
= Principal USD at Borrowing
− Principal USD at Repayment
```

where:

```text
Principal USD at Borrowing
= JPY Principal / Borrow FX
```

and:

```text
Principal USD at Repayment
= JPY Principal / Repayment FX
```

Interest cost is calculated separately from FX P&L.

---

## 11. Portfolio Valuation

Tech market value:

```text
Tech Market Value
= Tech Quantity × Current Tech Price
```

S&P 500 market value:

```text
S&P Market Value
= S&P Quantity × Current S&P Price
```

Gross Portfolio Value:

```text
Gross Portfolio Value
= Free Cash
+ Tech Market Value
+ S&P Market Value
+ US Cash Balance
```

---

## 12. Debt Mark-to-Market

The USD value of outstanding debt is recalculated each round.

```text
USD Debt MTM
= (
Outstanding JPY Principal
+ Accrued Floating Interest
)
/ Current USDJPY
```

Debt value can therefore change because of:

- additional borrowing;
- repayment;
- floating interest;
- USD/JPY movement.

---

## 13. Net Wealth

```text
Net Wealth
= Gross Portfolio Value
− USD Debt MTM
```

Net Wealth represents the player's current economic position.

A negative Net Wealth does not automatically mean bankruptcy.

---

## 14. Player Status

### ACTIVE

```text
Net Wealth ≥ 0
and
No repayment default
```

### AT RISK

```text
Net Wealth < 0
but
No repayment default
```

### BANKRUPT

Bankruptcy occurs only when a required repayment cannot be completed.

```text
Available Repayment Liquidity
< Debt Repayment Due
```

after valid asset sales and US Cash withdrawals.

Therefore:

> **Negative Net Wealth represents financial stress, while bankruptcy represents an actual repayment default.**

---

## 15. P&L Calculation

For explainability, final performance is separated into two main components.

### 15.1 Investment P&L

```text
Investment P&L
= Tech P&L
+ S&P 500 P&L
+ US Cash Interest
```

This measures the result generated by asset-allocation decisions.

---

### 15.2 Funding P&L

```text
Funding P&L
= FX P&L
− Floating Interest Cost
```

This measures the result generated by borrowing JPY.

---

### 15.3 Net P&L

```text
Net P&L
= Investment P&L
+ Funding P&L
− Information Cost
```

This allows the player to distinguish between:

- investment performance;
- FX impact;
- funding cost;
- information cost.

---

## 16. End Phase

At the end of Phase 3, the system automatically:

```text
1. Sells all remaining US Tech
2. Sells all remaining S&P 500
3. Withdraws all remaining US Cash
4. Calculates all remaining JPY principal
5. Calculates accumulated floating interest
6. Converts repayment requirement into USD
7. Repays remaining debt
8. Calculates Final Wealth
9. Calculates Investment P&L
10. Calculates Funding P&L
11. Calculates Net P&L
12. Determines Final Status
```

After successful settlement:

```text
Tech Holdings = 0
S&P Holdings = 0
US Cash = 0
Outstanding JPY Principal = 0
```

---

## 17. Assumptions

The current model assumes:

1. Phase 3 contains four rounds and one End Phase.
2. One round is normally three months.
3. BOJ rate is used as a proxy for JPY funding cost.
4. Borrowing rate is floating and changes by round.
5. A loan pays the rate of every round during which it remains outstanding.
6. Repayment occurs at the end of the current round before next-round data is revealed.
7. Partial loan repayment is not allowed.
8. Repaid borrowing capacity can be reused.
9. Free Cash earns no interest.
10. US Cash earns return only when funds are explicitly deposited.
11. Asset trades occur at current-round prices.
12. End Phase automatically liquidates all remaining assets.
13. Bankruptcy occurs only when required repayment cannot be completed.
14. No separate leverage multiplier is used in the current Phase 3 model.

---

## 18. Limitations

The current simulation does not fully model:

- transaction costs;
- bid–ask spreads;
- taxes;
- margin calls;
- collateral requirements;
- market impact;
- intraday price movements;
- credit spreads;
- derivatives hedging;
- stochastic asset-price paths;
- stochastic FX paths.

The market path is a **stylized scenario designed for educational simulation**, not a real-time market forecast.

---

## 19. Sample Calculation

Consider a Conservative Investor.

```text
Maximum JPY Principal = ¥12,000,000
Borrow Package = 50%
Borrow FX = 150

R1 BOJ Rate = 0.10%
R2 BOJ Rate = 0.10%
R3 BOJ Rate = 0.25%
R4 BOJ Rate = 0.25%

Round Length = 3 months
```

The player buys:

```text
10 Tech units at $450
10 S&P units at $520
```

### Step 1 — Borrowing

```text
JPY Loan
= 50% × ¥12,000,000
= ¥6,000,000
```

USD proceeds:

```text
Borrowed USD
= 6,000,000 / 150
= $40,000
```

### Step 2 — Investment

Tech purchase:

```text
10 × $450
= $4,500
```

S&P purchase:

```text
10 × $520
= $5,200
```

Ending Free Cash:

```text
$40,000
− $4,500
− $5,200
= $30,300
```

### Step 3 — Floating Interest

Assume the loan remains outstanding through all four rounds.

```text
Interest
= 6,000,000 × (
0.10% × 3/12
+ 0.10% × 3/12
+ 0.25% × 3/12
+ 0.25% × 3/12
)
```

```text
Interest
= ¥10,500
```

### Step 4 — End Phase

Assume:

```text
End USDJPY = 147
End Tech Price = $440
End S&P Price = $545
```

Tech liquidation:

```text
10 × 440
= $4,400
```

S&P liquidation:

```text
10 × 545
= $5,450
```

Total available cash:

```text
30,300
+ 4,400
+ 5,450
= $40,150
```

Total JPY repayment:

```text
¥6,000,000
+ ¥10,500
= ¥6,010,500
```

USD repayment:

```text
6,010,500 / 147
= $40,887.76
```

Final Wealth:

```text
$40,150
− $40,887.76
= −$737.76
```

### P&L Reconciliation

Investment P&L:

```text
Tech P&L
= 4,400 − 4,500
= −$100
```

```text
S&P P&L
= 5,450 − 5,200
= +$250
```

```text
Investment P&L
= −100 + 250
= +$150
```

FX P&L:

```text
FX P&L
= 6,000,000 / 150
− 6,000,000 / 147
= −$816.33
```

Floating Interest Cost:

```text
10,500 / 147
= $71.43
```

Funding P&L:

```text
Funding P&L
= −816.33 − 71.43
= −$887.76
```

Net P&L:

```text
Net P&L
= 150 − 887.76
= −$737.76
```

Therefore:

```text
Final Wealth ≈ Net P&L
```

The result shows that the investment portfolio was profitable, but the gain was more than offset by JPY appreciation and floating funding cost.

---

## 20. Logic Testing

| Test Case | Expected Result |
|---|---|
| Borrowing exceeds JPY cap | REJECT |
| Borrowing exceeds USD-equivalent cap | REJECT |
| BUY exceeds Free Cash | REJECT |
| SELL exceeds current holdings | REJECT |
| WITHDRAW exceeds US Cash | REJECT |
| Information purchase is unaffordable | REJECT |
| JPY appreciates | USD debt value increases |
| JPY depreciates | USD debt value decreases |
| BOJ rate increases | Interest cost increases for outstanding debt |
| Loan repaid at end of R2 | Only R1 + R2 interest is charged |
| HOLD asset | Quantity remains unchanged |
| Full repayment | Principal + accumulated floating interest are settled |
| Reborrow after repayment | Borrowing capacity is restored |
| Net Wealth < 0 without default | AT RISK |
| Repayment liquidity is insufficient | BANKRUPT |
| End Phase | Assets liquidated and debt settled |
| Final Wealth vs Net P&L | Reconciliation ≈ 0 |

---

## 21. Technical Route

The current financial prototype is built in:

```text
Excel
```

Excel is used to:

- validate formulas;
- test financial rules;
- test edge cases;
- reconcile cash, debt, and P&L;
- serve as the reference financial model.

The planned MVP route is:

```text
Excel Financial Logic
→ Python Financial Engine
→ Streamlit Interface
→ GitHub
→ Streamlit Community Cloud
```

Core Python modules are expected to cover:

```text
Borrowing
Trading
Cash
Interest
Repayment
Valuation
P&L
Player Status
```

Implementation principle:

> **Python output must match the expected Excel output before a rule is considered successfully implemented.**

---

## 22. Deployment Route and Fallback

Primary deployment route:

```text
GitHub
→ Streamlit Community Cloud
```

If the web application is not sufficiently stable before assessment:

```text
Fallback
= Excel Simulation Model
```

The Excel version can still demonstrate:

- player inputs;
- financial logic;
- borrowing and repayment;
- floating interest;
- FX exposure;
- portfolio valuation;
- P&L;
- player status;
- logic testing.

---


> **Week 4 formalizes the financial engine of the product: player decisions are converted into portfolio value, floating funding cost, FX exposure, debt value, Net Wealth, P&L, and player status through explicit and testable financial rules.**
