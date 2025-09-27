# Project: simple_auth

## 📌 Giới thiệu
Repo này minh họa 2 cơ chế **authentication cơ bản trong NodeJS**:
1. **Basic Auth**: xác thực bằng `Authorization header`.
2. **Cookie Auth**: xác thực bằng `cookie` + lưu session trong **MongoDB**.

---

## 🔧 Cài đặt
Clone project và cài đặt dependencies:

```bash
git clone <link-repo>
cd simple_auth
npm init -y
npm install express mongoose cookie-parser
