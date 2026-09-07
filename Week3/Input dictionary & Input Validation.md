# ARBIVERSE — CHECKPOINT TUẦN 3

**1. Mô tả chung về Arbiverse**

Game đưa người chơi qua ba giai đoạn:

**Phase 1 — Information Asymmetry / Pre-Arbitrage**

→ **Phase 2 — Thai Baht Crisis 1997**

→ **Phase 3 — Yen Carry Trade / Modern Global Market**

Ba phase không phải ba game tách biệt. Chúng thể hiện quá trình thị trường phát triển từ:

**Con người → Thị trường → Hệ thống**

Khi thị trường ngày càng kết nối và minh bạch hơn, cơ hội kiếm lợi nhuận từ chênh lệch đơn giản giảm dần và người chơi phải xử lý thêm các yếu tố như chi phí giao dịch, chi phí vốn, tỷ giá, thanh khoản, đòn bẩy và rủi ro hệ thống.

Người chơi chọn **một trong ba vai ngay từ đầu và giữ nguyên vai xuyên suốt game**:

- **Speculator — Nhà đầu cơ**
- **Investor — Nhà đầu tư**
- **Information Hunter — Thợ săn thông tin**

Tài sản và vốn được **reset về vốn ban đầu khi chuyển phase**, do mỗi phase mô phỏng một thị trường và loại tài sản khác nhau. Tuy nhiên, vai của người chơi và lợi thế cốt lõi của vai được giữ nguyên.


# INPUT DICTIONARY

**Cấu hình vai người chơi**
Lợi thế của ba vai được thiết kế theo ba nguồn lợi thế khác nhau:

| **Vai**                | **Lợi thế cốt lõi**                     |
| ---------------------- | --------------------------------------- |
| **Speculator**         | Khả năng vay vốn và sử dụng đòn bẩy cao |
| **Investor**           | Chi phí giao dịch thấp                  |
| **Information Hunter** | Chi phí tiếp cận thông tin thấp         |

***Lưu ý: Lợi thế này được giữ về bản chất xuyên ba phase, nhưng mức độ tác động thay đổi theo cấu trúc thị trường.***

## PHASE 1 — INFORMATION ASYMMETRY / PRE-ARBITRAGE

### 1.1 Core Game Inputs — Phase 1
| Input name | Meaning | Type | Unit | Example/Source | Validation | 
| :--- | :--- | :--- | :--- | :--- | :--- | 
| `player_role` | Vai trò của người chơi | enum | – | Speculator / Investor / Information Hunter — Team game design | Required; phải thuộc 1 trong 3 role | 
| `initial_cash` | Tiền mặt ban đầu | number | game currency | 100 — Team game design | > 0 | 
| `max_borrow_amount` | Hạn mức vay tối đa | number | game currency | 200 / 50 / 100 tùy role — Team game design | ≥ 0 | 
| `max_leverage` | Đòn bẩy tối đa | number | x | 3x / 1.5x / 2x — Team game design | ≥ 1 | 
| `borrowing_rate` | Lãi suất vay của từng role | number | % per period | 6% / 4% / 5% — Team game design | Theo role configuration | 
| `information_cost_multiplier` | Hệ số điều chỉnh chi phí mua thông tin | number | x | 1.5 / 1.0 / 0.5 — Team game design | > 0 | 
| `base_information_cost` | Chi phí cơ sở của một gói thông tin | number | game currency | Theo team game rule, tuỳ thuộc vào từng gói news. | ≥ 0 | 
| `total_rounds` | Tổng số vòng chơi Phase 1 | integer | round | 03 | > 0 | 
| `round_duration` | Khoảng thời gian mà một round đại diện | number | period | 5 minutes | > 0 | 
| `max_trade_value` | Giá trị giao dịch tối đa mà người chơi được phép thực hiện | number | asset unit / game currency | TBD — Team game rule | > 0 | 

### 1.2 User-entered Inputs — Phase 1

| Input name | Meaning | Type | Unit | Example | Valid range |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `buy_information` | Người chơi quyết định có mua thông tin hay không | boolean / enum | – | YES / NO — User decision | Chỉ YES / NO |
| `borrow_amount` | Số tiền người chơi muốn vay thêm để giao dịch | number | game currency | User-entered | 0 ≤ amount ≤ max_borrow_amount của role |
| `trade_action` | Người chơi muốn mua hay bán | enum | – | BUY / SELL | Chỉ BUY / SELL |
| `number_trade_action` | Số lần người chơi được giao dịch trong 1 round (01 phase có 3 round) | number | – | User-entered | 0 ≤ trade ≤ 3 |
| `selected_trader_id` | Thương nhân mà người chơi quyết định mua/bán với ai | string | – | TRADER_01 | Trader phải tồn tại và đang khả dụng |

### 1.3 Market / Information Inputs — Phase 1
| Input name | Meaning | Type | Unit | Example/Source | Validation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `bid_price` | Giá thương nhân sẵn sàng mua | number | game currency / unit | Calibrated scenario | > 0 |
| `ask_price` | Giá thương nhân sẵn sàng bán | number | game currency / unit | Calibrated scenario | > 0 và bid ≤ ask |
| `available_quantity` | Số lượng tài sản trader có thể giao dịch | number | asset unit | Scenario data | ≥ 0 |
| `quote_round` | Round báo giá có hiệu lực | integer | round | Scenario data | Valid round |
| `information_id` | ID của thông tin | string | – | INFO_01 | Unique |
| `headline_content` | Nội dung thông tin mà user nhìn thấy | string | – | Scenario / simulated information | Required |
| `base_information_cost` | Giá cơ sở để mua thông tin | number | game currency | Team-calibrated | ≥ 0 |
| `truth_label` | Xác định tin hữu ích hay noise | enum | – | SIGNAL / NOISE — Scenario internal | Chỉ game engine nhìn thấy |
| `reliability_level` | Độ đáng tin của nguồn thông tin | number | 0–1 hoặc score | Scenario calibrated | 0–1 nếu dùng probability |
| `affected_asset` | Asset mà thông tin tác động | string | – | ASSET_01 | Phải tồn tại |
| `price_impact_rule` | Rule thông tin tác động tới giá | rule | – | Rule-based scenario | Phải được định nghĩa trước |
| `available_from_round` | Round bắt đầu xuất hiện tin | integer | round | Scenario | Valid round |
| `expiry_round` | Round thông tin hết giá trị | integer | round | Scenario | ≥ available round |

---

## PHASE 2 — FX ARBITRAGE

### 2.1 Core Game Inputs — Phase 2
| Input name | Meaning | Type | Unit | Example/Source | Validation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `initial_cash` | Vốn ban đầu của Phase 2 | number | reporting currency | Team game rule | > 0 |
| `reporting_currency` | Đồng tiền chuẩn dùng tính NAV/P&L | string | – | USD / game-defined currency | Required |
| `max_borrow_amount` | Hạn mức vay tối đa | number | currency | Team game rule | ≥ 0 |
| `max_leverage` | Maximum leverage | number | x | Team game rule | ≥ 1 |
| `borrowing_rate` | Lãi suất vay vốn | number | % per period | Team/calibrated | Theo scenario |
| `transaction_fee_rate` | Phí giao dịch theo giá trị giao dịch | number | % | Team/calibrated | ≥ 0 |
| `fixed_transaction_fee` | Phí cố định mỗi giao dịch nếu có | number | currency | Team game rule | ≥ 0 |
| `base_information_cost` | Chi phí cơ sở để mua thông tin | number | currency | Team | ≥ 0 |
| `information_cost_multiplier` | Hệ số chi phí thông tin theo role | number | x | Role configuration | > 0 |
| `total_rounds` | Tổng số vòng Phase 2 | integer | round | Team | > 0 |
| `round_duration` | Khoảng thời gian mỗi round | number | period | Team assumption | > 0 |
| `max_trade_value` | Giá trị giao dịch tối đa mà người chơi được phép thực hiện | number | asset unit / game currency | TBD — Team game rule | > 0 |
| `execution_rule` | Quy tắc khớp giao dịch | rule | – | Rule-based engine | Required |
| `liquidity_rule` | Quy tắc liquidity ảnh hưởng execution/slippage | rule | – | Team scenario rule | Required nếu liquidity ảnh hưởng gameplay |

### 2.2 User-entered Inputs — Phase 2
| Input name | Meaning | Type | Unit | Example/Source | Validation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `exchange_amount` | Giá trị tiền mà người chơi muốn đem đi đổi | number | currency | 1,000 USD — User-entered | > 0 và ≤ số vốn khả dụng |
| `target_currency` | Đồng tiền mà người chơi muốn đổi sang | enum | – | THB / SGD | Chỉ được chọn currency có trong scenario |
| `borrow_amount` | Số tiền người chơi muốn vay thêm để thực hiện giao dịch | number | reporting currency | User-entered | 0 ≤ amount ≤ max_borrow_amount |
| `buy_market_type` | Thị trường mà người chơi chọn để mua đồng tiền | enum | – | ONSHORE / OFFSHORE | Chỉ ONSHORE hoặc OFFSHORE |
| `sell_market_type` | Thị trường mà người chơi chọn để bán đồng tiền | enum | – | ONSHORE / OFFSHORE | Chỉ ONSHORE hoặc OFFSHORE |

### 2.3 Market / Information / Macro Inputs — Phase 2
| Input name | Meaning | Type | Unit | Example/Source | Validation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `market_id` | ID thị trường FX | string | – | Scenario market | Unique |
| `currency_pair` | Cặp tiền được niêm yết | string | – | USD/JPY | Pair phải tồn tại |
| `bid` | Giá market mua base currency | number | quote/base currency | Calibrated FX scenario | > 0 |
| `ask` | Giá market bán base currency | number | quote/base currency | Calibrated FX scenario | > 0 và bid ≤ ask |
| `quote_round` | Round của quote | integer | round | Scenario | Valid round |
| `quote_expiry` | Thời gian quote còn hiệu lực | integer | round | Scenario | ≥ 0 |
| `transaction_fee_rate` | Phí giao dịch market-specific | number | % | Team/calibrated | ≥ 0 |
| `fixed_fee` | Fixed transaction charge | number | currency | Team rule | ≥ 0 |
| `market_liquidity` | Mức thanh khoản của market | number | currency / volume | Calibrated scenario | ≥ 0 |
| `max_executable_amount` | Maximum amount có thể khớp tại quote hiện tại | number | currency | Scenario rule | > 0 |
| `available_volume` | Volume còn khả dụng | number | currency | Scenario | ≥ 0 |
| `information_id` | ID thông tin FX | string | – | FX_INFO_01 | Unique |
| `headline` | Nội dung user nhìn thấy | string | – | Real-reference / simulated | Required |
| `market_target` | Pair/market mà tin ảnh hưởng | string | – | USD/JPY | Target phải tồn tại |
| `truth_label` | Signal hay noise | enum | – | SIGNAL / NOISE | Internal only |
| `information_delay` | Độ trễ của information | integer | round | Scenario | ≥ 0 |
| `expected_direction` | Hướng tác động mà scenario thiết kế | enum | – | UP / DOWN / NEUTRAL | Internal only |
| `expiry_round` | Round tin hết giá trị | integer | round | Scenario | Valid round |
| `central_bank_event` | Sự kiện từ ngân hàng trung ương | enum/string | – | RATE_CHANGE / INTERVENTION / NONE | Scenario-defined |
| `capital_flow_state` | Trạng thái dòng vốn | enum | – | NORMAL / INFLOW / OUTFLOW | Scenario-defined |
| `market_stress_state` | Trạng thái stress thị trường | enum | – | NORMAL / STRESS | Valid category |
| `fx_volatility` | Mức biến động tỷ giá | number | % hoặc index | Calibrated scenario | ≥ 0 |
| `market_event_id` | Event làm FX/market condition thay đổi | string | – | EVENT_FX_02 | ID phải tồn tại |

> *Lưu ý: `spread = ask - bid`, nên có thể tính tự động. Không cần lưu spread riêng nếu đã có bid và ask.*

---

## PHASE 3 — CARRY TRADE 

### 3.1 Core Game Inputs — Phase 3
| Input name | Meaning | Type | Unit | Example/Source | Validation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `buy_information` | Có mua thêm macro/news information không | boolean / enum | – | YES / NO — User decision | Chỉ YES / NO |
| `borrow_jpy` | Khối lượng JPY người chơi muốn vay | number | JPY | User-entered | >0 và ≤ max_borrow_jpy |
| `selected_leverage` | Mức đòn bẩy player lựa chọn | number / enum | x | 1x / 1.5x / 2x... — Team-defined options | 1 ≤ leverage ≤ max_leverage |
| `allocation_equity_pct` | % vốn sau khi vay được đầu tư vào US Equities | number | % | User-entered | 0–100 |
| `allocation_hy_bond_pct` | % vốn đầu tư vào High-yield Bonds | number | % | User-entered | 0–100 |
| `position_action` | Quyết định xử lý vị thế sau khi market thay đổi | enum | – | HOLD / REDUCE / CLOSE | Chỉ các category được định nghĩa |
| `reduce_percentage` | Tỷ lệ position muốn đóng bớt nếu chọn REDUCE | number | % | User-entered | 0–100; chỉ active khi REDUCE |

> *Lưu ý: Nếu chỉ có Equities và HY Bonds và không cho giữ cash:*
> `allocation_equity_pct + allocation_hy_pct = 100%`

### 3.3 Market / Information / Macro Inputs — Phase 3
| Input name | Meaning | Type | Unit | Example/Source | Validation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `round_id` | Round hiện tại | integer | round | Scenario | 1 → total rounds |
| `boj_policy_rate` | BOJ policy rate | number | % p.a. | BOJ official reference / calibrated scenario | Numeric; scenario-defined range |
| `fed_policy_rate_lower` | Lower bound Fed target range | number | % p.a. | Federal Reserve official reference | Numeric |
| `fed_policy_rate_upper` | Upper bound Fed target range | number | % p.a. | Federal Reserve official reference | ≥ lower bound |
| `boj_policy_signal` | Hướng policy của BOJ | enum | – | TIGHTEN / HOLD / EASE | Valid category |
| `fed_policy_signal` | Hướng policy của Fed | enum | – | TIGHTEN / HOLD / EASE | Valid category |
| `jpy_funding_rate` | Lãi suất thực tế game dùng để tính khoản vay | number | % p.a. | Calibrated simulated data | Theo scenario-defined range |
| `usd_jpy_bid` | Bid của USD/JPY | number | JPY/USD | FX historical reference / calibrated | > 0 |
| `usd_jpy_ask` | Ask của USD/JPY | number | JPY/USD | FX historical reference / calibrated | ≥ bid |
| `fx_volatility` | Mức volatility của USD/JPY | number | % / index | Calibrated scenario | ≥ 0 |
| `fx_regime` | Trạng thái FX | enum | – | NORMAL / JPY_STRENGTHENING / STRESS | Valid category |
| `us_equity_return` | Return US Equities trong round | number | % | Calibrated using US equity reference | > -100% |
| `hy_bond_return` | Return High-yield Bonds trong round | number | % | Calibrated using HY bond reference | > -100% |
| `macro_event_id` | ID macro event | string | – | EVENT_03 | ID phải tồn tại |
| `macro_event_type` | Loại macro event | enum | – | POLICY / INFLATION / LABOR / RISK_OFF | Scenario-defined |
| `headline` | Nội dung macro/news mà user đọc | string | – | Real-reference / simulated | Required |
| `truth_label` | Signal hữu ích hay noise | enum | – | SIGNAL / NOISE | Internal only |
| `impact_target` | Biến/tài sản bị ảnh hưởng | enum | – | FX / EQUITY / BOND / FUNDING | Valid category |
| `market_stress_state` | Mức stress thị trường | enum | – | NORMAL / STRESS / UNWIND | Valid category |
| `capital_flow_state` | Trạng thái dòng vốn nếu mechanic sử dụng | enum | – | NORMAL / OUTFLOW / FLIGHT_TO_SAFETY | Scenario-defined |
| `volatility_regime` | Trạng thái volatility tổng thể | enum | – | LOW / NORMAL / HIGH / CRISIS | Valid category |
| `information_id` | ID của news/signal | string | – | MACRO_INFO_01 | Unique |
| `base_information_cost` | Giá cơ sở để truy cập information | number | reporting currency | Team game rule | ≥ 0 |
| `expiry_round` | Round tin hết giá trị | integer | round | Scenario | ≥ display round |


# INPUT VALIDATION

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
