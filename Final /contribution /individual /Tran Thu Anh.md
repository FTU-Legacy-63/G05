## 1. My Main Responsibility

My primary responsibility was designing and refining game mechanics, market news, and scoring systems across ARBIVERSE's three phases. I also developed financial calculation formulas for Phases 1 and 3 and conducted scenario-based testing to validate game logic, financial calculations, and scoring criteria.

My work focused on translating financial concepts into interactive simulations where players interpret market information, make strategic decisions, manage risks, and experience the financial consequences of their actions.

## 2. My Concrete Outputs

### 2.1. Game Logic and Mechanics

**Phase 1 — Tulip Mania: Reconstructing Historical Speculation**

I redesigned the game logic to better reflect the progression of Tulip Mania, connecting speculative trading, changing market sentiment, and the eventual market crash within a coherent sequence of rounds.

The mechanics require players to consider market timing, information advantages, inventory accumulation, liquidity, and crash exposure. Final wealth incorporates both cash and remaining tulip inventory valued at the post-crash price, ensuring that earlier trading profits do not conceal the risk of holding speculative assets when the market collapses.

**Phase 2 — Triangular FX Arbitrage: Testing and Validation**

My contribution focused on testing the existing game logic rather than leading its design. I reviewed the two triangular currency-conversion routes, transaction costs, and Round 3's onshore/offshore market restrictions to assess their logical consistency. I found the overall mechanics reasonable and supported the validation of the existing design.

**Phase 3 — JPY Carry Trade: Designing from Scratch**

I designed the Phase 3 game logic from the ground up, creating a simulation in which players borrow JPY, convert it into USD, invest in US technology stocks, the S&P 500, or US cash, and manage subsequent debt repayment.

The mechanics require players to consider:

- **Borrowing and financing costs:** Whether to borrow and how interest on outstanding JPY debt affects profitability.
- **FX exposure:** How USD/JPY movements affect the USD obtained when borrowing and the cost of repayment.
- **Portfolio allocation:** How to distribute funds across assets with different return and risk characteristics.
- **Liquidity and repayment:** How much cash to retain to meet debt obligations without unfavorable forced liquidation.
- **Solvency and final wealth:** Whether available assets can cover outstanding debt and how investment returns, FX movements, and borrowing costs determine the final outcome.

These decisions are interdependent. For example, positive equity returns may not translate into an overall profit if JPY strengthens substantially before repayment. The game therefore evaluates the carry trade as a complete financing and investment strategy.

### 2.2. Market News and Information Design

I designed market news across all three phases, adapting its format and information structure to each market environment.

- **Phase 1 — Gossip and Speculative Sentiment:** Designed rumor-driven news reflecting the social dynamics of Tulip Mania. The content encourages players to distinguish potentially useful signals from market hype and consider how sentiment affects trading decisions.
- **Phase 2 — Newspaper-Style Reporting:** Used a formal financial-news format to provide market context without directly revealing the most profitable arbitrage route, requiring players to interpret developments and assess their trading implications.
- **Phase 3 — Contemporary Social Media:** Designed short, social-media-style updates reflecting how investors encounter competing market interpretations. Initial news intentionally leaves room for interpretation, while additional information is designed to clarify specific uncertainties and provide more decision-relevant context.

A key principle was to create **meaningful ambiguity rather than arbitrary confusion**. Additional information should offer a clear reason for players to investigate further, helping them reconsider borrowing, repayment, or portfolio allocation without guaranteeing a profitable outcome.

### 2.3. Financial Calculation Formulas

I developed and refined financial calculation formulas for Phases 1 and 3 to ensure that player outcomes reflect trading results, market movements, financing costs, and outstanding liabilities.

**Phase 1 — Wealth and Trading Performance**

$$
\text{Final Wealth} = \text{Final Cash} + (\text{Remaining Tulips} \times \text{Post-Crash Price})
$$

$$
\text{Net Return} = \frac{\text{Final Wealth} - \text{Initial Wealth}}{\text{Initial Wealth}} \times 100\%
$$

This framework captures both cash and remaining asset value, ensuring that final performance reflects the consequences of holding tulip inventory through the crash.

**Phase 3 — FX, Investment, and Debt**

My work covered the calculations for FX P&L, portfolio investment P&L, portfolio valuation, interest accrual, debt repayment, final wealth, and solvency. These formulas account for the interaction between asset returns, exchange-rate movements, and borrowing costs.

Final wealth deducts the USD value of remaining debt from portfolio and cash value, while solvency compares available liquidation value with outstanding repayment obligations. Return-based measures also help evaluate performance relative to the relevant capital base rather than relying solely on absolute profit.

### 2.4. Scoring System Refinement

I refined the scoring systems to align performance evaluation with the objective and risk profile of each phase. The frameworks distinguish financial performance, risk management, and decision quality, with different weightings reflecting each phase's central challenge.

**Phase 1 — Financial Performance and Trading Execution**

The scoring framework allocates 40 points to Financial Performance, 30 to Arbitrage and Trading Execution, 15 to Decision Quality, and 15 to Risk Management. The emphasis on financial results and trading execution reflects the importance of capturing speculative opportunities, while risk-management criteria account for inventory exposure, liquidity, and drawdown control. I also incorporated an activity-based score cap to reduce incentives for players to achieve high scores simply by avoiding meaningful trading decisions.

**Phase 2 — Arbitrage Profitability and Execution Discipline**

The framework allocates 50 points to Financial Performance, 30 to Risk Management, and 20 to Decision Quality. This prioritizes net returns while recognizing that apparent arbitrage opportunities may become unprofitable after transaction costs or market restrictions. Risk management and decision quality help distinguish effective execution from strategies that overlook trading constraints.

**Phase 3 — Carry-Trade Returns and Decision Quality**

The framework allocates 50 points to Financial Performance, 10 to Risk Management, and 40 to Decision Quality. Financial Performance combines FX Performance (20 points) and Portfolio Investment Performance (30 points). Risk Management covers liquidity, debt exposure, and portfolio risk, while Decision Quality evaluates capital deployment, debt utilization, signal–allocation alignment, and position sizing.

The high Decision Quality weighting reflects the interconnected nature of borrowing, currency exposure, investment allocation, and repayment. A profitable outcome alone does not necessarily indicate a sound strategy; players must also make decisions consistent with the information available at the time.

Across all three phases, I refined scoring definitions to improve consistency with the financial formulas and reduce unintended incentives, while preserving the distinct objectives of each trading environment.

### 2.5. Scenario-Based Testing

I prepared scenario-based test cases to examine game mechanics, financial calculations, and scoring outcomes under different conditions. Testing covered rule consistency, P&L and portfolio valuation, exchange-rate conversions, interest accrual, debt repayment, solvency, and scoring behavior.

I also considered edge cases such as unsold tulip inventory after a crash, adverse FX movements before repayment, and insufficient liquidity to cover debt. These tests helped identify ambiguities and inconsistencies that could be addressed through revisions to rules, formulas, and scoring criteria.

## 3. Evidence Links

- [Phase 1 — Game Mechanics, Formulas, and Scoring](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.4vqdpx5ydm91)
- **Phase 2 — Triangular FX Arbitrage:** [Add verified evidence link]
- [Phase 3 — JPY Carry Trade, Formulas, and Scoring](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.uqh77koqk4wh)
- [Scenario-Based Testing Documentation](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.qtq84zo3l7u0)

## 4. How My Work Is Used

My outputs connect game design, financial calculations, and performance evaluation. Game mechanics define the actions and risks available to players, while market news provides the information environment for their decisions. Financial formulas translate those decisions into measurable outcomes, and the scoring system evaluates profitability, risk management, and decision quality.

Together, these components provide the documented rules and evaluation framework used to implement, test, and refine ARBIVERSE's trading simulations.

## 5. Integration, Testing, and Revision

I reviewed the consistency between game rules, market scenarios, financial formulas, and scoring criteria. I conducted scenario-based testing across Phases 1–3 to identify edge cases and inconsistencies, then refined relevant rules, formulas, and scoring criteria. For Phase 2, my role was to test and validate the existing logic rather than lead its design.

## 6. Remaining Limitation

Some scoring thresholds and performance benchmarks require further calibration against actual gameplay data. Repeated testing would help determine whether the scoring systems consistently distinguish effective strategies from outcomes driven primarily by favorable market movements or excessive risk.

## 7. Summary of Individual Contribution

My contribution focused on designing and validating ARBIVERSE's game mechanics and evaluation framework. I redesigned Phase 1's speculative-market mechanics, tested Phase 2's existing arbitrage logic, and designed Phase 3's carry-trade mechanics from scratch. I also developed phase-specific market news, financial formulas for Phases 1 and 3, scoring criteria across all three phases, and scenario-based testing documentation.

These outputs connect market information and player decisions with measurable financial outcomes and structured performance evaluation.


