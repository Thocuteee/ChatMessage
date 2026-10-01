# ChatPulse – Real-Time Messaging & Social Collaboration Service

> Hệ thống ứng dụng chat thời gian thực độ trễ thấp được xây dựng trên nền tảng **Node.js, Express, Socket.IO và Prisma ORM**, tích hợp lưu trữ tệp Cloudinary và đóng gói trọn gói bằng Docker Compose.

---

## 📌 Tổng Quan Hệ Thống

Dự án giải quyết bài toán giao tiếp hai chiều theo thời gian thực (Real-time Bidirectional Communication) giữa người dùng cá nhân và các nhóm chat. Hệ thống được kiến trúc theo mô hình phân tách tầng rõ ràng (Controller - Service - Model/Prisma), đảm bảo tính module hóa và dễ mở rộng.

### ✨ Các Tính Năng Nổi Bật
- **Real-Time Engine:** Truyền nhận tin nhắn tức thì, hiển thị trạng thái đang soạn tin (typing indicator) và trạng thái trực tuyến (online/offline) qua Socket.IO Rooms.
- **Quản lý Hội thoại Đa cấp:** Hỗ trợ hội thoại trực tiếp 1-1 (Direct Messages) và hội thoại nhóm (Group Conversations) với quyền quản trị viên.
- **Tính năng Xã hội Toàn diện:** Ghim tin nhắn (Pinned Messages), biểu cảm tin nhắn (Reactions), thu hồi tin nhắn phía người gửi/hai chiều, kết bạn và chặn người dùng (Blocklist).
- **Lưu trữ Tệp Đa phương tiện:** Tích hợp Cloudinary API xử lý upload, xác thực định dạng và phân phối ảnh/tài liệu đính kèm an toàn.
- **Bảo mật & Quản lý Thiết bị:** Xác thực Stateless JWT, hỗ trợ xác minh email và theo dõi phiên đăng nhập đa thiết bị (Device Management).

---

## 🛠️ Công Nghệ Sử Dụng

- **Backend:** Node.js, Express.js
- **Real-time Protocol:** Socket.IO (WebSockets / Polling Fallback)
- **Database & ORM:** PostgreSQL / MySQL, Prisma ORM
- **Media Storage:** Cloudinary SDK
- **Containerization:** Docker, Docker Compose
- **Frontend:** React (Vite), Tailwind CSS

---

## 🏛️ Kiến Trúc Dữ Liệu (Prisma Schema Overview)

Hệ thống được thiết kế quan hệ chặt chẽ gồm các bảng nghiệp vụ chính:
- `User` & `Device`: Quản lý tài khoản, trạng thái xác thực và lịch sử thiết bị đăng nhập.
- `Conversation` & `Participant`: Quản lý phòng chat, vai trò thành viên (Admin/Member) và thời điểm đọc tin cuối.
- `Message`, `Attachment`, `Reaction`: Lưu trữ nội dung tin nhắn, liên kết media Cloudinary và các tương tác cảm xúc.
- `Friendship` & `Blocklist`: Xử lý mối quan hệ xã hội giữa các tài khoản và danh sách chặn tương tác.
