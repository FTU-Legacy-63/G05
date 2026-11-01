# 1. Most important original contribution of each member

| Member | Role | Most important original contribution |
| --- | --- | --- |
| Hoàng Tường Anh | Coordinator, game mechanics designer | Designed the rule set shared by all three phases: 5-minute rounds, whole-lot trader offers, optional paid information, a limited Stay in Cash action, and validation of every trade against cash, inventory and borrowing. |
| Nguyễn Minh Tâm | Data research, financial metrics | Researched the historical evidence and calibrated the numbers behind each phase. Built the source register and the financial metrics used in the scorecards. Full ownership of the financial mechanism, logic in Phase 2. In Phases 1 and 3, impact came from model testing and issue resolution. |
| Trần Thu Anh | Content, logic test | Wrote the period content players read (Amsterdam gazette, Bangkok and Singapore telex, 2024 social posts with paid leads). Checked the financial logic with independent calculations and test cases. Researched the historical and financial contexts of all three phases and wrote the in-game news content. |
| Lê Quỳnh Chi | Backend developer | Turned the financial logic and scoring files into working code: rounds, offers, three-leg FX routes, yen borrowing and repayment, fees, P&L, settlement, the 100-point scoring and debriefs for all three phases. Assembled the three phases into one playable file behind a menu. |
| Hoàng Hà Uyên | Frontend developer | Designed the player-facing interface and the character images in the role introduction. My design and playtest feedback was applied in the build. Worked to ensure that the financial mechanisms underlying the game were logically consistent, that player decisions generated reasonable financial outcomes, and that the overall gameplay experience was both understandable and engaging. By checking the applied logic and financial calculations in the game I could identify areas where the simulation could be improved. |

## 2. What was implemented and how the outputs were connected

All three phases are playable from the start screen to the final scorecard in one HTML file. It runs in the browser with no server, database or live market feed.

- Phase I, Tulip Mania: 3 rounds, $1,000 cash and six traders per round making whole-lot offers. It has $30 paid reports, market indicators, Stay in Cash / Execute Actions, and a crash at the end where unsold tulips are worth $0.
- Phase II, Thai Baht Crisis: 4 rounds, $100,000, and three-leg USD–SGD–THB routes with a 0.05% fee per leg. It has $1,000 paid reports and four onshore/offshore routes in Round 3. Round 4 has no gap, so trading only loses fees.
- Phase III, Carry Trade: 4 rounds plus settlement, starting at $0. Players borrow up to ¥18,000,000, invest in US Tech, the S&P 500 and interest-earning US Cash, and can repay early. The final settlement uses USD/JPY 147 and includes a bankruptcy check.
- Every phase: round debriefs, a 100-point score that judges decisions and not only profit, and a closing economic lesson.

Not implemented, and kept as future work: live market data, adaptive traders, variable spreads, execution delays and automated regression tests.

How the work was connected:

- Storyline & Master Rules (Hoang Tuong Anh): Built the core storyline connecting all three eras, set up the initial Excel model for Phase 3 borrowing and debt repayment, and created the scoring logic for Phases 1 and 3.
- Data Calibration & Independent Phase 2 Design (Nguyen Minh Tam): Led the research and calibration of historical market data across all three phases into balanced numbers suited for classroom play. Nguyen Minh Tam also served as the Lead designed the complete financial engine for Phase 2 (trading mechanism, operational formulas, and 100-point scoring framework).
- Market News & Financial Logic (Tran Thu Anh): Wrote the market news feeds that drive player decisions each round, and co-developed the mathematical formulas for portfolio valuation, P&L, and solvency across Phases 1 and 3.
- Coding & Technical Integration (Le Quynh Chi): Translated all economic models, news systems, and data into clean HTML and JavaScript code. This included building trading routes, enforcing input safeguards (such as blocking negative numbers and overspending), and creating the automated post-game scorecards.
- Visual Design & Independent Testing (Hoang Ha Uyen): Designed character avatars and news layouts on Canva to create an immersive setting. In parallel, independent testing against Excel models verified calculation accuracy, caught edge-case bugs, and smoothed user navigation before release.

## 3. How research, scenario design and testing changed the game

- Financial research changed the scenarios. BIS and Bank of Japan evidence on the August 2024 unwind produced USD/JPY 160 → 142 and US Tech 515 → 345 in Phase III. Repaying a yen loan therefore became a real FX-risk decision. The 1997 two-tier baht market (onshore 25.80 vs offshore 22.75, a +13.41% gap) became the four-route choice in Phase II Round 3.
- Scenario design built a trap into each phase, and tests confirmed it. In Phase II Round 4, trading finished with $107,634 and 77/100, while exiting finished with $107,714 and 88/100. That shows players that fees turn a closed gap into a loss.
- Testing changed the rules.
  - The information report cost more than the best audited trading profit, so the price was cut to $30.
  - Players could pass on every deal and skip a round, so Stay in Cash was added, limited to 2 uses.
  - A $0.01 allocation counted as a trade, so allocations now must be whole dollars within cash.
  - Phase II Round 3 credited only one route, so both profitable directions are now credited.
  - Phase III’s return base left out US Cash deposits, which was corrected.
- Scenario testing of the scoring. Running a passive player, a churner and a strong player against the expected score ranges exposed totals that did not add up and missing cut-offs. Rounding and score-cap scaling were fixed as a result. In Phase I, gameplay testing found a maximum return of about 40%, so full marks were set at 35%.
- Content changed the decision. The period news with paid leads makes Phase I a question of whether a $30 lead is worth buying. That is information asymmetry, which a plain price table would not show.
