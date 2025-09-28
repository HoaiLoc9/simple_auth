# Project: simple_auth

## 📌 Giới thiệu
Repo này minh họa 2 cơ chế **authentication cơ bản trong NodeJS**:
1. **Basic Auth** (Authorization header).
2. **Cookie Auth** (cookie + lưu session vào MongoDB).

Các ảnh minh họa kết quả test được lưu trong thư mục `public/results/`.

---

## 🔧 Cài đặt
Clone project và cài dependencies:
```bash
git clone <link-repo>
cd simple_auth
npm init -y
npm install express mongoose cookie-parser

## 🚀 Cách test với Postman (chi tiết)
1️⃣ Basic Auth

Chạy server Basic Auth:
**node basic_auth.js**

Tạo request GET tới route bảo vệ
Chọn tab Authorization → Type: Basic Auth.
Nhập Username và Password (ví dụ demo: admin / 1234 nếu server cấu hình như vậy).
Nhấn Send.

![GET BASIC AUTH](https://github.com/HoaiLoc9/simple_auth/blob/main/public/results/GETBASIC_AUTH.png?raw=true)

