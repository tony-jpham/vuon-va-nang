# Vườn & Nắng — Landing Page

Landing page giới thiệu **cây giống** và **dược liệu sấy khô**, host miễn phí trên GitHub Pages.

🔗 **Xem trực tiếp:** https://tony-jpham.github.io/vuon-va-nang/

## Trạng thái hiện tại

Ba file chính, không cần build tool, không cần Node.js:
- `index.html` — HTML/CSS thuần, toàn bộ nội dung trang.
- `products.json` — danh sách sản phẩm và giá, tách riêng để dễ cập nhật mà không cần sửa HTML.
- `images/` — ảnh sản phẩm thật (định dạng WebP, đã nén).

Mọi thay đổi commit lên branch `main` sẽ tự động deploy lại sau vài phút.

## Định hướng thiết kế

- **Bảng màu**: xanh rêu đậm (`#1F2B1E`), kraft giấy (`#DDC9A3` / `#EDE1C4`), rust/màu trái sấy (`#A8442A`), nền giấy (`#F6EFDD`).
- **Font**: `Fraunces` (tiêu đề, có chất serif hữu cơ), `Work Sans` (nội dung), `Space Mono` (nhãn, mã, giá — kiểu tem nhãn đóng gói thật).
- **Điểm nhấn riêng (signature)**: thẻ sản phẩm kiểu "tiêu bản thực vật" (specimen tag) dùng cho cả cây giống và dược liệu sấy.

## Các mục đã có trong trang

1. **Hero** — tiêu đề + mô tả (có nhấn yếu tố sức khoẻ) + 2 nút CTA (Xem sản phẩm / Đặt hàng).
2. **Cây giống chọn lọc** — 8 sản phẩm có ảnh thật (Phú quí, Ráy voi, Lưỡi hổ, Cỏ nhện, Đinh lăng lá tròn, Hoa hạnh phúc, Mã đề, Vàng anh), dạng **cuộn ngang (scroll-row)**, có snap, responsive mobile.
3. **Dược liệu sấy khô** — 4 sản phẩm có ảnh thật (Lá sen, Lá dứa, Lá sa kê, Thù lù), cùng kiểu cuộn ngang.
4. **Bảng giá chi tiết** — bảng 4 cột: Loại / Tên sản phẩm / Đơn vị tính / Giá tiền, render động từ `products.json` bằng JavaScript (`fetch`). Phân loại theo 6 nhóm: Cây cảnh, Dược liệu, Gia vị, Cây ăn quả, Khác, Dược liệu sấy khô — mỗi nhóm có màu chấm riêng.
5. **Câu chuyện** — giới thiệu thương hiệu (khu vườn tại Đức Huệ) + số liệu (40+ loại cây, 100% organic, 0% hoá chất/chất bảo quản) + lời mời ghé thăm vườn.
6. **Liên hệ** — số điện thoại/Zalo và địa chỉ vườn (link Google Maps).
7. **Footer**.

## Việc cần làm tiếp (chưa hoàn thiện)

- [ ] Bổ sung thêm ảnh thật cho các sản phẩm còn lại trong `products.json` (hiện chỉ 8/23 cây cảnh và 4/14 dược liệu sấy có ảnh).
- [ ] Cân nhắc thêm cột "Còn hàng/Hết hàng" hoặc nút "Đặt ngay" trong bảng giá.
- [ ] Cân nhắc thêm form liên hệ trực tiếp trên trang (hiện chỉ có số điện thoại/Zalo).

## Ghi chú kỹ thuật quan trọng

- **Ảnh phải nén trước khi đưa vào repo** — dùng squoosh.app hoặc TinyPNG, xuất định dạng **WebP** (quality ~80), resize về khoảng **750×560px** (đủ nét cho khung hiển thị 4:3 kể cả màn Retina, không lãng phí dung lượng).
- Ảnh sản phẩm nằm trong thư mục `images/`, đặt tên không dấu, dùng gạch nối (ví dụ `phu-qui.webp`, `la-sen-say.webp`).
- **Cập nhật giá/sản phẩm**: chỉ cần sửa `products.json`, không cần đụng vào `index.html`. Bảng giá tự render lại khi tải trang.
- **`fetch('products.json')` cần chạy qua HTTP** — mở `index.html` trực tiếp bằng double-click (giao thức `file://`) sẽ khiến bảng giá không tải được. Test local bằng `python3 -m http.server` hoặc tương đương.
- Site là **tĩnh hoàn toàn** — không có backend, không database.
- Repo là **public** (bắt buộc để dùng GitHub Pages miễn phí trên gói Free) — không đưa thông tin nhạy cảm (API key, thông tin cá nhân khách hàng...) vào code.
- File `.gitignore` đã loại `.DS_Store` (file rác của macOS Finder) khỏi git.

## Cách deploy / cập nhật

Repo đã được cấu hình GitHub Pages, deploy từ branch `main`, thư mục gốc (`/`).

```bash
git add .
git commit -m "Cập nhật nội dung"
git push
```

Sau khi push, trang sẽ tự build lại và cập nhật tại https://tony-jpham.github.io/vuon-va-nang/ sau khoảng 1-2 phút.

### Deploy lần đầu (tham khảo, đã thực hiện)

1. Tạo repo trên GitHub (`gh repo create vuon-va-nang --public --source=. --remote=origin --push`).
2. Bật GitHub Pages qua **Settings → Pages**, chọn branch `main`, thư mục `/root` (hoặc qua `gh api`).
3. (Tuỳ chọn) Gắn domain riêng bằng file `CNAME` + trỏ DNS.
