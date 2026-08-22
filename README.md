# GROUP README TEMPLATE

## Tên sản phẩm
ARBIVERSE

## Mã nhóm
G05

## Thành viên
| Họ tên | Mã sinh viên | Vai trò chính |
|---|---|---|
| Hoàng Tường Anh | 2413380006 | Leader, Coordinator and Game Mechanics Designer (Tasks: Game flow document, defining rules, limits, and winning conditions for all 3 levels) |
| Nguyễn Minh Tâm | 2412380044 | Data research and Financial Modelling (Tasks: Research data of 3 economic crises, do mathematical formulas on Excel: transaction costs, returns, arbitrage, capital...) |
| Trần Thu Anh | 2412480011 | Scenario and Financial Modelling (Tasks: Create ideas of 3 levels, decide which currency, selling price, purchasing price... and do financial modelling with member 2) |
| Lê Quỳnh Chi | 2412380012 | Lead Coder (Tasks: Run the core game loop: randomize price generation, trade logic.., dashboards) |
| Hoàng Hà Uyên | 2412380051 | Coder (Tasks: Interface designer, make features: countdown timers, motion effects, live P&L tracking) |

OUTPUT
Hoàng Tường Anh: 
Hệ thống tính điểm cuối game (Scoring Logic): Định nghĩa công thức xếp loại trader. Xếp hạng được tính dựa trên điểm trung bình của 3 Phase, chia thành các danh hiệu: "Master Macro Arbitrageur" (>=88 điểm), "Prudent Arbitrageur" (>=75 điểm) và "Opportunistic Speculator" (>=60 điểm). Logic đánh giá từng màn (Debriefing): Xây dựng hệ thống bài học rút ra (Key Lessons) tương ứng với từng hành động của người chơi tại file Giao diện màn hình (interface)

Nguyễn Minh Tâm:
Historical Data sheet
The Calculation Engine
Sheet Phase 1: Công thức tính Lợi nhuận gộp, trừ Phí mở mạng lưới, Phí thuê người đưa thư , Phí lưu kho để ra Lợi nhuận ròng.
Sheet Phase 2: Mô hình Arbitrage tam giác 3 bước , công thức trừ Bid-Ask spread, % phí giao dịch, và công thức tính cạn kiệt dự trữ ngoại hối của NHTW.
Sheet Phase 3: Công thức tính Carry Yield ròng sau chi phí vốn vay, công thức nhân đòn bẩy (L), công thức tính tỷ lệ ký quỹ danh mục (Margin Level) và điều kiện kích hoạt Margin Call / Bán tháo giải chấp (Liquidation).
Chuẩn hoá tham số cho coder
Thiết kế Hệ thống Tin tức & Ma trận Nhiễu. Gán trọng số và kênh tác động (Impact Weights & Transmission Channels) cho từng tin tức: xác định rõ tin nào tác động trực tiếp vào Cung/Cầu, Dự trữ ngoại hối hay Chỉ số rủi ro toàn cầu (Global Risk Dashboard), và tin nào không gây biến động cơ bản

Trần Thu Anh:
Thiết kế Vật phẩm: Định giá cơ sở (Base Price) và Hệ số rủi ro (Risk Factor) cho 4 loại hoa Tulip.
Thiết kế hồ sơ NPC: Thiết kế 3 nhân vật đại diện cho các tầng lớp thị trường (Grower, Merchant, Moneylender).
Xác định Thông số Cốt lõi: Gắn định mức phí mở khóa (Unlock Cost), chỉ số uy tín yêu cầu (Reputation Required) cho từng NPC.
Thiết lập sẵn các lệnh Mua/Bán (Bid/Ask), mức giá (Price) và Số lượng (Quantity) cho từng nhân vật.
Tiến trình thời gian: Viết tóm tắt nội dung cho tổng cộng 9 vòng chơi (3 vòng x 3 Phase), tạo ra một câu chuyện liền mạch dẫn dắt người chơi từ lúc thị trường bình yên đến khi hoảng loạn và sụp đổ.

Lê Quỳnh Chi
Xây dựng bộ lưu trữ các biến số của người chơi (Ví dụ: Số tiền đang có, vòng chơi hiện tại, số lượng hoa Tulip đang cầm).
Viết thuật toán sinh giá tự động (Price Generator) cho mỗi vòng chơi dựa trên các biến số vĩ mô Tâm và Thu Anh đã thiết kế.

Hoàng Hà Uyên
Thiết kế các mảnh ghép giao diện độc lập (Ví dụ: Khung thẻ bài NPC thương lái, Bảng điện tử hiển thị tỷ giá nhấp nháy, Nút bấm Mua/Bán).
Nhận dữ liệu từ Chi (như số dư = 50.000$) và gán vào giao diện. Gắn các hàm Chi đã viết vào các nút bấm (Ví dụ: Bấm nút "Mua" thì tự động gọi hàm khop_Lenh_Mua()).
Lập trình các hiệu ứng phản hồi người dùng: Hiện thông báo (Toast) màu xanh khi chốt lời thành công, chớp đỏ toàn màn hình khi bị Margin Call.
Tích hợp hệ thống âm thanh (tiếng báo động, tiếng đếm ngược) và hiệu ứng chuyển động để tăng áp lực thời gian.


## Mô tả ngắn về sản phẩm
ARBIVERSE là một game mô phỏng kinh doanh chênh lệch giá và sự phát triển của thị trường tài chính. Người chơi trải qua 03 giai đoạn phát triển của thị trường, hoá thân thành các vai trò khác nhau như thương nhân, chuyên viên giao dịch FX,... để phát hiện và tận dụng các cơ hội chênh lệch giá nhằm tối đa hoá lợi nhuận. Qua từng giai đoạn, người chơi phải quản lý thanh khoản, chi phí giao dịch và đòn bẩy, đồng thời thích ứng với thị trường ngày càng nhanh hơn, minh bạch hơn và có tính liên kết cao hơn. Điểm khác biệt của game là mô phỏng cách cơ hội arbitrage thay đổi theo sự phát triển của cơ sở hạ tầng và hiệu quả thị trường, giúp người chơi trực quan hoá mối quan hệ giữa information gap, market efficiency và arbitrage opportunities.		

## Vấn đề sản phẩm giải quyết
Sinh viên muốn hiểu arbitrage diễn ra như thế nào trong thực tế, thay vì chỉ biết khái niệm đơn giản “mua rẻ – bán đắt” trong sách vở.
Giảng viên gặp khó khăn trong việc truyền tải cho sinh viên cách arbitrage vận hành một cách dễ hiểu.
Arbitrage thực tế ngày càng phức tạp theo sự phát triển của thị trường, chịu ảnh hưởng bởi thông tin, chi phí giao dịch, thanh khoản, tỷ giá và rủi ro. Điều này khiến sinh viên khó kết nối kiến thức lý thuyết với cách thị trường tài chính vận hành và cách các cơ hội arbitrage thay đổi theo thời gian.

## Người dùng mục tiêu
Sinh viên chuyên ngành kinh tế và tài chính: Người chơi muốn trực tiếp thực hành các khái niệm lý thuyết như Arbitrage tam giác, Carry Trade, dòng tiền vĩ mô và cấu trúc vi mô thị trường thông qua mô phỏng tương tác. Giảng viên có thể sử dụng game như một công cụ học tập mô phỏng trong lớp học, giúp chuyển các khái niệm tài chính trừu tượng thành trải nghiệm thực tế, cho phép sinh viên trực tiếp thử nghiệm chiến lược, quan sát phản ứng của thị trường và học hỏi từ kết quả lời/lỗ (môn Tài chính quốc tế hoặc Thị trường và định chế tài chính)

## Scope
Phase 1: Information Asymmetry (Thị trường sơ khai)
* Người chơi tận dụng xuất thân và mở rộng quan hệ để tiếp cận nguồn thông tin, săn cơ hội mua rẻ - bán đắt sản phẩm giữa các thương nhân trong thị trường phân mảnh.
* Nhận diện các dấu hiệu bất ổn cung cầu để kịp thời thoát vị thế trước khi bong bóng đầu cơ sụp đổ.
Phase 2: Arbitrage Ngoại hối và Đa thị trường (FX Market)
* Người chơi tính toán và thực thi chiến lược lệch tỷ giá hối đoái giữa các thị trường Onshore/Offshore và chuỗi tỷ giá chéo.
* Trực tiếp xử lý các ma sát thực tế làm xói mòn lợi nhuận: chênh lệch bid-ask spread, độ trễ khớp lệnh, phí giao dịch và động thái can thiệp từ Ngân hàng Trung ương.
Phase 3: Arbitrage Lãi suất và Rủi ro Vĩ mô (Carry Trade)
* Người chơi vay đồng tiền lãi suất thấp để phân bổ vào danh mục tài sản sinh lời cao nhằm thu chênh lệch lợi tức ròng.
* Theo dõi bảng điều khiển rủi ro toàn cầu và học cách sống sót khi thị trường hoảng loạn kích hoạt làn sóng tháo chạy vị thế hàng loạt.

## Tính năng chính
* Mô phỏng sự thay đổi của giao dịch arbitrage qua từng thời kỳ: từ giao dịch giữa người với người (Phase 1), đến cross-market arbitrage (Phase 2), đến chiến lược Carry Trade liên thị trường (Phase 3).
* Chọn vai & nguồn tin: Người chơi được lựa chọn vai của chính mình, mỗi vai có một mạng lưới giao dịch và nguồn tin riêng, tạo ra lợi thế khác nhau trong việc tìm kiếm cơ hội giao dịch. 
* Mô phỏng sự biến động của thị trường: Giá cả, thanh khoản và các đợt sụp đổ/bong bóng hình thành từ cung cầu, tâm lý đầu cơ và sự can thiệp của ngân hàng trung ương.
* Mô phỏng ma sát giao dịch thực tế: Tích hợp các yếu tố ảnh hưởng đến lợi nhuận của nhà đầu tư như phí giao dịch, chênh lệch bid-ask spread, độ trễ lệnh và giới hạn thanh khoản theo quy mô.
* Quản trị danh mục & Bảng rủi ro toàn cầu: Công cụ quản lý vay vốn lãi suất thấp, điều chỉnh đòn bẩy, theo dõi các cú sốc vĩ mô và xử lý khủng hoảng .
* Giao diện tiến hóa & Dashboard đánh giá cuối game: thay đổi theo từng giai đoạn của trò chơi, từ một thị trường sơ khai với thông tin hạn chế đến một hệ thống giao dịch hiện đại với dữ liệu và công cụ phân tích đầy đủ hơn. Cuối game, người chơi được đánh giá không chỉ dựa trên số tiền kiếm được mà còn dựa trên cách ra quyết định, khả năng nắm bắt cơ hội và mức độ kiểm soát rủi ro.
