# ASSUMPTIONS 

## 1. Assumption chung

| Giả định | Lý do đơn giản hóa | Rủi ro nếu không công khai | Cách xử lý |
|---|---|---|---|
| Ba role giữ nguyên xuyên cả game | Giữ identity của player | Có thể hiểu nhầm mỗi phase chọn role mới | Ghi rõ từ màn hình đầu |
| Vốn reset sau mỗi phase | Các phase mô phỏng tài sản và thời kỳ khác nhau | Không phản ánh compounding xuyên thời gian | Final Score vẫn tích lũy |
| Mỗi role có giới hạn vay vốn, đòn bẩy, lãi suất vay và chi phí thông tin riêng | Tạo sự khác biệt về chiến lược và mức độ rủi ro giữa các role | Một role có thể quá mạnh hoặc quá yếu | Điều chỉnh thông qua playtest |
| Hạn mức vay cố định theo role | Dễ code và đơn giản hóa cơ chế tín dụng | Không phản ánh credit limit động trong thực tế | Để nâng cấp sau |
| Final Score không chỉ dựa trên profit | Tránh khuyến khích player tối đa hóa leverage | Có thể cần cân đối trọng số giữa các tiêu chí | Kết hợp P&L với Risk Discipline và decision quality |
| Historical data dùng để calibration | Tạo market conditions thực tế hơn mà không cần replay toàn bộ lịch sử | Không phản ánh chính xác diễn biến lịch sử | Công khai nguồn và phương pháp calibration |
| Market conditions và events là simulated | Dễ kiểm soát gameplay và scenario | Player có thể nhầm simulated data là historical data | Ghi rõ dữ liệu/môi trường được mô phỏng |

---

## 2. Assumption theo từng Phase

### Phase 1: Bất đối xứng thông tin (Information Asymmetry / Pre-Arbitrage)

| Giả định | Lý do đơn giản hóa | Rủi ro nếu không công khai | Cách xử lý |
|---|---|---|---|
| Phase 1 chỉ có một loại tulip | Giảm số lượng biến | Đơn giản hóa lịch sử | Ghi rõ là prototype |
| Phase 1 kéo dài 3 round, mỗi round 5 phút | Tạo cấu trúc gameplay rõ ràng | Không phản ánh timing lịch sử | Ghi rõ là game rule |
| Mỗi round player chỉ được thực hiện tối đa 3 lần giao dịch với một trader cụ thể | Hạn chế excessive trading và tạo trade-off trong quyết định | Có thể hạn chế strategy của player | Playtest |
| Trader quotes là simulated | Không tái tạo được từng quote lịch sử | Player có thể tưởng là số liệu lịch sử | Ghi rõ nguồn là team-created |
| Báo giá thay đổi mỗi round | Tạo market dynamics | Có thể bị random vô nghĩa | Thay đổi dựa trên market state |
| Phase 1 không có transaction fee | Tập trung vào information asymmetry | Thị trường thực vẫn có friction | Phase 2 bắt đầu đưa transaction cost vào |
| Mỗi round tối đa 1 paid information | Tránh mua toàn bộ thông tin | Có thể quá hạn chế | Playtest |
| Paid information vẫn có thể là noise | Không biến tiền thành “mua đáp án” | Player cảm thấy mất tiền vô ích | Debrief giải thích value of information |
| Information có information delay, reliability level và expiry round | Mô phỏng thông tin không hoàn hảo và có tính thời điểm | Tăng complexity | Hiển thị rõ các thuộc tính của information |
| Information Hunter có lợi thế giá tin và độ tin cậy của news cao hơn | Giữ role đơn giản và tạo information advantage | Có thể chưa đủ mạnh hoặc quá mạnh | Điều chỉnh nếu playtest cho thấy yếu/mạnh |
| Speculator có khả năng vay và leverage cao hơn | Tạo lợi thế vốn và risk-taking trade-off | Có thể khuyến khích đánh cược | Final Score có Risk Discipline |
| Lãi vay tính mỗi round | Cơ chế rõ ràng | Không phản ánh chính xác mọi convention thật | Ghi là game rule |

---

### Phase 2: Kinh doanh chênh lệch tỷ giá (FX Arbitrage)

| Giả định | Lý do đơn giản hóa | Rủi ro nếu không công khai | Cách xử lý |
|---|---|---|---|
| USD là đồng tiền hạch toán chung | Chuẩn hóa asset value, borrowing và P&L | Đơn giản hóa multi-currency accounting | Ghi rõ USD là reporting convention |
| Thị trường niêm yết theo bid/ask và spread = ask - bid | Phản ánh basic FX market structure | Không mô phỏng đầy đủ order book | Giới hạn ở executable quotes |
| Player phải chọn hai thị trường khác nhau để thực hiện cross-market arbitrage | Đảm bảo player thực hiện arbitrage thay vì directional speculation | Có thể giới hạn một số strategy | UI hướng dẫn route |
| Phase 2 có cả cross-market và triangular arbitrage | Thể hiện market integration | Có thể tăng độ khó | UI hướng dẫn route |
| Giao dịch bị giới hạn bởi available volume và max executable amount | Phản ánh liquidity constraints | Không mô phỏng full market depth | Sử dụng predefined liquidity limits |
| Mỗi lệnh chịu fixed fee và transaction fee rate | Đưa market friction vào arbitrage calculation | Fee structure được đơn giản hóa | Dùng predefined parameters |
| Execution delay hoặc market stress có thể gây slippage | Phản ánh execution risk | Slippage không hoàn toàn giống thực tế | Calibration |
| Central bank events có thể làm arbitrage opportunity biến mất trong cùng round | Thể hiện arbitrage opportunity có tính thời điểm | Event timing được simulated | Sử dụng predefined event scenarios |
| Phase 2 đóng FX position trong cùng round | Tập trung vào arbitrage | Không dạy holding FX risk | Phase 3 tập trung vào holding risk |
| Investor có chi phí lãi vay thấp nhất | Tạo lợi thế riêng cho role | Có thể khiến Investor quá mạnh | Chốt parameter sau playtest |

---

### Phase 3: Giao dịch chênh lệch lãi suất & Rủi ro vĩ mô (Carry Trade & Macro Risk)

| Giả định | Lý do đơn giản hóa | Rủi ro nếu không công khai | Cách xử lý |
|---|---|---|---|
| Yen Carry Trade không phải risk-free arbitrage | Đúng logic tài chính | Phức tạp hơn arbitrage | Tách riêng funding risk, FX risk và asset risk |
| Player vay JPY và chuyển đổi sang USD để đầu tư | Tạo cơ chế carry trade rõ ràng | Không cho phép alternative funding strategy | Ghi rõ là game rule |
| 100% số vốn sau vay phải được phân bổ vào US Equity và High-Yield Bonds | Tạo portfolio decision | Không phản ánh đầy đủ investment universe | Giới hạn asset classes trong prototype |
| Không được giữ tiền mặt USD nhàn rỗi | Buộc player chịu investment risk | Giảm strategic flexibility | Có thể mở rộng sau |
| Chi phí vốn chịu ảnh hưởng bởi lãi suất chính sách của BOJ | Liên kết funding cost với monetary policy | Không phản ánh toàn bộ funding market | Dùng policy rate làm proxy |
| Lợi suất tài sản USD gắn liền với khung lãi suất điều hành của Fed | Liên kết asset return với macro conditions | Không phản ánh toàn bộ yếu tố quyết định asset price | Tập trung vào key macro drivers |
| Player đồng thời chịu asset risk và FX risk | Phản ánh double exposure của carry trade | Có thể tạo large losses | Tách riêng asset P&L và FX impact |
| JPY tăng giá mạnh làm phình to nghĩa vụ nợ khi đáo hạn | Mô phỏng currency mismatch risk | FX dynamics được đơn giản hóa | Sử dụng predefined FX scenarios |
| Sau mỗi biến động thị trường, player chỉ có thể HOLD, REDUCE hoặc CLOSE | Giới hạn decision space và tập trung vào risk management | Không phản ánh toàn bộ portfolio strategies | Có thể mở rộng sau |
| Khi market_stress_state = UNWIND, có thể xảy ra đồng thời asset loss và JPY appreciation | Mô phỏng carry trade unwinding và double loss | Có thể tạo extreme scenario | Calibration mức độ stress |
