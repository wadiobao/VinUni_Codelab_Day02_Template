# Lab 02 — AI Log & Reflection

## Phase 6 — REFLECTION

| Yêu cầu tôi đã đưa cho AI | AI hỗ trợ gì | Điểm cần kiểm chứng hoặc lỗi quan sát được | Thay đổi tôi thực sự thực hiện | Cách kiểm tra lại |
|---|---|---|---|---|
| Lấy V-App làm mốc, tách phút đi vòng khỏi phút chờ. | Đề xuất phạm vi pilot và cách đo. | Baseline vận hành chưa đo. | Tôi đặt mục tiêu giảm 20% trung vị tổng phút đi vòng và chờ. | Đối chiếu quy trình V-App với log hành trình và phiên sạc. |
| Kiểm thử nhãn `[DRAFT_ONLY]` và ranh giới pin thấp. | Viết prompt, validator Python và hỗ trợ chẩn đoán lỗi API. | Lượt `gemini-2.5-flash` trả HTTP 404. | Tôi đạt **13/13 ca offline**. Lượt live với `gemini-3.5-flash` đạt **4/4**. | Đối chiếu kết quả N01, A01, A02 và A03 trong log. |
