
# 1. SIMULATED DATA

Dữ liệu mô phỏng các giai đoạn khủng hoảng tài chính và cơ chế thị trường qua 3 pha lịch sử điển hình.

---

## Phase 1 — Information Asymmetry / Pre-Arbitrage (Tulip Mania 1637)

| Round | Trader | Lệnh | Số lượng | Giá (CU) | Ghi chú vận hành & Ý nghĩa kinh tế |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **1** <br> *(Khởi động Tháng 1/1637)* | TRADER_A | SELL | 5 | 35 | • Mua từ A (35 CU) bán cho B (48 CU) → lãi 13 CU.<br>• Phản ánh giá nền trước cao trào đầu cơ. |
| | TRADER_B | BUY | 3 | 48 | |
| | TRADER_C | SELL | 4 | 42 | |
| | TRADER_D | BUY | 5 | 40 | |
| **2** <br> *(Đỉnh sốt giá)* | TRADER_A | SELL | 4 | 55 | Giá tăng vọt, kích thích người chơi vay tối đa đòn bẩy để gom hàng. |
| | TRADER_B | BUY | 3 | 75 | |
| | TRADER_C | SELL | 5 | 62 | |
| | TRADER_D | BUY | 4 | 68 | |
| **3** <br> *(Vỡ trận, đóng băng thanh khoản)* | TRADER_A | SELL | 8 | 40 | • Trader D rút lui hoàn toàn.<br>• Lực bán tháo ồ ạt, người chơi ôm hoa không thể thoát hàng. |
| | TRADER_B | BUY | 1 | 15 | |
| | TRADER_C | SELL | 6 | 35 | |
| | TRADER_D | BUY | 0 | 0 | |

---

## Phase 2 — Thai Baht Crisis (1997)

| Thông số mô hình | Round 1 (Neo tỷ giá)<br>*Cuối 1996 – Đầu 1997* | Round 2 (Thị trường kép & Squeeze)<br>*Tháng 5 – 6/1997* | Round 3 (Thả nổi vỡ trận)<br>*Tháng 7/1997* |
| :--- | :---: | :---: | :---: |
| **Tỷ giá Onshore** | 25.2 THB/USD | 25.5 THB/USD | 32.0 THB/USD |
| **Tỷ giá Offshore** | 25.3 THB/USD | 29.5 THB/USD | 32.0 THB/USD |
| **Lãi suất vay THB / round** | 2% | 8% *(Phạt Short)* | 4% |
| **Phí kiểm soát vốn On-Offshore** | 0% | 8% | 0% |
| **Dự trữ khả dụng của BOT** | 38.7 tỷ USD | < 8 tỷ USD | < 3 tỷ USD *(Cạn kiệt)* |

---

## Phase 3 — Yen Carry Trade / Modern Global Market

| Round | Đối tượng / Mã tài sản | Loại lệnh / Giao dịch | Hạn mức / Khối lượng | Báo giá / Mức sinh lời | Ghi chú vận hành & Ý nghĩa kinh tế |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **1** <br> *(Tích lũy & Vay rẻ)* | `USD/JPY` | Vay JPY & Đổi sang USD | Theo vai chơi | 155.0 JPY/USD | Lãi vay 0.25%/round. Đổi Yên sang USD giá nền. |
| | `US_TECH` | BUY *(Cổ phiếu M7)* | Max 100% danh mục | +10.0% / round | Cổ phiếu Big Tech tăng mạnh nhờ đòn bẩy và sóng AI. |
| | `US_SP500` | BUY *(S&P 500 Index)* | Max 100% danh mục | +6.0% / round | Thị trường chung tăng trưởng ổn định. |
| | `US_BOND` | BUY *(US Treasury 10Y)* | Max 100% danh mục | +1.5% / round | Lợi suất trái phiếu ổn định quanh 4.3%/năm quy đổi theo quý. |
| | `USD_CASH` | DEPOSIT *(Gửi USD)* | Không giới hạn | +1.2% / round | Lợi suất tiền mặt phi rủi ro từ Fed Funds Rate (5.25%/năm). |
| **2** <br> *(Đỉnh sốt giá & Can thiệp)* | `USD/JPY` | Duy trì nợ / Đổi thêm | Theo vai chơi | 160.0 JPY/USD | Lãi vay tăng lên 1.0%/round. Nợ JPY quy ra USD giảm (lãi ảo). |
| | `US_TECH` | HOLD / Mua thêm | Max 100% danh mục | +2.0% / round | Big Tech khựng lại do định giá căng; thị trường đi ngang. |
| | `US_SP500` | HOLD / Mua thêm | Max 100% danh mục | +1.0% / round | Thị trường chung chững lại, biến động nhạy cảm. |
| | `US_BOND` | HOLD / Mua thêm | Max 100% danh mục | +1.0% / round | Lợi suất ổn định, phòng thủ danh mục. |
| | `USD_CASH` | DEPOSIT *(Gửi USD)* | Không giới hạn | +1.2% / round | Lãi suất tiền mặt giữ nguyên. |
| **3** <br> *(Sập Unwind)* | `USD/JPY` | Mua lại JPY trả nợ | Toàn bộ nợ gốc + lãi | 142.0 JPY/USD | BOJ nâng lãi, phí vay vọt lên 3.5%/round. Tỷ giá rơi về 142 ép tăng nợ. |
| | `US_TECH` | SELL *(Bán tài sản)* | Toàn bộ danh mục | -25.0% / round | M7 sụt giảm sâu do quỹ đầu cơ bán tháo gom USD đổi JPY. |
| | `US_SP500` | SELL *(Bán tài sản)* | Toàn bộ danh mục | -12.0% / round | S&P 500 giảm theo đà rút vốn của thị trường. |
| | `US_BOND` | SELL *(Bán tài sản)* | Toàn bộ danh mục | +4.0% / round | Dòng tiền đổ vào tài sản trú ẩn đẩy giá trái phiếu tăng. |
| | `USD_CASH` | WITHDRAW *(Rút tiền)* | Toàn bộ tiền mặt | +1.2% / round | Lãi suất tiền mặt nhận đủ kỳ để cấn trừ nợ. |
## 2. DATA STRUCTURE

Dự án ưu tiên sử dụng cấu trúc dữ liệu đơn giản, dễ kiểm tra và phù hợp với tính chất của một game mô phỏng kịch bản (Scenario-based simulation). Cụ thể, nhóm kết hợp sử dụng 2 định dạng:

* **Spreadsheet (Excel/CSV)**

- **Dành cho khâu Thiết kế & Logic Test:** Sử dụng để team Content & Data thiết lập tỷ giá, tính toán chênh lệch (P&L), biên độ đòn bẩy và kiểm thử các kịch bản tĩnh (Scenarios) một cách trực quan.
  
- **JSON trong code - Dành cho khâu Lập trình (Frontend/Backend):** Dữ liệu chuẩn từ Spreadsheet sẽ được chuyển sang định dạng JSON. Định dạng này siêu nhẹ, thân thiện với web, giúp hệ thống truy xuất kịch bản nhanh chóng mà không làm nặng máy người chơi.

**💡 Lý do không sử dụng Database phức tạp:** 

Do ARBIVERSE vận hành hoàn toàn dựa trên dữ liệu mô phỏng (Simulated Data) tĩnh theo từng Phase, không yêu cầu cập nhật Real-time API hay xử lý truy vấn phức tạp. Việc sử dụng JSON giúp tránh phụ thuộc vào hạ tầng server cồng kềnh, đảm bảo game chạy mượt mà ngay trên lớp học.


## 3. DATA FLOW

## LUỒNG DỮ LIỆU CHUNG

Người chơi chọn Role  
↓  
Nạp cấu hình Role  
↓  
Reset vốn của Phase  
↓  
Nạp dữ liệu Round  
↓  
Hiển thị thông tin miễn phí  
↓  
Người chơi quyết định có mua thêm thông tin  
↓  
Người chơi quyết định vay / trả nợ  
↓  
Người chơi quan sát thị trường  
↓  
Đưa ra quyết định giao dịch  
↓  
Kiểm tra dữ liệu đầu vào  
↓  
Thực hiện phép tính tài chính  
↓  
Cập nhật Cash / Asset / Debt  
↓  
Cập nhật Market State  
↓  
Trả lãi cuối Round  
↓  
Tính chỉ tiêu đánh giá  
↓  
Round tiếp theo  

### Cuối Phase

Kết thúc Round cuối  
↓  
Thanh lý / định giá tài sản  
↓  
Tất toán nợ còn lại  
↓  
Kiểm tra phá sản  
↓  
Tính điểm Phase  
↓  
Hiển thị đánh giá  
↓  
Nếu không phá sản → Phase tiếp theo  

---

## LUỒNG DỮ LIỆU THEO TỪNG PHASE

###  Phase 1 — Information Asymmetry & Tulip Trading

Trader Quotes  
+  
1–2 tin miễn phí  
↓  
Người chơi đọc thông tin  
↓  
Có mua Paid Information?  
↓  
Có vay thêm / trả nợ?  
↓  
Quan sát Trader A / B / C / ...  
↓  
BUY / SELL / HOLD  
↓  
Kiểm tra:  
Cash / Inventory / Quantity / Trade Count  
↓  
Thực hiện giao dịch  
↓  
Cập nhật:  
Cash + Inventory + Debt  
↓  
Tính lãi vay cuối Round  
↓  
Market State thay đổi  
↓  
Trader Quotes thay đổi  
↓  
Round tiếp theo  

### Logic chính của Phase 1

- Người chơi tìm kiếm cơ hội chênh lệch giá giữa các Trader.
- Paid Information giúp giảm bất cân xứng thông tin.
- Người chơi có thể sử dụng vốn vay để mở rộng vị thế.
- Inventory có thể được giữ qua các Round.
- Khi thị trường bước sang trạng thái `Liquidity Freeze`, khả năng bán tài sản bị giới hạn.
- Cuối Phase, lượng tài sản chưa bán được sẽ được thanh lý theo `Liquidation Price`.

---

### Phase 2 — FX Arbitrage

Onshore / Offshore FX Quotes  
↓  
Tin miễn phí + Gói thông tin  
↓  
Người chơi tìm Arbitrage Opportunity  
↓  
Chọn chiến lược:  

Cross-Market Arbitrage  
hoặc  
Triangular Arbitrage  

↓  
Chọn Market + Trade Size  
↓  
Có vay vốn?  
↓  
Kiểm tra:  
Bid / Ask / Liquidity / Capital  
↓  
Thực hiện toàn bộ Trading Legs  
↓  
Trừ:  

Transaction Fee  
+ Funding Cost  
+ Slippage  
+ Capital-Control Cost (nếu có)  

↓  
Tính Net Arbitrage Profit  
↓  
Đóng toàn bộ vị thế FX  
↓  
Cập nhật:  
Cash + Debt + P&L  
↓  
Round mới  
↓  
Nạp FX Quotes mới  

> **Rule:** Không carry FX position sang Round tiếp theo. Mọi vị thế arbitrage phải được mở và đóng trong cùng một Round.

### Logic chính của Phase 2

Historical FX data có thể sử dụng **Mid Rate** làm tỷ giá tham chiếu.

Bid và Ask trong game được xây dựng từ Mid Rate và simulated spread.

Historical Mid Rate  
↓  
Apply Bid-Ask Spread  
↓  
Generate Executable Bid / Ask  
↓  
Apply Transaction Cost  
↓  
Apply Slippage  
↓  
Apply Capital-Control Cost nếu giao dịch Onshore ↔ Offshore  
↓  
Calculate Net Arbitrage Profit  

### Công thức Bid / Ask

`Bid = Mid × (1 - Spread / 2)`

`Ask = Mid × (1 + Spread / 2)`

### Net Arbitrage Profit

`Net Arbitrage Profit = Gross Arbitrage Profit - Transaction Fees - Funding Cost - Slippage Cost - Capital-Control Cost`

Trong đó:

- `Bid-Ask Spread` = chi phí thanh khoản / market-making.
- `Transaction Fee` = phí thực hiện giao dịch.
- `Funding Cost` = chi phí vay vốn.
- `Slippage` = chênh lệch giữa giá kỳ vọng và giá thực thi.
- `Capital-Control Cost` = ma sát riêng khi chuyển vốn giữa Onshore và Offshore.

---

### . Phase 3 — Portfolio & Leverage / JPY Carry Trade

JPY Interest Rate  
+  
USD/JPY Exchange Rate  
+  
Free News  
+  
Risk Event  
↓  
Người chơi quyết định mua thêm thông tin  
↓  
Chọn khoản vay JPY  
↓  
Chọn mức Leverage  
↓  
Vay JPY  
↓  
JPY → USD  
↓  
Phân bổ Portfolio  
↓  

US_TECH  
US_SP500  
US_BOND  
USD_CASH  

↓  
Market Event xảy ra  
↓  
Asset Return  
+  
FX Movement  
+  
Funding Rate Change  
↓  
Định giá lại Portfolio  
↓  
Kiểm tra Maintenance Margin  
↓  

Nếu vi phạm:  
Margin Call / Forced Liquidation  

Nếu không vi phạm:  
HOLD / REDUCE / CLOSE  

↓  
Bán tài sản  
↓  
USD → JPY  
↓  
Trừ:  

Funding Cost  
+ FX Conversion Cost  
+ Asset Transaction Cost  
+ Information Cost  

↓  
Trả nợ JPY  
↓  
Cập nhật:  
Cash + Portfolio + Debt  
↓  
Tính:  
P&L + Net Worth + Risk Metrics  
↓  
Round tiếp theo  

### Logic chính của Phase 3

Borrow JPY  
↓  
Convert JPY → USD  
↓  
Invest in US Assets  
↓  
Earn Asset Return  
↓  
USD/JPY Changes  
↓  
Revalue Assets and Debt  
↓  
Check Maintenance Margin  
↓  
HOLD / REDUCE / CLOSE  
↓  
Convert USD → JPY  
↓  
Repay JPY Debt + Interest  
↓  
Calculate Final P&L  

### Portfolio Assets

| Asset ID | Tài sản | Đặc điểm |
|---|---|---|
| `US_TECH` | US Big Tech / Magnificent 7 | High Return / High Risk |
| `US_SP500` | S&P 500 | Medium Return / Medium Risk |
| `US_BOND` | US Treasury 10Y | Defensive / Safe Haven |
| `USD_CASH` | USD Cash | Low Risk / Stable Return |

### Chi phí Phase 3

`Total Cost = JPY Funding Cost + FX Conversion Cost + Asset Transaction Cost + Information Cost`

### Net Worth

`Net Worth = Cash + Market Value of Portfolio - Outstanding Debt - Accrued Interest`

### Leverage

`Leverage = Total Asset Exposure / Player Equity`

### Margin Ratio

`Margin Ratio = Portfolio Value / Outstanding Debt`

Nếu:

`Margin Ratio < Maintenance Margin`

thì:

Trigger Margin Call  
↓  
Forced Asset Sale  
↓  
Convert USD → JPY  
↓  
Repay Debt  

---

## TÓM TẮT LOGIC 3 PHASE

### Phase 1

Information Asymmetry  
↓  
Find Price Differences  
↓  
Trade with Different Traders  
↓  
Manage Inventory & Liquidity Risk  

### Phase 2

FX Market Fragmentation  
↓  
Identify Arbitrage  
↓  
Execute Multiple Trading Legs  
↓  
Manage Spread, Fees & Funding Cost  

### Phase 3

Carry Trade & Portfolio Leverage  
↓  
Borrow Cheap Currency  
↓  
Invest in Risk Assets  
↓  
Manage FX + Asset + Leverage Risk  
↓  
Survive Margin Call / Market Unwind  


—
## 4. EARLY LOGIC TEST

### 4.1. Test 1 — Mua thông tin Phase 1
**Kịch bản cơ sở:**
*   **Input:** 
    *   Role: Information Hunter
    *   Cash: 100
    *   Giá cơ sở gói tin: 20
    *   Hệ số Information Hunter: 0.5
*   **Xử lý kỳ vọng:** 20 × 0.5 = 10
*   **Output kỳ vọng:** 
    *   Chi phí tin = 10
    *   Cash còn = 90
    *   `is_purchased` = TRUE (Nội dung được mở)

**Bảng theo dõi trạng thái:**
| Input | Expected | Actual | Status | Issue |
| :--- | :--- | :--- | :--- | :--- |
| Giá tin 20; hệ số 0.5 | Cost = 10 | Chưa chạy | Chờ backend | Không |

---

### 4.2. Test 2 — Giới hạn mua thông tin
*   **Tình huống:** Player đã mua một paid information trong Round 1.
*   **Input:** Player yêu cầu mua gói thứ hai.
*   **Output kỳ vọng:** **REJECT**
*   **Lý do:** Paid information limit reached (Đã đạt giới hạn mua tin).

---

### 4.3. Test 3 — Vay vốn
*   **Input (Role Speculator):**
    *   Debt = 0
    *   Borrow amount = 100
    *   Max borrow = 200
    *   Rate = 6%
*   **Xử lý kỳ vọng 1 (Khoản vay hợp lệ):** Lãi cuối round = 100 × 6% = 6.
*   **Xử lý kỳ vọng 2 (Vượt hạn mức):** Nếu yêu cầu vay 250 $\rightarrow$ **REJECT** vì 250 > 200.

---

### 4.4. Test 4 — Arbitrage Phase 1
*   **Input:**
    *   Trader A: SELL 2 @ 40
    *   Trader B: BUY 2 @ 55
    *   Player: BUY 2 từ A, SELL 2 cho B. (Không có transaction fee).
*   **Xử lý kỳ vọng:**
    *   Chi phí mua: 2 × 40 = 80
    *   Tiền bán: 2 × 55 = 110
    *   Lợi nhuận: 110 - 80 = 30
*   **Output kỳ vọng:** Lợi nhuận = 30, Số giao dịch đã dùng: `trades_used` = 2/3.

---

### 4.5. Test 5 — Giới hạn số giao dịch
*   **Tình huống:** Player đã thực hiện `trades_used = 3`.
*   **Input:** Player tiếp tục chọn lệnh BUY.
*   **Expected Output:** **REJECT**
*   **Lý do:** Maximum trades per round reached. (Lưu ý: Mua news hoặc vay vốn không làm tăng `trades_used`).

---

### 4.6. Test 6 — Cross-market Arbitrage Phase 2
*   **Input:**
    *   Bangkok: USD/THB Ask = 25.35
    *   Singapore: USD/THB Bid = 25.40
    *   Trade amount: 10,000 USD
*   **Xử lý kỳ vọng:**
    *   Gross profit = (25.40 - 25.35) × 10,000 = 500 THB
    *   Net Profit = 500 - Transaction Fee - Funding Cost - Slippage
*   **Kết luận kỳ vọng:** 
    *   Không được báo “arbitrage profitable” chỉ vì 500 > 0.
    *   Chỉ báo profitable nếu: **Net Profit > 0**.

---

### 4.7. Test 7 — Yen Carry Trade
*   **Input:**
    *   JPY vay: ¥15,000,000
    *   USD/JPY đầu kỳ: 150
    *   USD đầu tư: $100,000
    *   Asset return: +5%
    *   Funding rate: 0.5%
    *   USD/JPY cuối kỳ: 140
    *   *(Tạm bỏ transaction fee để kiểm tra core logic).*
*   **Xử lý kỳ vọng:**
    *   Portfolio USD cuối kỳ = 100,000 × 1.05 = 105,000 USD
    *   Đổi về JPY = 105,000 × 140 = ¥14,700,000
    *   Nợ + lãi = 15,000,000 × 1.005 = ¥15,075,000
    *   P&L = 14,700,000 - 15,075,000 = -375,000 JPY
*   **Expected Output:** Tài sản Mỹ tăng giá nhưng carry trade vẫn lỗ vì JPY tăng giá đủ mạnh. Đây là logic cốt lõi chứng minh: **Positive carry ≠ guaranteed profit**.

