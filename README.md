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

1. **Header** — logo + nav ngang trên desktop; trên mobile (≤720px) thu gọn thành **nút hamburger** góc phải, bấm mở dropdown menu (Sản phẩm / Bảng giá / Câu chuyện / Liên hệ), tự đóng khi chọn một mục.
2. **Hero** — tiêu đề + mô tả (có nhấn yếu tố sức khoẻ) + 2 nút CTA (Xem sản phẩm / Đặt hàng).
3. **Sản phẩm** — toàn bộ 72 sản phẩm từ `products.json` render dạng lưới thẻ "tiêu bản thực vật", có **bộ lọc theo loại** (nút pill), mỗi nút hiển thị kèm số lượng sản phẩm trong nhóm đó (ví dụ "Cây cảnh (34)"), nút "Tất cả" hiển thị tổng số. 58/72 sản phẩm đã có ảnh thật.
4. **Bảng giá nhanh** — bảng **2 cột** (Tên sản phẩm / Giá tiền, đã bỏ cột Loại và Đơn vị tính), render động từ `products.json` bằng JavaScript (`fetch`). Sản phẩm được **gom nhóm theo loại**, mỗi nhóm có 1 dòng tiêu đề riêng (nền đậm hơn, có chấm màu theo category) chèn trước danh sách sản phẩm cùng loại, thay vì lặp lại tên loại ở từng dòng.
5. **Câu chuyện** — giới thiệu thương hiệu (khu vườn tại Đức Huệ) + số liệu (40+ loại cây, 100% organic, 0% hoá chất/chất bảo quản) + lời mời ghé thăm vườn.
6. **Liên hệ** — số điện thoại/Zalo và địa chỉ vườn (link Google Maps + bản đồ nhúng).
7. **Footer**.

## Việc cần làm tiếp (chưa hoàn thiện)

- [ ] Bổ sung ảnh thật cho 14 sản phẩm còn thiếu trong `products.json` (58/72 đã có ảnh) — toàn bộ đều thuộc nhóm dược liệu sấy khô (`dried`).
- [ ] Xác minh tên khoa học/công dụng cho 7 sản phẩm mới thêm (Tùng nam mỹ, Thanh tú, Xương khỉ, Lá cẩm, Dr Thanh, Mơ lông tím, Ngải cứu) — hiện đánh dấu `verified: false` trong `products.json`, cần tra cứu nguồn trước khi công bố thông tin dược liệu/công dụng.
- [ ] Cân nhắc thêm cột "Còn hàng/Hết hàng" hoặc nút "Đặt ngay" trong bảng giá.
- [ ] Cân nhắc thêm form liên hệ trực tiếp trên trang (hiện chỉ có số điện thoại/Zalo).

## Ghi chú kỹ thuật quan trọng

- **Ảnh phải nén trước khi đưa vào repo** — xuất định dạng **WebP**. Có thể dùng squoosh.app/TinyPNG, hoặc dòng lệnh `cwebp -q 78 -resize 640 0 input.jpg -o output.webp` (cần cài qua `brew install webp` + `brew install libtiff`), resize chiều rộng khoảng **640px** là đủ nét cho khung thẻ sản phẩm, dung lượng trung bình ~150-200KB/ảnh.
- Ảnh sản phẩm nằm trong thư mục `images/`, đặt tên không dấu, dùng gạch nối, khớp với tên sản phẩm (ví dụ `phu-qui.webp`, `la-sen-say.webp`). Với sản phẩm có nhiều size (nhỏ/vừa/lớn), hậu tố size vào cuối tên file (ví dụ `vang-anh-nho.webp`, `vang-anh-lon.webp`).
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
