# SOLUTION_STRUCTURE

### 1. User → Input → Process → Output → User Action

Access -> Information -> Interpret -> Position -> Market reacts -> P&L/Learn[cite: 1]

- **Tiếp cận (Access):** Người chơi có thể tiếp cận/kết nối với những nhân vật, thị trường hoặc nguồn dữ liệu nào?[cite: 1]
- **Thông tin (Information):** Người chơi nhìn thấy những thông tin gì, tốc độ nhận thông tin nhanh ra sao, và lượng tín hiệu nhiễu (noise) lẫn trong đó là bao nhiêu?[cite: 1]
- **Phân tích (Interpret):** Người chơi tiến hành phân tích và giải mã các yếu tố về cung, cầu, dòng vốn, lãi suất và rủi ro[cite: 1].
- **Thiết lập vị thế (Position):** Ra quyết định: Mua / Bán / Nắm giữ / Vay mượn / Đầu tư / Phòng vệ rủi ro (Hedge) / Giảm đòn bẩy[cite: 1].
- **Thị trường phản ứng (Market reacts):** Các hành động của NPC, hành động của người chơi, các sự kiện ngẫu nhiên và điều kiện vĩ mô sẽ cùng tác động làm thay đổi giá cả và thanh khoản trên thị trường[cite: 1].
- **Lãi lỗ / Bài học (P&L / Learn):** Người chơi ghi nhận mức lợi nhuận hoặc thua lỗ (bằng tiền), qua đó thấu hiểu được lý do cốt lõi khiến quyết định của mình thành công hay thất bại[cite: 1].

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


### 4. (MVP) Specification

| Câu hỏi | Câu trả lời |
| :--- | :--- |
| **Core user need** | Sinh viên ngành Tài chính – Ngân hàng cần hiểu trực quan cách cơ hội kinh doanh chênh lệch giá (Arbitrage) biến mất khi thị trường tiến hóa, và tại sao các chiến lược giao dịch hiện đại (Carry Trade) luôn tiềm ẩn rủi ro thanh khoản cùng sụp đổ dây chuyền. |
| **Core input** | - **Origin Selection:** Chọn xuất thân/vị trí ban đầu.<br>- **Information Access:** Chi phí mở mạng lưới quan hệ, mua tin tức, thuê người đưa thư.<br>- **Trade Orders:** Khối lượng mua/bán, cặp tỷ giá arbitrage, hạn mức đòn bẩy vay JPY và tỷ lệ hedging. |
| **Core logic** | Vòng lặp giao dịch theo từng lượt (Round-based Engine):<br>`Access` ➔ `Information (Signal vs. Noise)` ➔ `Interpret` ➔ `Position (Trade & Leverage)` ➔ `Market Reacts (State-based Engine)` ➔ `P&L & Margin Call / Unwind`. |
| **Core output** | - **Live Tracking:** Biến động tài sản ròng (NAV), tiền mặt, tỷ lệ an toàn ký quỹ (Margin Level).<br>- **Market Dashboard:** Bảng giá Bid-Ask, Global Risk Dashboard.<br>- **End-of-Round Debrief:** Bảng phân tích nguyên nhân thắng/thua và cảnh báo giải chấp (Margin Call). |
| **Must include** | - Đủ 3 Phase đại diện cho 3 giai đoạn tiến hóa (Tulip Mania ➔ Thai Baht 1997 ➔ Modern Yen Carry).<br>- Các loại ma sát thị trường thực tế: Bid-Ask spread, chi phí mở tin tức, phí giao dịch, trượt giá.<br>- Hệ thống phân tách tin tức thật (True Signal) và tin tức nhiễu (Noise).<br>- Cơ chế The Unwind và kích hoạt Margin Call/Liquidation ở Phase 3. |
| **Not included yet** | - Chế độ chơi nhiều người (Multiplayer / PvP).<br>- Bảng xếp hạng trực tuyến (Online Leaderboard).<br>- AI thông minh tự thích ứng cho NPC (chỉ dùng Rule-based).<br>- Kết nối API dữ liệu thị trường thực tế (chỉ dùng Calibrated Sample Data).<br>- Hệ thống xác thực/tài khoản người dùng (chỉ chơi dạng Guest). |

---

### Scope Cutting Verification
- **Output quan trọng nhất:** Bảng theo dõi NAV và màn hình phân tích nguyên nhân Lời/Lỗ (Live NAV & Debrief Summary).
- **Tính năng lược bỏ:** Bỏ minigame trồng hoa ở Phase 1, bỏ cây hội thoại NPC phức tạp, bỏ đồ họa 3D.
- **Dữ liệu:** Sử dụng 100% Calibrated Sample Data trên file cấu hình/JSON thay vì gọi API ngoài.
- **Phân khúc người dùng:** Chỉ tập trung duy nhất vào Sinh viên khối ngành Kinh tế / Tài chính – Ngân hàng.
- **Hệ thống phụ:** Cắt bỏ hoàn toàn Account System, Chatbot AI và các Dashboard thống kê phụ.


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

