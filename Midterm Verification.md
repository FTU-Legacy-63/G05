# NHA408E | TECHNOLOGY APPLICATIONS IN FINANCE AND BANKING
## MIDTERM EXAM: Project Readiness & Contribution Verification

- **Group:** 5
- **Team representative:** Hoàng Tường Anh
- **Product:** Arbiverse — Phase III: JPY Carry Trade Simulation Game
- **Date:** 16/09/2026
- **Instructor:** Phan Trần Trung Dũng

---

### A. GROUP VERIFICATION

## 1. What is the biggest issue your team still needs to solve before Week 6?

**Answer:**
Our biggest issue is **validating and calibrating the existing scoring system so that each score difference is financially meaningful and can clearly distinguish between players with similar returns but different levels of risk-taking and decision quality**.

Our current scoring framework already evaluates three dimensions: **Financial Performance (50 points), Risk Management (30 points), and Decision Quality (20 points)**. However, the remaining challenge is to determine whether the current weights, thresholds, and score ranges are calibrated appropriately.

> For example, two players may achieve a similar final profit, but one may use a highly aggressive strategy with high JPY debt, weak liquidity, and concentrated asset exposure, while another may achieve a similar result with better liquidity and more controlled risk. The scoring system should be able to distinguish these two strategies in a clear and explainable way.

Therefore, the issue before Week 6 is not to redesign the scoring system from the beginning, but to **validate whether the current system correctly translates differences in return, risk, and decision quality into meaningful score differences**.

---

## 2. Why is this issue important?

**Answer:**
This issue is important because the final score is the main evaluation output of the game. If the scoring system is not properly calibrated, it may not accurately represent the quality of the player's financial decisions.

In the JPY carry-trade simulation, final performance depends on several interconnected factors. Players borrow in JPY, invest in USD-denominated assets, and are exposed to changes in funding cost, asset prices, and the USD/JPY exchange rate. A movement in USD/JPY changes the USD value of the player's JPY repayment obligation, while asset-price movements affect Investment P&L and floating interest affects Funding P&L.

This means that **profitability and decision quality are not always the same thing**. A player may earn a high profit because the simulated market moves strongly in their favor, even if they took excessive debt or concentration risk. Another player may earn a slightly lower return while maintaining better liquidity, lower debt exposure, and a more balanced portfolio.

If the scoring system gives too much weight to final profit, players may be encouraged to maximize risk rather than understand the trade-off between return, funding cost, FX exposure, liquidity, and portfolio risk.

Therefore, validating the scoring system is necessary to ensure that the final score is **fair, financially meaningful, and consistent with the learning objective of the game**.

---

## 3. What has your team done about this issue so far?

**Answer:**
So far, our team has already developed the main structure of the scoring system rather than evaluating players only by final profit.

First, we separated the player's final financial result into **Investment P&L** and **Funding P&L** so that we can identify whether the result comes from asset performance or from the JPY funding position.

Second, we designed a 100-point scoring framework consisting of:

- **Financial Performance: 50 points**
- **Risk Management: 30 points**
- **Decision Quality: 20 points**

Risk Management is further evaluated through factors such as **liquidity, JPY debt exposure, and portfolio concentration**. Decision Quality considers factors such as **capital efficiency, debt timing, information use, and action discipline**.

We have also developed rule-based feedback so that the final result does not only show a score, but also explains what the player did well and what could be improved.

In addition, we have reviewed sample strategies with different combinations of return and risk. This helped us identify the remaining question: whether the current score bands and weights are sensitive enough to distinguish between strategies that produce similar financial outcomes but involve different levels of risk.

Therefore, the scoring structure itself has already been designed. What remains is to **test and calibrate it systematically**.

---

## 4. What will your team do next about this issue?

**Answer:**
Before or during Week 6, our team will conduct structured scenario testing to validate and calibrate the scoring system.

We will compare players under controlled scenarios where only one important factor changes at a time. For example:

1. **Similar return, different risk:** two players earn similar Net P&L, but one has higher debt exposure, weaker liquidity, or greater asset concentration.
2. **Similar risk, different return:** two players take comparable levels of risk but achieve different financial results.
3. **High-return, high-risk versus moderate-return, controlled-risk:** to test whether the scoring system appropriately balances return and risk.
4. **Adverse market conditions:** to test how the scoring system responds when USD/JPY, asset prices, and funding costs move against the player.

Based on these tests, we will review the score thresholds and weights and adjust them if necessary.

We will also check whether small score differences are explainable. For example, if one player receives **96 points and another receives 97 points**, the additional point should come from a measurable difference such as stronger liquidity, lower debt exposure, better diversification, or more disciplined decision-making.

> Our Week 6 objective is therefore to make sure that the scoring system is not only mathematically complete, but also **consistent, explainable, and fair across different player strategies**.

---

### B. MEMBER CONTRIBUTION VERIFICATION

| Member | What did this member actually produce? | How is it used in the project? | What can this member personally explain, calculate, demonstrate, or reproduce? |
| :--- | :--- | :--- | :--- |
| **Hoàng Tường Anh** | Led the team in defining the overall decision flow of the game, co-designed the core financial logic, and supported the development of key assumptions. | His work determines how a player moves through each round: receive market information $\rightarrow$ decide whether to purchase additional information $\rightarrow$ borrow JPY $\rightarrow$ allocate funds to Tech, S&P 500, or US Cash $\rightarrow$ manage existing positions $\rightarrow$ decide whether to repay debt $\rightarrow$ close the round. The financial logic also determines how these decisions affect Free Cash, asset holdings, JPY debt, floating interest, P&L, and player status. | Can explain the complete game flow, justify the order of player decisions, demonstrate how borrowing/trading/repayment changes the game state, calculate key financial outputs, and explain the rationale behind the main game assumptions. |
| **Trần Thu Anh** | Designed the simulated market scenarios and developed assumptions for BOJ interest rates, USD/JPY movements, Tech prices, S&P 500 prices, and US Cash returns across the rounds. | Her work creates the market environment faced by players. BOJ rates determine JPY funding cost, USD/JPY determines FX exposure and the USD value of JPY debt, Tech and S&P prices create investment gains or losses, and US Cash returns provide a defensive investment alternative. | Can explain how each round's market scenario was constructed, justify the assumptions and simulated movements, reproduce the round-by-round market inputs, and demonstrate how changes in these variables affect player outcomes. |
| **Nguyễn Minh Tâm** | Conducted data analytics to support and validate the market assumptions and simulated inputs used in the game, including interest rates, FX rates, and asset-price movements. | Her analysis is used to assess whether the simulated values are financially reasonable and internally consistent before they are incorporated into each round. It supports the calibration of BOJ rates, USD/JPY, Tech, and S&P 500 movements and helps prevent unrealistic scenarios that could distort P&L or risk exposure. | Can explain the data-analysis process, reproduce key calculations and comparisons, assess whether a simulated market input is reasonable, and demonstrate how the analytical results were used to validate or revise the scenarios. |
| **Lê Quỳnh Chi** | Designed the user flow and interface structure of the game, including player inputs, round navigation, market-information display, decision sections, and result presentation. | Her work converts the financial engine into an interface that players can actually use. It determines how users view current-round information, enter borrowing and investment decisions, manage their portfolio and debt, proceed between rounds, and view P&L and final results. | Can demonstrate the complete user journey, explain how each screen connects to the game logic, show how player inputs are collected and validated, and reproduce the structure of the round and final-result interfaces. |
| **Hoàng Hà Uyên** | Developed the testing and player-evaluation framework, including financial logic test cases, P&L checking, final feedback, and the scoring structure. | Her work is used to verify whether borrowing, trading, interest, repayment, and End Phase settlement operate correctly. It also supports the final evaluation system, which separates Investment and Funding P&L and evaluates players through Financial Performance, Risk Management, Decision Quality, and rule-based feedback. | Can reproduce key test cases, verify whether financial outputs reconcile correctly, demonstrate how errors or invalid actions are identified, and explain how the final feedback and scoring system evaluate player performance. |
	`
