# GROUP README TEMPLATE

## Tên sản phẩm
**ARBIVERSE**

## Mã nhóm
**G05**

## Thành viên
| Họ tên | Mã sinh viên | Vai trò chính |
| :--- | :--- | :--- |
| **Hoàng Tường Anh** | 2413380006 | **Leader, Coordinator & Game Mechanics Designer**<br>*(Tasks: Game flow document, defining rules, limits, and winning conditions for all 3 levels)* |
| **Nguyễn Minh Tâm** | 2412380044 | **Data Research & Financial Modelling**<br>*(Tasks: Research data of 3 economic crises, do mathematical formulas on Excel: transaction costs, returns, arbitrage, capital...)* |
| **Trần Thu Anh** | 2412480011 | **Scenario & Financial Modelling**<br>*(Tasks: Create ideas of 3 levels, decide which currency, selling price, purchasing price... and do financial modelling with member 2)* |
| **Lê Quỳnh Chi** | 2412380012 | **Lead Coder**<br>*(Tasks: Run the core game loop: randomize price generation, trade logic.., dashboards)* |
| **Hoàng Hà Uyên** | 2412380051 | **Coder / Interface Designer**<br>*(Tasks: Interface designer, make features: countdown timers, motion effects, live P&L tracking)* |

---

## Mô tả ngắn về sản phẩm
**ARBIVERSE** là một game mô phỏng kinh doanh chênh lệch giá và sự phát triển của thị trường tài chính. Người chơi trải qua 03 giai đoạn phát triển của thị trường, hoá thân thành các vai trò khác nhau như thương nhân, chuyên viên giao dịch FX,... để phát hiện và tận dụng các cơ hội chênh lệch giá nhằm tối đa hoá lợi nhuận. Qua từng giai đoạn, người chơi phải quản lý thanh khoản, chi phí giao dịch và đòn bẩy, đồng thời thích ứng với thị trường ngày càng nhanh hơn, minh bạch hơn và có tính liên kết cao hơn. 

Điểm khác biệt của game là mô phỏng cách cơ hội arbitrage thay đổi theo sự phát triển của cơ sở hạ tầng và hiệu quả thị trường, giúp người chơi trực quan hoá mối quan hệ giữa **information gap**, **market efficiency** và **arbitrage opportunities**.

---

## Vấn đề sản phẩm giải quyết
- Sinh viên muốn hiểu arbitrage diễn ra như thế nào trong thực tế, thay vì chỉ biết khái niệm đơn giản “mua rẻ – bán đắt” trong sách vở.
- Giảng viên gặp khó khăn trong việc truyền tải cho sinh viên cách arbitrage vận hành một cách dễ hiểu.
- Arbitrage thực tế ngày càng phức tạp theo sự phát triển của thị trường, chịu ảnh hưởng bởi thông tin, chi phí giao dịch, thanh khoản, tỷ giá và rủi ro. Điều này khiến sinh viên khó kết nối kiến thức lý thuyết với cách thị trường tài chính vận hành và cách các cơ hội arbitrage thay đổi theo thời gian.

---

## Người dùng mục tiêu
- **Sinh viên chuyên ngành Kinh tế & Tài chính:** Người chơi muốn trực tiếp thực hành các khái niệm lý thuyết như Arbitrage tam giác, Carry Trade, dòng tiền vĩ mô và cấu trúc vi mô thị trường thông qua mô phỏng tương tác.
- **Giảng viên và các tổ chức giáo dục:** Có thể sử dụng game như một công cụ học tập mô phỏng trong lớp học (môn *Tài chính quốc tế* hoặc *Thị trường và Định chế tài chính*), giúp chuyển các khái niệm tài chính trừu tượng thành trải nghiệm thực tế, cho phép sinh viên trực tiếp thử nghiệm chiến lược, quan sát phản ứng của thị trường và học hỏi từ kết quả lời/lỗ.

---

## Scope

### Phase 1: Information Asymmetry (Thị trường sơ khai)
- Người chơi tận dụng xuất thân và mở rộng quan hệ để tiếp cận nguồn thông tin, săn cơ hội mua rẻ - bán đắt sản phẩm giữa các thương nhân trong thị trường phân mảnh.
- Nhận diện các dấu hiệu bất ổn cung cầu để kịp thời thoát vị thế trước khi bong bóng đầu cơ sụp đổ.

### Phase 2: Arbitrage Ngoại hối và Đa thị trường (FX Market)
- Người chơi tính toán và thực thi chiến lược lệch tỷ giá hối đoái giữa các thị trường Onshore/Offshore và chuỗi tỷ giá chéo.
- Trực tiếp xử lý các ma sát thực tế làm xói mòn lợi nhuận: chênh lệch bid-ask spread, độ trễ khớp lệnh, phí giao dịch và động thái can thiệp từ Ngân hàng Trung ương.

### Phase 3: Arbitrage Lãi suất và Rủi ro Vĩ mô (Carry Trade)
- Người chơi vay đồng tiền lãi suất thấp để phân bổ vào danh mục tài sản sinh lời cao nhằm thu chênh lệch lợi tức ròng.
- Theo dõi bảng điều khiển rủi ro toàn cầu và học cách sống sót khi thị trường hoảng loạn kích hoạt làn sóng tháo chạy vị thế hàng loạt.

---

## Tính năng chính
- **Mô phỏng sự thay đổi của giao dịch Arbitrage qua từng thời kỳ:** Từ giao dịch giữa người với người (Phase 1), đến cross-market arbitrage (Phase 2), đến chiến lược Carry Trade liên thị trường (Phase 3).
- **Chọn vai & Nguồn tin:** Người chơi được lựa chọn vai của chính mình, mỗi vai có một mạng lưới giao dịch và nguồn tin riêng, tạo ra lợi thế khác nhau trong việc tìm kiếm cơ hội giao dịch.
- **Mô phỏng sự biến động của thị trường:** Giá cả, thanh khoản và các đợt sụp đổ/bong bóng hình thành từ cung cầu, tâm lý đầu cơ và sự can thiệp của Ngân hàng Trung ương.
- **Mô phỏng ma sát giao dịch thực tế:** Tích hợp các yếu tố ảnh hưởng đến lợi nhuận của nhà đầu tư như phí giao dịch, chênh lệch bid-ask spread, độ trễ lệnh và giới hạn thanh khoản theo quy mô.
- **Quản trị danh mục & Bảng rủi ro toàn cầu:** Công cụ quản lý vay vốn lãi suất thấp, điều chỉnh đòn bẩy, theo dõi các cú sốc vĩ mô và xử lý khủng hoảng.
- **Giao diện tiến hóa & Dashboard đánh giá cuối game:** Thay đổi theo từng giai đoạn của trò chơi, từ một thị trường sơ khai với thông tin hạn chế đến một hệ thống giao dịch hiện đại với dữ liệu và công cụ phân tích đầy đủ hơn. Cuối game, người chơi được đánh giá không chỉ dựa trên số tiền kiếm được mà còn dựa trên cách ra quyết định, khả năng nắm bắt cơ hội và mức độ kiểm soát rủi ro.



