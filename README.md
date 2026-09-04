# Vườn & Nắng — Landing Page

Landing page giới thiệu **cây giống** và **dược liệu sấy khô**, host miễn phí trên GitHub Pages.

🔗 **Xem trực tiếp:** https://tony-jpham.github.io/vuon-va-nang/

## Trạng thái hiện tại

Không cần build tool, không cần Node.js:
- `index.html` — trang chủ (HTML/CSS thuần), danh sách sản phẩm, bộ lọc, tìm kiếm.
- `san-pham.html` — trang chi tiết 1 sản phẩm (`san-pham.html?id=<product-id>`), đọc dữ liệu từ `products.json`.
- `products.json` — danh sách sản phẩm và giá, tách riêng để dễ cập nhật mà không cần sửa HTML. Mỗi sản phẩm có `id` riêng (dùng để liên kết sang trang chi tiết và cho Google Analytics).
- `images/` — ảnh sản phẩm thật (định dạng WebP, đã nén).

Mọi thay đổi commit lên branch `main` sẽ tự động deploy lại sau vài phút.

## Định hướng thiết kế

- **Bảng màu**: xanh rêu đậm (`#1F2B1E`), kraft giấy (`#DDC9A3` / `#EDE1C4`), rust/màu trái sấy (`#A8442A`), nền giấy (`#F6EFDD`).
- **Font**: `Fraunces` (tiêu đề, có chất serif hữu cơ), `Work Sans` (nội dung), `Space Mono` (nhãn, mã, giá — kiểu tem nhãn đóng gói thật).
- **Điểm nhấn riêng (signature)**: thẻ sản phẩm kiểu "tiêu bản thực vật" (specimen tag) dùng cho cả cây giống và dược liệu sấy.

## Các mục đã có trong trang

1. **Header** — logo + nav ngang trên desktop; trên mobile (≤720px) thu gọn thành **nút hamburger** góc phải, bấm mở dropdown menu (Sản phẩm / Câu chuyện / Liên hệ), tự đóng khi chọn một mục.
2. **Hero** — tiêu đề + mô tả (có nhấn yếu tố sức khoẻ) + 2 nút CTA (Xem sản phẩm / Đặt hàng).
3. **Sản phẩm** — toàn bộ 74 sản phẩm từ `products.json` render dạng lưới thẻ "tiêu bản thực vật". Có **ô tìm kiếm theo tên** (không phân biệt dấu tiếng Việt) và **bộ lọc theo loại** (nút pill, kèm số lượng sản phẩm trong nhóm, ví dụ "Cây cảnh (40)"), hai cơ chế lọc kết hợp với nhau. 58/74 sản phẩm đã có ảnh thật. Mỗi thẻ hiển thị nhãn danh mục (luôn theo `category`) kèm badge phụ nếu sản phẩm có `tag` riêng (ví dụ "Phong thủy") khác với danh mục. Mỗi thẻ có link "Xem chi tiết" dẫn sang `san-pham.html`.
4. **Trang chi tiết sản phẩm** (`san-pham.html`) — ảnh lớn, giá, mô tả, lợi ích, nút liên hệ (Zalo/điện thoại), nút sao chép đường dẫn sản phẩm, và danh sách sản phẩm liên quan cùng loại.
5. **Câu chuyện** — giới thiệu thương hiệu (khu vườn tại Đức Huệ) + số liệu (40+ loại cây, 100% organic, 0% hoá chất/chất bảo quản) + lời mời ghé thăm vườn.
6. **Liên hệ** — địa chỉ vườn (link Google Maps) và 2 nút hành động nhanh: **Chat qua Zalo** và **Gọi điện** trực tiếp (không còn nhúng bản đồ Google Maps dạng iframe).
7. **Footer**.
8. **Google Analytics (gtag.js)** — chỉ tải trên domain production (`tony-jpham.github.io/vuon-va-nang/`), không chạy khi test local. Bắn các event tuỳ chỉnh: `view_product_image` (mở ảnh sản phẩm), `select_product_contact` (bấm liên hệ trên trang chi tiết), `share_product_link` (sao chép link sản phẩm), `select_contact` (bấm Zalo/gọi điện ở mục Liên hệ trang chủ).
9. **Favicon** — biểu tượng lá 🌿 nhúng dạng SVG data URI (không cần file ảnh riêng).

## Việc cần làm tiếp (chưa hoàn thiện)

- [ ] Bổ sung ảnh thật cho 16 sản phẩm còn thiếu trong `products.json` (58/74 đã có ảnh) — toàn bộ đều thuộc nhóm dược liệu sấy khô (`dried`), bao gồm 2 sản phẩm mới (Lá dâu tằm, Thuốc dòi tím).

## Ghi chú kỹ thuật quan trọng

- **Ảnh phải nén trước khi đưa vào repo** — xuất định dạng **WebP**. Có thể dùng squoosh.app/TinyPNG, hoặc dòng lệnh `cwebp -q 78 -resize 640 0 input.jpg -o output.webp` (cần cài qua `brew install webp` + `brew install libtiff`), resize chiều rộng khoảng **640px** là đủ nét cho khung thẻ sản phẩm, dung lượng trung bình ~150-200KB/ảnh.
- Ảnh sản phẩm nằm trong thư mục `images/`, đặt tên không dấu, dùng gạch nối, khớp với tên sản phẩm (ví dụ `phu-qui.webp`, `la-sen-say.webp`). Với sản phẩm có nhiều size (nhỏ/vừa/lớn), hậu tố size vào cuối tên file (ví dụ `vang-anh-nho.webp`, `vang-anh-lon.webp`).
- **Cập nhật giá/sản phẩm**: chỉ cần sửa `products.json`, không cần đụng vào `index.html`/`san-pham.html`. Danh sách sản phẩm và trang chi tiết tự render lại khi tải trang.
- **Mỗi sản phẩm phải có `id` duy nhất** trong `products.json` (dùng slug không dấu, ví dụ `plant-phu-qui`) — đây là khoá dùng để link sang `san-pham.html?id=...` và để gắn vào các event Google Analytics.
- **Trường `tag` là thông tin phụ trợ, không thay thế `category`** — nhãn danh mục trên thẻ sản phẩm luôn lấy từ `category` (qua `categories[key].label`). Chỉ set `tag` khi sản phẩm cần thêm 1 nhãn phụ khác với danh mục (ví dụ cây phong thuỷ trong nhóm "Cây cảnh" thì `tag: "Phong thủy"`); nếu `tag` trùng với nhãn category thì bỏ trống, không lặp lại.
- **`fetch('products.json')` cần chạy qua HTTP** — mở file HTML trực tiếp bằng double-click (giao thức `file://`) sẽ khiến trang không tải được dữ liệu. Test local bằng `python3 -m http.server` hoặc tương đương.
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
