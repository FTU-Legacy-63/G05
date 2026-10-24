
# Project Overview and Revision Summary

## 1. Game Overview

**Arbiverse** is an interactive educational game that introduces players to financial decision-making across three historical market settings. Instead of presenting finance as isolated formulas, the game asks players to interpret market conditions, evaluate information, select trading strategies, allocate capital, and observe the financial consequences of their decisions.

| Phase | Historical setting | Core gameplay and learning focus |
|---|---|---|
| **I — Tulip Mania** | Amsterdam, 1637 | Buy and sell tulips through trader offers; manage cash, inventory, information costs, and exposure to a market crash. |
| **II — Thai Baht Crisis** | Bangkok and Singapore, 1997 | Compare FX trading paths, interpret currency-market news, evaluate triangular and cross-market arbitrage, and account for transaction fees. |
| **III — Carry Trade** | Tokyo and New York, 2024 | Borrow JPY, convert funding to USD, allocate among US assets, monitor FX and portfolio risks, and repay debt at settlement. |

Players progress through **three rounds in Phase I** and **four rounds each in Phases II and III**. At each decision point, the game combines financial data with public market news and optional paid information. A results screen explains financial performance and a **100-point assessment** evaluates the quality of the player's choices.

The intended outcome is not to replicate every feature of a live trading platform. Arbiverse uses structured scenarios to make **speculation, arbitrage, leverage, and risk management** accessible and comparable across players.

---

## 2. Technical Architecture

### 2.1 Front End — Player Interface

The user interface is built with **HTML, CSS, and JavaScript** and runs in a web browser. The main `arbiverse.html` file contains a shared landing page and embeds the three phase-specific game experiences.

| Component | Implementation and purpose |
|---|---|
| **Landing page and navigation** | Historical phase cards, phase selection, instructions, and return-to-menu navigation. |
| **Market dashboard** | Round information, prices or exchange rates, capital and position indicators, and decision controls. |
| **Information interfaces** | Period-inspired news and optional private reports: historical-market presentation for Phase I, financial telex/fax-inspired material for Phase II, and modern market-information presentation for Phase III. |
| **Trading controls** | Accept/reject NPC offers; choose FX routes and allocations; borrow, invest, sell, repay, or hold positions, depending on the phase. |
| **Interactive feedback** | Confirmation prompts, countdown timers, validation messages, round settlements, and final performance scorecards. |
| **Responsive styling** | Layout adaptations for different viewport sizes, supported by visual indicators and modal interfaces. |

The shared page loads each phase inside an **iframe using embedded page content**. Navigation and phase-completion messages connect the individual experiences into one player journey.

### 2.2 Back End — Financial and Game-Logic Engine

Arbiverse **does not use a separate server-side back end or database** in the supplied version. Its computational back end is implemented as **client-side JavaScript**. This distinction is important for accurately describing the project architecture.

The logic layer performs five main functions:

1. **Scenario management:** Stores predefined round prices, exchange rates, news, market events, and permitted strategies.
2. **State management:** Tracks cash, inventory, allocations, positions, debt, information purchases, and round progression during a play session.
3. **Rule validation:** Checks available funds, tulip inventory, valid FX allocation increments, round trading caps, and phase-specific action constraints.
4. **Financial calculation:** Processes tulip purchases and sales, three-leg FX conversions and fees, JPY financing, investment returns, and final liquidation.
5. **Scoring and feedback:** Converts financial results and decision history into phase-specific criteria, final scores, and explanatory feedback.

**Game Logic Flow:**

Player input → JavaScript validation → Financial calculation

→ Updated game state → Round feedback / final score

The implementation is **self-contained and scenario-driven**. It does not require live market-price APIs, account authentication, or external trade execution. The absence of a persistent database also means this version should be described as a browser-session simulation, not an online trading service.

---

## 3. Implemented Revisions

Development and review focused on improving the consistency of financial calculations, clarity of player decisions, trading safeguards, and presentation of information. The following revisions are supported by the supplied HTML and associated calculation documentation.

| Area | Implemented revision | Contribution to the game |
|---|---|---|
| **Phase I — Starting conditions** | Simplified gameplay to **$1,000 initial cash, zero starting tulips, and cash-funded trading without active leverage**. | Keeps the focus on market timing, inventory, and liquidity. |
| **Phase I — Player decisions** | Introduced explicit **Stay in Cash** and **Execute Actions** choices, together with decision confirmation and activity tracking. | Makes inactivity and deliberate capital preservation more distinguishable. |
| **Phase II — Trade-size validation** | Enforced **1,000allocationincrements**,subjecttoavailablecashanda**50,000 per-round trading cap**. | Prevents negligible fractional trades and gives trading decisions clearer financial scale. |
| **Phase II — Route assessment** | Updated route definitions and scoring recognition so both profitable Round 3 directions are considered in performance feedback. | Aligns the assessment with the expanded route menu. |
| **Phase III — Portfolio accounting** | Added **US Cash deposits** to the capital base used in portfolio-return assessment. | Better reflects the fact that US Cash contributes investment income alongside equity positions. |
| **Across phases — Interface and feedback** | Refined historical presentation, information panels, trading prompts, result breakdowns, and shared navigation. | Improves continuity across the three distinct financial settings. |

These changes were intended to make player actions easier to understand and calculation outcomes easier to trace. The revision record describes **implemented improvements**, rather than treating every possible refinement as already complete.

---

## 4. Future Development Opportunities

The current version prioritizes educational clarity and structured financial decision making. Future improvements could include:

- **Dynamic markets:** Introduce alternative price movements, variable NPC responses, and different economic scenarios to improve replayability.

- **Realistic FX Trading:** Incorporate bid–ask spreads, liquidity constraints, execution delays, and cross-border transfer restrictions.

- **Advanced portfolio analytics:** Add more detailed capital tracking, drawdown analysis, and stress-testing features to strengthen risk assessment.

- **Improved learning experience:** Provide optional tutorials, adjustable difficulty levels, and more detailed post-round feedback.

- **Technical development:** Implement automated testing, cross-device optimization, saved game progress, and modular code architecture to improve reliability and scalability.


