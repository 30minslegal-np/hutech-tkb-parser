# HUTECH TKB Parser

Công cụ chuyển thời khóa biểu PDF HUTECH thành bảng Google Sheet trong vài giây, dùng Gemini AI chạy trực tiếp trong trình duyệt.

**Live demo**: `https://<tên-github-user>.github.io/hutech-tkb-parser/`

## Đặc điểm

- Single-file HTML, không backend, chạy trên GitHub Pages
- Gemini API key lưu local trong trình duyệt — không gửi đi đâu khác
- Parse được cả TKB tuần (có ngày) lẫn TKB học kỳ (cột ngày bị cắt)
- Bảng preview edit inline trước khi xuất
- Export: copy TSV (paste vào Sheet) hoặc tải CSV
- Chia sẻ cho bạn cùng lớp, mỗi người tự lấy key Gemini miễn phí
- Giao diện tiếng Việt, tối ưu mobile

## Deploy GitHub Pages (5 phút)

### Bước 1: Tạo repo
```bash
# Tạo repo mới trên GitHub: hutech-tkb-parser (public)
# Clone về máy:
git clone https://github.com/<username>/hutech-tkb-parser.git
cd hutech-tkb-parser
```

### Bước 2: Copy index.html
- Copy file `index.html` vào thư mục gốc của repo
- Commit và push:
```bash
git add index.html README.md
git commit -m "Initial commit - HUTECH TKB parser"
git push
```

### Bước 3: Bật GitHub Pages
- Vào repo → Settings → Pages
- Source: Deploy from a branch
- Branch: `main`, folder `/ (root)`
- Save

Sau ~1 phút, truy cập `https://<username>.github.io/hutech-tkb-parser/`

### Bước 4 (tùy chọn): Custom domain
Nếu muốn host dưới `tkb.delulu.vn` hoặc `tools.go-global.co`:
- Thêm file `CNAME` trong repo với nội dung là domain
- Vào DNS provider thêm CNAME record trỏ về `<username>.github.io`
- Quay lại Settings → Pages, thêm custom domain

## Cách dùng

1. Mở trang web
2. Bước 1: dán Gemini API key (lấy miễn phí tại `aistudio.google.com/app/apikey`)
3. Bước 2: kéo thả file PDF TKB vào ô
4. Chờ ~5-10 giây, Gemini bóc tách ra bảng
5. Click các ô để sửa nếu có chỗ cần chỉnh
6. Bấm **Copy** rồi vào Google Sheet `LichHoc`, click ô B hàng trống đầu tiên, Ctrl+V
7. Các cột ngày giờ sẽ auto-format vì Sheet đã setup sẵn từ Apps Script v2

## Liên kết với hệ thống tự động hóa

Web app này chỉ làm 1 việc: PDF → CSV/TSV. Phần còn lại (tạo Calendar, nhắc Telegram, KPI Dashboard) do Apps Script v2 xử lý sau khi bạn paste dữ liệu vào Sheet. Không thay thế Apps Script — bổ sung cho phần nhập liệu.

## Chi phí

Gemini free tier: 15 request/phút, 1.500 request/ngày. Mỗi lần parse 1 PDF = 1 request. Hoàn toàn đủ dùng cá nhân và chia sẻ cho cả lớp.

## Bảo mật

API key chỉ lưu trong `localStorage` của trình duyệt, không transmit đi đâu trừ khi gọi Gemini. Mã nguồn mở, check được. Chia sẻ link an toàn.

## License

MIT — tự do sao chép, chỉnh sửa, phân phối.

---

Thuộc hệ sinh thái công cụ học vụ của [delulu.vn](https://delulu.vn).
