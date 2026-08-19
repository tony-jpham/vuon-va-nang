# Vườn & Nắng — Landing Page

Landing page giới thiệu **cây cảnh** và **nông sản sấy khô**, dựng để host miễn phí trên **GitHub Pages**.

## Trạng thái hiện tại

File duy nhất: `index.html` — HTML/CSS thuần, không cần build tool, không cần Node.js. Chỉ cần push lên repo GitHub và bật Pages là chạy.

## Định hướng thiết kế

- **Bảng màu**: xanh rêu đậm (`#1F2B1E`), kraft giấy (`#DDC9A3` / `#EDE1C4`), rust/màu trái sấy (`#A8442A`), nền giấy (`#F6EFDD`).
- **Font**: `Fraunces` (tiêu đề, có chất serif hữu cơ), `Work Sans` (nội dung), `Space Mono` (nhãn, mã, giá — kiểu tem nhãn đóng gói thật).
- **Điểm nhấn riêng (signature)**: dải quy trình "Từ vườn đến tay bạn" (Thu hái → Phơi & sấy → Đóng gói → Giao đến bạn) và thẻ sản phẩm kiểu "tiêu bản thực vật" (specimen tag).

## Các mục đã có trong trang

1. **Hero** — tiêu đề + mô tả + 2 nút CTA (Xem sản phẩm / Đặt hàng).
2. **Quy trình** (dải 4 bước, nền xanh đậm).
3. **Cây cảnh chọn lọc** — 3 sản phẩm mẫu, dạng **cuộn ngang (scroll-row)**, có snap, responsive mobile.
4. **Nông sản sấy khô** — 3 sản phẩm mẫu, cùng kiểu cuộn ngang.
5. **Bảng giá chi tiết** — bảng 5 cột: Loại / Tên sản phẩm / Đơn vị tính / Số lượng-Trọng lượng / Giá tiền. Tự cuộn ngang trên mobile.
6. **Câu chuyện** — giới thiệu thương hiệu + số liệu (120+ loại cây, 15 vườn liên kết, 0% chất bảo quản).
7. **Trích dẫn khách hàng**.
8. **Liên hệ** — thông tin + form (đang trỏ Formspree placeholder).
9. **Footer**.

## Việc cần làm tiếp (chưa hoàn thiện)

- [ ] **Thay ảnh thật** — hiện tại các ô ảnh sản phẩm đang dùng gradient + icon SVG placeholder, chưa có ảnh chụp thật.
- [ ] **Đăng ký Formspree** (miễn phí) và thay `your-form-id` trong thẻ `<form action="https://formspree.io/f/your-form-id">` bằng ID thật để form liên hệ gửi được.
- [ ] **Cập nhật giá thật** trong bảng giá (hiện là giá mẫu minh hoạ).
- [ ] **Cập nhật thông tin liên hệ thật** (số điện thoại, Zalo/Facebook hiện là placeholder `0000 000 000`, `vuonvanang`).
- [ ] Cân nhắc thêm cột "Còn hàng/Hết hàng" hoặc nút "Đặt ngay" trong bảng giá (đã đề xuất, chưa làm).

## Ghi chú kỹ thuật quan trọng

- **Ảnh nên nén trước khi đưa vào repo** (dùng squoosh.app hoặc TinyPNG), mỗi ảnh nên dưới ~200-300KB để site tải nhanh.
- **Không dùng link ảnh chia sẻ công khai từ Google Drive** — không ổn định lâu dài (không phải direct-link, có thể bị chặn hotlink hoặc đổi chính sách). Cách tốt hơn: bỏ ảnh vào thư mục `images/` trong repo, hoặc dùng CDN ảnh miễn phí như Cloudinary/ImageKit.
- Site là **tĩnh hoàn toàn** — không có backend, không database. Mọi thay đổi nội dung (giá, sản phẩm) đều phải sửa trực tiếp trong `index.html` rồi commit lại.

## Cách deploy lên GitHub Pages

1. Tạo repo mới trên GitHub (ví dụ `vuon-va-nang`).
2. Đẩy `index.html` (và thư mục `images/` nếu có) lên repo.
3. Vào **Settings → Pages**, chọn branch `main`, thư mục `/root`.
4. Trang sẽ chạy tại `https://<username>.github.io/vuon-va-nang/`.
5. (Tuỳ chọn) Gắn domain riêng bằng file `CNAME` + trỏ DNS.
