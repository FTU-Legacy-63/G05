
# DATA & SIMULATION CALIBRATION

## Phase 1: Tulip Mania
* **Initial cash:** $1,000
* **Information cost:** $200

| Round | Trader | Order | Quantity | Price (CU) | Total value (CU) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Round 1** | TRADER_A | SELL | 5 | 28 | 140 |
| | TRADER_B | BUY | 4 | 32 | 128 |
| | TRADER_C | SELL | 4 | 29 | 116 |
| | TRADER_D | BUY | 3 | 33 | 99 |
| | TRADER_E | SELL | 2 | 31 | 62 |
| | TRADER_F | BUY | 1 | 34 | 34 |
| **Round 2** | TRADER_A | SELL | 7 | 58 | 406 |
| | TRADER_B | BUY | 8 | 63 | 504 |
| | TRADER_C | SELL | 6 | 60 | 360 |
| | TRADER_D | BUY | 5 | 62 | 310 |
| | TRADER_E | SELL | 3 | 57 | 171 |
| | TRADER_F | BUY | 4 | 64 | 256 |
| **Round 3** | TRADER_A | SELL | 10 | 18 | 180 |
| | TRADER_B | BUY | 3 | 15 | 45 |
| | TRADER_C | SELL | 8 | 19 | 152 |
| | TRADER_D | BUY | 4 | 14 | 56 |
| | TRADER_E | SELL | 4 | 20 | 80 |
| | TRADER_F | BUY | 0 | 0 | 0 |

---

## Phase 2: Thai Baht Crisis
* **Initial USD cash:** $100,000
* **Transaction fee / leg:** 0.05%
* **Information cost:** $1,000

| Round / Venue | Quoted USD/THB | Quoted USD/SGD | Quoted SGD/THB (Market) | Theoretical SGD/THB |
| :--- | :--- | :--- | :--- | :--- |
| **Round 1** | 25 | 1.43 | 17.35 | 17.48 (=25/1.43) |
| **Round 2** | 25.2 | 1.44 | 17.8 | 17.5 |
| **Round 3 (Onshore)** | 25.8 | 1.43 | 18.04 | 18.04 |
| **Round 3 (Offshore)**| 22.75 | 1.43 | 15.91 | 15.91 |
| **Round 4 (Thả nổi & Sụp đổ)** | 30.00 | 1.46 | 20.55 | 20.55 |

---

## Phase 3: JPY Carry Trade
* **Starting Free cash:** $0
* **Max JPY Borrowing cap:** 18,000,000 JPY
* **Information cost:** $600
* **Transaction fee:** 0.05%

| Market variable | Round 1 | Round 2 | Round 3 | Round 4 | End Phase |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **USD/JPY** | 150.00 | 160.00 | 142.00 | 152.00 | 147.00 |
| **BOJ JPY rate (round)** | 0.10% | 0.10% | 0.25% | 0.25% | - |
| **US Tech Index Level** | 450.00 | 515.00 | 345.00 | 410.00 | 400.00 |
| **S&P 500 Index Level** | 520.00 | 570.00 | 490.00 | 510.00 | 525.00 |
| **US Cash return / round**| 0.20% | 1.50% | 0.30% | 0.75% | - |
| **Quarter length (months)**| 3 | 3 | 3 | 3 | - |

---

## SOURCE REGISTER

| Source | Information Used |
| :--- | :--- |
| **McClure & Thomas** - *Financial History Review* | Historical context of Tulip Mania: hidden bulb supply and sequestered capital in winter 1636, market panic, and total liquidity freeze in February 1637. |
| **Garber** - *Journal of Political Economy* | Historical price series of common tulip bulbs (Witte Croonen rising 26x to 57 florins and crashing over 95%). Used to calibrate Phase 1 prices: Round 1 (28–34 CU), Round 2 (57–64 CU), Round 3 crash (15–20 CU), and post-crash liquidation value. |
| **Bank of Thailand** - *Lessons from Asian Financial Crisis* | The pegged exchange rate regime (~25 THB/USD), speculative attacks by hedge funds, and the official managed float on July 2, 1997. |
| **IMF (1998)** - *Thailand: Statistical Appendix, Report No. 98/119* | Key macro data: depletion of usable net foreign reserves (< 3 Billion USD), defense interest rates, forward contracts, and the two-tier market split (Onshore 25.80 vs. Offshore 22.75 THB/USD). Used to calibrate Phase 2 cross-rates (USD/THB, USD/SGD, SGD/THB) and the 0.05% fee per leg. |
| **Bank for International Settlements (BIS, 2024)** - *Quarterly Review (Sep 2024)* | Market dynamics of the August 2024 Yen Carry Trade unwind: USD/JPY reversal from 160+ down to 142, tech stock sell-off (~25%), spike in volatility (VIX > 60), and mass liquidation. |
| **Bank of Japan (BOJ)** - *Monetary Policy Releases (July 31, 2024)* | Official decision to raise the policy rate from 0–0.10% to 0.25%, used to set Phase 3 floating borrowing costs (0.10% in R1–R2 to 0.25% in R3–R4). |
| **Federal Reserve Bank of St. Louis (FRED)** - *Federal Funds Effective Rate (DFF)* | US monetary policy holding interest rates high (5.25%–5.50%), used to model the risk-free return of the defensive US Cash asset (0.20% to 1.50% per round). |
| **Federal Reserve Bank of St. Louis (FRED)** - *10-Year Treasury Rate (DGS10)* | Flight-to-safety trend during market panics where capital rushes into safe US government bonds. |
| **S&P Dow Jones Indices / Bloomberg Market Data** | Historical performance and price levels of major US stock indexes during the 2024 unwind: US Tech Index (450 to 515, then falling to 345) and S&P 500 Index (520 to 570, then falling to 490). |
| **Team-created Simulation** *(Calibrated Game Data)* | **Phase 1:** Initial cash $1,000, $200 news fee, 6 trader quote pairs (Trader A to F) across 3 rounds.<br>**Phase 2:** Initial cash $100,000, 3-leg triangular arbitrage paths (Path A & B), $600 intel fee, round trading caps, and cross-market venue routing.<br>**Phase 3:** Initial $0 free cash, 18,000,000 JPY borrowing limit, $600 info cost, 4 loan packages (25%–100%), and end-phase settlement formulas. |

---

## Why We Calibrated the Historical Numbers into Simulated Game Data

When designing ARBIVERSE, our goal wasn’t to build a dry historical archive or a live trading terminal. We wanted an interactive educational game where students can actually feel the market mechanics and learn from their mistakes within a 15-to-20-minute class session.

In the real world, financial crises take months or years to unfold, involving millions of messy, fractional transactions. If we directly copied raw historical numbers, the math would be confusing, interest on a 3-minute round would only be a few pennies, and the key financial lessons would be completely lost.

Therefore, we separated our data into two layers:
1. **Historical Evidence:** Real historical research to set the narrative background, timeline, and realistic ranges.
2. **Controlled Simulated Numbers:** Clean, simplified numbers calibrated to trigger specific trading behaviors, market traps, and risk dilemmas.

### 1. Phase 1: Tulip Mania (1636–1637)
* **The Real History:** Research shows that during the winter of 1636, tulip bulbs were buried underground. Because no one could see how many bulbs were actually planted, speculation exploded on paper contracts. Prices for common varieties skyrocketed about 26 times by early February 1637, only to crash by over 95% within days once green sprouts appeared and revealed a massive hidden supply.
* **Why We Simulated the Numbers:**
  * **Starting Capital ($1,000) & Round 1 Base (28–34 CU):** We set starting cash at $1,000 so a player could immediately buy small bundles (1 to 5 bulbs). In Round 1, we offered bulk discounts: buying 5 bulbs from Trader A cost only 28 CU each, while buying 1–2 bulbs cost 31–34 CU. This creates a natural psychological temptation to buy in bulk and hoard inventory for the next round.
  * **Round 2 Euphoria (57–64 CU):** Prices almost double, and buyer demand is at its peak. Buying all the available sell orders costs around $937—almost the entire starting wallet. This intentionally tempts the player to use leverage to chase quick profits.
  * **Round 3 Crash & The Inverted Spread Trap (Sell 18–20 CU vs. Buy 15 CU):** When panic hits, buyers vanish. To simulate this "liquidity freeze," the highest price any buyer is willing to pay drops to 15 CU, while panic-sellers dump bulbs at 18–20 CU. Because sell prices are higher than buy prices, flipping for a quick profit is mathematically impossible. Players who hoarded bulbs at 60 CU are completely trapped and forced to liquidate at a worthless 15–20 post-crash price.

### 2. Phase 2: Thai Baht Crisis (1997)
* **The Real History:** Thailand originally pegged the baht around 25 to 25.5 THB per USD. As speculators attacked the currency, the Bank of Thailand (BOT) fought back on May 15, 1997, by creating a two-tier market: banning offshore access to baht. This caused offshore baht to plunge to 29.5 while the onshore rate stayed near 25.5. Eventually, with under $3 billion in usable reserves left, the BOT had to surrender on July 2, 1997, letting the baht collapse past 30–32.
* **Why We Simulated the Numbers:**
  * **Round 1 & 2 Discrepancies:** We engineered a clean triangular arbitrage gap between the market quote and the theoretical cross-rate:
   
TheoreticalSGD/THB=USD/THBUSD/SGD

    * In Round 1, SGD/THB trades at 17.35 vs. the 17.48 theoretical rate, giving a small profit (+0.76% gross) along Path B.
    * In Round 2, SGD/THB jumps to 17.80 vs. 17.50 theoretical, flipping the winning direction to Path A (+1.71% gross).
  * **Round 3 Two-Tier Market ($25.80 Onshore vs. $22.75 Offshore):** To simulate the BOT capital controls, buying baht in Bangkok is cheap (25.80 baht per dollar), while offshore hedge funds are desperately buying baht at 22.75 per dollar to cover their short positions. This creates a massive +13.41% arbitrage opportunity, teaching players how capital controls break price parity across borders.
  * **Round 4 The Fee Drag Trap:** When the currency floats to 30.00 THB/USD and SGD/THB hits 20.55, the market returns to theoretical equilibrium (0% price gap). Because every triangular trade has a 0.05% fee per leg (around 0.15% across all 3 conversions), trading in Round 4 is guaranteed to lose money. This teaches the critical lesson: when mispricings disappear, the smartest move is **Stay in Cash**.

### 3. Phase 3: JPY Carry Trade (2024)
* **The Real History:** With the US Fed holding rates at 5.25%–5.50% and the Bank of Japan (BOJ) sitting near 0%, global traders borrowed cheap yen to buy booming US tech stocks. USD/JPY drifted from 150 to an overbought peak of 160–161.9 in July 2024. But on July 31, the BOJ unexpectedly raised its policy rate to 0.25%, triggering the massive "Black Monday" unwind on August 5. USD/JPY plunged to 142, tech stocks dropped around 25%, and VIX spiked above 60.
* **Why We Simulated the Numbers:**
  * **$0 Free Cash & ¥18,000,000 Borrowing Limit:** Starting with zero dollars forces the player to borrow yen to fund their portfolio - which is the fundamental definition of a carry trade.
  * **The USD/JPY Path (150 → 160 → 142 → 152 → 147):**
    * **Round 1 (150) to Round 2 (160):** When the dollar climbs to 160 yen, your yen debt actually shrinks in dollar terms. This gives players a false sense of paper profits, tempting them to stay overleveraged.
    * **Round 3 (142):** When the yen sharply strengthens to 142, repaying the yen debt suddenly becomes much more expensive in US dollars.
  * **US Tech Stocks (450 → 515 → 345) & S&P 500 (520 → 570 → 490):** Tech stocks rally (+14%), stall near the top (+2%), and then suffer a brutal -33% crash during the unwind in Round 3. Players who went all-in on tech get hit by a double disaster: their stock portfolio collapses while their yen debt explodes.
  * **US Cash (0.20% to 1.50% yield):** Gives players a safe, interest-earning shelter reflecting Fed rates. Idle free cash earns 0%, so players must actively deposit funds into US Cash to protect capital and hedge against the crash.



