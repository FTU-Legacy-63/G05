## 1. PRODUCT SCOPE

**Overview:** Phase 3 is a JPY Carry Trade simulation game spanning 4 rounds. Players borrow JPY, convert it to USD, and manage loans and asset trades amidst changing market conditions.
* Carry build-up
* Crowded carry
* Carry unwind
* Recovery
* End phase settlement

**Core Loop:** Read Market Info → Borrow JPY → Manage Loans → Trade Assets → Market Update → Track P&L & Debt → End Phase Settlement. 

---

## 2. MAIN FEATURES AND SUPPORTING FEATURES

### Main features
* Select a player role with unique financial constraints.
* Borrow JPY and manage multiple loan packages across rounds.
* Buy / Sell / Hold US risk assets (US Tech, S&P 500).
* Deposit / Withdraw / Hold defensive assets (USD Cash).
* Hold / Repay open JPY loans (requires selling assets for liquidity if needed).
* Track real-time Portfolio Value, USD Debt, Net Wealth, and Player Status.

### Supporting features

| Feature | Purpose |
| :--- | :--- |
| **How to play** | Game instructions |
| **Role Selection** | Explain different advantages of each role |
| **Round Briefing** | Helps the user understand the background and current game context |
| **Market Information** | Provides the current market situation |
| **Paid information** | Allows purchasing additional information accuracy if there is enough free cash. The Information Hunter will receive one additional piece of information hint |
| **JPY Funding panel** | Select borrowing packages (25%, 50%, 75%, 100%) and view remaining capacity |
| **Loan ledger** | Track open loans, locked rates, and Hold/Repay actions |
| **Trading desk** | Execute Buy/Sell/Hold and Deposit/Withdraw actions |
| **Market close** | Displays changes after each round |
| **P&L breakdown** | Helps players identify the exact sources of their profit or loss (Asset returns, FX movements, Interest costs, and Information cost) |
| **End Phase Settlement** | Auto-liquidate assets and repays all debt |
| **Debrief** | Explain decisions and learning outcomes |

---

## 3. CORE AND OPTIONAL FEATURES

### Core features
* **Core A (Onboarding):** Home -> How to play -> Role selection -> Role confirmation
* **Core B (Role Parameters):** 

| Role | Max USD Equivalent | Max JPY Principal | Information Cost |
| :--- | :--- | :--- | :--- |
| Investor | $80,000 | ¥12,000,000 | $200 |
| Information Hunter | $100,000 | ¥15,000,000 | $100 |
| Speculator | $120,000 | ¥18,000,000 | $300 |

* **Core C (JPY Borrowing):**
  * Players select borrowing packages each round (0%, 25%, 50%, 75%, 100% of remaining capacity).
  * It automatically validates the requested amount against the player's role-specific constraints (Max JPY Principal and Max USD Equivalent). 
  * Upon approval, the system dynamically converts the borrowed JPY into USD, adds it to the player's Free Cash, and recalculates the remaining borrowing capacity. 

* **Core D (Loan Ledger & Repayment):**
  * The system maintains a detailed ledger for all open loan packages across rounds. 
  * It automatically tracks and accumulates floating interest costs based on the Bank of Japan (BOJ) rate for each active round. Players can choose to “Hold” or “Repay” loans. 
  * Repayments must be settled in full (no partial payments allowed). 
  * The system calculates the exact USD amount required for repayment based on the current USD/JPY exchange rate and validates it against the player's available liquidity. 
  * Each loan package has:
    * Loan ID
    * Open Round
    * Borrow %
    * Requested Principal
    * Accepted Principal
    * Outstanding Principal
    * Months Outstanding
    * Accrued Floating Interest
    * Actual Repay Round (null nếu chưa repay)

* **Core E (Trading):**
  * Players can execute Buy, Sell, or Hold actions for risk assets (US Tech and S&P 500) and Deposit or Withdraw USD Cash. 
  * The system performs real-time UI validation: preventing Buy orders if the total cost exceeds available Free Cash, and blocking Sell orders if the quantity exceeds Current Holdings. 
  * For Hold actions, the system automatically updates the portfolio's market value based on real-time asset price fluctuations without requiring manual input. 

* **Core H (Round engine & Player status):**
  * At the end of each round:
    * The system automatically updates all market parameters, including the USD/JPY exchange rate, BOJ interest rate, and asset prices. 
    * It carries forward the player's asset holdings and dynamically recalculates the Gross Portfolio Value, current USD Debt, and Net Wealth without requiring manual input. 
    * Based on these real-time calculations, the system evaluates the player's financial health and displays a clear status indicator on the UI: ACTIVE (healthy portfolio), AT RISK (negative net wealth but no defaults), or BANKRUPT (insufficient liquidity for mandatory repayments). This immediate visual feedback directly guides the player's strategy for the next round. 

* **Core I (End phase settlement):** 
  * At the end of Phase 3 (after 4 rounds):
    * The system executes an automated settlement process. It auto-liquidates all remaining risk assets (US Tech and S&P 500) and withdraws all defensive US Cash to consolidate the player's available liquidity. 
    * The system then calculates the total outstanding JPY debt, converts it to USD using the final exchange rate, and automatically settles all remaining balances. 
    * Finally, it computes the Final USD Wealth and Net P&L, presenting these definitive metrics on the Final Evaluation screen so players can review the overall success of their Carry Trade strategy.

**Status Logic:**
* **ACTIVE:** Net Wealth ≥ 0 and no payment default has occurred. 
* **AT RISK:** Net Wealth < 0 but no payment default has occurred yet. 
* **BANKRUPT:** Occurs when a repayment is due or selected, but the player has insufficient liquidity to settle it. 
* **END PHASE:** All remaining assets are auto-liquidated and all outstanding debt is settled. 

### Optional features
These features will only be implemented after the core 4-round flow is fully stable. They must not alter core financial logic, add unnecessary steps, or overcomplicate the user experience for borrowing, trading, and repayment. 

| Optional Feature | Purpose |
| :--- | :--- |
| **Market Move Animation** | Visual cues for changes in USD/JPY, asset prices, and market conditions to make the Market Close screen easier to understand |
| **Price Chart** | Visual trends for US Tech, S&P 500, and USD/JPY over 4 rounds, preventing players from having to memorize single data points |
| **Save History** | Records the player's borrowing, trading, and repayment decisions for review during the final Debrief |
| **Sound Effect** | Audio feedback for significant market movements, transaction confirmations, or bankruptcy to increase interaction |
| **Export Result** | Allows players to export their Final Result or Decision Summary into PDF for review or course reporting |

---

## 4. Feature Ownership

| Feature / Workstream | Type | Owner chính | Supporting Members | Contribution / Evidence |
| :--- | :--- | :--- | :--- | :--- |
| **Scoring System** | Core Output | Hoàng Tường Anh | Nguyễn Minh Tâm | Build the end-of-phase scoring system, including Financial Performance, Risk Management, and Decision Quality; link the score with financial outputs from the Calculation Engine |
| **Final Evaluation & Debrief** | Core Output | Hoàng Tường Anh | Nguyễn Minh Tâm, Trần Thu Anh | Design the P&L Breakdown, What You Did Well, What Could Be Improved, Key Lessons, and the Final Evaluation Screen |
| **Main Interface & User Flow** | Core Interface | Lê Quỳnh Chi | Hoàng Hà Uyên, Hoàng Tường Anh | Design the overall flow from Home → How to Play → Role Selection → 4 Rounds → Final Result → Debrief |
| **Historical Market Data** | Core Data | Nguyễn Minh Tâm | Trần Thu Anh, Hoàng Tường Anh | Standardize USD/JPY data, BOJ rate, asset prices, US Cash return, and market parameters for each round |
| **Phase 3 Calculation Engine** | Core Logic | Nguyễn Minh Tâm | Trần Thu Anh, Hoàng Tường Anh | Build formulas for JPY borrowing, FX conversion, interest, repayment, portfolio value, debt MTM, Net Wealth, Final Wealth, and Net P&L |
| **JPY Funding & Borrowing Logic** | Core Feature | Nguyễn Minh Tâm | Trần Thu Anh | Build borrowing packages, role borrowing caps, JPY principal, USD-equivalent caps, and JPY → USD conversion logic |
| **Loan Management & Repayment** | Core Feature | Nguyễn Minh Tâm | Lê Quỳnh Chi, Hoàng Hà Uyên | Build the Loan Ledger, HOLD/REPAY actions, interest accumulation, repayment validation, and restoration of borrowing capacity |
| **Trading Logic** | Core Feature | Nguyễn Minh Tâm | Lê Quỳnh Chi, Hoàng Hà Uyên | Logic for BUY/SELL/HOLD US Tech & S&P 500; DEPOSIT/WITHDRAW/HOLD US Cash; cash and holdings validation |
| **Player State Management** | Core Technical | Lê Quỳnh Chi | Nguyễn Minh Tâm, Hoàng Hà Uyên | Save and update Free Cash, asset holdings, US Cash, open loans, debt, the current round, and player decisions |
| **Round Progression Engine** | Core Technical | Lê Quỳnh Chi | Nguyễn Minh Tâm, Trần Thu Anh | Transition state from Round 1 → 4, update market parameters, and carry forward portfolio/debt between rounds |
| **Market Scenario & Round Narrative** | Supporting | Trần Thu Anh | Nguyễn Minh Tâm | Build market trends for each round: build-up → crowded carry → unwind → recovery |
| **Market News & Information Content** | Supporting | Trần Thu Anh | Hoàng Hà Uyên | Write news, additional information, and market context to support decision-making |
| **Information Feature** | Supporting | Trần Thu Anh | Hoàng Tường Anh, Nguyễn Minh Tâm | Build information content, Information Cost, and logic to support player decisions |
| **Reusable UI Components** | Core Interface | Lê Quỳnh Chi | Hoàng Hà Uyên | Design Trading Cards, Funding Panel, Loan Cards, Market Dashboard, buttons, status badges, and Review Decision Drawer |
| **UI–Logic Integration** | Core Integration | Hoàng Hà Uyên | Lê Quỳnh Chi, Nguyễn Minh Tâm | Receive state/calculation from the engine and bind to UI; connect BUY/SELL/HOLD, Borrow, HOLD/REPAY, and Lock In actions with system functions |
| **User Feedback & Error Messages** | Supporting | Hoàng Hà Uyên | Lê Quỳnh Chi | Toasts/error states for insufficient cash, oversell, borrowing over cap, invalid repayment, and transaction confirmation |
| **Visual Effects & Interaction Feedback** | Optional | Hoàng Hà Uyên | Lê Quỳnh Chi | Animations for market moves, transitions, sound effects, and visual feedback after the user Locks In or Market Closes |
| **End Phase Settlement** | Core Logic | Nguyễn Minh Tâm | Lê Quỳnh Chi, Hoàng Tường Anh | Auto-liquidate assets, repay remaining JPY debt, calculate Final USD Wealth, Net P&L, and Final Status |
| **System Integration & Final Testing** | Integration | All members | — | Test the full flow, calculation consistency, UI output, error paths, and final evaluation |

