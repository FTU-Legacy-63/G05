

# Individual Contribution Report — Hoàng Hà Uyên - 2412380051

**Project: ARBIVERSE — An Arbitrage Game Simulation**

## 1. My Main Responsibilities
My main responsibilities in the Arbiverse project focused on **financial logic verification, scenario testing, user flow development, and visual interface design**.
During the initial development stage, I worked with my teammates to brainstorm the game concept, identify the financial education problem, define the project scope and target users, and research relevant financial mechanisms. As the project progressed, I contributed to designing the user flow and interface interactions for the Phase 3 MVP, before extending the user-flow documentation to the complete three-phase game.
In the final development stages, my work focused on reviewing trading mechanisms, identifying potential bugs, developing financial test cases, and designing historical game characters and market news interfaces.
## 2. My Concrete Outputs
### 2.1. Game Mechanics and Logic Review
I reviewed the financial mechanisms across all three phases to evaluate whether the game rules produced reasonable and consistent outcomes.
My analysis focused on the relationship between player decisions, trading restrictions, capital allocation, and financial results. Rather than only checking whether a function worked technically, I also considered whether the mechanics reflected appropriate financial reasoning and encouraged meaningful decisions.
For **Phase 1**, I examined NPC trading offers, cash management, inventory restrictions, and information costs. For **Phase 2**, I reviewed FX trading routes, exchange-rate conversions, transaction fees, and capital limits. For **Phase 3**, I examined JPY borrowing, portfolio allocation, financing costs, and final settlement.
This process helped identify potential logical inconsistencies and supported discussions about improvements to the game's financial mechanisms.
### 2.2. Financial Test Case Development and Consistency Checks
I developed structured testing scenarios and Excel calculation models to examine whether the game's financial results matched the underlying trading rules.

The test cases covered normal trading decisions, capital constraints, transaction costs, cash balances, exchange-rate movements, and end-of-round settlements. I also examined boundary conditions and alternative player strategies to identify potentially unexpected outcomes.
One example was the **Phase 1 Paid News pricing analysis**. By comparing information costs with potential trading profits, I demonstrated that the original $600 information price exceeded the $392 profit identified in a benchmark trading scenario. This analysis supported the team's subsequent reduction of the price to $200.
For Phase 2, I used Excel to verify three-leg currency conversions, transaction fees, round-level P&L, and cash rollover. In Phase 3, I focused on reviewing the consistency between investment returns, allocated capital, borrowing costs, and debt repayment.
These checks provided supporting evidence for evaluating the reliability of the game's financial calculations.

### 2.3. Interface Design

I contributed to the visual identity of Arbiverse by developing character concepts and market-news interfaces suited to the historical environment of each phase.
The character designs reflected three distinct financial settings:

- **Phase 1 — Tulip Mania (1637):** A stylized Dutch tulip trader inspired by seventeenth-century clothing and trading culture.
- **Phase 2 — Thai Baht Crisis (1997):** A currency-market participant reflecting the financial trading environment of Southeast Asia during the Asian Financial Crisis.
- **Phase 3 — Carry Trade (2024):** A modern financial trader representing contemporary currency speculation and investment activities.

I also developed historical news-interface concepts. Phase 1 adopted a traditional Dutch market presentation, Phase 2 used financial fax and telex communication styles, and Phase 3 featured a modern digital financial-news interface. My objective was to create visual distinctions between the phases while maintaining a consistent game identity and making market information more engaging and accessible.

### 2.4. User Flow Development
I contributed to developing the user flow of Arbiverse, particularly during the MVP stage of Phase 3. My work involved mapping how players would navigate the interface, interpret market information, select financial actions, confirm transactions, and receive feedback. For the Phase 3 MVP, I helped define the sequence of player interactions involving JPY borrowing, currency conversion, portfolio allocation, buying and selling assets, and debt management. I also considered how individual buttons and actions should function within this process.
During the final integration stage, I extended the user-flow documentation to all three phases, creating a common player journey while preserving their different financial mechanisms.
This work supported a more coherent interaction structure and helped connect player decisions with the financial outputs displayed by the game.

## 3. Evidence Links

### 3.1. Files Contributed

The following materials represent my main analytical, testing, documentation, and design contributions.

| File / Deliverable | My Contribution |
|---|---|
| Phase 1 Financial Testing | Excel-based scenarios for trading, information costs, cash balances, and P&L verification. |
| Phase 2 Financial Testing | Verification of FX routes, currency conversions, transaction fees, and capital allocation. |
| Bug Identification Document | Documentation of identified issues, their implications, and suggested revisions. |
| User Flow Documentation | Player journey, decision points, interaction sequences, and round progression. |
| Character & News Interface Designs | Historical character concepts and market-news presentation for all three phases. |

### 3.2. File Evidence: Documents Created or Edited
**Financial Testing and Scenario Verification**
- [Phase 1 — Logic Testing and Scenario Checks](https://docs.google.com/spreadsheets/d/19pNVhJkqKKm8KNC2crFjKl85rRt2YlLM/edit)
- [Phase 2 — Financial Testing](https://docs.google.com/spreadsheets/d/1-k_zdxcSb3vkX4zh-KJXiIvMv87RGCXQ/edit)
**Bug Identification**
- [Bug Identification Document](https://docs.google.com/document/d/1ijHxYT5-wR4AT1TDO4IiQ4eN8Vmh835ivXgghOYQQiQ/edit)
**Visual and Interface Design**
- [Game Characters and News Interface — Canva](https://www.canva.com/design/DAHWumkgacQ/8TJe4EMBSaADFr7vEPsTHA/edit)
**User Flow Documentation**
- `user_flow.md` 
## 4. Personal Mark on the Product
My contribution to Arbiverse can be summarized in two areas: **financial reliability and player experience**.
From the financial perspective, I helped the team evaluate whether trading decisions produced consistent and explainable outcomes. My testing scenarios and calculation checks supported the identification of issues involving transaction costs, trading constraints, and capital accounting. From the player-experience perspective, I contributed to structuring the game's user flow and developing historical visual concepts. These outputs helped connect the financial mechanisms with the player's actual interactions, making the three phases easier to navigate and visually distinguish. A particularly meaningful part of my contribution was connecting theoretical financial reasoning with practical gameplay. By examining both the calculation logic and the player's decision-making process, I supported the development of a simulation that was educational as well as interactive.

## 5. What I Actually Did, Week by Week

My responsibilities evolved throughout the seven-week development process, from initial research and planning to MVP interaction design, testing, and final integration.

| Week | Main Focus | My Contribution |
|---|---|---|
| **Week 1** | Idea Development | Collaborated with teammates to brainstorm the financial game concept and explore potential learning objectives. |
| **Week 2** | Problem & Scope Definition | Contributed to identifying the financial education problem, target users, project scope, and relevant financial concepts. |
| **Week 3** | Research & Initial Planning | Supported background research and developed preliminary ideas for user flow, inputs, and player interactions. |
| **Week 4** | Phase 3 MVP Design | Contributed to designing the Phase 3 interface and organizing the main steps of the carry-trade simulation. |
| **Week 5** | Phase 3 Interaction Design | Refined the MVP user flow and defined player actions, button functions, and transaction confirmation steps. |
| **Week 6** | Full Game Integration | Reviewed the integration of all three phases, developed the complete user-flow documentation, and participated in gameplay testing. |
| **Week 7** | Testing & Final Refinement | Reviewed financial logic, documented bugs and test cases, and developed or refined character and market-news interface designs. |

The table summarizes my development journey from early project planning to the final stages of gameplay verification and visual refinement.

## 6. Integration, Testing and Revision

My work was closely connected to the iterative development process.

During financial testing, I examined how changes to trading rules or capital requirements could affect other mechanisms and the resulting player outcomes. When the team revised the gameplay, I reviewed the updated logic and adjusted relevant test scenarios to check its consistency.

Bug identification was also an important part of this process. I investigated potential issues, considered their financial implications, and communicated findings or suggested solutions for team discussion.

For user flow and visual design, I refined interface concepts as the game developed, ensuring that the player journey and historical presentation remained consistent with the implemented mechanics.

Through these activities, I contributed to connecting the team's conceptual design with a functioning and understandable financial simulation.

## 7. What I Personally Learned

Working on Arbiverse helped me understand the difference between learning financial concepts theoretically and implementing them in an interactive simulation. One important lesson was that **a technically functioning mechanism is not necessarily a financially reasonable one**. Trading rules must also be evaluated in terms of incentives, realistic outcomes, and how different player strategies interact.I also improved my ability to develop financial test cases, interpret P&L results, and identify relationships between individual rules and overall game performance.
Beyond financial analysis, designing user flows and historical interfaces strengthened my understanding of user experience. I learned that financial information needs to be both accurate and accessible for players to make meaningful decisions. Finally, the project helped me develop communication and problem-solving skills through collaborative discussions, testing, and revisions.
## 8. Difficulties Encountered and How I Handled Them
One of the main challenges was understanding how different financial mechanisms interacted within the game. Changes to trading limits, information costs, or other rules could affect both profitability and player decisions. To address this, I broke down complex mechanisms into smaller transactions and used Excel to compare expected calculations with actual game outcomes. I also tested alternative strategies and edge cases to identify issues that might not appear during normal gameplay.
Another challenge was designing historically appropriate characters and interfaces, especially since I had limited experience in game design. I researched the visual characteristics of each period, including clothing, color palettes, and communication styles, before developing the designs in Figma and Canva. I also asked a friend majoring in art for feedback on character proportions, colors, and overall composition, which helped me refine the designs.
## 9. Message for Future Generations
For future students undertaking similar projects, I would recommend starting the testing process early and maintaining clear documentation throughout development. Even minor details, such as transaction costs, trading restrictions, or interface interactions, can significantly influence the overall functionality and user experience. Identifying potential issues at an early stage can help reduce unnecessary revisions later.
I would also emphasize the importance of effective teamwork and open communication. Since different components of a project are often closely connected, regular discussions and constructive feedback are essential to ensuring consistency and making improvements.
Finally, I would encourage future students to remain open to exploring areas beyond their academic background. As a finance student, working on Arbiverse allowed me to gain practical experience in visual design, user experience, and financial testing. I believe that being willing to learn new skills, question initial assumptions, and adapt to challenges is just as valuable as the final product itself.



