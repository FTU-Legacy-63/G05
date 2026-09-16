# NHA408E | TECHNOLOGY APPLICATIONS IN FINANCE AND BANKING
## MIDTERM EXAM: Project Readiness & Contribution Verification

- **Group:** 5
- **Team representative:** Hoàng Tường Anh
- **Product:** Arbiverse — Phase III: JPY Carry Trade Simulation Game
- **Date:** 16/09/2026
- **Instructor:** Phan Trần Trung Dũng

---

### A. GROUP VERIFICATION

#### 1. What is the biggest issue your team still needs to solve before Week 6?
The biggest issue our team still needs to solve is to ensure consistency between the financial rules designed in our model and the logic implemented in the game engine.

The most critical case is the timing between floating-interest accrual and debt repayment. According to our intended financial logic, if a JPY loan remains outstanding during a round and is repaid at the end of that round, it must still incur that round’s interest. For example, a loan opened in Round 1 and repaid at the end of Round 2 should include both Round 1 and Round 2 interest, but no Round 3 interest.

However, the current prototype does not yet fully process repayment and interest accrual in this exact order. Therefore, the main issue before Week 6 is to make sure that the implemented game engine follows the financial rules consistently.

#### 2. Why is this issue important?
This issue is important because the financial engine is the core of our product. Almost every final output depends on whether borrowing, interest accrual, repayment, and valuation are processed correctly.

If the timing is inconsistent, the system may calculate the wrong interest expense and repayment amount. This would then affect Funding P&L, Net P&L, Final Wealth, risk indicators, player feedback, and the final score.

It can also affect fairness between players. A player should not be able to avoid one round of interest simply because repayment is processed earlier than interest accrual in the program.

Therefore, before improving the interface or further calibrating the scoring system, we need to make sure that the underlying financial logic produces correct and consistent results.

#### 3. What has your team done about this issue so far?
So far, our team has worked on this issue by first formalizing the financial logic before changing the implementation:
- In Week 4, we defined the intended sequence of each round as: current-round decisions, current-round valuation, floating-interest accrual, repayment, round summary, and then the release of the next round’s data.
- We also created sample calculations and test cases to determine the expected financial result. For example, for a loan opened in Round 1 and repaid at the end of Round 2, we confirmed that the interest should include the rates of both Round 1 and Round 2 only.
- In addition, the prototype separates borrowing, interest, repayment, valuation, and P&L calculations into different parts of the financial engine. This has helped us identify that the key problem is not the interest formula itself, but the order in which these calculations are executed.

#### 4. What will your team do next about this issue?
Before or during Week 6, our team will revise the game engine so that repayment is treated as an end-of-round settlement event rather than being executed immediately when the player selects the repayment option.

The intended sequence will be:
$$\text{Player decisions} \longrightarrow \text{Current-round interest accrual} \longrightarrow \text{Repayment settlement} \longrightarrow \text{Portfolio \& debt calculation} \longrightarrow \text{Round summary} \longrightarrow \text{Next-round data release}$$

After making this change, we will test several repayment paths, including repayment at the end of Round 1, Round 2, Round 4, and repayment only at the End Phase.

For each case, we will compare the game output with our reference financial calculations. We will only consider the issue resolved when the interest expense, repayment amount, Funding P&L, Net P&L, and Final Wealth reconcile correctly.

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
