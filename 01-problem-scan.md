Họ tên: Nguyễn Vũ Khanh
MSV: 2A202603427
# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **VinFast / Vinhomes** | Tốn thời gian | **(Bài toán chính)** Phân tích log sự cố thiết bị thông minh (trụ sạc, smarthome) rườm rà, kỹ thuật viên mất 20-30 phút đối chiếu chéo tài liệu để xác định lỗi gốc. |
| 2 | **VinFast / Vinhomes** | Lặp lại | Hệ thống vận hành NOC bị nhiễu loạn do hàng ngàn cảnh báo giả (false alarms) từ cảm biến phần cứng mỗi ngày, tốn nhân lực đóng thủ công. |
| 3 | **Xanh SM** | Pain từ người khác | Tài xế báo sự cố hết pin/va chạm thực địa, điều phối viên mất nhiều thời gian tra cứu và điều xe, khiến khách chờ lâu và tài xế bức xúc. |
| 4 | **Vinmec** | Tốn thời gian | Bác sĩ mất 20-30 phút/bệnh nhân để trích xuất thông tin lâm sàng từ bệnh án điện tử và viết tóm tắt hồ sơ xuất viện. |
| 5 | **Vinhomes** | AI-upgrade | Hệ thống app Vinhomes Resident nhận khiếu nại nhưng phản hồi rập khuôn, nhân viên phải đọc thủ công và chuyển ticket đến từng ban quản lý. |
---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Tự động hóa phân tích log kỹ thuật và lọc │
│                   cảnh báo giả cho thiết bị thông minh NOC  │
│ Công ty thành viên: [X] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ thuật viên NOC tuyến đầu (L1)       │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhận Alert hệ thống ──> 2. Kéo Log dữ liệu thủ công    │
│──> 3. Mở Wiki/PDF tra cứu mã lỗi ──> 4. Xác định lỗi hay    │
│   cảnh báo giả ──> 5. Tạo Ticket điều thợ / Đóng cảnh báo.  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3,4 (⏱ 30 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2, 3, và 4       │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Tự động đóng/phân loại chính xác 80% cảnh báo giả           │
│ Giảm thời gian chẩn đoán lỗi từ 30 phút ──> dưới 3 phút     │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [X] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Tự động tra cứu và điều phối cứu hộ sạc   │
│                   pin cho tài xế Xanh SM trên thực địa      │
│ Công ty thành viên: [ ] VinFast  [X] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Tài xế chờ đợi, Điều phối viên quá tải  │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tài xế gọi báo ──> 2. Tra GPS ──> 3. Tìm trạm trống    │
│   ──> 4. Soạn tin nhắn hướng dẫn ──> 5. Gọi cứu hộ (nếu cần)│  
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3,4 (⏱ 10 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3,4              │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Tự động đóng/phân loại chính xác 80% cảnh báo giả           │
│ Giảm tổng thời gian xử lý sự cố từ 15 phút ──> dưới 3 phút  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Phân loại và điều hướng tự động khiếu nại │
│                   của cư dân trên App Vinhomes Resident     │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bộ phận CSKH, Cư dân                   │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│  1. Nhận khiếu nại (text/ảnh) ──> 2. Nhân viên đọc thủ công │
│   ──> 3. Phân loại mảng (Kỹ thuật/An ninh/Vệ sinh...)       │
│   ──> 4. Chuyển ticket cho Ban quản lý tòa nhà tương ứng.   │  
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2,3 (⏱ 12 giờ/lượt)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2,3              │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Tự động đóng/phân loại chính xác 80% cảnh báo giả           │
│ Tự động route chính xác 90% ticket trong thời gian < 5 phút │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
