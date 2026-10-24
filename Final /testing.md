
# Arbiverse — Game Logic & Testing

**Scope:** Phase 1 — Tulip Mania; Phase 2 — Thai Baht Crisis; Phase 3 — Carry Trade

**Purpose:** Validate financial calculations, player decisions, scoring, and edge cases.

---

## 1. Testing Approach

| Method | Coverage | Result |
|---|---|---|
| Source review | Rules, transaction constraints, decision flow, scoring formulas | Completed |
| JavaScript syntax check | Embedded scripts in all three phases (`node --check`) | **PASS** |
| Independent financial calculations | Phase 1 trading/news cases; Phase 2 three-leg FX conversions | **PASS** for benchmark cases |
| Execution of Phase 2 scoring function | $1,000 and $50,000 allocation scenarios | **PASS**: matches reported scores |
| Browser playthrough | Buttons, timers, popups, reload, responsive layout | **Not independently verified** |

**Status key:**

- **PASS** = Checked against source or calculated output.
- **REVIEW** = Known design/scoring concern.
- **MANUAL** = Requires an interactive browser run.

A passing calculation does not imply every UI path has been tested.

---

## 2. Phase 1 — Tulip Mania

**Rules checked:** $1,000 starting cash; three trading rounds; $200 per paid information purchase; end-of-game tulip valuation at $15 each; trading limited by available cash, inventory, and NPC offers.

### 2.1 Core Game Testing

| # | Scenario to Test | Expected Result | Status |
|---|---|---|---|
| 1 | Player skips additional information | No information cost; no additional information revealed | MANUAL |
| 2 | Player purchases additional information | Information cost deducted; additional information revealed | MANUAL |
| 3 | Player tries to buy information with insufficient cash | Purchase is rejected | MANUAL |
| 4 | Player chooses no leverage | No debt; purchasing power equals cash balance | REVIEW |
| 5 | Player chooses maximum leverage | Borrowing and debt are recorded correctly | REVIEW |
| 6 | Player accepts a BUY offer with enough tulips | Tulips decrease; cash increases | MANUAL |
| 7 | Player accepts a BUY offer with insufficient tulips | Offer is rejected | MANUAL |
| 8 | Player accepts a SELL offer with enough cash | Cash decreases; tulips increase | MANUAL |
| 9 | Player accepts a SELL offer using leverage | Purchase is allowed; borrowed amount becomes debt | MANUAL |
| 10 | Player tries to accept a SELL offer without enough purchasing power | Offer is rejected | MANUAL |
| 11 | Player rejects an offer | No change to portfolio; offer remains available | MANUAL |
| 12 | Player tries to accept the same offer twice | Second attempt is rejected | MANUAL |
| 13 | Player accepts multiple different offers | Each accepted offer is processed correctly | MANUAL |
| 14 | Player combines a buy offer and sell offer to arbitrage | Correct arbitrage profit is generated | MANUAL |
| 15 | Player chooses an offer with no arbitrage opportunity | Trade is processed normally; no artificial arbitrage profit | MANUAL |
| 16 | Player buys tulips and holds them | Tulip holdings remain unchanged until the next decision | MANUAL |
| 17 | Player sells part of their holdings | Only the selected quantity is deducted | MANUAL |
| 18 | Player reaches the maximum leverage limit | Additional borrowing is not allowed | REVIEW |
| 19 | Player incurs information costs and trading costs in the same phase | Cash is reduced correctly for all applicable expenses | MANUAL |
| 20 | End of Phase 1 | Cash, tulip holdings, tulip value, and debt are calculated correctly | MANUAL |
| 21 | End of Phase 2 | Updated position is correctly carried forward from Phase 1 | MANUAL |
| 22 | End of Phase 3 | Final pre-crash position is calculated correctly | MANUAL |
| 23 | Player holds tulips through the crash | Remaining tulips are valued at $20 each | MANUAL |
| 24 | Player sells all tulips before the crash | No tulip value remains after the crash | MANUAL |
| 25 | Player has outstanding debt after the crash | Debt is deducted from final wealth | MANUAL |
| 26 | Player finishes with cash only | Final wealth equals cash balance minus outstanding debt | PASS |
| 27 | Player finishes with tulips and cash | Both are included in final wealth | PASS |
| 28 | Player makes no trades in a phase | Portfolio carries forward unchanged | MANUAL |
| 29 | Player uses high leverage and holds tulips until the crash | Large potential loss is correctly reflected in final P&L | MANUAL |
| 30 | Player executes a profitable arbitrage strategy | Final P&L reflects the realized arbitrage profit | MANUAL |
| 31 | Player executes a loss-making strategy | Final P&L correctly reflects the loss | MANUAL |
| 32 | Player decisions do not affect market indicators | Speculation, liquidity, confidence, and market prices remain determined by the scenario | PASS |
| 33 | Different player strategies are tested | Different decisions produce different portfolio outcomes | MANUAL |
| 34 | Player enters invalid input or makes an invalid decision | System prevents the action and does not corrupt the portfolio | MANUAL |

### 2.2 Bankruptcy and Solvency Testing

| # | Scenario to Test | Expected Result | Status |
|---|---|---|---|
| B01 | Liquidation value exceeds debt due | Player remains in the game | PASS |
| B02 | Liquidation value equals debt due | Player remains in the game | PASS |
| B03 | Liquidation value is below debt due | Player is declared BANKRUPT | PASS |
| B04 | Player has insufficient cash but enough asset value | Player is not bankrupt if total liquidation value covers debt due | REVIEW |
| B05 | Player uses high leverage and has insufficient assets | Player is declared BANKRUPT if liquidation value is below debt due | PASS |
| B06 | Player becomes bankrupt in Phase 1 | Game ends for that player; Phase 2 is not played | MANUAL |
| B07 | Player becomes bankrupt in Phase 2 | Game ends for that player; Phase 3 is not played | MANUAL |
| B08 | Player becomes bankrupt in Phase 3 | Game ends; result is recorded | MANUAL |
| B09 | Player becomes bankrupt after accepting an offer | Trade is recorded, then bankruptcy is checked | REVIEW |
| B10 | Bankrupt player's final result is calculated | Performance and Final Score are still recorded | REVIEW |

**Accounting check:**

`Final Wealth = Ending Cash + (Remaining Tulips × $15) − Outstanding Debt`

`Net P&L = Final Wealth − $1,000`

Paid information reduces cash and therefore final profit.

---

## 3. Phase 2 — Thai Baht Crisis

**Objective:** Verify route selection, three-leg FX conversions, transaction costs, cash rollover, information purchases, capital limits, and the 100-point scoring model.

**Game parameters:**

- Starting cash: **$120,000**
- Duration: **4 rounds**
- Maximum allocation: **$50,000 per round**
- Trade-size increment: **$1,000**
- Fee per FX leg: **0.05%**
- Paid information: **$600 per report**
- Rounds 1, 2, and 4: **Path A / Path B**
- Round 3: **Four Onshore/Offshore routes**
- **Stay in Cash** is a separate action.

### 3.1 Trading and Validation Tests

| ID | Test Case | Expected Result | Status |
|---|---|---|---|
| P2-01 | Enter $0.01, $999, or $1,500 | Invalid sizes cannot be executed; completed trade must respect the $1,000 increment | PASS — source |
| P2-02 | Enter $1,000 and $50,000 | Boundary amounts satisfy the trade-size rule | PASS — source |
| P2-03 | Request $51,000 or more than available cash | Round cap and available-cash constraints prevent over-allocation | PASS — source |
| P2-04 | R1: Path B with 50,000|NettradingP&L**+306.93** | PASS — calculated |
| P2-05 | R2: Path A with 50,000|NettradingP&L**+782.18** | PASS — calculated |
| P2-06 | R3: Route A / Route D with 50,000|**+6,625.09 / +$6,622.18** | PASS — calculated |
| P2-07 | R3: Route B / Route C with 50,000|**-5,983.30 / −$5,981.03** | PASS — calculated |
| P2-08 | Buy one paid report | Deduct **$600**; preserve the quoted FX rates and route mechanics | PASS — source |
| P2-09 | Select Stay in Cash | No conversion or FX transaction fee; capital remains available next round | PASS — source |
| P2-10 | Reach R4 and trade instead of exiting | Any small gross spread is offset by transaction fees; R4 exit-discipline score is lower | PASS — calculated / source |
| P2-11 | Let timer expire after two manual cash stays | Automatic cash settlement may bypass the manual stay limit | REVIEW |
| P2-12 | Replay the same route/capital sequence | Expected identical returns and score; interactive confirmation required | MANUAL |

**R3 naming convention:**

- Displayed **Route A** = `CROSSB`
- Displayed **Route B** = `CROSSA`
- Displayed **Route C** = `CROSSC`
- Displayed **Route D** = `CROSSD`

Use the display labels in screenshots and the internal identifiers when inspecting code.

### 3.2 Independent Calculation and Cash Reconciliation

The finance engine executes **three conversions** and then subtracts transaction cost and information cost:

**Gross Final USD:**

`Gross Final USD = Allocated USD × conversion factor 1 × factor 2 × factor 3`

**Gross P&L:**

`Gross P&L = Gross Final USD − Allocated USD`

**FX Fees:**

`FX Fees = Allocated USD × [1 − (1 − 0.0005)^3]`

**Round Net P&L:**

`Round Net P&L = Gross P&L − FX Fees − (Paid Reports × $600)`

**Ending Cash:**

`Ending Cash = Starting Cash + Round Net P&L`

Each conversion factor is a multiplication or division according to the quoted currency pair.

**Important:** The code applies the three-leg fee formula to the initial allocation, rather than reducing the converted amount after each leg. The audit workbook uses the same convention.

**Benchmark:** $50,000 allocated in each of the first three rounds; correct routes; no purchased reports; cash exit in R4.

| Round | Decision | Allocated | Net P&L | Approx. Cash After Round |
|---|---|---|---|---|
| R1 | Path B | 50,000|+306.93 | $120,306.93 |
| R2 | Path A | 50,000|+782.18 | $121,089.11 |
| R3 | Route A | 50,000|+6,625.09 | $127,714.20 |
| R4 | Stay in Cash | $0 | $0 | $127,714.20 |

*Displayed values are rounded to cents; calculations retain full precision. The total benchmark P&L is approximately **+$7,714.21**.*

As a route-direction check, R3 quotes are:

- **USD/THB Onshore:** 25.80
- **USD/THB Offshore:** 22.75

THB is therefore cheaper to buy Onshore.

Routes A and D exploit this direction; B and C reverse it and lose money.

Public and paid news should be checked against this quote interpretation during a manual playthrough.

---

## 4. Phase 3 — Carry Trade

**Objective:** Reconcile JPY borrowing, USD funding, equity transactions, US Cash interest, debt repayment, final liquidation, and the three scoring pillars.

**Core parameters:**

- Initial Free Cash: **$0**
- Maximum outstanding JPY principal: **¥18,000,000**
- Borrowing origination fee: **0.01%**
- Equity buy/sell fee: **0.05%**
- Paid information: **$600 per item**
- Duration: **4 rounds**

Four rounds use changing USD/JPY, BOJ rates, asset prices, and US Cash returns.

### 4.1 Borrowing, Trading, and Settlement Cases

| ID | Test Case | Expected Result | Status |
|---|---|---|---|
| P3-01 | Select Round 1 borrowing | 25%, 50%, 75%, or 100% loan package; **0% is unavailable in R1** | PASS — source |
| P3-02 | Borrow more than remaining capacity | Outstanding principal cannot exceed ¥18,000,000; repaid principal restores borrowing capacity | PASS — source |
| P3-03 | Borrow JPY and convert to USD | USD credited at current USD/JPY, **minus** the one-time 0.01% fee | PASS — calculated |
| P3-04 | Buy US Tech or S&P 500 | Purchase cost includes 0.05% fee; reject orders exceeding Free Cash | PASS — source |
| P3-05 | Sell stocks | Holdings fall and Free Cash rises by net sale proceeds after 0.05% fee | MANUAL |
| P3-06 | Deposit / withdraw US Cash | Transfer between Free Cash and US Cash; only US Cash earns the round's specified return | PASS — source |
| P3-07 | Accrue BOJ interest over a round | Each open loan earns `principal × annual BOJ rate × months/12` in JPY | PASS — source / calculated |
| P3-08 | Repay early | Repayment covers principal plus previous accrued interest **and current-round interest** | PASS — source |
| P3-09 | Finish R4 with open assets/debt | Use **separate end-phase settlement prices**; sell assets, withdraw US Cash, then settle JPY debt | PASS — source |
| P3-10 | Finish with insufficient funds for JPY repayment | Bankruptcy and unpaid-debt amounts are reported | PASS — source; MANUAL UI |
| P3-11 | Borrow but never invest | FX outcome may be scored; portfolio points and meaningful-investment participation are restricted | PASS — source |
| P3-12 | Recycle one deposit or move funds repeatedly | Cumulative capital-deployed count may increase without matching new exposure | REVIEW |

**Important scope note:**

`Never borrow → zero score` is implemented as an inactivity branch, but it is not a normal playable R1 choice because the first-round borrowing selection starts at 25%.

Interface tests should therefore focus on the available loan packages.

### 4.2 Worked Financial Checks

#### 4.2.1 Borrowing Example — Round 1

A 25% loan of ¥18 million equals **¥4,500,000**.

At USD/JPY = 150:

**Gross USD Funding:**

`¥4,500,000 / 150 = $30,000.00`

**Origination Fee:**

`$30,000 × 0.0001 = $3.00`

**Net Free Cash:**

`$30,000 − $3 = $29,997.00`

**Round 1 Accrued Interest:**

`¥4,500,000 × 0.001 × (3/12) = ¥1,125`

This is an independently calculated check using the R1 rate and duration, **not a claim that the full browser flow was played**.

For early repayment, the program adds the current round's interest even when earlier interest was already accrued.

#### 4.2.2 Final Accounting

Final accounting follows the game's `computeBreakdown()` logic.

**Tech P&L:**

`Tech P&L = Total Tech sale proceeds − Total Tech purchase costs`

**S&P P&L:**

`S&P P&L = Total S&P sale proceeds − Total S&P purchase costs`

**Investment P&L:**

`Investment P&L = Tech P&L + S&P P&L + US Cash interest`

**FX P&L:**

`FX P&L = USD value of JPY principal when borrowed − USD value of that principal when repaid`

**Funding P&L:**

`Funding P&L = FX P&L − JPY interest paid in USD − origination fees`

**Net P&L:**

`Net P&L = Investment P&L + Funding P&L − Paid Information Cost`

Stock purchase costs and sale proceeds already incorporate their transaction fees.

At final settlement:

1. Assets are sold at `SETTLEMENT_PRICES`, which can differ from R4 displayed prices.
2. Outstanding JPY debt is converted at the settlement FX rate.
3. Final USD wealth is calculated.

**Final USD Wealth:**

`Final USD Wealth = Available Liquidity − Final USD Debt`



