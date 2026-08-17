# HƯỚNG DẪN DEPLOY NTU FEEDBACK DEMO

## 1. Chuẩn bị Google Form
1. Tạo Google Form theo mẫu `GOOGLE_FORM_TEMPLATE.md`.
2. Nhấn **Send/Gửi** → biểu tượng liên kết → Copy link.
3. Giữ link này để cấu hình `SURVEY_URL` trên Streamlit Cloud.

## 2. Kiểm tra local
```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
```
Mở `http://localhost:8501`. Kiểm tra Tổng quan, Phân tích phản hồi, Tra cứu, SPARQL, Lọc, Ưu tiên và Xuất kết quả.

## 3. Upload lên GitHub
Khuyến nghị repository **Private** nếu chưa muốn công khai source code; Streamlit app vẫn có thể đặt Public.

Cách dùng giao diện web GitHub:
1. GitHub → dấu `+` → **New repository**.
2. Đặt tên `NTU-Feedback-Demo`.
3. Chọn **Private** (khuyến nghị) hoặc **Public**.
4. Create repository.
5. **Add file → Upload files**.
6. Giải nén ZIP trên máy, kéo toàn bộ *nội dung bên trong thư mục* `NTU-Feedback-Demo` vào vùng upload.
7. Commit changes.

## 4. Deploy Streamlit Community Cloud
1. Mở `https://share.streamlit.io`.
2. Đăng nhập bằng GitHub và cấp quyền cho repository.
3. **Create app** → chọn repository `NTU-Feedback-Demo`, branch `main`.
4. Main file path: `app.py`.
5. App URL: chọn tên dễ nhớ, ví dụ `ntu-feedback-demo`.
6. Advanced settings: khuyến nghị Python 3.11.
7. Trong **Secrets**, dán:
```toml
SURVEY_URL = "https://forms.gle/LINK_CUA_BAN"
```
8. Deploy.

## 5. Cho phép mọi người truy cập
Trong app → **Share** hoặc App settings → **Sharing** → chọn Public.
Link demo có dạng:
`https://<ten-ban-chon>.streamlit.app`

## 6. Sau khi triển khai
- Mở link bằng cửa sổ Incognito/Ẩn danh để xác nhận không cần đăng nhập.
- Thử nút Google Form.
- Không đưa file dữ liệu thô hoặc mapping mã giảng viên gốc lên GitHub.
