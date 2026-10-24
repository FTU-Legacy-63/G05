

## 1. My Main Responsibility

I took ownership of designing and developing Phase 2 (Thai Baht Crisis). I wrote the historical crisis background, built the underlying 5-state logic flow, and worked out the core math for the 3-leg triangular arbitrage (Paths A and B) and the split Onshore/Offshore market. I also created the conversion rate matrix, modeled how transaction fees add up, set up input rules to catch errors, wrote the news and paid intelligence feeds, and designed the full 100-point scoring system with tailored end-of-game lessons.

I led the data research and calibration across all three phases. I gathered historical numbers from trusted research and institutions (Garber, IMF reports, Bank of Thailand, BIS, BOJ, and FRED) and turned them into clean, balanced simulation datasets so the game feels realistic without being overwhelming.

I actively collaborated on Phase 1 and Phase 3. I helped shape the core economic logic and player roles, built and ran Excel models to verify the numbers, and helped spot and fix calculation bugs across the board.

## 2. My Concrete Outputs

### 2.1. Calibrated Operational Datasets (Phases 1–3)

- **Historical Data Research:** I dug into the background of all three crises (Tulip Mania, the 1997 Thai Baht crisis, and the August 2024 Yen Carry Trade unwind) and pulled real-world data from historical papers and major financial bodies like the IMF, BIS, BOJ, FED, Bank of Thailand, and Garber.
- **Economic Assumptions & Data Calibration:** Real-life financial crises take months to unfold and involve messy numbers. Based on our gameplay goals and time limits, I set practical economic assumptions to turn those raw figures into clean, balanced simulation numbers:
  - Scaled the numbers down and compressed the timeline so players can do the math comfortably during each round.
  - Carefully set up the bid/ask spreads, exchange rates, interest rates, and asset prices across rounds to trigger real market dilemmas, pricing gaps, and sudden liquidation squeezes.

### 2.2. Game Logic, Mechanics, Rules & Scoring Framework

**Phase 2 – Thai Baht Crisis (Primary Lead, Designer)**

- **Core Trading Logic & 3-Leg Triangular Arbitrage:** I designed the basic execution flow and financial math for trading across three currencies (USD, THB, SGD). This included both Path A and Path B, along with cross-border routes between the Bangkok Onshore and Singapore Offshore markets.
- **Conversion Rate Matrix Testing:** I set up and ran tests on the conversion rate tables round by round. This helped make sure our theoretical cross-rates were spot-on, so winning directions delivered expected returns while losing paths took realistic hits.
- **Compounded Fee Model:** I built the formula to calculate how exchange fees stack up across all three currency swaps:

  \[
  \text{Total Fee Drag} = \text{Allocated Capital} \times \left[1-(1-\text{Fee Rate})^3\right]
  \]

  This reflects real-life trading costs and makes sure players feel the fee drag when prices settle back to normal.

- **Input Validation & Form Blocking:** I created the rules that block bad inputs right at submission:
  - Rejects negative numbers or text in the capital field.
  - Blocks orders that try to spend more cash than the player actually has.
  - Stops players from submitting without picking a trading path.
  - Automatically locks the form and defaults to "Stay in Cash" if the round countdown reaches zero.
- **Scenario Test Cases (S1–S30):** I wrote a full suite of 30 test cases covering everyday trades, human errors, capital limits, two-tier market traps, and zero-participation penalties.
- **100-Point Scoring Framework:** I developed the full grading system broken into four core areas, complete with leaderboard tiers and end-of-game economic takeaways:

| Scoring Component | Points | Evaluation Criteria |
|---|---:|---|
| Financial Performance | 50 | Net P&L Return (30); Capital Efficiency (20) |
| Arbitrage & Trading Execution | 20 | Two-Tier Market Adaptation (10); Fee Drag Management (10) |
| Decision Quality | 20 | Capital Allocation (8); Exit Timing Discipline (7); Information Use (5) |
| Risk Management | 10 | Cash Buffer (10) |
| **Total** | **100** | |

- **Financial Performance (50 pts):** Split into Net P&L Return (30 pts), measuring profit made on the money actually traded, and Capital Efficiency (20 pts), measuring overall profit relative to the starting $100,000 cash (defaults to 0 if the player never traded).
- **Arbitrage & Trading Execution (20 pts):** Evaluates Two-Tier Market Adaptation (10 pts), spotting the Onshore–Offshore split in Round 3, and Fee Drag Management (10 pts), keeping trading costs reasonable compared to gross gains.
- **Decision Quality (20 pts):** Covers Capital Allocation (8 pts), sizing up positions during big-opportunity rounds; Exit Timing Discipline (7 pts), sitting in cash during Round 4 once prices equalize; and Information Use (5 pts), making smart, cost-effective use of news.
- **Risk Management (10 pts):** Evaluates Cash Buffer (10 pts), keeping a safe cash cushion throughout the game.

### 2.3. Phases 1 & 3 – Tulip Mania & JPY Carry Trade (Co-developer)

- **Core Economic Logic & Rules:** I teamed up with my group to design the underlying mechanics, including the hidden-inventory panic and frozen buyer market in Phase 1, plus the low-interest JPY borrowing, portfolio leverage, and currency reversal shock in Phase 3.
- **Game Roles:** I helped outline the distinct trader profiles, setting up customized cash limits, news prices, and fee structures.
- **Excel Modeling & Bug Fixing:** I tested Excel model sheets across both phases, running cross-phase scenario tests to catch and patch calculation bugs, broken formulas, and timing issues.

## 3. Evidence Links

- **Data Phases 1–3:** [Data Research and Calibration](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.dbzbh4y1cko3)
- **Phase 2 – Logic, Decision Flow, Conversion Rate Matrix, Parameters:** [Phase 2 Design](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.b3qx63u794fl)
- **Phase 2 Scoring:** [Scoring Phase 2](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.vr0yglav7wj5)
- **Phase 2 Scenario Tests:** [Scenario Tests Phase 2](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.213rs79gcz4)

## 4. How My Work Is Used

My outputs provide the empirical, quantitative, and logical foundation for ARBIVERSE's gameplay and evaluation system.

The calibrated datasets across Phases 1–3 transform historical market crises into balanced, actionable trading scenarios. For Phase 2, my game logic, conversion mechanics, and input validation rules establish the operational engine for triangular arbitrage, managing capital allocation and execution constraints. The 100-point scoring framework translates trading outcomes, execution discipline, and risk management into measurable performance metrics and tailored economic debriefs.

Together, these components connect economic assumptions, calculation engines, and automated assessment to deliver a realistic and structured educational experience.

## 5. Integration, Testing and Revision

I worked closely with my team members to test the game logic, financial formulas, and scoring rules across all three phases.

We ran playtests and scenario simulations to check whether the financial results matched actual player choices, helping us catch calculation errors and unexpected edge cases. Based on our test results, I helped fix broken formulas, clean up confusing trading rules, and fine-tune scoring benchmarks to make sure everything ran smoothly.

These tweaks made our calculations much more reliable, kept scoring fair, and improved overall game balance.

## 6. Remaining Limitation

Even though we based the game on real history and tested it carefully, the exchange rates and trading amounts in each round are still fixed. In the real world, prices change every second based on how much people buy and sell, but our game doesn't have that real-time price change yet.

Also, some of our score cutoffs still need more testing with different players. We need more test runs to make sure the score truly shows good financial decisions, not just luck or players finding tricks in the rules to get an easy win.

## 7. Summary of Individual Contribution

My contribution centered on researching and calibrating the operational datasets across all three phases, as well as independently designing the entire framework for Phase 2 (Thai Baht Crisis).

I gathered real historical records and adjusted the numbers into balanced game data so players could experience real market dilemmas within short classroom rounds. For Phase 2, I took full ownership of building the 3-leg triangular arbitrage math, the two-tier Onshore/Offshore currency split, transaction fee formulas, input rules to block invalid entries, and the full 100-point scoring framework. For Phases 1 and 3, I actively tested the game logic and financial formulas in our Excel models, helped shape trading rules, and worked with my teammates to catch and fix calculation bugs.

These outputs connected economic history, calibrated data, and practical trading mechanics with structured financial calculations and clear performance evaluation.
