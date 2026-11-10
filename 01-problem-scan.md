# Lab 02 — Problem Scan & Quick Assessments: AI Bridge Assistant (Trợ Lý Cầu Nối Thay Thế Comtor)

**Học viên:** Nguyễn Mạnh Quyền (Nguyen Manh Quyen)  
**Mã sinh viên:** 2A202603518  
**Vai trò:** AI Product Engineer — Vin Smart Future (Vingroup)  
**Đơn vị phối hợp:** Khối Kỹ Thuật Phần Mềm Toàn Cầu (Global Software Engineering Unit) — VinFast & Xanh SM (GSM) / Vingroup  
**Ngày thực hiện:** 09/11/2026  

---

## 🏛️ 1. Bối cảnh & Mục tiêu Chiến lược

Tại **Vin Smart Future (Vingroup)**, các dự án công nghệ trọng điểm như hệ thống phần mềm điều khiển xe điện thông minh (VinFast EV Infotainment & ADAS), nền tảng điều vận xe điện quy mô lớn (Xanh SM Smart Dispatching Platform), và đô thị thông minh (Vinhomes Smart City IoT) đều đòi hỏi sự phối hợp chặt chẽ giữa:
- **Người giao việc (Requester / Client / Product Owner / Global PM):** Các đối tác Tier-1 quốc tế (Bosch, Continental, Qualcomm, đối tác Nhật Bản, châu Âu, Bắc Mỹ) và Giám đốc Sản phẩm Tập đoàn.
- **Người thực thi (Execution Team):** Đội ngũ kỹ sư nội bộ Vin Smart Future, các đối tác phát triển phần mềm thuê ngoài (Outsource Software Vendors), chi nhánh đa quốc gia và các chuyên gia/freelancer phân tán toàn cầu.

Trong môi trường làm việc đa ngôn ngữ (Việt - Anh - Nhật), đa văn hóa và lệch múi giờ (Time-zone Gap), rào cản giao tiếp là nguyên nhân lớn nhất gây lãng phí nguồn lực:
1. **Yêu cầu (Requirements / Specs) thường xuyên bị hiểu sai, mơ hồ, thiếu ngữ cảnh kỹ thuật.**
2. **Các quyết định kiến trúc và nghiệp vụ cũ nằm rải rác** trong hàng trăm tài liệu Jira, Confluence, email, tin nhắn Slack/Teams và file ghi âm cuộc họp, dẫn đến tình trạng "không ai nhớ đầy đủ bối cảnh lịch sử".
3. **Vị trí Communicator / Comtor (Người cầu nối):** Đóng vai trò then chốt nhưng chi phí nhân sự cực kỳ đắt đỏ, mỗi comtor chỉ có thể hỗ trợ tối đa 2-3 dự án, dễ bị quá tải, thiếu hiểu biết sâu về kỹ thuật chuyên sâu (domain-specific jargon) và trở thành **điểm nghẽn cổ chai (Single Point of Failure)** trong luồng thông tin dự án.

Tài liệu này thực hiện **Quét cơ hội (SCAN)** và **Đánh giá sơ bộ (QUICK-ASSESS)** để xác lập bài toán có sức ảnh hưởng lớn nhất: **AI Bridge Assistant: Trợ lý AI có trí nhớ dự án thay thế và nâng chuẩn Comtor**.

---

# 🔍 Phase 1 — SCAN: Quét Cơ Hội Qua 4 Lenses

Áp dụng 4 lăng kính nghiệp vụ:
1. **Lặp lại (Repetitive):** Dịch thuật tài liệu spec, ghi chép biên bản cuộc họp (Meeting Minutes), tổng hợp danh sách việc cần làm (Action Items) diễn ra hàng ngày ở mọi dự án.
2. **Tốn thời gian (Time-consuming):** Comtor và kỹ sư mất 40-60% thời lượng trong ngày chỉ để họp, giải thích lại yêu cầu, tra cứu quyết định cũ và dịch qua lại hai chiều.
3. **AI có thể tốt hơn (AI-upgrade):** Khả năng ghi nhớ toàn bộ kho tri thức dự án (Project Memory), đối chiếu mâu thuẫn tức thì giữa các phiên bản spec, chấm điểm độ rõ ràng của yêu cầu và dịch kèm sắc thái văn hóa / thuật ngữ kỹ thuật chuẩn xác.
4. **Pain từ người khác (Stakeholder Pain):** Khách hàng/PM bực bội vì dev làm sai spec; Dev kiệt sức vì rework liên tục; Comtor kiệt sức vì bị réo tên 24/7 ở mọi kênh trao đổi.

### 📋 Bảng Quét 6 Bài Toán Vận Hành Tại Vin Smart Future & Đối Tác:

| # | Đơn vị / Mảng | Lens áp dụng | Mô tả bài toán & Điểm nghẽn vận hành thực tế |
|---|---------------|--------------|---------------------------------------------|
| 1 | **Global Software Dev (VinFast / Xanh SM)** | **Lặp lại, Tốn thời gian & Pain** | **AI Bridge Assistant — Trợ lý AI thay thế Comtor (LỰA CHỌN CHÍNH):** Giao tiếp bất đối xứng giữa PM quốc tế và dev offshore. Yêu cầu mơ hồ, quyết định cũ phân tán, comtor chi phí cao và là điểm nghẽn đơn độc. Tỷ lệ rework do hiểu sai yêu cầu lên tới 25-35%. |
| 2 | **VinFast EV Engineering** | Tốn thời gian & AI-upgrade | **Tự động đối chiếu tài liệu kỹ thuật & API Spec đa ngôn ngữ:** Tài liệu kiến trúc xe điện từ đối tác Đức/Nhật dịch sang tiếng Việt thường sai lệch thuật ngữ viễn thám pin (BMS telemetry), mất 2-3 tuần rà soát thủ công mỗi bản release. |
| 3 | **Xanh SM Dispatching Team** | Pain từ người khác | **Phân giải xung đột yêu cầu & cảnh báo lệch múi giờ:** Đội dev tại Việt Nam và chuyên gia thuật toán tối ưu hóa điều vận tại châu Âu thường tranh cãi về logic phân bổ chuyến xe vì không đồng bộ biên bản họp. |
| 4 | **Vin Smart Future Core Services** | Lặp lại & Tốn thời gian | **Hệ thống tự động trích xuất và định tuyến Ticket:** Hàng trăm yêu cầu thay đổi (Change Requests - CR) gửi qua email, Slack từ đối tác không được chuẩn hóa thành format User Story / Acceptance Criteria chuẩn, tốn 2 giờ/ticket để phân loại. |
| 5 | **Vinhomes Smart City Software** | AI có thể tốt hơn | **Trợ lý Onboarding kỹ sư mới & Tra cứu tri thức dự án (Project Knowledge RAG):** Kỹ sư outsource mới mất trung bình 3-4 tuần chỉ để đọc tài liệu cũ và làm phiền Tech Lead để hiểu lý do vì sao kiến trúc lại thiết kế như hiện tại. |
| 6 | **Vinmec HealthTech Outsourcing** | Tốn thời gian & Rủi ro | **Audit chất lượng biên bản họp & Kiểm tra tuân thủ bảo mật dữ liệu y tế (HIPAA/GDPR):** Bản ghi họp lâm sàng với chuyên gia nước ngoài dễ bị rò rỉ dữ liệu định danh bệnh nhân nếu comtor không có kỹ năng ẩn danh hóa dữ liệu (Anonymization). |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Thẻ Bài Toán Tiềm Năng

---

### 🎴 QUICK PROBLEM CARD #1: AI Bridge Assistant — Trợ Lý Thay Thế & Nâng Chuẩn Comtor (LỰA CHỌN ƯU TIÊN)

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                                       │
│                                                                             │
│ Bài toán (1 câu): Xây dựng Trợ lý AI có trí nhớ dự án, hỗ trợ dịch họp      │
│ trực tiếp, RAG tài liệu cũ và tự động làm rõ yêu cầu, gửi bản xác nhận      │
│ hai ngôn ngữ sau họp nhằm thay thế điểm nghẽn Comtor và giảm thiểu rework. │
│ Công ty thành viên: [x] Vin Smart Future   [x] VinFast   [x] Xanh SM        │
│                                                                             │
│ Ai đang đau (Actor)?                                                        │
│ - Người giao việc (Khách hàng, PM quốc tế): Bực bội vì dev hiểu sai spec,  │
│   tiến độ trễ, thiếu tài liệu xác nhận chính thức sau các cuộc họp.         │
│ - Người thực thi (Team Dev outsource, công ty đa quốc gia, freelancer):    │
│   Hoang mang vì yêu cầu mơ hồ, không dám hỏi lại vì rào cản ngoại ngữ.      │
│ - Comtor (Người cầu nối hiện tại): Kiệt sức vì quá tải, dịch không kịp,    │
│   thiếu kiến thức công nghệ chuyên sâu, chi phí nhân sự quá cao.           │
│                                                                             │
│ Workflow thủ công hiện tại (4 bước):                                        │
│   1. [Họp thảo luận]: Khách hàng và Dev họp qua Teams/Zoom với 1 Comtor     │
│   ──> 2. [Comtor dịch & ghi chú]: Comtor vừa dịch đuổi vừa take note sơ sài│
│   ──> 3. [Lục lọi thông tin cũ]: Dev gặp vướng mắc, hỏi Comtor tra email   │
│   ──> 4. [Soạn spec & Rework]: Dev code theo cách hiểu, phát hiện sai sót   │
│                                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                                            │
│ - Bước 2 & 3: Dịch sót ý kỹ thuật, biên bản thiếu quyết định cốt lõi; lục   │
│   tìm quyết định cũ mất 2-4 tiếng/lần; thời gian chốt spec mất 5-7 ngày.    │
│ - Bước 4: Tỷ lệ code xong phải đập đi làm lại (rework) chiếm 25-35% sprint. │
│                                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                                       │
│ - Hỗ trợ họp trực tiếp: Dịch real-time (< 3s), bắt action item, cảnh báo    │
│   ngay trong cuộc họp nếu thỏa thuận mới mâu thuẫn với quyết định cũ.       │
│ - Nạp tài liệu & bản ghi họp (Project Memory RAG), trả lời hỏi đáp kèm trích│
│   dẫn nguồn chính xác bằng ngôn ngữ bản địa của từng bên.                   │
│ - Đánh giá độ rõ của spec (Clarity Score 1-10), sinh câu hỏi làm rõ và tự   │
│   động soạn thảo bản xác nhận hai ngôn ngữ (Dual-language Confirmation)     │
│   có gắn tiền tố bắt buộc [DRAFT_ONLY] cho con người phê duyệt.             │
│                                                                             │
│ Đo thành công bằng gì (Metric có số)?                                        │
│ - Thời gian từ nhận yêu cầu thô đến khi chốt spec: từ 6 ngày ──> dưới 2 ngày│
│ - Tỷ lệ rework do hiểu sai yêu cầu: từ 28% ──> dưới 8%.                     │
│ - Số lần hỏi lại comtor/người giao việc: giảm 65%.                          │
│ - Thời gian onboarding thành viên mới: từ 3 tuần ──> dưới 4 ngày.           │
│ - Groundedness (câu trả lời có trích dẫn nguồn đúng): đạt ≥ 95%.            │
│ - Tỷ lệ chặn Prompt Injection độc hại: 100%.                                │
│                                                                             │
│ Quick Architecture: [x] Hybrid (Rule-based Glossary/RBAC + LLM RAG + HITL) │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 🎴 QUICK PROBLEM CARD #2: Trợ Lý Đối Chiếu Tài Liệu Kỹ Thuật & Kiến Trúc Xe Điện Đa Ngôn Ngữ

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                                       │
│                                                                             │
│ Bài toán: Tự động phát hiện xung đột và sai lệch thuật ngữ giữa tài liệu    │
│ kiến trúc hệ thống xe điện (tiếng Đức/Nhật) và tài liệu triển khai (Việt). │
│ Đơn vị: [x] VinFast Automotive Software Unit                                │
│                                                                             │
│ Ai đang đau? Solution Architect, Kỹ sư hệ thống nhúng (Embedded Engineers). │
│                                                                             │
│ Workflow thủ công:                                                          │
│   Nhận tài liệu đối tác ──> Dịch máy thô (Google Translate) ──> Kỹ sư đọc   │
│   đối chiếu từng bảng tham số CAN-Bus ──> Phát hiện lỗi sau khi nạp firmware│
│                                                                             │
│ Bước tốn thời gian nhất: Đối chiếu bảng mã lỗi và giao thức viễn thám pin   │
│ mất 40 giờ công/bản release; phát hiện sai sót ở giai đoạn test xe thật.     │
│ AI can help: So sánh ma trận tham số kỹ thuật, cảnh báo sai số đơn vị đo    │
│ và thuật ngữ không đồng nhất giữa hai phiên bản tài liệu.                   │
│ Metric: Giảm 85% thời gian đối chiếu spec, sai sót tham số về 0 trước SIT. │
│ Architecture: [x] Rule-based schema check + LLM diff extraction             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 🎴 QUICK PROBLEM CARD #3: Trợ Lý Onboarding Kỹ Sư Mới & Khai Thác Tri Thức Dự Án

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                                       │
│                                                                             │
│ Bài toán: Hỗ trợ lập trình viên mới gia nhập dự án tra cứu toàn bộ bối cảnh │
│ lịch sử kỹ thuật (Architecture Decision Records - ADR) bằng ngôn ngữ tự     │
│ nhiên, giảm áp lực kèm cặp cho Tech Lead.                                   │
│ Đơn vị: [x] Xanh SM Cloud Core Platform                                     │
│                                                                             │
│ Ai đang đau? Kỹ sư mới gia nhập dự án, Tech Lead dự án.                     │
│                                                                             │
│ Workflow thủ công:                                                          │
│   Đọc tài liệu Wiki cũ ──> Không hiểu tại sao code lại viết như vậy ──>     │
│   Hỏi Tech Lead ──> Tech Lead mất 2 tiếng giải thích bối cảnh cuộc họp cũ.  │
│                                                                             │
│ Bước tốn thời gian nhất: Tech Lead mất 15-20% quỹ thời gian làm việc mỗi     │
│ tháng chỉ để trả lời những câu hỏi lặp đi lặp lại về quyết định cũ.         │
│ AI can help: RAG đa thể thức (truy vấn chat history, pull request, ticket   │
│ Jira) trả lời chính xác lý do tại sao quyết định được đưa ra vào ngày nào.  │
│ Metric: Rút ngắn thời gian dev mới commit code đầu tiên từ 18 ngày ──> 3 ngày│
│ Architecture: [x] LLM RAG + Vector DB + Permission-aware retrieval          │
└─────────────────────────────────────────────────────────────────────────────┘
```
