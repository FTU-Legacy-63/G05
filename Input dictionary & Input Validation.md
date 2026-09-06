**ARBIVERSE — CHECKPOINT TUẦN 3**

**Câu hỏi trung tâm:** Sản phẩm cần thông tin gì để hoạt động, thông tin đó đến từ đâu và có đủ khả thi để sử dụng hay không?

**1. Mục tiêu Tuần 3**

Mục tiêu của Tuần 3 là xác định đầy đủ dữ liệu cần thiết để Arbiverse có thể vận hành, kiểm tra tính khả thi của các nguồn dữ liệu và chuẩn bị cấu trúc dữ liệu đủ rõ để chuyển sang xây dựng logic tài chính hoàn chỉnh ở Tuần 4.

Game đưa người chơi qua ba giai đoạn:
**Phase 1 — Information Asymmetry / Pre-Arbitrage**
→ **Phase 2 — Thai Baht Crisis 1997**
→ **Phase 3 — Yen Carry Trade / Modern Global Market**

Ba phase không phải ba game tách biệt. Chúng thể hiện quá trình thị trường phát triển từ:
**Con người → Thị trường → Hệ thống**

Khi thị trường ngày càng kết nối và minh bạch hơn, cơ hội kiếm lợi nhuận từ chênh lệch đơn giản giảm dần và người chơi phải xử lý thêm các yếu tố như chi phí giao dịch, chi phí vốn, tỷ giá, thanh khoản, đòn bẩy và rủi ro hệ thống. Đây cũng là backbone của game concept hiện tại.

Người chơi chọn **một trong ba vai ngay từ đầu và giữ nguyên vai xuyên suốt game**:

- **Speculator — Nhà đầu cơ**
- **Investor — Nhà đầu tư**
- **Information Hunter — Thợ săn thông tin**

Tài sản và vốn được **reset về vốn ban đầu khi chuyển phase**, do mỗi phase mô phỏng một thị trường và loại tài sản khác nhau. Tuy nhiên, vai của người chơi và lợi thế cốt lõi của vai được giữ nguyên.



**2. INPUT DICTIONARY**

**2.1. Cấu hình vai người chơi**
Lợi thế của ba vai được thiết kế theo ba nguồn lợi thế khác nhau:

| **Vai**                | **Lợi thế cốt lõi**                     |
| ---------------------- | --------------------------------------- |
| **Speculator**         | Khả năng vay vốn và sử dụng đòn bẩy cao |
| **Investor**           | Chi phí giao dịch thấp                  |
| **Information Hunter** | Chi phí tiếp cận thông tin thấp         |

***Lưu ý: Lợi thế này được giữ về bản chất xuyên ba phase, nhưng mức độ tác động thay đổi theo cấu trúc thị trường.***

**3. PHASE 1 — INFORMATION ASYMMETRY / PRE-ARBITRAGE**

Phase 1 mô phỏng một thị trường chưa có sàn giao dịch tập trung.
Game tạo sẵn các trader như:

- Trader A muốn bán X tulip tại giá Y;
- Trader B muốn mua X tulip tại giá Y1;
- Trader C có muốn mua X tulip tại giá Y2.

Người chơi phải tự quan sát các báo giá để tìm:
**Mua rẻ ở trader này → bán cao cho trader khác.**
Phase 1 chỉ sử dụng **một loại tulip**, nhưng giá mua, giá bán và số lượng của từng trader khác nhau.
Sau mỗi round, báo giá và khối lượng của các trader thay đổi theo trạng thái thị trường và quy tắc mô phỏng.

**3.1. Dữ liệu cốt lõi — Phase 1**

| **Tên dữ liệu**               | **Ý nghĩa**                           | **Kiểu** | **Đơn vị**    | **Ví dụ/Nguồn**                            | **Kiểm tra**          | **Kết quả bị ảnh hưởng**       |
| ----------------------------- | ------------------------------------- | -------- | ------------- | ------------------------------------------ | --------------------- | ------------------------------ |
| player\_role                  | Vai người chơi                        | enum     | –             | Speculator / Investor / Information Hunter | Bắt buộc; thuộc 3 vai | Toàn bộ cấu hình role          |
| initial\_cash                 | Tiền mặt ban đầu                      | number   | game currency | 100 — nhóm tự thiết kế                     | > 0                   | Khả năng mua tài sản/thông tin |
| max\_borrow\_amount           | Hạn mức vay tối đa                    | number   | game currency | 200 / 50 / 100                             | ≥ 0                   | Khả năng mở rộng vốn           |
| max\_leverage                 | Đòn bẩy tối đa                        | number   | lần           | 3 / 1,5 / 2                                | ≥ 1                   | Quy mô vị thế tối đa           |
| borrowing\_rate               | Lãi suất vay theo mỗi round           | number   | %/round       | 6% / 4% / 5%                               | ≥ 0                   | Chi phí vay, P&L               |
| current\_debt                 | Dư nợ hiện tại                        | number   | game currency | 50                                         | 0 ≤ debt ≤ hạn mức    | Lãi vay, khả năng vay thêm     |
| information\_cost\_multiplier | Hệ số giá tin theo role               | number   | lần           | 1,5 / 1 / 0,5                              | > 0                   | Giá tin thực tế                |
| total\_rounds                 | Tổng số round                         | integer  | round         | 3                                          | = 3                   | Tiến trình phase               |
| max\_trades\_per\_round       | Số giao dịch mua/bán tối đa mỗi round | integer  | giao dịch     | 3                                          | = 3                   | Số hành động giao dịch         |

**Lưu ý**

**Phase 1 không có phí giao dịch.**
Do chưa có sàn giao dịch hiện đại, các chi phí trực tiếp được mô phỏng trong Phase 1 chỉ gồm:

1. **chi phí vay vốn;**
2. **chi phí mua thông tin.**

Lợi thế chi phí giao dịch của Investor bắt đầu phát huy rõ từ Phase 2.

**3.2. Cấu hình ba vai — Phase 1**

| **Thông số**            | **Speculator** | **Investor**         | **Information Hunter** |
| ----------------------- | -------------- | -------------------- | ---------------------- |
| Tiền ban đầu            | 100            | 100                  | 100                    |
| Hạn mức vay             | **200**        | 50                   | 100                    |
| Đòn bẩy tối đa          | **3x**         | 1,5x                 | 2x                     |
| Lãi suất vay/round      | 6%             | **4%**               | 5%                     |
| Hệ số giá mua thông tin | **1,5x**       | 1x                   | **0,5x**               |
| Lợi thế chính Phase 1   | Vốn và đòn bẩy | Chi phí vốn thấp hơn | Thông tin rẻ           |

Các con số trên là **tham số cân bằng do nhóm tự thiết kế**, không phải dữ liệu lịch sử. 
Chúng sẽ được kiểm tra lại bằng playtest.

**3.3. Dữ liệu do người chơi nhập — Phase 1**

| **Tên dữ liệu**           | **Ý nghĩa**                            | **Kiểu** | **Đơn vị**    | **Ví dụ** | **Khoảng hợp lệ**               |
| ------------------------- | -------------------------------------- | -------- | ------------- | --------- | ------------------------------- |
| buy\_information          | Có mua gói thông tin trả phí hay không | boolean  | –             | YES       | YES / NO                        |
| selected\_information\_id | Gói thông tin muốn mua                 | string   | –             | INFO\_01  | Phải khả dụng trong round       |
| borrow\_amount            | Số tiền muốn vay thêm                  | number   | game currency | 50        | Không vượt hạn mức còn lại      |
| repay\_amount             | Số tiền muốn trả nợ                    | number   | game currency | 20        | Không vượt dư nợ và tiền mặt    |
| trade\_action             | Hành động giao dịch                    | enum     | –             | BUY       | BUY / SELL / HOLD               |
| trade\_quantity           | Số tulip muốn giao dịch                | integer  | tulip         | 2         | > 0 và đủ điều kiện             |
| selected\_trader\_id      | Trader được lựa chọn                   | string   | –             | TRADER\_A | Trader tồn tại và đang có quote |

Một lần BUY hoặc SELL được tính là **một giao dịch**.
Mua thông tin và vay vốn **không được tính vào giới hạn ba giao dịch mỗi round**.


**3.4. Dữ liệu gói thông tin — Phase 1**

Mỗi round:

- tất cả người chơi nhận **1–2 thông tin miễn phí**;
- thông tin miễn phí có thể là tín hiệu thật hoặc noise;
- người chơi được mua tối đa **1 gói thông tin trả phí**;
- thông tin trả phí **vẫn có thể sai hoặc chứa noise**;
- Information Hunter không được đảm bảo nhận tin chính xác hơn, mà chỉ có **lợi thế về giá mua**.

| **Tên dữ liệu**           | **Ý nghĩa**             | **Kiểu** | **Ví dụ**                   | **Kiểm tra**               |
| ------------------------- | ----------------------- | -------- | --------------------------- | -------------------------- |
| information\_id           | Mã tin                  | string   | INFO\_01                    | Không trùng                |
| information\_type         | Loại thông tin          | enum     | SUPPLY                      | Thuộc danh sách định trước |
| information\_source\_type | Miễn phí hay trả phí    | enum     | PAID                        | FREE / PAID                |
| base\_information\_cost   | Giá cơ sở               | number   | 20                          | ≥ 0                        |
| information\_content      | Nội dung tin            | string   | Nguồn cung có dấu hiệu giảm | Không rỗng                 |
| signal\_quality           | Tín hiệu thật hay noise | enum     | REAL                        | REAL / NOISE               |
| available\_round          | Round tin xuất hiện     | integer  | 2                           | 1–3                        |

Giá thực tế:
**Chi phí thông tin = Giá cơ sở × Hệ số giá tin theo role**

Ví dụ gói tin giá 20:

- Speculator: 30
- Investor: 20
- Information Hunter: 10

**3.5. Dữ liệu trader — Phase 1**

| **Tên dữ liệu**     | **Ý nghĩa**                    | **Kiểu** | **Đơn vị**          | **Ví dụ** |
| ------------------- | ------------------------------ | -------- | ------------------- | --------- |
| trader\_id          | Mã trader                      | string   | –                   | TRADER\_A |
| order\_side         | Trader muốn mua hay bán        | enum     | –                   | SELL      |
| quote\_price        | Giá trader đưa ra              | number   | game currency/tulip | 40        |
| available\_quantity | Số lượng trader muốn giao dịch | integer  | tulip               | 5         |
| round               | Round báo giá có hiệu lực      | integer  | round               | 1         |

Ví dụ:

| **Trader** | **Lệnh** | **Số lượng** | **Giá** |
| ---------- | -------- | ------------ | ------- |
| A          | SELL     | 5            | 40      |
| B          | BUY      | 3            | 55      |
| C          | SELL     | 4            | 48      |

Người chơi có thể phát hiện cơ hội:

**Mua từ A tại 40 → bán cho B tại 55.**

**3.6. Trạng thái thị trường — Phase 1**

| **Tên dữ liệu**    | **Ý nghĩa**                 | **Khoảng** |
| ------------------ | --------------------------- | ---------- |
| supply\_level      | Mức cung                    | 0–100      |
| demand\_level      | Mức cầu                     | 0–100      |
| speculation\_level | Mức đầu cơ                  | 0–100      |
| credit\_condition  | Mức độ dễ tiếp cận tín dụng | 0–100      |
| market\_confidence | Niềm tin                    | 0–100      |
| market\_liquidity  | Khả năng tìm người mua/bán  | 0–100      |

Sáu biến trên đều được sử dụng để làm thay đổi báo giá, số lượng lệnh và trạng thái của market qua từng round. Raw design cũng xác định đây là các biến chính của market state Phase 1.

**3.7. Các biến hệ thống tự tính — Phase 1**

Người chơi **không nhập** các biến sau.

**Chi phí thông tin**
actual\_information\_cost = base\_information\_cost × information\_cost\_multiplier

**Chi phí vay mỗi round**
round\_interest = current\_debt × borrowing\_rate

**Hạn mức vay còn lại**
remaining\_borrow\_capacity = max\_borrow\_amount − current\_debt

**Giá trị giao dịch**
trade\_value = quote\_price × trade\_quantity

**Số giao dịch còn lại**
trades\_remaining = 3 − trades\_used

**Giá trị tài sản ròng**
net\_worth = cash + inventory\_value − current\_debt

**3.8. Quy tắc vay vốn — Phase 1**

Để giảm độ phức tạp code trong MVP, **hạn mức vay được giữ cố định theo role trong từng phase**, không tự động thay đổi theo equity.

Điều kiện:
current\_debt + borrow\_amount ≤ max\_borrow\_amount

Cuối mỗi round:
cash = cash − round\_interest

Người chơi có thể:

- vay thêm giữa các round;
- trả bớt nợ;
- tất toán toàn bộ nợ.

Nếu cuối phase vẫn còn nợ, hệ thống tự động yêu cầu tất toán.

**4. PHASE 2 — THAI BAHT CRISIS 1997**

Phase 2 chuyển từ chênh lệch giá giữa các trader sang chênh lệch giá giữa các **thị trường FX**.
Hai loại cơ hội chính:
**Cross-market arbitrage**
So sánh cùng một cặp tiền giữa:

- Bangkok/onshore;
- Singapore/offshore;
- USD/offshore.

**Triangular arbitrage**
Ví dụ:
**USD → THB → SGD → USD**
Raw design xác định Phase 2 sử dụng cả cross-market và triangular arbitrage, đồng thời đưa bid–ask, liquidity và execution vào gameplay.
Người chơi **không giữ vị thế FX sang round sau mà phải đóng vị thế trước khi round sau bắt đầu (hệ thống tự động đóng khi ấn kết thúc)**.
Mỗi round là một tập hợp báo giá và cơ hội mới.
**4.1. Dữ liệu cốt lõi — Phase 2**

| **Tên dữ liệu**               | **Ý nghĩa**                  | **Kiểu**     | **Ví dụ**  | **Kiểm tra**                | **Kết quả bị ảnh hưởng**  |
| ----------------------------- | ---------------------------- | ------------ | ---------- | --------------------------- | ------------------------- |
| currency\_pair                | Cặp tiền                     | string       | USD/THB    | Pair tồn tại                | Route giao dịch           |
| market\_id                    | Thị trường báo giá           | string       | BANGKOK    | Market tồn tại              | Giá thực hiện             |
| bid\_rate                     | Giá market mua               | number       | 25,40      | > 0                         | Tiền nhận khi bán         |
| ask\_rate                     | Giá market bán               | number       | 25,35      | Ask ≥ Bid trong cùng market | Tiền trả khi mua          |
| trade\_amount                 | Quy mô giao dịch             | number       | USD 10.000 | > 0                         | P&L                       |
| base\_transaction\_fee        | Phí giao dịch cơ sở          | number       | 0,05%      | ≥ 0                         | P&L                       |
| transaction\_cost\_multiplier | Hệ số phí theo role          | number       | 0,6        | > 0                         | Phí thực tế               |
| borrow\_amount                | Khoản vay phục vụ giao dịch  | number       | 50         | Trong hạn mức               | Funding                   |
| borrowing\_rate               | Lãi vay theo round           | number       | %          | ≥ 0                         | Chi phí vốn               |
| market\_liquidity             | Khả năng thực hiện giao dịch | number/state | HIGH       | Hợp lệ                      | Quy mô khớp               |
| execution\_slippage           | Sai lệch giá khi thực hiện   | number       | 0,01%      | ≥ 0                         | Net P&L                   |
| crisis\_state                 | Trạng thái khủng hoảng       | enum         | PRESSURE   | Hợp lệ                      | Quotes, spread, liquidity |

Các thông tin về chính sách và bảo vệ tỷ giá chỉ đóng vai trò **bối cảnh lịch sử/problem evidence**, không phải một mechanic player trực tiếp điều khiển.

**4.2. Chi phí Phase 2**
Phase 2 có ba nhóm chi phí trực tiếp:
**1. Chênh lệch bid–ask**
Không được tính bằng mid-rate.
Player phải mua tại **ask** và bán tại **bid**.
**2. Phí giao dịch**
**transaction\_fee = trade\_value × base\_transaction\_fee × role\_multiplier**
Investor có lợi thế ở phần này.
**3. Chi phí vay vốn**
Nếu sử dụng tiền vay:
**funding\_cost = current\_debt × borrowing\_rate**
Lãi được tính theo round.
Ngoài ra, **slippage** và thanh khoản có thể khiến lợi nhuận thực tế thấp hơn lợi nhuận nhìn thấy ban đầu.
FX thực tế chủ yếu là thị trường OTC, phân tán và dealer đóng vai trò trung gian, vì vậy việc Phase 2 đưa nhiều nguồn quote và execution friction vào game có cơ sở thực tế.

**4.3. Dữ liệu do người chơi nhập — Phase 2**

| **Tên dữ liệu**           | **Ý nghĩa**                 |
| ------------------------- | --------------------------- |
| arbitrage\_type           | CROSS\_MARKET / TRIANGULAR  |
| borrow\_amount            | Số vốn muốn vay             |
| trade\_amount             | Quy mô giao dịch            |
| selected\_market\_buy     | Market mua                  |
| selected\_market\_sell    | Market bán                  |
| selected\_route           | Route triangular            |
| buy\_information          | Có mua thêm thông tin không |
| selected\_information\_id | Gói thông tin được chọn     |

**4.4. Biến hệ thống tự tính — Phase 2**
**Cross-market gross profit**
gross\_profit = (sell\_bid − buy\_ask) × quantity
**Phí thực hiện**
total\_transaction\_fee = Σ fee của từng leg
**Lợi nhuận ròng**
net\_profit = gross\_profit − transaction\_fee − funding\_cost − slippage\_cost
**Triangular arbitrage**
Hệ thống lần lượt chuyển đổi:
Currency 1 → Currency 2 → Currency 3 → Currency 1
Sau khi dùng đúng bid/ask và trừ toàn bộ chi phí:

- nếu final\_amount > initial\_amount → profitable;
- nếu final\_amount ≤ initial\_amount → không profitable.

**5. PHASE 3 — YEN CARRY TRADE / MODERN GLOBAL MARKET**

Phase 3 không còn là arbitrage thông thường.
Người chơi phải thực hiện các bước chơi như sau:
**Vay JPY → đổi sang USD → phân bổ vào nhiều tài sản → nhận lợi suất → bán tài sản → đổi USD về JPY → trả nợ.**
Carry Trade khai thác chênh lệch giữa chi phí funding thấp và lợi suất tài sản cao, nhưng player phải chịu rủi ro tỷ giá, tài sản và đòn bẩy. BIS cũng mô tả carry trade là vị thế cross-currency thường sử dụng leverage, vay đồng tiền có lãi suất thấp để mua tài sản có lợi suất cao và nhạy cảm với tỷ giá, lãi suất và volatility.

**5.1. Dữ liệu cốt lõi — Phase 3**

| **Tên dữ liệu**               | **Ý nghĩa**                  | **Kiểu**    | **Ví dụ**        | **Kiểm tra**   | **Kết quả bị ảnh hưởng** |
| ----------------------------- | ---------------------------- | ----------- | ---------------- | -------------- | ------------------------ |
| jpy\_funding\_rate            | Lãi suất vay JPY             | number      | 0,5%             | ≥ 0            | Funding cost             |
| funding\_amount\_jpy          | Số JPY vay                   | number      | ¥15.000.000      | ≥ 0            | Exposure                 |
| max\_leverage                 | Đòn bẩy tối đa theo role     | number      | 3x               | ≥ 1            | Risk capacity            |
| usd\_jpy\_bid                 | Giá bán USD lấy JPY          | number      | 149,90           | > 0            | FX conversion            |
| usd\_jpy\_ask                 | Giá mua USD bằng JPY         | number      | 150,10           | Ask ≥ Bid      | FX conversion            |
| asset\_id                     | Tài sản Mỹ                   | string      | US500            | Phải tồn tại   | Portfolio                |
| asset\_price                  | Giá tài sản                  | number      | 100              | > 0            | Portfolio value          |
| asset\_return                 | Lợi suất tài sản trong round | number      | +5%              | Scenario range | P&L                      |
| allocation                    | Tỷ trọng danh mục            | number      | 40%              | 0–100%         | Portfolio return         |
| base\_asset\_transaction\_fee | Phí mua/bán tài sản          | number      | 0,1%             | ≥ 0            | P&L                      |
| transaction\_cost\_multiplier | Hệ số phí theo role          | number      | 0,6              | > 0            | P&L                      |
| market\_liquidity             | Thanh khoản                  | state       | LOW              | Hợp lệ         | Execution                |
| market\_regime                | Trạng thái thị trường        | enum        | RISK\_OFF        | Hợp lệ         | Asset/FX behavior        |
| risk\_event                   | Sự kiện rủi ro               | enum/object | BOJ\_RATE\_SHOCK | Hợp lệ         | Market state             |

Danh sách tài sản cụ thể có thể thay đổi theo scenario. Dataset mẫu có thể sử dụng các nhóm như:

- SP 500;
- US Technology;
- US Treasury;
- Gold;

sau đó mở rộng nếu cần.
Raw design cũng định hướng Phase 3 sử dụng global rates, FX, funding và nhiều loại asset thay vì một tài sản duy nhất.

**5.2. Bốn loại chi phí trực tiếp — Phase 3**
**1. Chi phí vay JPY**
funding\_cost = JPY debt × funding rate
Lãi được tự động thanh toán cuối mỗi round.
**2. Chi phí chuyển đổi ngoại tệ**
Player chịu bid–ask spread khi:
**JPY → USD**
và khi:
**USD → JPY**
Không tạo thêm một loại phí FX giả nếu không cần thiết; spread đã phản ánh friction cơ bản.        
**3. Chi phí mua/bán tài sản**
asset\_transaction\_cost = trade\_value × base\_fee × role\_multiplier
Đây là nơi lợi thế của Investor tiếp tục phát huy.
**4. Chi phí mua thông tin**
Thông tin bổ sung trong Phase 3 có thể liên quan đến:

- Fed;
- BOJ;
- lạm phát;
- thanh khoản;
- risk sentiment;
- định vị thị trường.

Information Hunter tiếp tục có lợi thế về chi phí tiếp cận thông tin.

**5.3. Những yếu tố không được gọi là “cost”**
**FX Gain/Loss**
JPY tăng giá hoặc giảm giá tạo lãi/lỗ tỷ giá.
Đây là **market risk**, không phải transaction cost.
**Asset Gain/Loss**
Giá tài sản tăng/giảm tạo P&L danh mục.
Đây là **investment return**, không phải cost.
**Leverage**
Đòn bẩy là hệ số khuếch đại exposure, không phải cost.
**Margin**
Margin là constraint về vốn, không phải cost.
**Liquidity**
Liquidity ảnh hưởng khả năng thoát vị thế và giá thực hiện, không phải một khoản phí cố định.

**5.4. Dữ liệu do người chơi nhập — Phase 3**

| **Tên dữ liệu**           | **Ý nghĩa**             |
| ------------------------- | ----------------------- |
| borrow\_amount\_jpy       | Số JPY muốn vay         |
| selected\_assets          | Các tài sản muốn đầu tư |
| portfolio\_allocation     | Tỷ trọng từng tài sản   |
| leverage\_level           | Đòn bẩy lựa chọn        |
| buy\_information          | Có mua thông tin không  |
| selected\_information\_id | Gói tin lựa chọn        |
| position\_action          | HOLD / REDUCE / CLOSE   |

Điều kiện:
Σ allocation = 100%

**5.5. Biến hệ thống tự tính — Phase 3**
**Lợi suất danh mục**
portfolio\_return = Σ(asset\_weight × asset\_return)
**Chi phí vốn JPY**
funding\_cost\_jpy = JPY debt × funding\_rate
**Chi phí giao dịch tài sản**
asset\_transaction\_cost = Σ(trade\_value × fee × role\_multiplier)
**Giá trị cuối cùng bằng JPY**
ending\_JPY = ending\_USD × USDJPY\_bid
**Nghĩa vụ nợ**
debt\_due = JPY principal + funding\_cost
**P&L Carry Trade**
net\_carry\_P&L = ending\_JPY − debt\_due − transaction\_costs

## 2. INPUT VALIDATION

### 2.1. Kiểm tra chung
| Quy tắc | Áp dụng | Xử lý khi vi phạm |
| :--- | :--- | :--- |
| `player_role` phải thuộc 3 role | Cả game | Không cho bắt đầu |
| `cash` ≥ 0 | Cả game | Kiểm tra trạng thái phá sản |
| `borrow_amount` ≥ 0 | Cả game | Từ chối input |
| Dư nợ không vượt hạn mức | Cả game | Không cho vay thêm |
| Đòn bẩy không vượt giới hạn role | Cả game | Không cho tăng exposure |
| Gói tin phải tồn tại | Cả game | Không cho mua |
| Player phải đủ tiền mua tin | Cả game | Không mở thông tin |
| Các tỷ lệ dùng cùng định dạng decimal | Cả game | Chuẩn hóa trước khi tính |

### 2.2. Phase 1
| Quy tắc | Xử lý |
| :--- | :--- |
| Mỗi round tối đa 3 giao dịch BUY/SELL | Không cho giao dịch thứ 4 |
| Mua news không tính là trade | Không tăng `trades_used` |
| Vay/trả nợ không tính là trade | Không tăng `trades_used` |
| Mỗi round tối đa 1 gói tin trả phí | Khóa lựa chọn mua thêm |
| `trade_quantity` ∈ N* | Từ chối giá trị 0/âm/lẻ |
| BUY không vượt quantity trader đang bán | Giảm/từ chối giao dịch |
| BUY không vượt cash khả dụng | Từ chối giao dịch |
| SELL không vượt inventory player | Từ chối giao dịch |
| Trader phải tồn tại ở round hiện tại | Từ chối |

### 2.3. Phase 2
| Quy tắc | Xử lý |
| :--- | :--- |
| Bid và Ask > 0 | Loại quote lỗi |
| Ask ≥ Bid trong cùng market | Đánh dấu dữ liệu không hợp lệ |
| Market phải tồn tại | Từ chối |
| Currency pair phải tồn tại | Từ chối |
| 0 < Trade amount < Số dư khả dụng của player | Từ chối nếu sai |
| Trade size ≤ market liquidity | Giảm hoặc từ chối trade |
| Triangular arbitrage phải đủ route | Không cho execute |
| Không carry vị thế qua round | Tự động close trước khi chuyển round |

### 2.4. Phase 3
| Quy tắc | Xử lý |
| :--- | :--- |
| Khoản vay JPY > 0 | Từ chối nếu bằng 0/âm |
| Leverage ≤ max leverage của role | Từ chối |
| Asset phải tồn tại | Từ chối |
| Allocation từng asset từ 0 tới 100% | Từ chối |
| Tổng allocation = 100% | Không cho xác nhận danh mục |
| USD/JPY > 0 | Loại dữ liệu lỗi |
| Không được bán quá lượng asset đang sở hữu | Từ chối |
| Không đủ tiền trả lãi | Thanh lý tài sản / phá sản |
