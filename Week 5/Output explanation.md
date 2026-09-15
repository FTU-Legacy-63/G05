# PHASE 3 — OUTPUT EXPLANATION

## 1. Purpose

The output should not only display numbers but also help the user understand:

- where current money and assets are located;
- why the portfolio increases / decreases;
- why JPY debt changes in value when converted into USD;
- how floating interest is formed;
- whether P&L comes from assets, FX, or funding cost;
- whether the user is **ACTIVE**, **AT RISK**, or **BANKRUPT**;
- how much USD remains at the end of the Phase after liquidating assets and repaying all debt.

### Output Explanation Structure

The display structure should be consistent:

```text
Result
  ↓
Reason
  ↓
Meaning
  ↓
Next Action
```

---

## 2. Summary Table of Main Outputs

| Output | Calculation | Meaning for the Player | UI Display | Explanation |
|---|---|---|---|---|
| **Free Cash** | Beginning Cash + Borrowing + Sales + Withdrawals − Purchases − Deposits − Information Cost − Repayment | USD immediately available for the next decision | `FREE CASH: $10,300` | The USD currently available to buy assets, deposit into US Cash, or repay debt |
| **US Cash Balance** | Previous US Cash + Deposit − Withdrawal + Return | Defensive asset that earns return by round | `US CASH: $1,015` | Different from idle Free Cash; only US Cash earns return |
| **US Tech Holdings** | Previous Quantity + Buy Quantity − Sell Quantity | Number of US Tech units currently owned by the player | `US TECH: 15 units` | Value changes according to the US Tech price of the round |
| **S&P 500 Holdings** | Previous Quantity + Buy Quantity − Sell Quantity | Number of S&P 500 units currently owned by the player | `S&P 500: 10 units` | Value changes according to the S&P 500 price |
| **Outstanding JPY Principal** | Total principal of all open loan packages | Total unpaid JPY principal | `JPY PRINCIPAL: ¥12,000,000` | Principal still outstanding, excluding accrued interest |
| **Accrued Floating Interest** | Σ(Outstanding Principal × BOJ Rate of Round × Months / 12) | Accumulated funding cost | `INTEREST DUE: ¥25,000` | A loan is subject to the BOJ rate of each round in which it remains outstanding |
| **Debt in USD** | (Outstanding Principal + Accrued Interest) / Current USDJPY | Current value of the debt when converted into USD | `DEBT IN USD: $84,555` | A stronger JPY makes the debt more expensive in USD terms |
| **Remaining Borrowing Capacity** | Max JPY Principal − Outstanding JPY Principal | Amount of JPY the player can still borrow | `REMAINING JPY CAPACITY: ¥3,750,000` | Borrowing capacity is fixed in JPY and is restored after a loan package is repaid |
| **Gross Portfolio Value** | Free Cash + Tech Value + S&P Value + US Cash Balance | Total asset value before deducting debt | `PORTFOLIO VALUE: $92,400` | This is not yet Net Wealth because JPY debt has not been deducted |
| **Net Wealth** | Gross Portfolio Value − Debt in USD | Current net value of the player | `NET WEALTH: $7,845` | Used to evaluate the current financial status |
| **Round Status** | Based on Net Wealth and payment status | Indicates whether the player is financially stable or at risk | `ACTIVE / AT RISK / BANKRUPT` | Quickly summarizes the financial condition after the round |
| **Final USD Wealth** | Cash remaining after auto-liquidation and full debt settlement | Final asset value of the player | `FINAL USD WEALTH: $6,500` | USD remaining after paying all principal and interest |
| **Net P&L** | Portfolio P&L + FX P&L − Interest Cost − Information Cost | Final profit / loss for the Phase | `NET P&L: -$6,423` | Indicates whether the overall strategy generated a profit or loss |

---

## 3. Loan Outputs

The Loan Ledger must help the player clearly see each individual loan.

| Output | Content to Display | Meaning | UI Example |
|---|---|---|---|
| **Loan ID** | L1, L2, L3, L4 | Distinguishes each loan by the round in which it was opened | `L2` |
| **Open Round** | Round in which the loan was opened | Indicates when interest begins to accrue | `Opened: Round 2` |
| **Accepted Principal** | Principal accepted by the system | Actual loan amount created | `¥7,500,000` |
| **Outstanding Principal** | Unpaid principal | Current remaining debt principal | `¥7,500,000` |
| **Months Outstanding** | Total number of months the loan has existed | Used to calculate accrued interest | `6 months` |
| **Accrued Floating Interest** | Interest accumulated across rounds | Funding cost that must be paid | `¥8,438` |
| **Current BOJ Rate** | BOJ rate of the current round | Rate applied if the loan remains outstanding in the current round | `0.25%` |
| **Loan Action** | HOLD / REPAY | Decision for the current loan | `[HOLD] [REPAY]` |

### Explainability for Floating Interest

Example of a loan opened in Round 1 and repaid at the Start of Round 3:

```text
Interest =
Principal × (
    R1 Rate × R1 Months / 12
    +
    R2 Rate × R2 Months / 12
)
```

The explanation should help the player understand that the loan is subject to the **floating BOJ rate of each round in which the loan remains outstanding**.

---

## 4. Market Outputs

Market outputs provide the context needed for the player to understand changes in the portfolio and debt.

| Market Output | Display | Role |
|---|---|---|
| **USD/JPY** | Current rate + change from the previous round | Helps explain FX risk of the debt |
| **BOJ Rate** | Current policy rate | Provides context about the funding environment |
| **US Tech Price** | Current price | Used to calculate market value and make trading decisions |
| **S&P 500 Price** | Current price | Used to calculate market value and make trading decisions |
| **US Cash Return** | Return of the round | Shows the benefit of a defensive cash position |
| **Market News** | 3 news cards | Supports decision-making |
| **Additional Information** | Additional signal if the user purchases it | Supports information advantage |

### Example Market Move

| Variable | Before | After | Interpretation |
|---|---:|---:|---|
| **USD/JPY** | 160 | 142 | JPY strengthens, debt in USD increases |
| **US Tech** | $515 | $345 | Risk asset falls sharply |
| **S&P 500** | $570 | $490 | Equity market declines |
| **BOJ Rate** | 0.10% | 0.25% | Funding environment becomes tighter |

---

## 5. Output After Each Round

After the user selects **LOCK IN**, Market Close should display outputs in the following order:

| Group | Output to Display |
|---|---|
| **Market Move** | USD/JPY, BOJ Rate, US Tech, S&P 500, US Cash Return |
| **Portfolio** | Ending Free Cash, Tech Holdings, S&P Holdings, US Cash |
| **Debt** | Outstanding Principal, Accrued Interest, Debt in USD |
| **Result** | Gross Portfolio Value, Net Wealth, Round Status |
| **Next Action** | CONTINUE TO NEXT ROUND |

### UI Example

```text
MARKET CLOSE
────────────────────────

USD/JPY:   160 → 142
US Tech:   $515 → $345
S&P 500:   $570 → $490


YOUR POSITION
────────────────────────

Portfolio Value:   $74,268
Debt in USD:       $84,555
Net Wealth:        -$10,287


STATUS: AT RISK
```

### Short Explanation

> JPY strengthened while risk assets fell, increasing the USD value of your debt and reducing your portfolio value.

The explanation should be short, direct, and connect **market movement → financial impact**.

---

## 6. Status Output

| Status | Condition | Meaning on UI | Suggested Color |
|---|---|---|---|
| **ACTIVE** | Net Wealth ≥ 0 and no payment default | Player maintains a positive financial position | Green |
| **AT RISK** | Net Wealth < 0 but no default on required repayment | Portfolio is weak but the game continues | Orange |
| **BANKRUPT** | Required repayment cannot be made due to insufficient liquidity | Game ends | Red |
| **PHASE COMPLETE** | End Phase Settlement completed | Player completes Phase 3 | Blue / Green |

---

## 7. Repayment Output

When the user selects **REPAY**, the system must clearly display the amount that needs to be paid before confirming the transaction.

| Output | Example |
|---|---:|
| **Principal Due** | ¥7,500,000 |
| **Accrued Floating Interest** | ¥8,438 |
| **Total JPY Due** | ¥7,508,438 |
| **Current USD/JPY** | 142 |
| **USD Repayment Required** | $52,876 |
| **Available Liquidity** | $55,000 |

Available Liquidity is determined after valid:

```text
SELL / WITHDRAW
```

actions are allowed before repayment.

---

### 7.1. If Liquidity Is Sufficient

```text
REPAYMENT SUCCESSFUL

Loan L1 has been fully repaid.
```

After that:

- outstanding principal decreases;
- accrued interest of the loan is settled;
- the loan is closed;
- JPY borrowing capacity is restored.

---

### 7.2. If Liquidity Is Insufficient

```text
PAYMENT DEFAULT — BANKRUPT
```

Display:

| Output | Value |
|---|---:|
| **Available Liquidity** | $50,000 |
| **USD Repayment Required** | $52,876 |
| **Shortfall** | -$2,876 |

After payment default:

```text
Status = BANKRUPT
```

Do not allow further new borrowing.

---

## 8. End-of-Phase P&L Breakdown

To help the user understand the sources of profit / loss, the Final Result needs to separate P&L into different components.

| P&L Component | Meaning | General Formula | Example |
|---|---|---|---:|
| **Portfolio P&L** | Profit / loss from assets | Tech P&L + S&P P&L + US Cash Return | -$774 |
| **FX P&L** | Profit / loss caused by JPY movement between borrowing and repayment | FX effect on principal | -$5,383 |
| **Interest Cost** | Borrowing interest cost | Total interest of all loans | -$66 |
| **Information Cost** | Cost of purchasing information | Total fee paid | -$200 |
| **Net P&L** | Total result | Portfolio P&L + FX P&L − Interest − Info Cost | **-$6,423** |

### UI Priority

The total result should be displayed first:

```text
NET P&L
-$6,423
```

Then display the breakdown to explain **why**.

Flow:

```text
Net P&L
  ↓
Portfolio P&L
  ↓
FX P&L
  ↓
Interest Cost
  ↓
Information Cost
```

---

## 9. End Phase Settlement

At the end of Round 4, the system automatically:

```text
Auto Sell US Tech
        ↓
Auto Sell S&P 500
        ↓
Auto Withdraw US Cash
        ↓
Calculate Debt Due
        ↓
Convert USD to JPY
        ↓
Repay All Loans
        ↓
Final USD Wealth
```

### Final Settlement Outputs

| Output | Meaning |
|---|---|
| **Assets Liquidated** | USD received from closing positions |
| **Available Liquidity** | Total USD available for settlement |
| **Outstanding JPY Principal** | Unpaid principal |
| **Accrued Floating Interest** | Floating interest still payable |
| **Total JPY Due** | Principal + interest |
| **End Phase USD/JPY** | FX rate used for settlement |
| **USD Repayment Required** | USD needed to settle debt |
| **Final USD Wealth** | USD remaining if settlement is successful |
| **Net P&L** | Final profit / loss of the Phase |
| **Final Status** | Phase Complete / Bankrupt |

---

## 10. Final Result

### 10.1. Phase Completed

```text
PHASE COMPLETE
```

| Output | Value |
|---|---:|
| **Final USD Wealth** | +$1,200 |
| **Net P&L** | +$1,200 |
| **Portfolio P&L** | +$3,500 |
| **FX P&L** | -$1,900 |
| **Floating Interest Cost** | -$300 |
| **Information Cost** | -$100 |

---

### 10.2. Bankrupt Case

```text
INSOLVENT / BANKRUPT
```

| Output | Value |
|---|---:|
| **Available Liquidity** | $12,400 |
| **Debt Due** | $15,100 |
| **Shortfall** | -$2,700 |

### Explanation

> Available liquidity was not enough to cover the required JPY repayment.


