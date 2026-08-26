# SOLUTION_STRUCTURE

### 1. User → Input → Process → Output → User Action

Access -> Information -> Interpret -> Position -> Market reacts -> P&L/Learn

- **Tiếp cận (Access):** Người chơi có thể tiếp cận/kết nối với những nhân vật, thị trường hoặc nguồn dữ liệu nào?
- **Thông tin (Information):** Người chơi nhìn thấy những thông tin gì, tốc độ nhận thông tin nhanh ra sao, và lượng tín hiệu nhiễu (noise) lẫn trong đó là bao nhiêu?
- **Phân tích (Interpret):** Người chơi tiến hành phân tích và giải mã các yếu tố về cung, cầu, dòng vốn, lãi suất và rủi ro.
- **Thiết lập vị thế (Position):** Ra quyết định: Mua / Bán / Nắm giữ / Vay mượn / Đầu tư / Phòng vệ rủi ro (Hedge) / Giảm đòn bẩy.
- **Thị trường phản ứng (Market reacts):** Các hành động của NPC, hành động của người chơi, các sự kiện ngẫu nhiên và điều kiện vĩ mô sẽ cùng tác động làm thay đổi giá cả và thanh khoản trên thị trường.
- **Lãi lỗ / Bài học (P&L / Learn):** Người chơi ghi nhận mức lợi nhuận hoặc thua lỗ (bằng tiền), qua đó thấu hiểu được lý do cốt lõi khiến quyết định của mình thành công hay thất bại.

### 2. Initial Required Information

**Thông tin Thị trường (Market Information)**
- Giá cả / Báo giá (Prices / quotes)
- Tỷ giá hối đoái (Exchange rates)
- Lãi suất (Interest rates)
- Chênh lệch giá mua – bán (Bid–ask spreads)

**Tín hiệu Thị trường (Market Signals)**
- Cung & cầu (Supply & demand)
- Tin tức / Thông tin (News / information)
- Dòng vốn (Capital flows)
- Động thái của Ngân hàng Trung ương (Central bank actions)

**Điều kiện Giao dịch (Trading Conditions)**
- Chi phí giao dịch (Transaction costs)
- Thanh khoản thị trường (Liquidity)
- Độ trễ khớp lệnh (Execution delay)
- Khối lượng giao dịch (Trading volume)

**Vị thế & Rủi ro của Người chơi (Player Position & Risk)**
- Nguồn vốn / Vị thế giao dịch (Capital / positions)
- Đòn bẩy tài chính (Leverage)
- Mức độ biến động (Volatility)
- Rủi ro tiền tệ / Rủi ro huy động vốn (Currency / funding risk)


### 3. Core Process Type

So sánh giá cả → Nhận diện cơ hội chênh lệch giá → Tính toán lợi nhuận tiềm năng → Hạch toán chi phí và rủi ro → Ra quyết định giao dịch.


### 4. Minimum Viable Product (MVP) Specification — Phase 3 Focus

| Câu hỏi | Chi tiết triển khai MVP |
| :--- | :--- |
| **Core user need** | Sinh viên ngành Tài chính – Ngân hàng cần hiểu trực quan cách cơ hội lợi nhuận từ Carry Trade đi kèm với rủi ro tỷ giá và đòn bẩy, đồng thời nhận được bảng tổng kết đa chiều đánh giá kỷ luật giao dịch cùng bài học kinh tế cốt lõi sau cú sốc The Unwind. |
| **Core input** | - **Cấu hình vị thế:** Khối lượng vay JPY và tỷ lệ phân bổ vào danh mục tài sản sinh lời (US Equities, High-yield Bonds).<br>- **News và thông tin nhiễu:** Các biến động tin tức vĩ mô, chỉ số kinh tế, tâm lý thị trường,....|
| **Core logic** | Vòng lặp vĩ mô theo lượt (Round-based Macro Engine):<br>`Tin tức & Tín hiệu vĩ mô (Fed/BOJ Rates)` ➔ `Vào lệnh & Thiết lập đòn bẩy` ➔ `Cú sốc thị trường (The Unwind Squeeze)` ➔ `Ghi nhận chuỗi quyết định` ➔ `Xuất màn hình Tổng kết giai đoạn (Debrief & Summary Dashboard)`. |
| **Core output** | **Màn hình Tổng kết Giai đoạn (End-of-Phase Debrief Dashboard):**<br>- **-Hiệu suất đánh giá kết quả chơi (KPI Cards)**<br>- **Đánh giá Quyết định Giao dịch của bạn (Decision Debrief Bullets):** Nhận xét chi tiết các nước đi cụ thể (ví dụ: mức độ lạm dụng đòn bẩy khi thị trường đảo chiều, khả năng thoát hàng trước khi bị Margin Call, việc bỏ lỡ cơ hội do thiếu phòng hộ).<br>- **Bài học Kinh tế Cốt lõi (Key Lessons Bullets):** Rút ra 3 nguyên lý tài chính thực tế tương ứng với kịch bản vừa trải qua.|
| **Must include** | - Cơ chế vay JPY lãi suất thấp và đầu tư tài sản sinh lời cao tại thị trường Mỹ.<br>- Sự kiện cao trào cú sốc "The Unwind" (lãi suất BOJ đảo chiều, JPY tăng vọt buộc giải chấp hàng loạt).<br>- Hệ thống logic tính điểm cho 4 thẻ chỉ số (Lợi nhuận, Rủi ro, Lọc tin tức, Điểm tổng).<br>- Bảng tổng kết giao diện trực quan hiển thị đánh giá quyết định và bài học kinh tế.<br>- Hướng dẫn người chơi cách sử dụng và khai thác game.
| **Not included yet** | - Phase 1 (Tulip Mania) và Phase 2 (Thai Baht 1997).<br>- Bảng theo dõi số dư chi tiết từng giây trong lúc chơi.<br>- Chế độ chơi nhiều người (Multiplayer / PvP).<br>- Bảng xếp hạng trực tuyến (Online Leaderboard).<br>- Kết nối API dữ liệu thị trường trực tiếp. |

___

### Scope Cutting Verification

* **Output quan trọng nhất:** Màn hình Dashboard Tổng kết Màn chơi (End-of-Phase Debrief Dashboard) với 4 thẻ chỉ số điểm và 2 khối nội dung: *Đánh giá quyết định giao dịch* & *Bài học kinh tế cốt lõi*.
* **Tính năng tinh gọn:** Lược bỏ toàn bộ các màn hình theo dõi số dư phức tạp; chuyển toàn bộ dữ liệu giao dịch thành các nhận xét và chỉ số đánh giá cô đọng tại màn hình kết thúc.
* **Dữ liệu:** Sử dụng kịch bản vĩ mô định sẵn (Calibrated Macro Scenarios) phản ánh cú sốc đảo chiều dòng tiền Carry Trade.
* **Mục tiêu sản phẩm:** Cung cấp trải nghiệm mô phỏng ngắn gọn nhưng đọng lại bài học thực tế sâu sắc cho sinh viên.

### 5. Fallback / Out of Scope

**In scope:**
- Hệ thống phân vai, thông tin và quyền truy cập thị trường.
- Mô phỏng các nghiệp vụ: Kinh doanh chênh lệch giá cơ bản (Simple Arbitrage), chênh lệch giá liên thị trường / tam giác (Cross-market / Triangular Arbitrage), và giao dịch chênh lệch lãi suất (Carry Trade).
- Tính toán lợi nhuận / thua lỗ (P&L), chi phí giao dịch và các chỉ số rủi ro.
- Mô phỏng thị trường và các sự kiện khủng hoảng dựa trên kịch bản tĩnh (Rule-based).
- Hệ thống ghi nhận quyết định của người chơi, từ đó dẫn đến các phản ứng của thị trường và kết quả tương ứng.

**Out of scope:**
- Giao dịch bằng tiền thật.
- Chế độ nhiều người chơi (Multiplayer) và Bảng xếp hạng trực tuyến.
- Tích hợp AI đóng vai trò Trader hoặc sử dụng Học máy (Machine Learning).
- Tái tạo dữ liệu lịch sử thị trường một cách toàn diện và chính xác tuyệt đối.
- Xây dựng hạ tầng giao dịch hoặc hệ thống môi giới chuyên nghiệp.
- Dự báo thị trường thực tế hoặc đưa ra lời khuyên đầu tư tài chính.

**Fallback:**
- Loại bỏ âm thanh và hiệu ứng chuyển động để tránh giật lag
- Bỏ phase 1, tập trung vào phase 2 và 3 thể hiện cơ chế arbitrage tốt hơn

### 6. Initial Route Hypothesis

Ban đầu, nhóm giả định rằng sinh viên sẽ tiếp thu các khái niệm tài chính hiệu quả hơn khi họ được trực tiếp trải nghiệm hệ quả từ những quyết định của mình, thay vì chỉ nghiên cứu các công thức và ví dụ lý thuyết suông.

Do đó, ARBIVERSE được xây dựng theo một lộ trình phát triển tuần tự:

Học khái niệm → Gia nhập thị trường → Nhận diện cơ hội → Ra quyết định tài chính → Quan sát kết quả → Rút ra bài học → Điều chỉnh chiến lược

Trò chơi bắt đầu với sự bất cân xứng thông tin, tiến tới kinh doanh chênh lệch tỷ giá (FX arbitrage) cùng các ma sát thị trường, và cuối cùng đưa vào nghiệp vụ giao dịch chênh lệch lãi suất (carry trade) gắn liền với rủi ro vĩ mô. Khi thị trường ngày càng trở nên phức tạp, sinh viên được kỳ vọng sẽ chuyển đổi tư duy từ việc đơn thuần tìm kiếm cơ hội sang việc đánh giá tỷ suất sinh lời và quản trị rủi ro.

Giả thuyết cốt lõi là vòng lặp "Quyết định - Phản hồi" (decision - feedback loop) này sẽ giúp sinh viên thấu hiểu sâu sắc hơn về mối liên hệ thực tế giữa kinh doanh chênh lệch giá, tính hiệu quả của thị trường, khả năng sinh lời và rủi ro.


### 7. Responsibility by Output

#### Hoàng Tường Anh:
- Hệ thống tính điểm cuối game (Scoring Logic): Định nghĩa công thức xếp loại trader. Xếp hạng được tính dựa trên điểm trung bình của 3 Phase, chia thành các danh hiệu: "Master Macro Arbitrageur" (>=88 điểm), "Prudent Arbitrageur" (>=75 điểm) và "Opportunistic Speculator" (>=60 điểm).
- Logic đánh giá từng màn (Debriefing): Xây dựng hệ thống bài học rút ra (Key Lessons) tương ứng với từng hành động của người chơi tại file
- Giao diện màn hình (interface)

#### Nguyễn Minh Tâm:
- Historical Data sheet
- The Calculation Engine
  - *Sheet Phase 1:* Công thức tính Lợi nhuận gộp, trừ Phí mở mạng lưới, Phí thuê người đưa thư, Phí lưu kho để ra Lợi nhuận ròng.
  - *Sheet Phase 2:* Mô hình Arbitrage tam giác 3 bước, công thức trừ Bid-Ask spread, % phí giao dịch, và công thức tính cạn kiệt dự trữ ngoại hối của NHTW.
  - *Sheet Phase 3:* Công thức tính Carry Yield ròng sau chi phí vốn vay, công thức nhân đòn bẩy (L), công thức tính tỷ lệ ký quỹ danh mục (Margin Level) và điều kiện kích hoạt Margin Call / Bán tháo giải chấp (Liquidation).
- Chuẩn hoá tham số cho coder
- Thiết kế Hệ thống Tin tức & Ma trận Nhiễu. Gán trọng số và kênh tác động (Impact Weights & Transmission Channels) cho từng tin tức: xác định rõ tin nào tác động trực tiếp vào Cung/Cầu, Dự trữ ngoại hối hay Chỉ số rủi ro toàn cầu (Global Risk Dashboard), và tin nào không gây biến động cơ bản

#### Trần Thu Anh:
- Thiết kế Vật phẩm: Định giá cơ sở (Base Price) và Hệ số rủi ro (Risk Factor) cho 4 loại hoa Tulip.
- Thiết kế hồ sơ NPC: Thiết kế 3 nhân vật đại diện cho các tầng lớp thị trường (Grower, Merchant, Moneylender).
- Xác định Thông số Cốt lõi: Gắn định mức phí mở khóa (Unlock Cost), chỉ số uy tín yêu cầu (Reputation Required) cho từng NPC.
- Thiết lập sẵn các lệnh Mua/Bán (Bid/Ask), mức giá (Price) và Số lượng (Quantity) cho từng nhân vật.
- Tiến trình thời gian: Viết tóm tắt nội dung cho tổng cộng 9 vòng chơi (3 vòng x 3 Phase), tạo ra một câu chuyện liền mạch dẫn dắt người chơi từ lúc thị trường bình yên đến khi hoảng loạn và sụp đổ.

#### Lê Quỳnh Chi
- Xây dựng bộ lưu trữ các biến số của người chơi (Ví dụ: Số tiền đang có, vòng chơi hiện tại, số lượng hoa Tulip đang cầm).
- Viết thuật toán sinh giá tự động (Price Generator) cho mỗi vòng chơi dựa trên các biến số vĩ mô Tâm và Thu Anh đã thiết kế.

#### Hoàng Hà Uyên
- Thiết kế các mảnh ghép giao diện độc lập (Ví dụ: Khung thẻ bài NPC thương lái, Bảng điện tử hiển thị tỷ giá nhấp nháy, Nút bấm Mua/Bán).
- Nhận dữ liệu từ Chi (như số dư = 50.000$) và gán vào giao diện. Gắn các hàm Chi đã viết vào các nút bấm (Ví dụ: Bấm nút "Mua" thì tự động gọi hàm khop_Lenh_Mua()).
- Lập trình các hiệu ứng phản hồi người dùng: Hiện thông báo (Toast) màu xanh khi chốt lời thành công, chớp đỏ toàn màn hình khi bị Margin Call.
- Tích hợp hệ thống âm thanh (tiếng báo động, tiếng đếm ngược) và hiệu ứng chuyển động để tăng áp lực thời gian.

