
# Individual Contribution Report — Trần Thu Anh

**Project: ARBIVERSE — An Arbitrage Game Simulation**

## 1. Executive Summary of Role and Responsibilities

My primary responsibility was designing and refining game mechanics, market news, financial logic, and scoring systems across ARBIVERSE's three phases. I redesigned the Tulip Mania simulation in Phase 1, tested the existing triangular FX arbitrage logic in Phase 2, and designed the JPY carry trade simulation from scratch in Phase 3. I also developed financial calculation formulas for Phases 1 and 3, refined scoring systems across all three phases, and conducted scenario-based testing to verify that the implemented game logic, parameters, and scoring reflected the intended design.

My work focused on translating real-world financial concepts into interactive simulations where players interpret market information, make strategic decisions, manage risks, and experience the financial consequences of their actions.

## 2. Personal Mark on the Product

My contribution was to ensure that each phase contained the financial logic, information environment, and evaluation mechanisms necessary to create a coherent trading simulation.

### 2.1. Phase 1 — Tulip Mania: Realistic Speculation and Crash Consequences

I developed the game mechanics, financial logic, and market news to represent the progression of speculative trading. I ensured that the mechanics required players to consider market timing, inventory accumulation, liquidity, and crash exposure. The financial calculations accounted for both cash and remaining tulip inventory valued at the post-crash price, ensuring that holding assets through a crash had consequences for final wealth.

The rumor-based news reflected the speculative sentiment surrounding Tulip Mania and encouraged players to interpret information rather than follow every market signal blindly.

### 2.2. Phase 2 — Triangular FX Arbitrage: Spread Prediction and Period-Appropriate News

My contribution focused on designing market news that enabled players to infer and predict currency spreads without directly revealing arbitrage opportunities. I developed information in varied formats, including emails, conversations, and other period-appropriate communications that reflected the context of 1997. These different formats provided clues about market conditions, encouraging players to interpret information and estimate spreads before making trading decisions.

I also tested the existing game logic, reviewing currency-conversion routes, transaction costs, and onshore/offshore market restrictions to assess whether the mechanics remained consistent with the intended arbitrage experience.

### 2.3. Phase 3 — JPY Carry Trade: Integrated Financing and Investment Decisions

I designed the game mechanics, financial logic, and market news from scratch. I ensured that the simulation connected the full carry-trade process: borrowing JPY, converting it into USD, investing across US technology stocks, the S&P 500, or US cash, and repaying the debt.

The mechanics incorporated borrowing costs, exchange-rate exposure, portfolio allocation, liquidity, debt repayment, and solvency. The financial calculations reflected how investment returns, FX movements, and interest expenses jointly determined final wealth.

I also designed social-media-style market news to present competing interpretations of market developments and help players make allocation and borrowing decisions under uncertainty.

### 2.4. Across All Phases — Consistency Between Design and Evaluation

I refined scoring criteria to align with each phase's objectives and risk profile. I also tested whether financial formulas, scoring parameters, and code behavior were consistent with the intended game rules. This helped ensure that performance was evaluated not only by financial outcomes but also by risk management and decision quality where relevant.

## 3. What I Actually Did, Week by Week

### Weeks 1–2 — Assisting in General Game Design

Contributed to the development of ARBIVERSE's overall game design, helping establish the structure and direction of the trading simulation before working on individual phases.

### Week 3 — Building Phase 1

Developed the Tulip Mania mechanics, financial logic, and market news. Focused on representing speculative market behavior, the consequences of holding inventory through a crash, and the relationship between player decisions and final wealth.

### Week 4 — Building Phase 3

Designed the JPY carry trade mechanics, financial calculations, and market news from scratch. Integrated borrowing, currency conversion, investment allocation, interest accrual, repayment, and solvency into a connected gameplay process.

### Week 5 — Retesting Phase 3 and Designing Phase 2 News

Retested Phase 3 after the midterm review to identify and address scoring problems. Also designed market news for Phase 2, aiming to communicate relevant financial information while requiring players to interpret arbitrage opportunities.

### Weeks 6–7 — Final Product Testing and Refinement

Tested the final product to check whether the code correctly reflected the intended game mechanics. Evaluated whether parameters were suitable, checked scoring outcomes for correctness, and revised market news to improve clarity and align it with each phase's theme. This final testing focused on consistency between the design intention and the implemented gameplay experience.

## 4. Files Contributed

My contributions covered the following deliverables:

- **General game design:** Contributions to the overall structure and direction of ARBIVERSE.
- **Phase 1:** Tulip Mania mechanics, financial calculation logic, market news, and scoring framework.
- **Phase 2:** Market news design and testing of the existing triangular FX arbitrage logic.
- **Phase 3:** JPY carry trade mechanics, financial calculations, market news, and scoring refinement.
- **Final testing:** Scenario testing, parameter checks, scoring validation, and market-news revisions.

## 5. File Evidence: Documents Created or Edited

- **Phase 1 — Game Mechanics, Formulas, and Scoring:** [PHASE 1 DESIGN & NEWS](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.4vqdpx5ydm91)
- **Phase 2 — Triangular FX Arbitrage:** [PHASE 2 NEWS](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.p1jb2v28ypr7)
- **Phase 3 — JPY Carry Trade, Formulas, and Scoring:** [PHASE 3 DESIGN & NEWS](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.uqh77koqk4wh)
- **Scenario-Based Testing:** [TESTING](https://docs.google.com/document/d/1YlQwlsCcfVtesl8XTI6wmZ5mdOPjVqJLEY8KQGPG3X8/edit?hl=vi&tab=t.qtq84zo3l7u0)

## 6. What I Personally Learned

I learned how to translate financial concepts into game mechanics that are both realistic and accessible to players. The project strengthened my understanding of how market information, trading decisions, transaction costs, exchange rates, financing, and risk interact to determine financial outcomes. I also learned the importance of testing the implemented product against its original design, particularly when parameters and scoring systems can influence player behavior.

## 7. Difficulties Encountered and How I Handled Them

One of the main challenges was balancing real-world financial accuracy with the simplicity required for an engaging game. Real-world arbitrage, for example, depends on currency-conversion rates, transaction costs, market restrictions, and execution conditions. Translating these factors into a game required preserving the essential logic without overwhelming players with unnecessary complexity. I approached this by focusing on the financial factors most relevant to player decisions and reviewing whether the rules communicated them clearly.

Another challenge was designing market news that was realistic, comprehensible, and consistent with the overall game. News needed to reflect the characteristics of each market while providing enough information for players to make informed decisions without making the correct strategy immediately obvious. I adapted the format and tone to each phase, from speculative rumors in Phase 1 to financial reporting in Phase 2 and social-media-style updates in Phase 3.

Finally, ensuring that the implemented game behaved as intended required repeated testing. I checked parameters, scoring outcomes, and edge cases, then revisited Phase 3's scoring after the midterm review. This helped identify areas where the scoring system needed refinement to better reflect the intended objectives.

## 8. Message for Future Generations

Start by understanding the financial concept you want the game to simulate, then identify the essential decisions and risks players should experience. Do not sacrifice the core logic simply to make the rules easier; instead, simplify the presentation while preserving the important relationships. Design market news around the decisions players need to make, and test the final product against the original design rather than assuming that correct documentation guarantees correct implementation.

## 9. Summary of Individual Contribution

Across seven weeks, I contributed to ARBIVERSE's general game design, built the mechanics, financial logic, and news for Phases 1 and 3, designed market news and tested existing logic for Phase 2, and participated in final product testing. My work focused on making the simulations financially meaningful, the information understandable, and the scoring consistent with the intended player experience. Through iterative testing and refinement, I helped connect financial concepts with the mechanics and evaluation systems used in the final trading simulation.


