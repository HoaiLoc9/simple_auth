# Project: simple_auth

## 📌 Giới thiệu
Repo này minh họa 2 cơ chế **authentication cơ bản trong NodeJS**:
1. **Basic Auth** (Authorization header).
2. **Cookie Auth** (cookie + lưu session vào MongoDB).

Các ảnh minh họa kết quả test được lưu trong thư mục `public/results/`.

---

## 🔧 Cài đặt
Clone project và cài dependencies:

git clone <link-repo>
cd simple_auth
npm init -y
npm install express mongoose cookie-parser
'''
## 🚀 Cách test với Postman (chi tiết)
1️⃣ Basic Auth

Chạy server Basic Auth:
**node basic_auth.js**

Tạo request GET tới route bảo vệ
Chọn tab Authorization → Type: Basic Auth.
Nhập Username và Password (ví dụ demo: admin / 1234 nếu server cấu hình như vậy).
Nhấn Send.

## 📷 Kết quả test

### Basic Auth
![GET BASIC AUTH](https://github.com/HoaiLoc9/simple_auth/blob/main/public/results/GETBASIC_AUTH.png?raw=true)

2️⃣ Cookie Auth (dùng MongoDB để lưu session)
Chạy server Cookie Auth:
**node cookie_auth.js**

Bước A — Login (lấy cookie)
Request: POST http://localhost:3000/login
Header: Content-Type: application/json
Body (raw JSON):
{
  "username": "your_username",
  "password": "your_password"
}

Gửi request → server trả về cookie session (Postman sẽ tự động lưu cookie nếu bật tính năng cookies).

Ảnh minh họa login trả cookie:
### Cookie Auth
- **Login**
![POST LOGIN COOKIES](https://github.com/HoaiLoc9/simple_auth/blob/main/public/results/POSTLOGIN_COOKIES.png?raw=true)

Bước B — Kiểm tra session trong MongoDB
Mở MongoDB, kiểm tra collection session (tên collection tuỳ config trong code, ví dụ sessions).
Bạn sẽ thấy document session tương ứng với user vừa login.

Ảnh minh họa session trong MongoDB:
- **Session trong MongoDB**
![COOKIE MONGO](https://github.com/HoaiLoc9/simple_auth/blob/main/public/results/COOKIE_MONGO.png?raw=true)

Bước C — Gọi API bảo vệ bằng cookie
Tạo request GET http://localhost:3000/profile
Đảm bảo Postman gửi cookie session (Postman → tab Cookies hoặc bật "Send cookies automatically").
Gửi request → server trả về thông tin user nếu cookie hợp lệ.

Ảnh minh họa lấy profile bằng cookie:
- **Lấy profile**
![GET PROFILE COOKIE AUTH](https://github.com/HoaiLoc9/simple_auth/blob/main/public/results/GET_PRO5_COOKIE_AUTH.png?raw=true)

Bước D — Xoá cookie (thủ công hoặc bằng API)
Bạn có thể xoá cookie trong Postman hoặc gọi API xoá cookie (nếu server có route).
Sau khi xoá cookie/đăng xuất, gọi lại route bảo vệ sẽ bị từ chối.

Ảnh minh họa xoá cookie:
- **Xoá cookie**
![COOKIES DELETE](https://github.com/HoaiLoc9/simple_auth/blob/main/public/results/COOKIES_DELETE.png?raw=true)

Bước E — Logout
Request: POST http://localhost:3000/logout (nếu server cung cấp).
Sau logout, session trên DB có thể bị xóa hoặc mark invalid (tùy implement).

Ảnh minh họa logout:
- **Logout**
![POST LOGOUT](https://github.com/HoaiLoc9/simple_auth/blob/main/public/results/POST_LOGOUT.png?raw=true)
