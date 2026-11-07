Họ tên: Nguyễn Vũ Khanh
MSV: 2A202603427
## 1. AI đã giúp em như thế nào trong quá trình làm bài?

Trong dự án này, em đã sử dụng mô hình Gemini chủ yếu dưới vai trò một Business Analyst để hỗ trợ quá trình nghiên cứu và chuẩn hóa quy trình:

Giải thích thuật ngữ hệ thống chuyên sâu: Dữ liệu sự cố từ trạm sạc thường chứa các thuật ngữ và mã lỗi viễn thông phức tạp (ví dụ: `OCPP_Status_Faulted`, `BMS_Over_Volt`, `Heartbeat_Timeout`). Khi em nhập các từ khóa này, AI đã giải thích rất cặn kẽ ý nghĩa và cơ chế hoạt động của giao thức trạm sạc. Nó giúp em hiểu rõ bản chất của sự cố để từ đó em có thể điền chính xác vào cột "Bottleneck" và "Business Impact" trong bảng Problem Statement.

Cấu trúc hóa ý tưởng lộn xộn: Khi em có một loạt các ý tưởng thô về quy trình xử lý sự cố hiện tại , em đã đưa cho AI và yêu cầu sắp xếp chúng thành các bước tuyến tính. AI đã giúp em gộp các bước trùng lặp và phân định rõ Input/Output của từng giai đoạn, làm cơ sở để em tự thiết kế workflow một cách khoa học nhất.

## 2. Điểm yếu, Sai sót và Ảo giác của AI

Xu hướng Over-Automation: Khi em hỏi về quy trình tương lai , ban đầu AI liên tục đề xuất các giải pháp tự động hóa 100% như: "Khi phát hiện lỗi, AI sẽ tự động gửi lệnh reset phần cứng từ xa để khắc phục ngay lập tức". AI hoàn toàn không tự nhận thức được các rủi ro cháy nổ và bỏ qua yếu tố con người .

## 3. Cách em điều chỉnh Prompt để kiểm soát AI


Em cung cấp bối cảnh cho AI khi prompt: thay vì hỏi mở "Mã lỗi này xử lý sao?", em đổi Prompt thành: *"Đây là quy định xử lý sự cố nội bộ (dán kèm 1 đoạn text). Dựa TUYỆT ĐỐI vào tài liệu này, hãy tóm tắt các bước kỹ thuật viên cần làm..."*. 

Yêu cầu định dạng Output chặt chẽ: Thay vì để AI trả lời bằng văn bản dài dòng, em sử dụng Prompt: *"Hãy trình bày sự khác biệt giữa hai quy trình dưới dạng Bảng, giới hạn mỗi ô không quá 30 chữ"*. Điều này giúp em chắt lọc được đúng những Key Metrics cần thiết để đưa vào báo cáo Deep-dive mà không bị ngợp thông tin.