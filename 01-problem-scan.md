# Lab 02 — Problem Scan & Quick Problem Cards

## Phase 1 — SCAN

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | VinFast | Lặp lại | Phát hiện hồ sơ bảo hành thiếu thông tin trước khi chuyển thẩm định. **Giả định** 200 hồ sơ/tháng × 15 phút/hồ sơ = 50 giờ công/tháng. |
| 2 | Xanh SM | Tốn thời gian | Giảm chờ sạc giữa ca bằng cách so sánh phút đi vòng và chờ dự kiến khi đến trạm. **Ước tính đầu vào cần xác minh** 243–910 giờ-xe/tháng trên 1.000 xe. |
| 3 | Xanh SM | Pain từ người khác | Tra soát cuốc nghi bị thu tiền hai lần. **Ước tính đầu vào cần xác minh** 37–156 giờ công/tháng trên 1.000 xe. |
| 4 | Vinhomes | AI có thể tốt hơn | Phân loại yêu cầu sửa chữa để chuyển đúng đội kỹ thuật. **Giả định** 500 yêu cầu/tháng × 5 phút/yêu cầu ≈ 42 giờ công/tháng. |
| 5 | Vinmec | Lặp lại | Gợi ý lấp lịch khám hủy sát giờ từ danh sách chờ. **Giả định** 60 lịch/tháng × 20 phút/lịch = 20 giờ lịch khám trống/tháng. |

Các giờ ở bảng dùng để sàng lọc cơ hội. Giờ-xe, giờ công và giờ lịch khám là các đơn vị tác động khác nhau. Tần suất thực tế và thời gian có thể tiết kiệm đều **chưa đo**.

## Phase 2 — QUICK-ASSESS

### Quick Problem Card #2 — Chờ sạc giữa ca

| Trường | Nội dung |
|---|---|
| Bài toán (1 câu) | Tài xế cần chọn trạm phù hợp với ca đang chạy và giảm tổng thời gian đi vòng cộng chờ đến khi bắt đầu sạc. |
| Công ty thành viên | Xanh SM |
| Ai đang đau (Actor)? | Tài xế taxi điện giữa hai cuốc. Điều phối viên hỗ trợ ngoại lệ theo giả thuyết cần xác minh. |
| Workflow thủ công hiện tại (3–5 bước) | 1. Xem nhu cầu sạc, gợi ý lộ trình và phiên sạc trong V-App. 2. So sánh và chọn trạm, có thể hỏi điều phối khi khó quyết định. 3. Đi đến trạm. 4. Chờ trụ phù hợp. 5. Bắt đầu sạc. Green SM xác nhận các tính năng tra cứu của V-App. Cách chọn thực tế, hỗ trợ và hàng đợi cần đối chiếu với người vận hành. [Công bố Green SM][green-sm] |
| Bước nào tốn thời gian/lỗi nhất? | Giả thuyết ở bước 4, khoảng **12 phút/lượt** trong một kịch bản minh họa. Quyết định ở bước 2 có thể ảnh hưởng thời gian chờ ở bước 4. Thời lượng thực tế **chưa đo**. |
| AI có thể nhảy vào hỗ trợ ở bước nào? | Ở bước 2, rule lọc trạm đủ điều kiện và xếp theo phút đi vòng + phút chờ dự kiến tại ETA. Bản lab dùng ETA và thời gian chờ mô phỏng. |
| Đo thành công bằng gì (Metric có số)? | **Mục tiêu đề xuất** giảm ít nhất **20%** trung vị tổng phút đi vòng và chờ so với nhóm dùng quy trình V-App hiện hành trong điều kiện tương đương. Baseline **chưa đo**. |
| Quick Architecture | **Rule** làm lõi. Gemini chỉ tạo bản nháp theo quyết định đã tính để thử ranh giới trong lab. |

### Quick Problem Card #4 — Chuyển yêu cầu sửa chữa đúng đội

| Trường | Nội dung |
|---|---|
| Bài toán (1 câu) | Yêu cầu sửa chữa mô tả tự do có thể mất thời gian phân loại và chuyển qua nhiều đội trước khi được tiếp nhận. |
| Công ty thành viên | Vinhomes |
| Ai đang đau (Actor)? | Nhân viên tiếp nhận yêu cầu, đội kỹ thuật và cư dân chờ phản hồi. |
| Workflow thủ công hiện tại (3–5 bước) | **Giả thuyết** 1. Tiếp nhận yêu cầu. 2. Đọc mô tả và hỏi thêm nếu thiếu thông tin. 3. Xác định nhóm lỗi và chuyển đội. 4. Đội xác nhận hoặc trả yêu cầu để phân lại. |
| Bước nào tốn thời gian/lỗi nhất? | Bước 2–3, **giả định 5 phút/lượt** cho đọc và phân loại. Thời lượng thực tế **chưa đo**. |
| AI có thể nhảy vào hỗ trợ ở bước nào? | Ở bước 2–3, ánh xạ danh mục hoặc từ khóa rõ vào đội đã quy định. Nhân viên xử lý yêu cầu mơ hồ và các trường hợp có nguy cơ an toàn. |
| Đo thành công bằng gì (Metric có số)? | **Mục tiêu đề xuất** trung vị phân loại **≤ 3 phút/lượt**, tỷ lệ vào đúng đội ngay lần đầu **≥ 90%** trên mẫu được kỹ thuật xác nhận. Baseline **chưa đo**. |
| Quick Architecture | **Rule**, thử với danh mục lỗi và ma trận đội phụ trách. |

### Quick Problem Card #1 — Hồ sơ bảo hành thiếu thông tin

| Trường | Nội dung |
|---|---|
| Bài toán (1 câu) | Nhân viên mất thời gian rà hồ sơ và yêu cầu bổ sung thông tin trước khi hồ sơ đủ điều kiện thẩm định. |
| Công ty thành viên | VinFast |
| Ai đang đau (Actor)? | Nhân viên tiếp nhận bảo hành và cố vấn dịch vụ tại xưởng. |
| Workflow thủ công hiện tại (3–5 bước) | **Giả thuyết** 1. Nhận hồ sơ. 2. So trường và chứng từ với checklist. 3. Ghi mục thiếu để xưởng bổ sung. 4. Kiểm lại và chuyển hồ sơ đủ thông tin sang thẩm định. |
| Bước nào tốn thời gian/lỗi nhất? | Bước 2. Đề bài giả định **15 phút/lượt** cho lượt rà hồ sơ. Phần thời gian riêng theo bước và baseline thực tế **chưa đo**. |
| AI có thể nhảy vào hỗ trợ ở bước nào? | Ở bước 2, rule kiểm tra trường bắt buộc và sự hiện diện của chứng từ theo loại hồ sơ. Nhân viên xử lý ngoại lệ và xác nhận kết quả rà. |
| Đo thành công bằng gì (Metric có số)? | **Mục tiêu đề xuất** trung vị rà **≤ 8 phút/hồ sơ** và phát hiện **≥ 95%** hồ sơ có mục bắt buộc bị thiếu trên tập đã gán nhãn. Baseline **chưa đo**. |
| Quick Architecture | **Rule**, dựa trên checklist có phiên bản. |

## So sánh và chọn đề tài

| Card | Tác động cần kiểm chứng | Khả năng lấy dữ liệu | Mức độ đo lường | Rủi ro chính |
|---|---|---|---|---|
| #2 · Xanh SM | Xe rời trạng thái sẵn sàng nhận cuốc trong lúc đi vòng và chờ. Quy mô 243–910 giờ-xe/tháng là ước tính cần xác minh. | Cần quyền lấy log hành trình, sự kiện đến và bắt đầu sạc, ảnh chụp trạng thái trạm tại thời điểm quyết định. Chưa có mẫu vận hành. | Đo được nếu ghép đủ sự kiện theo phiên, cố định lộ trình gốc và so với V-App trên các ca tương đương. | Pin hoặc trạng thái trụ hết hạn, nhiều xe dồn về cùng trạm, đề xuất trùng tính năng V-App. |
| #4 · Vinhomes | Có thể giảm thời gian chuyển việc và số lượt chuyển lại. Giả định khối lượng rà khoảng 42 giờ công/tháng. | Cần phiếu đã ẩn danh, danh mục lỗi, đội được giao ban đầu và đội xử lý cuối cùng. Chưa có mẫu. | Đo thời gian phân loại và đối chiếu đúng đội theo nhãn được xác nhận. | Chuyển sai đội làm chậm sửa chữa, đặc biệt với yêu cầu khẩn. |
| #1 · VinFast | Có thể giảm công rà và vòng bổ sung. Giả định khối lượng rà 50 giờ công/tháng. | Có thể bắt đầu với checklist và hồ sơ đã ẩn danh. Cần phiên bản checklist và nhãn mục thiếu từ người thẩm định. | Dễ kiểm độ bao phủ với nhãn trường thiếu và đo phút rà trên cùng loại hồ sơ. | Rule lỗi thời có thể báo thiếu sai. Hồ sơ có thể chứa dữ liệu nhạy cảm. |

Chọn **#2** cho DEEP-DIVE. Sự khác biệt cần đo là giá trị của dự báo **phút chờ lúc xe đến**, khi quy trình mốc đã có gợi ý lộ trình sạc và thông tin về các phiên đang diễn ra. Trước khi đề xuất tích hợp, cần xác nhận V-App đang dùng gì để xếp trạm và có tính phút chờ tại ETA hay không. [Công bố Green SM][green-sm]

[green-sm]: https://www.greensm.com/vn-vi/news/ra-mat-tinh-nang-moi-goi-y-lo-trinh-sac-va-danh-sach-phien-sac-tren-ung-dung-v-app
