
# Financial Logic

## 1. Overview

Arbiverse applies a different financial mechanism in each phase. Players must interpret market information, allocate capital, account for transaction costs, and manage exposure as conditions change.

| Phase | Main Mechanism | Main Sources of Gain/Loss | End-of-Phase Accounting |
|---|---|---|---|
| **I — Tulip Mania** | Buy/sell tulips through fixed NPC offers | Price differences, inventory retained during the crash, information costs | Cash + remaining tulips valued at **$15 each** |
| **II — Thai Baht Crisis** | Three-leg USD–SGD–THB arbitrage | Quoted cross-rate differences, onshore/offshore spreads, FX fees, paid news | All routes close in USD each round; final balance is USD cash |
| **III — Carry Trade** | Borrow JPY, convert to USD, allocate to US assets | Equity prices, US Cash interest, USD/JPY changes, JPY financing costs and trading fees | Liquidate assets and repay outstanding JPY debt at final settlement prices |

**Accounting convention:** Phase I and II start with their own USD cash capital; Phase III begins with **$0 Free Cash** and is financed through JPY borrowing. Cash balances and P&L are carried forward *within* each phase, not transferred between phases.

---

## 2. Phase I — Tulip Mania

### 2.1 Starting Position and Execution

| Parameter | Implemented Rule |
|---|---|
| Initial cash | **$1,000** |
| Initial tulips | **0** |
| Market rounds | **3** |
| Paid information | **$200 per report** |
| Trading | Accept or reject individual **whole-lot** NPC offers |
| Financing | Cash-funded trading; no active leverage |
| Crash valuation | **$15 per unsold tulip** |

NPC offers specify a **quantity** and **unit price**. An NPC **SELL** offer means the player *buys* tulips; an NPC **BUY** offer means the player *sells* tulips. A purchase requires sufficient cash; a sale requires sufficient tulip inventory.

**Purchase Cost:**

`Purchase Cost = Quantity × Ask Price`

**Sale Revenue:**

`Sale Revenue = Quantity × Bid Price`

**Cash After Buy:**

`Cash After Buy = Cash Before Buy − Purchase Cost`

**Cash After Sale:**

`Cash After Sale = Cash Before Sale + Sale Revenue`

**Tulips After Buy:**

`Tulips After Buy = Tulips Before Buy + Quantity`

**Tulips After Sale:**

`Tulips After Sale = Tulips Before Sale − Quantity`

The game deducts paid information directly from cash. Unsold tulips are carried into later rounds, where prices and buyer availability may change. For trade-level **realized profit**, the scoring replay matches sales against earlier purchases using **first-in, first-out (FIFO)** cost basis.

### 2.2 Final Wealth and P&L

**Final Wealth:**

`Final Wealth = Ending Cash + (Remaining Tulips × $15) − Outstanding Debt`

**Final Net P&L:**

`Final Net P&L = Final Wealth − $1,000`

**Final Return (%):**

`Final Return (%) = Final Net P&L / $1,000 × 100`

The debt term is zero under the current no-leverage setup. The final $15 valuation ensures that retaining tulips through the crash affects final wealth even when no sale occurs.

**Illustrative audit result:**

The best identified feasible combination of current NPC offers produces **$392 trading profit before news**.

- **No paid reports:** +$392 Net P&L
- **One 200report:**+192 Net P&L
- **Two 200reports:**-8 Net P&L

This is an offer-specific calculation, not a guaranteed player outcome.

### 2.3 Performance Assessment

| Pillar | Points | What Is Assessed |
|---|---:|---|
| Financial Performance | 30 | Final Net P&L (20); capital efficiency (10) |
| Arbitrage & Trading Execution | 30 | Profit capture (15); opportunity use (10); execution (5) |
| Decision Quality | 25 | Information use (8); cycle adaptation (12); consistency (5) |
| Risk Management | 15 | Inventory control (7); liquidity (5); drawdown (3) |
| **Total** | **100** | **Final Score = min(Raw Score, Activity Score Cap)** |

The scoring replay tracks realized gains, within-round trading spreads, cash, inventory and wealth across the three rounds. The activity cap distinguishes sustained position management from little or no trading.

---

## 3. Phase II — Thai Baht Crisis

### 3.1 Capital and Quoted Rates

| Parameter | Implemented Rule |
|---|---|
| Initial capital | **$120,000** |
| Trading rounds | **4** |
| Maximum allocation | **$50,000 per round**, subject to available cash |
| Trade-size increment | **$1,000** |
| Transaction fee | **0.05% per FX leg**; three legs per trade |
| Paid information | **$600 per report** |
| Currency pairs | USD/THB, USD/SGD, SGD/THB |

Rates are expressed as **units of the second currency per one unit of the first**: for example, USD/THB = 25.80 means USD 1 converts to THB 25.80. A conversion therefore **multiplies** by the rate in the quoted direction and **divides** in the reverse direction.

**Implied Cross-Rate:**

`Implied SGD/THB = (USD/THB) ÷ (USD/SGD)`

Discrepancies between the **quoted SGD/THB** and **implied SGD/THB** determine the direction and potential gross return of standard triangular arbitrage.

In Round 3, the split between **Onshore (Bangkok)** and **Offshore (Singapore)** quotes creates four cross-market routes.

### 3.2 Available Trading Routes

| Rounds | Displayed Option | Three-Leg Conversion |
|---|---|---|
| 1, 2, 4 | **Path A** | USD → SGD → THB → USD |
| 1, 2, 4 | **Path B** | USD → THB → SGD → USD |
| 3 | **Route A** (`CROSSB`) | USD → THB (Onshore) → SGD (Offshore) → USD |
| 3 | **Route B** (`CROSSA`) | USD → SGD (Onshore) → THB (Offshore) → USD |
| 3 | **Route C** (`CROSSC`) | USD → THB (Offshore) → SGD (Onshore) → USD |
| 3 | **Route D** (`CROSSD`) | USD → SGD (Offshore) → THB (Onshore) → USD |

**Stay in Cash** is an alternative to executing a route. A cash decision incurs **no FX trading fee**, although any information already purchased is still charged.

### 3.3 Three-Leg Execution, Fees and Cash Rollover

For allocated capital `C`, the finance engine converts sequentially through all three legs.

In the implementation, fees are calculated separately on the **initial allocation** rather than deducted from the amount at each intermediate conversion.

**Gross Final USD:**

`Gross Final USD = C × Leg 1 Factor × Leg 2 Factor × Leg 3 Factor`

**Gross P&L:**

`Gross P&L = Gross Final USD − C`

**FX Trading Fee:**

`FX Trading Fee = C × [1 − (1 − 0.0005)^3]`

**Information Fee:**

`Information Fee = Number of Reports Purchased × $600`

**Round Net P&L:**

`Round Net P&L = Gross P&L − FX Trading Fee − Information Fee`

**Ending Cash:**

`Ending Cash = Starting Cash + Round Net P&L`

For a leg converting in the reverse direction of its quoted pair, its factor is `1 / quoted rate`.

An allocation returns to USD after the third leg; there is no open FX position carried into the next round.

#### Worked Example — Round 3, Route A, $50,000

**Leg 1 — USD → THB Onshore:**

`$50,000 × 25.80 = THB 1,290,000`

**Leg 2 — THB → SGD Offshore:**

`THB 1,290,000 ÷ 15.91 ≈ SGD 81,081.08`

**Leg 3 — SGD → USD:**

`SGD 81,081.08 ÷ 1.43 ≈ $56,700.06`

**Gross P&L:**

`$56,700.06 − $50,000 ≈ $6,700.06`

**Three-Leg Fee:**

`$50,000 × [1 − (1 − 0.0005)^3] ≈ $74.96`

**Net Trading P&L:**

`$6,700.06 − $74.96 ≈ $6,625.09`

**Result: +$6,625.09 before paid news.**

A full benchmark sequence — **R1 Path B, R2 Path A, R3 Route A** at $50,000 each, then **R4 Stay in Cash**, with no purchased reports — produces approximately:

- **Cumulative Net P&L:** +$7,714.20
- **Final Cash:** $127,714.20

The workbook retains full calculation precision, so rounded display values may differ by $0.01 when summed.

### 3.4 Performance Assessment

| Pillar | Points | Components |
|---|---:|---|
| Financial Performance | 50 | Net P&L Return (50) |
| Risk Management | 30 | Cash buffer (10); R3 capital-control adaptation (10); fee drag (10) |
| Decision Quality | 20 | R2–R3 capital efficiency (8); R4 exit discipline (7); information use (5) |
| **Total** | **100** | Score calculated from the four-round trading history |

The **scoring Net Return** uses:

`Scoring Net Return (%) = sum(Round Net P&L) / sum(Allocated Capital) × 100`

This is distinct from the **final wealth return** calculated against the original $120,000.

In the cash-close round, allocation and trading fees are zero.

---

## 4. Phase III — Carry Trade

### 4.1 Financing and Portfolio Setup

| Parameter | Implemented Rule |
|---|---|
| Initial Free Cash | **$0** |
| Maximum outstanding JPY principal | **¥18,000,000** |
| Borrowing fee | **0.01%**, paid once when a loan is accepted |
| JPY loan interest | Round-specific annual BOJ rate; simple accrual over that round's months |
| Equity trading fee | **0.05%** per buy and per sell |
| Paid information | **$600 per item** |
| Investment choices | US Tech, S&P 500, US Cash, or unallocated Free Cash |
| Timeline | **Four rounds of three months each** |

Borrowing capacity is based on **currently outstanding JPY principal**. Repaying principal releases capacity for future borrowing.

On borrowing, JPY principal is converted to USD at that round's USD/JPY spot rate.

**Gross USD Borrowed:**

`Gross USD Borrowed = Accepted JPY Principal / USDJPY_at_borrow`

**Origination Fee:**

`Origination Fee = Gross USD Borrowed × 0.0001`

**Net USD Free Cash:**

`Net USD Free Cash = Gross USD Borrowed − Origination Fee`

**JPY Interest for Round:**

`JPY Interest = Outstanding JPY Principal × Annual BOJ Rate × (Months / 12)`

**USD Repayment Due:**

`USD Repayment Due = (JPY Principal + Accrued JPY Interest) / USDJPY_at_repayment`

**Example:**

Borrowing **¥4,500,000** at USD/JPY **150** gives:

- **Gross USD Funding:** $30,000
- **Origination Fee:** $3
- **Net Free Cash:** $29,997
- **Annual BOJ Rate:** 0.10%
- **Round Duration:** 3 months

**Interest Calculation:**

`¥4,500,000 × 0.001 × (3 / 12) = ¥1,125`

The loan accrues **¥1,125** interest for the round.

The example assumes the loan remains open for that period.

### 4.2 Investing and Mark-to-Market Accounting

Stocks are bought and sold in USD, with transaction fees incorporated into the transaction values.

US Cash is a separate interest-earning balance; **Free Cash does not earn the US Cash return**.

**Stock Purchase Cost:**

`Stock Purchase Cost = Quantity × Purchase Price × (1 + 0.0005)`

**Stock Sale Proceeds:**

`Stock Sale Proceeds = Quantity × Sale Price × (1 − 0.0005)`

**US Cash Interest:**

`US Cash Interest = US Cash Balance × Round US Cash Return`

**Gross Portfolio Value:**

`Gross Portfolio Value = Free Cash + Tech Market Value + S&P Market Value + US Cash Balance`

**Outstanding USD Debt:**

`Outstanding USD Debt = (JPY Principal + Accrued JPY Interest) / Current USDJPY`

**Net Wealth:**

`Net Wealth = Gross Portfolio Value − Outstanding USD Debt`

At the close of each round, the game accrues interest on open JPY loans and credits interest on US Cash.

Borrowing in JPY creates **FX risk**: a *lower* USD/JPY rate means more USD is needed to repay a given JPY debt.

### 4.3 Final Settlement and P&L Reconciliation

At phase end, remaining equities are automatically sold and US Cash is withdrawn.

The settlement values are **separate from the displayed Round 4 market prices**:

| Final Settlement Variable | Value |
|---|---:|
| USD/JPY | **147** |
| US Tech | **$400** |
| S&P 500 | **$525** |

All remaining debt is then converted into USD and settled.

The game separately reports available liquidity, debt paid, any unpaid debt, and final USD wealth.

**Tech P&L:**

`Tech P&L = Total Tech Net Sale Proceeds − Total Tech Purchase Costs`

**S&P P&L:**

`S&P P&L = Total S&P Net Sale Proceeds − Total S&P Purchase Costs`

**Investment P&L:**

`Investment P&L = Tech P&L + S&P P&L + Total US Cash Interest`

**FX P&L:**

`FX P&L = Σ [JPY Principal / USDJPY_at_borrow − JPY Principal / USDJPY_at_repayment]`

**Funding P&L:**

`Funding P&L = FX P&L − JPY Interest Paid in USD − Borrowing Fees`

**Total Net P&L:**

`Total Net P&L = Investment P&L + Funding P&L − Paid Information Costs`

**Final USD Wealth:**

`Final USD Wealth = Available USD Liquidity − Remaining USD Debt Due`

Purchase and sale fees are **already included** in the stock P&L above.

Borrowing fees and interest are part of **Funding P&L**, so they must not be deducted a second time.

If liquidation proceeds do not cover debt due, the game records the unpaid amount and a bankruptcy outcome.

### 4.4 Performance Assessment

| Pillar | Points | Components |
|---|---:|---|
| Financial Performance | 50 | FX return (20); portfolio investment return (30) |
| Risk Management | 10 | Liquidity coverage (4); debt exposure (3); portfolio concentration (3) |
| Decision Quality | 40 | Participation (5); debt utilization (5); signal–allocation alignment (20); position sizing (10) |
| **Total** | **100** | Includes a participation condition for decision-quality scoring |

The code evaluates **FX Return** against total USD funding borrowed and **Portfolio Return** against cumulative Tech purchases, S&P purchases and US Cash deposits.

Allocation quality is also assessed against the game-defined acceptable Tech/S&P/cash weight ranges for each round.

These are the implemented *scoring conventions*, not alternative cash-flow formulas.


