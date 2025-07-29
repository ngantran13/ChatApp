
# Messaging API - Hướng dẫn sử dụng

## Tổng quan
Đây là hệ thống API gửi và nhận tin nhắn (dạng text hoặc file), có sử dụng JWT để xác thực người dùng.

## Các API chính

### 1. Đăng nhập (Login)
- **Phương thức**: `POST`
- **URL**: `/login`
- **Body**:
```json
{
  "username": "tên người dùng",
  "password": "mật khẩu"
}
```
- **Kết quả**: Trả về `accessToken` và `refreshToken`.
---

### 2. Gửi tin nhắn (text/file)
- **Phương thức**: `POST`
- **URL**: `/send-message`
- **Header**: `Authorization: Bearer <accessToken>`
- **Form Data**:
  - `username`: tên người nhận
  - `text`: nội dung tin nhắn (tuỳ chọn)
  - `file`: file đính kèm (tuỳ chọn)
- **Kết quả trả về**:
  - `1`: Người nhận đang online
  - `2`: Người nhận offline, lưu vào hàng chờ
  - `3`: Không phải bạn bè → không gửi

---

### 3. Lấy tin nhắn chờ
- **Phương thức**: `GET`
- **URL**: `/get-messages`
- **Header**: `Authorization: Bearer <accessToken>`
- **Trả về**: Danh sách tin nhắn chờ

---

### 4. Refresh token
- **Phương thức**: `POST`
- **URL**: `/refresh-token`
- **Header**:`refreshToken: <refreshToken>`
- **Kết quả**: Trả về `accessToken` mới (dùng `refreshToken` mới)

---

