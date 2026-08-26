# PROJECT PROPOSAL


## 1. Problem Direction

- Sinh viên muốn hiểu cách arbitrage hoạt động trong thực tế, thay vì chỉ học khái niệm đơn giản “mua thấp – bán cao” từ giáo trình.
- Giảng viên cũng gặp khó khăn trong việc giải thích cơ chế arbitrage một cách rõ ràng và trực quan.
- Khi thị trường tài chính phát triển, arbitrage trở nên phức tạp hơn do chịu ảnh hưởng của thông tin, chi phí giao dịch, thanh khoản, tỷ giá và rủi ro. Vì vậy, sinh viên khó kết nối kiến thức lý thuyết với cách thị trường tài chính vận hành và cách các cơ hội arbitrage thay đổi theo thời gian.


## 2. Target User

### Primary users

Sinh viên đại học chuyên ngành Tài chính, Ngân hàng, Kinh tế và các lĩnh vực liên quan. ARBIVERSE đặc biệt phù hợp với sinh viên học Tài chính quốc tế, Thị trường và các định chế tài chính hoặc các môn học tương tự.

### Secondary users

Câu lạc bộ tài chính và các tổ chức giáo dục có nhu cầu sử dụng công cụ tương tác để giảng dạy các khái niệm về arbitrage.

## 3. User Task

### Phase 1 – Information Asymmetry

Người chơi phải thu thập và so sánh thông tin từ các thương nhân khác nhau để xác định chênh lệch giá và các cơ hội arbitrage tiềm năng.

Người chơi cần:

- Tìm kiếm và kiểm tra thông tin hữu ích.
- So sánh giá được đưa ra bởi các thương nhân.
- Xác định cơ hội mua và bán.
- Quyết định giao dịch với thương nhân nào và giao dịch bao nhiêu.
- Quyết định thời điểm vào hoặc thoát vị thế khi điều kiện thị trường thay đổi.

**Key user decision:** *Cơ hội nào đáng tin cậy và tôi có nên hành động dựa trên thông tin mình đang có?*

### Phase 2 – FX Arbitrage

Người chơi phải theo dõi tỷ giá giữa các thị trường và xác định liệu một chênh lệch tỷ giá có thực sự tạo ra lợi nhuận sau khi tính đến chi phí giao dịch hay không.

Người chơi cần:

- So sánh tỷ giá giữa các thị trường.
- Tính toán lợi nhuận arbitrage tiềm năng.
- Xem xét bid–ask spread, phí giao dịch, độ trễ khớp lệnh và thanh khoản.
- Quyết định có nên thực hiện giao dịch hay chờ đợi.
- Quyết định lượng vốn phân bổ cho cơ hội.
- Đóng vị thế trước khi chênh lệch giá biến mất.

**Key user decision:** *Chênh lệch giá này có đủ lớn và tồn tại đủ lâu để tôi thực sự kiếm được lợi nhuận không?*

### Phase 3 – Carry Trade & Macro Risk

Người chơi phải đánh giá lợi nhuận tiềm năng của carry trade đồng thời theo dõi các rủi ro có thể làm thay đổi kết quả.

Người chơi cần:

- So sánh lãi suất đi vay và lãi suất đầu tư.
- Tính toán lợi nhuận kỳ vọng.
- Quyết định mức vốn vay và mức đòn bẩy sử dụng.
- Theo dõi tỷ giá và các chỉ báo kinh tế vĩ mô.
- Quyết định duy trì, giảm hoặc đóng vị thế khi điều kiện thị trường thay đổi.

**Key user decision:** *Lợi nhuận tiềm năng có xứng đáng với mức rủi ro tôi đang chấp nhận không, và khi nào tôi nên thoát khỏi vị thế?*


## 4. Desired User Outcome

Users should be able to:

- Hiểu cách các cơ hội arbitrage xuất hiện và biến mất.
- Tính toán lợi nhuận thực tế sau khi trừ chi phí giao dịch.
- Hiểu FX arbitrage và carry trade.
- Trải nghiệm tác động của thanh khoản, đòn bẩy và rủi ro thị trường.
- Đưa ra quyết định tài chính tốt hơn trong điều kiện không chắc chắn.

## 5. Product Statement

Sản phẩm nhận các đầu vào từ người chơi như thông tin, lựa chọn giao dịch, quy mô giao dịch, đòn bẩy và thời điểm giao dịch, sau đó xử lý chúng thông qua các quy tắc thị trường như biến động giá, chi phí giao dịch, thanh khoản, tỷ giá và các cú sốc thị trường.

Sản phẩm tạo ra các đầu ra theo thời gian thực như cơ hội giao dịch, giá thị trường, P&L và mức độ rủi ro. Người chơi sử dụng các kết quả này để điều chỉnh chiến lược và đưa ra quyết định giao dịch tiếp theo.

Sản phẩm được xây dựng theo ba giai đoạn liên kết:

**Phase 1 – Information Asymmetry:** Input: thông tin thu thập từ các thương nhân → Processing: so sánh thông tin và giá → Output: cơ hội arbitrage tiềm năng → Decision: lựa chọn cơ hội để giao dịch.

**Phase 2 – FX Arbitrage:** Input: tỷ giá và điều kiện giao dịch → Processing: tính lợi nhuận sau spread, phí, độ trễ và thanh khoản → Output: lợi nhuận thực tế tiềm năng → Decision: quyết định có nên và có cần thực hiện giao dịch nhanh hay không.

**Phase 3 – Carry Trade & Macro Risk:** Input: lãi suất, tỷ giá, đòn bẩy và điều kiện kinh tế vĩ mô → Processing: tính lợi nhuận kỳ vọng và mức độ rủi ro → Output: P&L và các chỉ số rủi ro → Decision: quyết định duy trì, giảm hoặc đóng vị thế.


## 6. Main Output

Một game tương tác bao gồm:

- 3 giai đoạn thị trường có độ phức tạp tăng dần.
- Giá và điều kiện thị trường thay đổi theo thời gian.
- Cơ chế giao dịch và arbitrage.
- Dashboard theo dõi P&L và rủi ro theo thời gian thực.
- Chi phí giao dịch, spread, thanh khoản và đòn bẩy.
- Đánh giá cuối game dựa trên lợi nhuận và khả năng quản trị rủi ro.


## 7. Product Pattern

ARBIVERSE kết hợp simulation, gamification và progressive learning.

### 1. Simulation

Game tái hiện các môi trường thị trường tài chính được đơn giản hóa, trong đó người chơi đưa ra quyết định dưới các điều kiện như bất cân xứng thông tin, chi phí giao dịch, hạn chế thanh khoản, biến động tỷ giá và cú sốc thị trường.

### 2. Gamification

Người chơi tương tác với thị trường thông qua các quyết định giao dịch, giới hạn thời gian, vốn ban đầu, theo dõi P&L, chỉ số rủi ro và điểm số. Những yếu tố này giúp các khái niệm tài chính trở nên trực quan và khuyến khích người chơi học thông qua trải nghiệm.

### 3. Progressive Learning

Độ khó và mức độ phức tạp tăng dần qua ba phase:

**Phase 1: Information →** Tìm kiếm cơ hội

**Phase 2: Efficiency →** Nắm bắt cơ hội

**Phase 3: Risk →** Quản lý hậu quả

Khi người chơi tiến xa hơn, thị trường trở nên kết nối và hiệu quả hơn, khiến cơ hội arbitrage khó khai thác hơn và rủi ro lớn hơn.

**Overall pattern:**

> **Trải nghiệm thị trường → Đưa ra quyết định → Quan sát kết quả → Học từ kết quả → Điều chỉnh chiến lược**


## 8. Finance and Banking Relevance

The game applies concepts directly relevant to:

- FX trading: tỷ giá, spread, tỷ giá chéo.
- Risk management: rủi ro thị trường, thanh khoản và đòn bẩy.
- Financial markets: arbitrage và hiệu quả thị trường.
- Banking: treasury, dòng vốn và rủi ro kinh tế vĩ mô.


## 9. Feasibility

Prototype có thể được phát triển dưới dạng game web tương tác, sử dụng cơ chế tạo giá ngẫu nhiên, các công thức tài chính được định nghĩa trước, logic giao dịch và dashboard tương tác.

The **MVP** sẽ tập trung vào:

1. Three playable phases
2. Trading mechanics
3. Dynamic prices
4. P&L calculation
5. Risk indicators
6. End-game scoring


## 10. Revision Notes

- Giữ mô hình tài chính đơn giản nhưng đủ thực tế.
- Mỗi phase tập trung vào một khái niệm tài chính khác nhau.
- Đánh giá dựa trên lợi nhuận đi kèm quản trị rủi ro, không chỉ lợi nhuận.
- Hạn chế yếu tố ngẫu nhiên quá mức.
- Cung cấp giải thích sau các quyết định quan trọng để đảm bảo game vẫn mang tính giáo dục.


## 11. Open Questions

- Nên sử dụng những đồng tiền và tài sản nào?
- Mỗi phase nên kéo dài bao lâu?
- Chi phí giao dịch, spread và đòn bẩy nên được thiết lập ở mức nào?
- Người chơi có nên cạnh tranh trực tiếp với nhau không?
- Những tính năng nào là cần thiết cho MVP?
- Làm thế nào để đo lường việc game có thực sự cải thiện khả năng hiểu tài chính của sinh viên?
