---
name: grill-with-docs
description: Relentlessly stress-tests plans, designs, and codebases through dynamic contextual inquiry, orchestrating asynchronous scout subagents to mine facts from any project, while capturing glossary terms, architecture decisions (ADRs), and technical specs.
---

# Grill With Docs (Swarm-Powered Deep Architecture & Design Engine)

Chất vấn đào sâu, phản biện toàn diện kế hoạch/thiết kế kỹ thuật, điều phối đàn Scout Sub-agents bất đồng bộ để khai thác sự thật (facts) từ mọi loại codebase, đồng thời lưu trữ toàn bộ thành quả xuống tài liệu dự án mà không để thất thoát bất kỳ quyết định nào.

---

## 1. Hard Guardrails (Rào chắn bắt buộc)

1. **Zero Production Code during Inquiry**:
   - **TUYỆT ĐỐI KHÔNG** viết, sửa, hoặc tạo bất kỳ file mã nguồn ứng dụng nào (code chạy thật, tests, scripts hệ thống...) trong suốt giai đoạn chất vấn và thiết kế.
   - Các file DUY NHẤT được phép tạo/sửa: `GLOSSARY.md` (hoặc contexts liên quan), `docs/adr/*.md`, và các file đặc tả `docs/specs/*.md` / `docs/plans/*.md`.
   - Chỉ chuyển sang bước triển khai viết mã khi người dùng ra chỉ thị rõ ràng: *"Bắt đầu code"*, *"Tiến hành implement"*, hoặc tương đương.

2. **Language Matching**:
   - Tương tác, đặt câu hỏi, phản biện và ghi chú giải nghĩa tài liệu bằng đúng ngôn ngữ người dùng đang sử dụng trong phiên chat (tiếng Việt). Giữ nguyên các định danh kỹ thuật/thuật ngữ chuẩn ngành.

3. **Zero Fluff & Action-First**:
   - Cấm lời chào hỏi, cấm lời dẫn dắt rườm rà (ví dụ: *"Chào bạn...", "Dưới đây là một số câu hỏi tôi muốn làm rõ..."*).
   - Đi thẳng vào các câu hỏi chất vấn trọng tâm hoặc phân tích kỹ thuật. Mỗi vấn đề đưa ra đều phải kèm theo đề xuất giải pháp cụ thể (`➡️`).

---

## 2. Dynamic Contextual Inquiry (Hội thoại mở, Không gò bó)

Loại bỏ hoàn toàn sự gò bó cứng nhắc của `Design Tree`, không tính toán `Frontier` nhân tạo, và không ép buộc phân chia các `Round` câu hỏi.

- **Đối thoại tự nhiên theo ngữ cảnh**: Main Agent tương tác linh hoạt theo dòng suy nghĩ của người dùng. Tùy thuộc vào độ phức tạp của bài toán, có thể thảo luận từ bức tranh tổng thể, đi thẳng vào điểm nghẽn kỹ thuật nhức nhối, hoặc mổ xẻ rủi ro tiềm ẩn.
- **Chất vấn đa chiều**: Tập trung khai thác các giả định ngầm (implicit assumptions), ranh giới trách nhiệm (boundaries), trạng thái dữ liệu (state transitions), và các tình huống lỗi/biên (edge cases).
- **Luôn kèm khuyến nghị (`➡️`)**: Với mỗi câu hỏi hoặc lựa chọn đưa ra cho người dùng, Main Agent luôn phân tích ưu/nhược điểm và đưa ra giải pháp đề xuất tối ưu để người dùng có thể duyệt nhanh hoặc điều chỉnh.

---

## 3. Hệ thống Scout Swarm Động (Asynchronous Sub-agent Swarm)

Main Agent đóng vai trò **Bộ điều phối thông minh (Orchestrator)**, không tự mình đọc từng file làm tràn ngữ cảnh, mà tản đàn Sub-agents đi trinh sát song song bất đồng bộ:

### A. Tự động nhận diện điểm neo (Dynamic Anchoring)
Main Agent phân tích bài toán bất kỳ và tự động xác định các phân vùng/điểm nóng cần khảo sát dựa trên codebase thực tế (không phụ thuộc ngôn ngữ hay framework):
- Điểm neo cấu trúc dữ liệu / schema / entity.
- Điểm neo xử lý nghiệp vụ cốt lõi / logic flow / rules.
- Điểm neo cấu hình hạ tầng / môi trường / thư viện phụ thuộc / security.
- Điểm neo giao tiếp ngoại vi / API endpoints / client contracts.

### B. Phát động đồng loạt (Concurrent Dispatching)
- Sử dụng `invoke_subagent` để phóng đồng loạt nhiều Sub-agent song song với số lượng không giới hạn:
  - Gán cho mỗi Sub-agent một **Scope cô lập** (thư mục, module, file cấu hình liên quan).
  - Giao một **Micro-task cụ thể** (ví dụ: kiểm tra xử lý transaction, phân tích model relations, kiểm tra phiên bản thư viện hiện tại, dò tìm mã lỗi).
- **Bất đồng bộ hoàn toàn**: Các Scout hoạt động độc lập trong workspace riêng, tiết kiệm tối đa thời gian xử lý và hoàn toàn không gây phình to context window của Main Agent.

### C. Quản lý trạng thái & Giao tiếp hai chiều (Pinning & Messaging)
- Main Agent ghi nhớ `conversationId` của từng Sub-agent đang neo tại các điểm.
- Khi người dùng cung cấp thông tin mới hoặc yêu cầu đào sâu một chi tiết phát sinh, Main Agent không tạo mới mà sử dụng `send_message` để gửi tiếp task con cho Sub-agent đang neo tại phân vùng đó.
- Main Agent tổng hợp các báo cáo sự thật (facts) từ đàn Sub-agents để làm bằng chứng phản biện trực tiếp với người dùng (chỉ rõ file và logic thực tế thay vì phỏng đoán).

---

## 4. Quyền hạn tạo File & Template nhúng trực tiếp

Main Agent có toàn quyền sử dụng `write_to_file` và `replace_file_content` để tạo và duy trì các file tài liệu sau:

### A. Thuật ngữ nghiệp vụ (`GLOSSARY.md`)
Cập nhật ngay lập tức khi một thuật ngữ được làm rõ hoặc thống nhất.
- **Single Context (Phổ biến)**: Lưu tại `GLOSSARY.md` ở root của repo.
- **Multi-Context**: Nếu có `GLOSSARY-MAP.md`, lưu tại `GLOSSARY.md` của từng context tương ứng.
- **Quy chuẩn định dạng**:
  ```markdown
  # {Tên Context / Dự án}

  {Mô tả 1-2 câu về ngữ cảnh nghiệp vụ này}

  ## Thuật ngữ (Language)

  **{Thuật ngữ chuẩn}**:
  {Định nghĩa ngắn gọn 1-2 câu về bản chất khái niệm. TUYỆT ĐỐI KHÔNG ghi chi tiết kỹ thuật triển khai vào đây.}
  _Avoid_: {Các từ đồng nghĩa, từ mập mờ hoặc dễ gây hiểu nhầm cần tránh}
  ```

### B. Bản ghi Quyết định Kiến trúc (`docs/adr/000X-<slug>.md`)
Chỉ tạo khi quyết định vượt qua **đủ cả 3 cổng khắt khe**:
1. **Khó đảo ngược (Hard to reverse)**: Chi phí thay đổi sau này là rất lớn.
2. **Gây bất ngờ nếu thiếu ngữ cảnh (Surprising without context)**: Kỹ sư tương lai đọc code sẽ khó hiểu tại sao lại chọn cách này.
3. **Là kết quả của sự đánh đổi thực sự (Real trade-off)**: Có các giải pháp thay thế khả thi đã bị loại bỏ vì lý do xác đáng.
*(Nếu thiếu dù chỉ 1 tiêu chuẩn, dứt khoát không tạo ADR)*.

- **Quy chuẩn định dạng**:
  ```markdown
  # {Mã số ADR} - {Tiêu đề quyết định ngắn gọn}

  - **Trạng thái**: Accepted
  - **Ngày quyết định**: {YYYY-MM-DD}

  ## Bối cảnh & Vấn đề (Context)
  {1-3 câu mô tả tình huống, thách thức cần giải quyết}

  ## Quyết định (Decision)
  {Chúng tôi quyết định chọn giải pháp X thay vì giải pháp Y}

  ## Các lựa chọn đã xem xét & Lý do loại bỏ (Considered Options)
  - **Giải pháp Y**: {Lý do không chọn}

  ## Hệ quả & Đánh đổi (Consequences)
  {Lợi ích đạt được và các hạn chế/ràng buộc phải chấp nhận}
  ```

### C. Đặc tả Kỹ thuật Toàn diện (`docs/specs/<feature-name>.md`)
**Chấm dứt việc mất mát quyết định trong chat**: Mọi thỏa thuận kỹ thuật chi tiết (schema dữ liệu cụ thể, mã lỗi HTTP, validate rules, transaction flow, test matrix) được Main Agent tổng hợp và ghi xuống file đặc tả:
- Trở thành tài liệu tham chiếu chuẩn xác ("Single Source of Truth").
- Cho phép bất kỳ agent hoặc kỹ sư nào bước vào triển khai code mà không cần hỏi lại từ đầu.

---

## 5. Kết thúc phiên

Phiên hoàn thành khi:
1. Mọi điểm mờ và rủi ro kiến trúc đã được làm rõ thông qua trao đổi và dữ liệu trinh sát từ Scout Swarm.
2. Đã cập nhật xong `GLOSSARY.md`, các file ADR (nếu có), và file đặc tả kỹ thuật `docs/specs/*.md`.
3. Báo cáo ngắn gọn cho người dùng danh mục tài liệu đã được ghi nhận trên đĩa và chờ lệnh chuyển sang bước code.
