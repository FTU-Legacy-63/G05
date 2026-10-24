
# Bug Status, Fixes & Verification Record

## 1. Phase 1 — Tulip Mania

### 1.1 Documented fixes and improvements

| ID | Problem identified | Implemented correction | Status / verification |
|---|---|---|---|
| **P1-01** | Information previously cost **$600**, greater than the 392maximumtradingprofitintheauditedofferscenario.|Reducedtheprivate-newspriceto**200/report**, making one purchase economically recoverable under the best audited strategy. | **Fixed (build comparison)**; pricing and profit cross-checked in Phase 1 Excel. |
| **P1-02** | Progressing a round required at least one accepted trade, limiting deliberate capital preservation. | Added explicit **Stay in Cash** and **Execute Actions** options before opening the trader offers. | **Fixed (build comparison)**; action controls and bindAction(). |
| **P1-03** | The earlier interaction did not provide a structured way to reconsider a trade-action selection. | Added **Change action**, available before any trade has been executed in that round. | **Fixed (build comparison)**; renderAction() and bindAction(). |
| **P1-04** | End-round controls did not clearly distinguish committing a cash decision from confirming trading activity. | Added conditional trading-panel display, confirmation state, action-dependent end-round button and explanatory guidance. | **Fixed (build comparison)**; updateLockBtn(), lockFooter. |
| **P1-05** | Inactivity and round decisions needed a record suitable for scoring and review. | Added roundStays, action and actionConfirmed to round state; a no-trade round is recorded as a cash decision. | **Fixed (build comparison)**; endRound(). |

### 1.2 Financial safeguards established in the current implementation

| ID | Issue prevented or controlled | Current implementation / expected outcome | Status |
|---|---|---|---|
| **P1-06** | Selling tulips the player does not own | A sell offer is rejected if state.tulips < offered quantity. Starting inventory is **zero**, so a player must first acquire tulips. | **Present (source check)** |
| **P1-07** | Purchases beyond available cash | A purchase is rejected if the full NPC offer value exceeds cash; no negative-cash purchase is recorded. | **Present (source check)** |
| **P1-08** | Duplicate execution of one NPC offer | Resolved and accepted offers are tracked so the same offer cannot be used repeatedly within its round. | **Present (source check)** |
| **P1-09** | Treating sale receipts alone as profit, or ignoring cost basis | The replay/scoring logic reconstructs purchase lots, sale proceeds and realised results; the financial audit reconciles offer-level cash movements. | **Present + Verified (selected calculations)** |
| **P1-10** | Ignoring unsold inventory after the crash | Final wealth includes **ending cash + remaining tulips × post-crash valuation** (less any applicable debt). | **Present (source check)** |
| **P1-11** | Buying private information without sufficient funds | Selected reports are checked against available cash, and paid reports are tracked to avoid repeat charges for the same unlock. | **Present (source check)** |
| **P1-12** | Awarding a normal high score without meaningful gameplay | The final score applies an **Activity Score Cap** to the raw scoring result. | **Present (source check)** |

---

## 2. Phase 2 — Thai Baht Crisis

### 2.1 Documented fixes and improvements

| ID | Problem identified | Implemented correction | Status / verification |
|---|---|---|---|
| **P2-01** | Fractional allocations such as **0.01**couldcountasatradingdecision.|AddedCAPSTEP=1000;acceptedallocationsarein**1,000 increments**. | **Fixed (build comparison)**; validateCapInput(). |
| **P2-02** | User-entered allocations could be awkward when they exceeded wallet balance or the trading limit. | The input now snaps to the highest permitted $1,000 step, respecting **available cash and the $50,000 round cap**. | **Fixed (build comparison)**; maxAllocation(). |
| **P2-03** | Round 3 originally displayed only two cross-market choices. | Expanded the two-tier market to **four routes (A, B, C and D)**, while retaining the two standard paths in other rounds. | **Fixed (build comparison)**; STRATS and route selector. |
| **P2-04** | New options needed actual executable conversion chains, not just UI labels. | Added the conversion-leg definitions for the additional routes, with each leg using its designated Onshore/Offshore quote. | **Fixed (build comparison)**; Finance.legs(). |
| **P2-05** | Evaluating only one "optimal" route could misclassify a second profitable Round 3 strategy. | Added an alternative optimal route through optimalAlt and isOptimal(). | **Fixed (build comparison)**; optimal-path checks. |
| **P2-06** | Capital-control adaptation scoring did not cover all four cross-market choices. | Both valid profitable directions are recognised for the full adaptation score; reversed directions are treated consistently. | **Fixed (build comparison)**; computeScore(). |
| **P2-07** | News-use and opportunity assessment depended on direct equality with a single route ID. | Updated scoring checks to use the route-aware optimality helper. | **Fixed (build comparison)**; isOptimal() in scoring. |
| **P2-08** | Cross-market diagrams could be unclear about where each conversion occurred. | Added **Onshore/Offshore venue labels** to the currency-conversion pipeline. | **Fixed (build comparison)**; renderPipeline(). |
| **P2-09** | Round results gave limited visibility into why a particular currency path worked. | Expanded the debrief to show **quoted vs implied SGD/THB rates, market discrepancy, trading breakdown and optimal route(s)**. | **Fixed (build comparison)**; renderRoundDebrief(). |
| **P2-10** | Allocation entry and news-purchase feedback could be difficult to follow. | Improved $1,000-step input controls and paid-information unlocking feedback, including a visible cash-balance update. | **Fixed (build comparison)**; ticket and news UI. |
| **P2-11** | The round summary needed to reflect that either of two R3 routes could be successful. | Updated result descriptions to list alternative optimal choices rather than displaying only one route. | **Fixed (build comparison)**; debrief and final feedback. |

### 2.2 Financial validation and existing safeguards

| ID | Test condition | Expected or independently checked result | Status |
|---|---|---|---|
| **P2-12** | Correct three-leg conversion with fees | Gross Profit = Gross Final USD − Allocated USD; fee is calculated by the game's formula Capital × [1 − (1 − feeRate)^3]. | **Verified (calculation)** |
| **P2-13** | Incorrect or oversized order | Reject invalid/negative input; do not confirm a route until capital has been confirmed; allocation cannot exceed cash or round cap. | **Present (source check)** |
| **P2-14** | Double-counting paid-news cost in cash | Report cost reduces available cash when purchased; settlement deducts its effect from net profit without charging the wallet a second time. | **Present + Verified (selected ledger cases)** |
| **P2-15** | Capital not flowing correctly into the following round | Settlement returns the closed FX loop to USD, retains idle cash, subtracts fees, and carries the resulting cash balance forward. | **Verified (calculation)** |
| **P2-16** | Divide-by-zero when a player makes no trade | No-trade round return is set to **0%** when allocated capital is zero. | **Present (source check)** |
| **P2-17** | Lack of termination protection when funds are exhausted | A non-positive ending cash balance triggers the insolvency result branch. | **Present (source check)** |

### 2.3 Phase 2 benchmark — Financial reconciliation

| Round | Decision | Allocated USD | Approximate net P&L |
|---|---|---|---|
| R1 | Path B | 50,000|+306.93 |
| R2 | Path A | 50,000|+782.18 |
| R3 | Route A | 50,000|+6,625.09 |
| R4 | Stay in Cash | $0 | $0.00 |
| **Final** | **No paid news** | — | **+$7,714.20; score 88/100** |

---

## 3. Phase 3 — Carry Trade

### 3.1 Documented financial correction

| ID | Problem identified | Implemented correction | Status / verification |
|---|---|---|---|
| **P3-01** | Portfolio-performance numerator included **US Cash interest**, while the denominator could include only stock-purchase capital. This could exaggerate investment returns. | The return base now includes **Tech purchase cost + S&P 500 purchase cost + US Cash deposits**. The same basis is used in the result display. | **Fixed (build comparison)**; scorePortfolioPerformance() and final metrics. |

### 3.2 Existing safeguards and settlement logic

The following are important financial controls verified in the reference code. They demonstrate **what the game currently handles**, not necessarily separate, dated bug fixes.

| ID | Test condition | Implemented behaviour | Status |
|---|---|---|---|
| **P3-02** | Borrowing exceeds funding capacity | JPY borrowing is constrained by the outstanding-principal limit; approved loan value is converted using the current USD/JPY quote. | **Present (source check)** |
| **P3-03** | Borrowing cost omitted | The loan quotation applies the origination fee; periodic JPY interest is accrued and included in repayments. | **Present + Verified (selected calculation)** |
| **P3-04** | Stock order exceeds available USD | Tech/S&P buy orders include their transaction fees and are rejected if total cost exceeds Free Cash. | **Present (source check)** |
| **P3-05** | US Cash movement produces artificial money | Deposits move funds from Free Cash to US Cash; withdrawals reverse the transfer, while earned interest is accounted for separately. | **Present (source check)** |
| **P3-06** | Loan repayment ignores interest or currency conversion | Repayment accounts for JPY principal and accrued/current interest, converted at the applicable USD/JPY rate. | **Present (source check)** |
| **P3-07** | Open positions and debts remain unsettled at game end | A dedicated final settlement liquidates assets using settlement prices and processes remaining JPY liabilities. | **Present (source check)** |
| **P3-08** | Insufficient final liquidity goes unreported | The settlement flow includes a bankruptcy/unpaid-debt result where applicable. | **Present (source check)** |
| **P3-09** | Final P&L mixes financing and investment outcomes | The breakdown reports investment gains/losses separately from FX funding gains/losses, interest, fees and information cost. | **Present (source check)** |

---

## 4. Shared User Experience and Testing Improvements

| ID | Area | Improvement visible in the current game | Evidence status |
|---|---|---|---|
| **UX-01** | Information interfaces | Period-inspired market news: historical newspaper in Phase 1, fax/telex-style information in Phase 2, and modern market information in Phase 3. | **Present (source/design)** |
| **UX-02** | Decision guidance | Market indicators, round-specific instructions, action confirmation, trading visuals and user-facing validation messages. | **Present (source)** |
| **UX-03** | Round outcomes | Phase-specific debriefs connect player decisions with financial results and next-round progression. | **Present (source)** |
| **UX-04** | Final outputs | P&L breakdowns, scoring components and qualitative feedback provide a reviewable result for each phase. | **Present (source)** |
| **UX-05** | Independent evidence | Calculation workbooks and a structured test report document representative player scenarios and edge cases. | **Verified (selected cases)** |



