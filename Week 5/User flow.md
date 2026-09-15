## START AND END POINT
* **Start:** Home / Phase 3 introduction
* **End:** Final result + Debrief after all rounds
* **Overall flow:** Home → How to play → Choose role → Role confirmation → Round 1 → Round 2 → Round 3 → Round 4 → Final settlement → Debrief
* **Flow each round:** Round briefing → Read news + indicators → Buy /skip Private brief → Add/Skip JPY Funding → Buy/Sell/Hold → Repay debt/ not repay → Review Decisions → Lock In → Market Close → Round Result → Next Round

## USER GOAL
* **Player's Goal:** Execute the Yen Carry Trade strategy across 4 rounds to maximize profit (Net P&L). Players must continuously restructure their portfolios and manage their JPY debt to maintain liquidity, avoiding bankruptcy caused by exchange rate and interest rate fluctuations.
* The user journey is linear: Home -> How to Play -> Role Selection -> Trading Desk. At the Trading Desk, players immediately see the JPY Funding section to execute the first step, which is borrowing capital.
* Allowing players to execute all actions (Borrow, Repay, Buy, Sell) freely within the same round enables them to dynamically manage cash flow and handle liquidity risk in a highly realistic manner.
* The metrics displayed at Market Close (P&L and Active/At Risk status) provide clear signals on whether the player should hold their positions for the next round or immediately liquidate assets to repay debt.

---

### HAPPY PATH

| Step | User Action | System Response | Evidence |
| :--- | :--- | :--- | :--- |
| 1 | The player clicks “How to Play.” | The system displays the game instructions | |
| 2 | The player clicks “Start” → “Role Selection” → “Confirm Your Role.” | The system displays the available roles and the benefits of each role (Information Hunter, Speculator, Arbitrageur) | 3 role cards with descriptions + confirmation popup |
| 3 | The player clicks “Enter Market” after reviewing the market information (market state bars and briefing) | The screen is divided into two sections. The left side displays market information, while the right side displays the Trading Desk with portfolio metrics | Sticky header: Portfolio Value, USD Cash, JPY Debt, Net Wealth |
| 4 | The player clicks “Buy Information” to purchase hidden information | The system deducts the information fee from the player's cash and displays the accuracy level of the information for each role, along with an additional hint available only to the Information Hunter. | Information card |
| 5 | The player selects the 100% JPY borrowing option and clicks “Confirm and Proceed” | The system converts the borrowed JPY into USD Cash and records the corresponding amount as JPY Debt | 4 borrowing options: 25%, 50%, 75%, 100% |
| 6 | The player uses the borrowed USD Cash to “Deposit” funds into the USD Bank and “Buy” US Tech and S&P 500 assets | The system deducts the corresponding amount from USD Cash and increases the USD Bank balance and the number of asset units held | Trading panel |
| 7 | The player clicks “Sell” to sell assets | The system records the sell order and adds the proceeds to USD Cash | |
| 8 | With sufficient cash available, the player clicks “Repay” and selects the Round 1 loan | The system checks that the available USD Cash is sufficient and allows the player to repay the loan immediately | |
| 9 | With cash still remaining, the player continues to click “Buy” to purchase assets | The system deducts the corresponding amount from USD Cash and increases the number of units held | |
| 10 | The player continues playing through Rounds 2, 3, and 4 | | |
| 11 | The player clicks “End Phase” at the end of round 4 | The system summarizes the player's actions and displays the Debrief, including P&L, Lessons, and other results | |

---

### ALTERNATIVE PATH

| Step | User Action | System Response | Evidence |
| :--- | :--- | :--- | :--- |
| 1 | In the JPY Funding section, the player decides not to repay any existing debt or borrow additional funds | The system records that no changes have been made to the player's cash flow | A warning informs the player that outstanding debt must be repaid by the end of the phase; otherwise, the player will become bankrupt |
| 2 | In the Asset Markets section, the player does not buy or sell any assets and only clicks “Hold” | The system maintains the player's current position | The asset card changes its status to “Holding” |

---

### ERROR PATH

| Step | User Action | System Response | Evidence |
| :--- | :--- | :--- | :--- |
| 1 | The player has used 75% of their credit capacity but still attempts to borrow an additional 50% or 100% | The system disables the options that exceed the remaining 25% borrowing capacity | |
| 2 | The player's USD Cash is less than the Total Cost required for repayment | The system requires the player to sell assets before repaying the loan | |
| 3 | The player enters a Sell Quantity greater than the number of units currently held | The system rejects the transaction | Warning text: “You only own ... units” |
| 4 | The player becomes bankrupt and clicks “See What Went Wrong” | The system skips the remaining rounds and redirects the player directly to the Debrief screen, explaining the reasons for the account failure | Status displayed as “Insolvent” |

