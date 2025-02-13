# 🚀 Giải thích ngắn gọn và dễ hiểu  

## 1️⃣ Critical Rendering Path (CRP) – Quá trình trình duyệt hiển thị trang web  
Là chuỗi các bước trình duyệt thực hiện để biến **HTML, CSS, JavaScript** thành giao diện hiển thị trên màn hình.  

### 🔹 Quy trình:  
1. **Phân tích HTML → DOM**  
2. **Phân tích CSS → CSSOM**  
3. **Kết hợp DOM + CSSOM → Render Tree**  
4. **Tính toán vị trí các phần tử (Layout)**  
5. **Vẽ lên màn hình (Paint & Composite)**  

### ✅ Tối ưu CRP:  
- Giảm HTML, CSS, JS không cần thiết  
- Dùng `async`, `defer` cho JS  
- Load hình ảnh và font chữ tối ưu  

---

## 2️⃣ XSS vs CSRF – Lỗ hổng bảo mật web  
### 🦠 XSS (Cross-Site Scripting) – Chèn mã độc vào trang web  
- Hacker **thêm mã JavaScript** vào trang web để **đánh cắp dữ liệu người dùng** (cookie, token, session…).  
- **Ví dụ:** Bình luận có chứa `<script>alert('Bị hack!')</script>` chạy trên trình duyệt người khác.  

### ✅ Phòng chống:  
- Escape dữ liệu (`& < >`)  
- Dùng **CSP (Content Security Policy)**  
- Tránh dùng `innerHTML`, `document.write`  

---

### 🛡 CSRF (Cross-Site Request Forgery) – Giả mạo yêu cầu người dùng  
- Hacker **gửi yêu cầu thay bạn** mà bạn không biết.  
- **Ví dụ:** Bạn đang đăng nhập Facebook, nhấp vào **link giả** và nó tự động **đổi mật khẩu** của bạn.  

### ✅ Phòng chống:  
- Dùng **CSRF Token**  
- Kiểm tra **SameSite Cookie**  
- Hạn chế **GET request** cho tác vụ quan trọng  

---

## 3️⃣ HTTP vs SSL – Giao thức truyền dữ liệu  
### 🌐 HTTP (HyperText Transfer Protocol)  
- Giao thức giúp **trình duyệt và server giao tiếp** với nhau.  
- 🚨 **Không mã hóa**, dễ bị hacker chặn thông tin (man-in-the-middle attack).  

### 🔒 SSL/TLS (Secure Sockets Layer / Transport Layer Security)  
- **Mã hóa dữ liệu** giữa trình duyệt và server → **HTTPS** an toàn hơn.  
- Ngăn chặn **hack mật khẩu, đánh cắp dữ liệu**.  

### ✅ Làm sao biết trang có SSL?  
- **🔒 Ổ khóa trên trình duyệt** (HTTPS)  
- Không có cảnh báo "Trang web không an toàn"  

---

## 4️⃣ CSP (Content Security Policy) – Khiên chắn chống XSS  
**🔐 CSP giúp ngăn trang web tải mã độc** từ nguồn không tin cậy.  
- Chặn **inline script (`<script>` trực tiếp)**  
- Chỉ cho phép **tài nguyên từ domain an toàn**  

### ✅ Ví dụ CSP Header:  
```http
Content-Security-Policy: default-src 'self'; script-src 'self' https://trusted.com
