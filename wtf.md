Dưới đây là lời giải ngắn gọn, chuẩn xác cho bài tập Bài 12: Xây Dựng Trang Tài Liệu Kỹ Thuật Cho Dự Án AI Chatbot Hỗ Trợ Học Tập (Session 9):

Phần 1: Phân tích theo cú pháp Markdown
Tại sao chọn Markdown thay vì Word/Google Docs cho dự án AI?

Nhẹ hơn & Tối ưu Token: Markdown là văn bản thô (Plain Text) không chứa mã định dạng ẩn rườm rà như Word, giúp giảm số lượng token đầu vào khi đưa vào AI.

Tích hợp Git tốt: Dễ dàng theo dõi lịch sử chỉnh sửa từng dòng (Git Diff) và render trực tiếp trên GitHub.

Tránh lỗi định dạng: Không bị xung đột file hoặc lỗi mã hóa nhị phân khi nhiều lập trình viên cùng làm việc.



[x] Tích hợp API Gemini

[ ] Bổ sung cơ chế chống Hallucination

---

Phần 2: Phân tích Token & Tối ưu PromptTính toán giới hạn lượt hỏi trước khi AI "quên" ngữ cảnh:Mỗi lượt hỏi đáp tốn: $300 \text{ (Prompt)} + 500 \text{ (Response)} = 800 \text{ tokens}$.Số lượt tối đa: $\frac{8,000 \text{ tokens}}{800 \text{ tokens/lượt}} = 10 \text{ lượt}$.Kết luận: Sau 10 lượt hỏi, chatbot bắt đầu vượt quá giới hạn Context Window và quên thông tin đầu cuộc hội thoại.Bảng so sánh Prompt trước và sau tối ưu:Tình huốngTrước khi tối ưu (Dài dòng)Sau khi tối ưu (Cô đọng, giữ ngữ cảnh)1. Hỏi về môn học"Bạn có thể vui lòng giải thích cho tôi môn Cấu trúc dữ liệu học về cái gì được không? Tôi là sinh viên năm nhất..."[Context: SV năm 1 - IT108]\nTóm tắt cốt lõi môn Cấu trúc dữ liệu trong 3 ý chính.2. Sửa code"Hãy giúp tôi tìm lỗi sai trong đoạn code Python này vì nó cứ báo lỗi khi chạy..."[Bug Fix - Python]\nTìm lỗi cú pháp/logic trong đoạn code sau: [Chèn code]3. Lên lịch học"Tôi muốn bạn tạo cho tôi một thời gian biểu học tập từ thứ Hai đến chủ nhật sao cho hợp lý..."[Goal: Study Plan]\nLập lịch học 5 môn (IT101, Toán, Lý, Anh, Python) trong tuần.Phần 3: Xử lý Hallucination bằng MarkdownÝ nghĩa Hallucination Rate 8% & Template File .md:Ý nghĩa: Cứ 100 câu trả lời, AI có trung bình 8 câu bịa đặt thông tin sai lệch nhưng trình bày rất tự tin.Template lưu câu trả lời:Markdown> **Câu hỏi:** Giải thích thuật toán QuickSort?
> **Phản hồi AI:** [Nội dung câu trả lời của AI...]

- [ ] **Đã kiểm chứng ✅** (Thông tin chính xác, khớp tài liệu giáo trình)
- [x] **Cần xác minh ⚠️** (Cần kiểm tra lại độ chính xác của đoạn code minh họa)
Phần 4: Bẫy dữ liệu tổng hợpBẫy 1 (Thiếu dòng phân cách bảng):Ảnh hưởng: Bảng sẽ biến thành văn bản thô, dính liền nhau bằng dấu |, mất hoàn toàn giao diện lưới trực quan.Cách sửa: Bổ sung ngay dòng phân cách tiêu đề chứa dấu gạch ngang (ví dụ: | :--- | :--- |).Bẫy 2 (AI thiếu dữ liệu training & cách giảm Hallucination):Hành vi của AI: AI sẽ cố gắng "đoán" hoặc tự bịa ra thông tin giả mạo (Hallucination) để trả lời sinh viên.Giải pháp Prompt Engineering: Thêm điều kiện giới hạn nghiêm ngặt: "Nếu dữ liệu không có sẵn trong ngữ cảnh, hãy từ chối trả lời và nói rõ 'Tôi chưa có thông tin này', tuyệt đối không tự bịa đặt."
