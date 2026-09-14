# WEEK 4 — FINANCIAL LOGIC, TECHNICAL READINESS & MIDTERM

## 1. Project Logic Chain

```text
Problem
→ Người chơi khó thấy đồng thời tác động của asset return, FX risk và JPY funding cost trong carry trade

Target User
→ Sinh viên tham gia financial simulation game

User Task
→ Vay JPY → đổi sang USD → đầu tư → quản lý danh mục → quản lý khoản vay → trả nợ

Input
→ Role + Borrowing + Market Data + Trading Decisions + Repayment Decisions

Financial Logic
→ Borrowing → FX Conversion → Trading → Floating Interest
→ Portfolio Valuation → Debt Valuation → Repayment → P&L → Player Status

Output
→ Cash, Portfolio Value, Debt, Net Wealth, P&L, Status

User Action
→ BUY / SELL / HOLD / DEPOSIT / WITHDRAW / REPAY / BORROW
```

---

## 2. Input – Financial Logic – Output Mapping

| Input | Financial meaning | Rule / Calculation | Output |
|---|---|---|---|
| Player role | Giới hạn tài chính | Lookup role parameters | Max borrowing, info cost |
| Borrow package | Quy mô vay JPY | Borrow % × Max JPY Principal | JPY loan |
| USD/JPY | FX risk | JPY / USDJPY | USD funding / USD debt |
| BOJ rate by round | Floating funding cost | Interest calculated using each round's BOJ rate | Interest cost |
| Information decision | Chi phí thông tin | Check affordability | Information / cost |
| BUY / SELL / HOLD | Quyết định đầu tư | Validate cash and holdings | Asset holdings |
| DEPOSIT / WITHDRAW | Defensive allocation | Transfer Free Cash ↔ US Cash | US Cash balance |
| REPAY / HOLD | Quản lý khoản vay | Full repayment by loan package | Remaining debt |
| Asset prices | Market risk | Quantity × Price | Portfolio value |
| Portfolio + Debt | Financial position | Assets − Debt | Net Wealth |
| End Phase | Final settlement | Liquidate assets + repay debt | Final P&L |

---

## 3. Formula and Rules

### 3.1 Borrowing

Người chơi chọn:

```text
0% / 25% / 50% / 75% / 100%
```

```text
Requested JPY
= Borrow % × Maximum JPY Principal
```

Khoản vay chỉ được chấp nhận khi đồng thời thỏa:

```text
Outstanding JPY ≤ Max JPY Principal
```

và:

```text
Outstanding JPY / Current USDJPY ≤ Max USD Equivalent
```

Sau khi được chấp nhận:

```text
Borrowed USD
= Accepted JPY Principal / USDJPY at borrowing
```

USD nhận được được cộng vào Free Cash.

---

### 3.2 Floating Interest

Lãi suất vay là **floating theo từng round**.

Khoản vay đang outstanding trong round nào thì chịu BOJ rate của round đó:

```text
Interest
= Σ [Outstanding Principal × BOJ Rate of Round × Round Months / 12]
```

Ví dụ khoản vay mở ở R1 và giữ đến End Phase:

```text
Interest
= Principal × (
R1 Rate × R1 Months / 12
+ R2 Rate × R2 Months / 12
+ R3 Rate × R3 Months / 12
+ R4 Rate × R4 Months / 12
)
```

Nếu khoản vay được trả tại **Start R3**:

```text
Interest
= Principal × (
R1 Rate × R1 Months / 12
+ R2 Rate × R2 Months / 12
)
```

Không tính lãi R3 vì khoản vay đã được trả trước khi R3 bắt đầu.

---

### 3.3 Trading

#### BUY

```text
Purchase Cost
= Quantity × Current Price
```

BUY được chấp nhận khi:

```text
Purchase Cost ≤ Available Free Cash
```

#### SELL

SELL được chấp nhận khi:

```text
Sell Quantity ≤ Current Holdings
```

```text
Sale Proceeds
= Sell Quantity × Current Price
```

#### HOLD

Holdings không đổi nhưng Market Value thay đổi theo giá thị trường.

---

### 3.4 US Cash

Free Cash và US Cash được theo dõi riêng.

```text
DEPOSIT:
Free Cash ↓
US Cash ↑
```

```text
WITHDRAW:
US Cash ↓
Free Cash ↑
```

Không được withdraw vượt quá US Cash hiện có.

Chỉ US Cash sinh lãi:

```text
US Cash Interest
= US Cash Balance × US Cash Return
```

Idle Free Cash không sinh lãi.

---

### 3.5 Information

Thông tin chỉ được mua khi:

```text
Beginning Free Cash ≥ Information Cost
```

Nếu không đủ tiền:

```text
Information Purchase = REJECT
Information Cost = 0
```

---

### 3.6 Debt Repayment

Mỗi khoản vay ở các round sau có hai lựa chọn:

```text
HOLD / REPAY
```

Repayment xảy ra tại **đầu round**, sau SELL / WITHDRAW và trước new borrowing.

Không cho phép partial repayment.

```text
Total JPY Due
= JPY Principal + Accumulated Floating Interest
```

```text
USD Repayment
= Total JPY Due / Current USDJPY
```

Sau khi trả hết một loan package, borrowing capacity được phục hồi.

---

### 3.7 FX Logic

```text
USD Debt
= JPY Debt / USDJPY
```

```text
USDJPY ↑
→ JPY depreciates
→ USD value of debt ↓
→ Positive for carry trade
```

```text
USDJPY ↓
→ JPY appreciates
→ USD value of debt ↑
→ Negative for carry trade
```

FX P&L:

```text
FX P&L
= JPY Principal / Borrow FX
− JPY Principal / Repayment FX
```

---

### 3.8 Portfolio and Net Wealth

```text
Tech Market Value
= Tech Quantity × Tech Price
```

```text
S&P Market Value
= S&P Quantity × S&P Price
```

```text
Gross Portfolio Value
= Free Cash
+ Tech Market Value
+ S&P Market Value
+ US Cash
```

```text
USD Debt MTM
= (Outstanding JPY Principal + Accrued Floating Interest)
  / Current USDJPY
```

```text
Net Wealth
= Gross Portfolio Value − USD Debt MTM
```

---

### 3.9 Player Classification

```text
ACTIVE
= Net Wealth ≥ 0 and no repayment default
```

```text
AT RISK
= Net Wealth < 0 but no repayment default
```

```text
BANKRUPT
= Debt repayment due > available liquidity
  after valid asset sales and US Cash withdrawals
```

Negative Net Wealth does not automatically mean bankruptcy.

---

### 3.10 Final P&L

```text
Portfolio P&L
= Tech P&L + S&P P&L + US Cash Interest
```

```text
Net P&L
= Portfolio P&L
+ FX P&L
− Floating Interest Cost
− Information Cost
```

---

## 4. Assumptions and Limitations

### Assumptions

- Phase 3 gồm 4 rounds và End Phase.
- Một round mặc định bằng 3 tháng.
- BOJ rate là floating funding rate và có thể thay đổi giữa các round.
- Khoản vay chịu rate của từng round mà nó còn outstanding.
- Repayment xảy ra ở đầu round.
- Không cho phép partial repayment.
- Repaid borrowing capacity có thể được sử dụng lại.
- Free Cash không sinh lãi.
- End Phase tự động liquidate toàn bộ tài sản và settle remaining debt.

### Limitations

Model chưa xét:

- transaction cost;
- bid–ask spread;
- tax;
- margin call;
- collateral requirement;
- market impact;
- intraday volatility;
- hedging derivatives.

Market path là stylized scenario phục vụ simulation, không phải dự báo thị trường thực tế.

---

## 5. Sample Calculation / Logic Test

### Input

```text
Role = Conservative Investor
Max JPY Principal = ¥12,000,000
Borrow = 50%
Borrow FX = 150

R1 Rate = 0.10%
R2 Rate = 0.10%
R3 Rate = 0.25%
R4 Rate = 0.25%

Each Round = 3 months

Tech = 10 units × $450
S&P = 10 units × $520
```

### Step 1 — Borrowing

```text
JPY Loan
= 50% × ¥12,000,000
= ¥6,000,000
```

```text
Borrowed USD
= 6,000,000 / 150
= $40,000
```

### Step 2 — Investment

```text
Tech Purchase
= 10 × 450
= $4,500
```

```text
S&P Purchase
= 10 × 520
= $5,200
```

```text
Ending Free Cash
= 40,000 − 4,500 − 5,200
= $30,300
```

### Step 3 — Floating Interest to End Phase

```text
Interest
= 6,000,000 × [
0.10% × 3/12
+ 0.10% × 3/12
+ 0.25% × 3/12
+ 0.25% × 3/12
]

= ¥10,500
```

### Step 4 — End Phase

Assume:

```text
End USDJPY = 147
Tech End Price = $440
S&P End Price = $545
```

Asset liquidation:

```text
Tech = 10 × 440 = $4,400
S&P = 10 × 545 = $5,450

Total Available Cash
= 30,300 + 4,400 + 5,450
= $40,150
```

Debt repayment:

```text
Total JPY Due
= 6,000,000 + 10,500
= ¥6,010,500
```

```text
USD Repayment
= 6,010,500 / 147
= $40,887.76
```

Final Wealth:

```text
Final Wealth
= 40,150 − 40,887.76
= −$737.76
```

P&L reconciliation:

```text
Portfolio P&L
= −100 + 250
= +$150
```

```text
FX P&L
= 6,000,000/150 − 6,000,000/147
= −$816.33
```

```text
Interest Cost
= 10,500 / 147
= $71.43
```

```text
Net P&L
= 150 − 816.33 − 71.43
= −$737.76
```

Expected:

```text
Final Wealth ≈ Net P&L
```

---

## 6. Logic Testing

| Test | Expected Result |
|---|---|
| Borrow vượt JPY cap | REJECT |
| Borrow vượt USD-equivalent cap | REJECT |
| BUY vượt Free Cash | REJECT |
| SELL vượt holdings | REJECT |
| WITHDRAW vượt US Cash | REJECT |
| Buy information không đủ tiền | REJECT |
| JPY appreciation | USD Debt tăng |
| JPY depreciation | USD Debt giảm |
| BOJ rate tăng ở round sau | Interest cost tăng đối với debt còn outstanding |
| Repay Start R3 | Chỉ tính interest R1 + R2 |
| HOLD asset | Quantity giữ nguyên |
| Repay loan | Principal + accumulated floating interest được thanh toán |
| Repay rồi borrow lại | Borrowing capacity được phục hồi |
| Net Wealth âm | AT RISK |
| Không đủ liquidity trả nợ | BANKRUPT |
| End Phase | Assets liquidated, debt settled |
| Final Wealth vs Net P&L | Reconciliation ≈ 0 |

---

## 7. Technical Route

Current prototype:

```text
Excel
```

Excel được sử dụng để:

- validate financial formulas;
- test game rules;
- test edge cases;
- reconcile P&L.

MVP route:

```text
Excel Financial Logic
→ Python Financial Engine
→ Streamlit Interface
→ GitHub
→ Streamlit Community Cloud
```

Nguyên tắc implementation:

```text
Python Expected Output
= Excel Expected Output
```

trước khi logic được đưa vào product.

---

## 8. Deployment Route and Fallback

Primary deployment:

```text
GitHub → Streamlit Community Cloud
```

Fallback:

```text
Excel Simulation Model
```

Nếu web application chưa ổn định tại thời điểm assessment, Excel vẫn có thể chứng minh:

- input;
- financial logic;
- calculation;
- P&L;
- player status;
- scenario testing.

---
