
# PLAYER OUTPUTS & EXPLANATIONS

## 1. Understanding the Game Results

Arbiverse is a financial simulation game consisting of three phases: **Tulip Mania (1637), Thai Baht Crisis (1997), and Carry Trade (2024)**.

In each phase, players observe market information, make financial decisions, and receive feedback based on their performance.

The game evaluates players through three main aspects:

- **Financial Performance:** How much profit or loss the player generates.
- **Decision Quality:** How effectively the player uses available information and identifies opportunities.
- **Risk Management:** How well the player controls losses, maintains liquidity, and manages financial exposure.

### Common Outputs

| Output | Explanation |
|---|---|
| Cash Balance | The amount of money currently available for trading or investment. |
| Gross Profit | Profit earned before deducting relevant costs and fees. |
| Net Profit & Loss (P&L) | The actual profit or loss after applicable costs. |
| Net Return (%) | Profit or loss expressed as a percentage of the relevant capital amount. |
| Final Wealth | The player's remaining wealth after final asset valuation and any required debt settlement. |
| Final Score (/100) | The overall performance score based on financial results, decisions, and risk management. |
| Trader Archetype | A description of the player's trading behavior and investment style. |
| Decision Log | A record of the actions and transactions completed during the game. |

**Important:** Financial profit and game scores are different. A player may earn a high profit but receive a lower score because of excessive risk or poor trading decisions.

---

## 2. PHASE I — TULIP MANIA (1637)

### 2.1. Game Overview

In Phase I, players experience the historical Tulip Mania in Amsterdam, where speculative demand causes tulip prices to rise rapidly before the market crashes.

Each player begins with **$1,000 in cash and no tulips**. The game consists of three trading rounds.

Players can buy tulips, sell their existing holdings, purchase additional market information, or stay in cash.

The objective is to identify profitable trading opportunities while avoiding excessive exposure to the market bubble.

### 2.2. Market and Trading Outputs

| Output | Explanation |
|---|---|
| Cash | Money available after buying or selling tulips and paying for information. |
| Tulips | The number of tulips currently owned by the player. |
| Market Price | The current reference price of one tulip. |
| Total Wealth | The total estimated value of cash and tulip holdings at the current market price. |
| Speculation | Indicates how strongly market prices are driven by investor excitement and expectations. |
| Liquidity | Shows how easily market participants can buy or sell tulips. |
| Confidence | Reflects the level of optimism or uncertainty among traders. |
| Market News | Information about market conditions that may influence trading decisions. |
| Trading Offers | Opportunities to buy or sell tulips at specific prices and quantities. |
| Stay in Cash | The decision not to trade during a round, subject to the game's limits. |

**Example:**

A player holds $600 in cash and owns 2 tulips worth $250 each.

Total Wealth = $600 + (2 × 250)=**1,100**

Although the player's estimated wealth is $1,100, this value may decrease significantly if tulip prices fall before the player sells.

### 2.3. Round Debrief

At the end of each round, the game provides a summary of the player's trading activities.

The Round Debrief explains whether the player bought tulips, sold tulips, completed both types of transactions, or decided not to trade.

It also provides feedback based on market conditions, including speculation, liquidity, and confidence.

This helps players understand whether their decisions were appropriate for the current stage of the market cycle.

### 2.4. Final Results

After the third round, the tulip market crashes. The game values every remaining tulip at **$15**.

| Output | Explanation |
|---|---|
| Final Cash | The amount of cash remaining after all transactions and information costs. |
| Remaining Tulips | The number of tulips still held after the market crash. |
| Final Wealth | Cash plus the value of remaining tulips at the post-crash price. |
| Final P&L | The difference between final wealth and initial capital. |
| Final Score | The overall assessment of trading performance, decision quality, and risk management. |
| Trader Archetype | A description of the player's investment behavior. |
| Activity Score Cap | A possible score limitation based on participation and activity conditions. |

**Calculation:**

Final Wealth = Final Cash + (Remaining Tulips × $15)

Final P&L = Final Wealth − $1,000

**Example:**

A player finishes with $900 cash and 4 remaining tulips.

Final Wealth = $900 + (4 × 15)=**960**

Final P&L = $960 − 1,000=**-40**

The player loses $40 because the remaining tulips are worth significantly less after the crash.

### 2.5. Performance Evaluation

| Criteria | Maximum Score | Explanation |
|---|---:|---|
| Financial Performance | 30 | Measures trading profit and capital efficiency. |
| Arbitrage & Trading Execution | 30 | Evaluates the player's ability to identify and execute profitable opportunities. |
| Decision Quality | 25 | Assesses information usage, market adaptation, and consistency of decisions. |
| Risk Management | 15 | Evaluates inventory exposure, liquidity management, and drawdown control. |
| **Total** | **100** | Overall score, subject to any applicable activity cap. |

The game also assigns a Trader Archetype, such as *The Disciplined Arbitrageur*, *The Prudent Exiter*, or *The Bubble Rider*, based on the player's behavior.

**Key Learning Outcome:**

The main lesson of Phase I is that rising asset prices do not guarantee sustainable profits. Successful traders must recognize speculative risks, manage inventory, and understand when to exit the market.

---

## 3. PHASE II — THAI BAHT CRISIS (1997)

### 3.1. Game Overview

Phase II simulates foreign-exchange trading during the 1997 Asian Financial Crisis.

Players begin with **$120,000** and participate in four trading rounds.

The objective is to identify arbitrage opportunities arising from differences between exchange rates across currency markets.

Players can allocate up to **$50,000 per round**, using increments of $1,000.

Each trading strategy involves three currency conversions, and transaction fees are charged on each conversion.

### 3.2. Market and Trading Outputs

| Output | Explanation |
|---|---|
| Cash Balance | The amount of USD available for trading. |
| Cumulative Net Profit | Total profit or loss accumulated from completed trading rounds. |
| Round Cap | The maximum amount of capital allowed for trading in the current round. |
| Allocated Capital | The amount of money committed to a specific trading strategy. |
| Exchange Rate Board | Displays currency exchange rates used to evaluate trading opportunities. |
| Trading Path | The sequence of currency conversions selected by the player. |
| Transaction Fee | A trading cost charged on each currency conversion, with a fee rate of 0.05% per leg. |
| Market News | Information about economic conditions and currency-market developments. |
| Paid Information | Additional market information purchased by the player. |
| Stay in Cash | The decision not to execute a trade during the round. |
| Trading Status | Indicates whether the player remains active or has become insolvent. |

### 3.3. Exchange Rate and Arbitrage Outputs

Players compare market exchange rates with theoretically implied exchange rates to identify possible arbitrage opportunities.

**Implied Cross Rate**

Implied SGD/THB = USD/THB ÷ USD/SGD

This calculation shows the exchange rate that should theoretically exist between SGD and THB based on the two USD exchange rates.

**Market Discrepancy**

Market Discrepancy (%) = (Actual SGD/THB − Implied SGD/THB) ÷ Implied SGD/THB × 100

A discrepancy indicates a difference between actual and implied exchange rates.

However, a difference does not automatically generate profit. The player must select the appropriate trading direction and consider transaction fees.

### 3.4. Round Settlement Outputs

After completing a trade, the game displays a settlement report showing the financial result.

| Output | Explanation |
|---|---|
| Selected Route | The currency-conversion strategy executed by the player. |
| Allocated Capital | The amount of USD used for the transaction. |
| Gross USD | The total USD received after the currency conversions, before relevant costs. |
| Transaction Fees | The total fees charged for the three conversions. |
| Information Cost | The cost of additional market information purchased during the round. |
| Net Profit | Profit remaining after subtracting the original capital and relevant costs from the returned USD. |
| Net Return (%) | Net profit divided by the allocated trading capital. |
| Optimal Call | The strategy identified by the game as the best decision for that round. |

**Calculation:**

Net Profit = Gross USD − Allocated Capital − Transaction Fees − Information Cost

Net Return (%) = Net Profit ÷ Allocated Capital × 100

For rounds without allocated trading capital, the game reports a net return of 0.00%.

**Example:**

A player allocates $50,000 and receives $50,600 after currency conversions.

Transaction fees = $75

Information cost = $100

Net Profit = $50,600 − $50,000 − $75 − 100=**425**

Net Return = $425 ÷ $50,000 × 100 = **0.85%**

The player earns $425 after accounting for trading and information costs.

### 3.5. Final Results

At the end of Round 4, the game produces a summary of the player's overall financial performance.

| Output | Explanation |
|---|---|
| Initial Capital | The starting capital of $120,000. |
| Final Wealth | The remaining cash balance after all four rounds. |
| Cumulative Net Profit | Total net profit or loss across the four rounds. |
| Final Return (%) | Overall investment return relative to the initial capital. |
| Final Score | Evaluation of financial performance, risk management, and decision quality. |
| Performance Tier | A classification of the player's overall trading performance. |
| Optimal Call History | Comparison between the player's actual decisions and the game's optimal decisions. |

**Calculation:**

Final Return (%) = (Final Wealth − $120,000) ÷ $120,000 × 100

The Financial Performance score separately uses cumulative net profit divided by total trading capital allocated across rounds.

### 3.6. Performance Evaluation

| Criteria | Maximum Score | Explanation |
|---|---:|---|
| Financial Performance | 50 | Evaluates trading profitability relative to allocated capital. |
| Risk Management | 30 | Measures cash reserves, adaptation to capital controls, and transaction fee management. |
| Decision Quality | 20 | Evaluates capital efficiency, exit decisions, and information usage. |
| **Total** | **100** | Overall player score. |

The game assigns a performance tier based on the final score, ranging from *Master Arbitrageur* to *Capital Depleted*.

**Key Learning Outcome:**

Phase II demonstrates that foreign-exchange arbitrage depends on both exchange-rate differences and trading costs. Successful traders must identify profitable currency routes, allocate capital efficiently, and recognize situations where remaining in cash is the better decision.

---

## 4. PHASE III — CARRY TRADE (2024)

### 4.1. Game Overview

Phase III simulates a Japanese yen-funded carry trade.

Players begin with **$0 free cash** and obtain investment capital by borrowing Japanese yen (JPY).

The borrowed yen is converted into US dollars and can be invested in US technology assets, the S&P 500 asset, or interest-earning US Cash.

The game lasts four rounds, followed by a final settlement in which remaining investments are liquidated and outstanding loans are settled.

The main challenge is to earn investment returns while managing currency fluctuations, borrowing costs, and financial risk.

### 4.2. Market and Portfolio Outputs

| Output | Explanation |
|---|---|
| USD/JPY Exchange Rate | The amount of Japanese yen equivalent to one US dollar. |
| BOJ Funding Rate | The annual interest rate applied to yen borrowing in the game. |
| US Tech Price | The current price of the technology investment asset. |
| S&P 500 Price | The current price of the S&P 500 investment asset. |
| Free Cash | USD available but not currently invested. |
| US Cash | Funds deposited into the game's interest-earning cash asset. |
| Gross Portfolio | Total value of free cash and all investment holdings. |
| JPY Principal | The outstanding amount of yen originally borrowed, excluding accrued interest. |
| Debt (USD) | The current USD value of the outstanding yen debt. |
| Net Wealth | Gross Portfolio minus the USD value of outstanding debt. |
| Credit Line Used | The amount of borrowing capacity currently utilized. |
| Trading Status | Shows whether the player's financial position is active, at risk, or bankrupt. |

### 4.3. Portfolio Valuation

**Gross Portfolio**

Gross Portfolio = Free Cash + Tech Holdings + S&P Holdings + US Cash

**Net Wealth**

Net Wealth = Gross Portfolio − Debt (USD)

**Example:**

A player owns investments worth $12,000 and holds $2,000 in Free Cash.

The current USD value of outstanding yen debt is $10,000.

Gross Portfolio = $12,000 + 2,000=**14,000**

Net Wealth = $14,000 − 10,000=**4,000**

This means the player's actual net financial position is $4,000, even though the portfolio contains $14,000 in assets.

### 4.4. Currency Risk Explanation

Exchange-rate movements directly affect the cost of repaying yen-denominated debt.

When USD/JPY decreases, the Japanese yen strengthens relative to the US dollar.

Consequently, the same yen debt requires more US dollars to repay.

**Example:**

A player borrows ¥1,500,000.

At USD/JPY = 150:

Debt Value = ¥1,500,000 ÷ 150 = **$10,000**

If USD/JPY decreases to 125:

Debt Value = ¥1,500,000 ÷ 125 = **$12,000**

The USD value of the debt increases by $2,000, even though the yen principal remains unchanged.

This example excludes interest and borrowing fees.

### 4.5. End-of-Round Outputs

At the end of each round, the game displays a Market Close report.

| Output | Explanation |
|---|---|
| Gross Portfolio Value | Current estimated market value of the player's assets and cash. |
| USD Debt (MTM) | Current USD value of yen-denominated liabilities. |
| Net Wealth | Portfolio value after subtracting the outstanding USD debt value. |
| US Cash Interest | Interest earned on the US Cash position during the round. |
| Portfolio Allocation | The proportion of the portfolio invested in different assets. |
| Trading Status | Indicates the player's current financial condition. |

These figures represent the player's position at the end of the round, rather than the final amount received after liquidation and loan settlement.

### 4.6. End Phase Settlement

After Round 4, the game automatically sells remaining investments and processes the repayment of outstanding loans.

The final settlement uses the following game prices:

- US Tech: $400
- S&P 500: $525
- USD/JPY: 147

Outstanding loan balances include the original principal and accrued yen interest.

| Output | Explanation |
|---|---|
| Available Liquidity | Cash available after liquidating investments and withdrawing US Cash, before debt settlement. |
| Debt Repaid | The value of outstanding debt covered by available liquidity. |
| Remaining Debt | The amount of debt that cannot be repaid. |
| Loans Settled | Number of outstanding borrowing positions processed during settlement. |
| Final USD Wealth | Available liquidity minus total debt owed at settlement. |
| Bankruptcy Warning | Appears when the player does not have enough liquidity to cover outstanding debt. |

**Calculation:**

Final USD Wealth = Available Liquidity − Total Debt

**Example:**

Available Liquidity = $18,000

Total Debt = $20,000

Final USD Wealth = $18,000 − 20,000=**-2,000**

The player has insufficient funds to repay the debt and therefore faces bankruptcy.

### 4.7. Final Profit & Loss Outputs

The final report separates investment performance from the financial effects of borrowing and currency movements.

| Output | Explanation |
|---|---|
| Investment P&L | Combined gains or losses from Tech, S&P 500, and interest earned on US Cash. |
| Tech P&L | Profit or loss generated by technology investments after relevant trading fees. |
| S&P 500 P&L | Profit or loss generated by S&P 500 investments after relevant trading fees. |
| US Cash Interest | Income earned from the interest-bearing US Cash position. |
| Funding P&L | Net financial impact of currency movements and borrowing costs. |
| FX P&L | Gains or losses caused by changes in the USD value of yen principal. |
| Floating Interest Cost | Interest expenses accumulated on yen borrowing. |
| Borrowing Cost | One-time borrowing fee of 0.01%. |
| Information Cost | Total cost of optional market information. |
| Net P&L | Final profit or loss after combining investment and funding results and deducting information costs. |
| Net P&L Return (%) | Net profit or loss divided by USD funding used. |

**Calculation:**

Net P&L = Investment P&L + Funding P&L − Information Cost

Net P&L Return (%) = Net P&L ÷ USD Funding Used × 100

The game displays a 0% return when no funding was used.

Stock transaction fees of 0.05% per trade are already included in the relevant investment results and should not be deducted twice.

**Example:**

Investment P&L = +$1,500

FX P&L = −$600

Interest and Borrowing Costs = −$200

Information Cost = $100

Net P&L = $1,500 − $600 − $200 − 100=**+600**

Although the investments generated $1,500 in profit, the final result is only $600 after considering currency movements and other costs.

### 4.8. Performance Evaluation

| Criteria | Maximum Score | Explanation |
|---|---:|---|
| FX Performance | 20 | Evaluates the currency-related result of the yen-funded strategy. |
| Portfolio Investment Performance | 30 | Evaluates returns generated from investment assets. |
| Liquidity Management | 4 | Measures the player's ability to maintain sufficient liquidity. |
| Debt Exposure Management | 3 | Evaluates control over borrowing and financial obligations. |
| Portfolio Risk Management | 3 | Evaluates the player's exposure to investment risk. |
| Participation & Capital Deployment | 5 | Measures meaningful participation and the use of available capital. |
| Debt Utilization | 5 | Evaluates how effectively the player uses borrowed funds. |
| Signal–Allocation Alignment | 20 | Assesses whether portfolio allocation is consistent with market information. |
| Position Sizing Quality | 10 | Evaluates whether investment amounts are appropriate for market conditions. |
| **Total** | **100** | Overall player performance score. |

The final report also compares the player's portfolio allocation with the game's acceptable allocation ranges.

The Trader Archetype and final verdict provide additional feedback on the player's investment behavior, including strengths, weaknesses, and areas for improvement.

**Key Learning Outcome:**

Phase III illustrates the interaction between investment returns, currency movements, and borrowing costs.

A carry trade may generate positive investment returns but still produce losses if the funding currency strengthens or borrowing expenses become too high.

Therefore, successful carry trading requires disciplined portfolio allocation, effective debt management, and careful monitoring of exchange-rate risks.

---

## 5. OVERALL INTERPRETATION

Across all three phases, Arbiverse evaluates not only the financial outcome but also the quality of the player's decisions.

| Evaluation Question | Relevant Outputs |
|---|---|
| Did the player generate a profit? | Final P&L, Cumulative Net Profit, Net P&L |
| How much wealth remains? | Final Wealth, Final USD Wealth |
| What caused the profit or loss? | Trading History, Transaction Costs, Investment P&L, FX P&L |
| Did the player make appropriate decisions? | Decision Quality Score, Optimal Call, Allocation Alignment |
| Was financial risk controlled effectively? | Liquidity, Inventory Exposure, Debt Exposure, Drawdown |
| What can the player improve? | Round Debrief, Trader Archetype, Performance Score, Economic Lesson |

---

## 6. CONCLUSION

Arbiverse demonstrates three important principles of financial decision-making.

**First, profitability does not always reflect the quality of a financial strategy.** Players must also consider risk exposure, capital efficiency, and the sustainability of returns.

**Second, financial markets are influenced by both information and investor behavior.** Successful decisions require an understanding of market conditions rather than simply following price movements.

**Finally, effective risk management is essential for long-term financial performance.** Whether trading speculative assets, exploiting exchange-rate differences, or investing with borrowed money, players must balance potential returns against possible losses.

Through these three historical scenarios, Arbiverse helps players develop practical skills in trading, financial analysis, investment decision-making, and risk management.



