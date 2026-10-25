# Telegram AI CRM Automation

Tự động tiếp nhận khách hàng từ Telegram, tư vấn bước đầu bằng AI, lưu thông tin
vào Notion CRM và chỉ chuyển cho Sale khi khách thật sự cần hỗ trợ trực tiếp.

## Điểm nổi bật
- Chống tạo trùng lead bằng Chat ID
- Gom nhiều tin nhắn liên tiếp của khách để bot không trả lời từng dòng nhỏ
- Không chuyển Sale khi khách mới nói nhu cầu chung, chỉ chuyển khi có SĐT hợp lệ và nhu cầu rõ
- Tự ghi chú khách cho Sale, tạm dừng bot sau khi đã chuyển Sale
- Phát hiện spam, tin nhắn lặp, và xử lý trường hợp Sale không liên hệ được

## Luồng xử lý
1. Nhận tin nhắn từ Telegram
2. Kiểm tra khách cũ trong Notion CRM
3. Chống tạo trùng lead mới
4. Gom tin nhắn và chốt tin cuối
5. Kiểm tra đã chuyển Sale chưa
6. Kiểm tra spam và tin nhắn lặp
7. AI tư vấn và chuẩn hoá dữ liệu thành JSON
8. Cập nhật CRM và trả lời khách
9. Chuyển lead cho Sale qua nhóm Telegram

## Công nghệ
n8n, Telegram Bot, Notion API, Google Gemini (AI Agent + Basic LLM Chain), JavaScript

## Cách cài đặt
1. Trong n8n chọn Import from file, nạp `workflows/automation-telegram.example.json`.
2. Tạo credentials: Telegram, Notion, Google Gemini.
3. Thay các placeholder `YOUR_...` bằng giá trị thật (ID database Notion, Chat ID nhóm Sale).
4. Tạo database Notion với các cột workflow sử dụng (Chat ID, Tin nhắn chờ, Bot tạm dừng?, Giai đoạn Sale...).