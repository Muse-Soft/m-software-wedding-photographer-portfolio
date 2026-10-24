# Thiết kế giao diện — Portfolio nhiếp ảnh gia chụp cưới (một trang)

- Mã việc: TEC-49 · Epic: TEC-48 · Project: m-software-wedding-photographer-portfolio
- Phong cách: sang trọng, nền tối, ảnh lớn là trọng tâm.
- Phạm vi: tài liệu thiết kế đủ để Dev triển khai (không kèm code; Dev dựng theo đúng bố cục, màu, chữ dưới đây).

## 1. Nguyên tắc chung

- Một trang duy nhất, cuộn dọc, thứ tự section đúng như mục 3.
- Ảnh là nhân vật chính: mỗi section ưu tiên ảnh lớn, chữ chỉ làm nhiệm vụ dẫn dắt và kêu gọi hành động.
- Khoảng trắng (thực chất là khoảng tối) rộng rãi, không nhồi nhét; mỗi section chỉ một thông điệp.
- Mobile-first: mọi bố cục dưới đây đều có bản mobile (1 cột, ảnh full-width) trước, rồi mở rộng lên desktop.
- Ảnh dùng ảnh thật của nhiếp ảnh gia (placeholder: ảnh cưới mẫu cùng tông tối, ấm); tuyệt đối không dùng ảnh stock sáng chói, không dùng ảnh minh họa hoạt hình.

## 2. Bảng màu (nền tối, sang trọng)

| Vai trò | Màu | Hex | Ghi chú |
|---|---|---|---|
| Nền chính | Đen than | `#121212` | Toàn trang |
| Nền phụ (xen kẽ section) | Đen xám | `#1C1C1E` | Hero, Gói chụp, Form |
| Nền thẻ / khối nổi | Xám than | `#26262A` | Thẻ gói, thẻ nhận xét |
| Chữ chính | Trắng ngà | `#F5F1EA` | Tiêu đề, nội dung |
| Chữ phụ | Xám nhạt | `#A8A29E` | Mô tả, chú thích |
| Điểm nhấn (accent) | Vàng đồng | `#C9A227` | Nút chính, giá, gạch chân tiêu đề, icon |
| Viền mờ | Trắng 10% | `rgba(255,255,255,0.10)` | Viền thẻ, đường chia section |
| Trạng thái lỗi (form) | Đỏ nhạt | `#E57373` | Chỉ dùng khi báo lỗi form |

Quy tắc: accent vàng đồng chỉ dùng cho tối đa 1 nút chính + giá + điểm nhấn nhỏ mỗi section, không tô nền lớn bằng vàng đồng.

## 3. Typography

- Tiêu đề (display): **Playfair Display**, serif, sang trọng; cỡ desktop 48–64px (hero 72px), mobile 32–40px; độ đậm 600; giãn dòng 1.15.
- Tiêu đề section: Playfair Display 36px desktop / 28px mobile, kèm gạch vàng đồng 48px × 3px phía dưới, căn trái (trừ hero căn giữa).
- Nội dung: **Inter**, sans-serif; 16–18px, giãn dòng 1.6; chữ phụ 14px.
- Nút: Inter 16px, đậm 600, chữ hoa toàn bộ (uppercase), khoảng cách chữ 0.5px.
- Font load qua Google Fonts; fallback: Playfair Display → Georgia, serif; Inter → system-ui, sans-serif.
- Không dùng quá 2 họ font trên toàn trang.

## 4. Bố cục từng section (theo thứ tự)

### 4.1. Header (cố định trên cùng, sticky)
- Nền `#121212` mờ 90%, cao 72px; logo (tên studio, Playfair Display) bên trái; menu bên phải: Bộ sưu tập · Gói chụp · Quy trình · Nhận xét · Liên hệ; nút chính "Đặt lịch chụp" (nền vàng đồng, chữ đen) ở cuối menu.
- Mobile: menu thu thành nút hamburger; nút "Đặt lịch chụp" vẫn hiển thị.

### 4.2. Hero (full viewport, 100vh)
- Ảnh nền: 1 ảnh cưới lớn full-bleed, phủ lớp tối gradient từ dưới lên (đen 70% → trong suốt) để chữ đọc được.
- Nội dung căn giữa: dòng nhỏ uppercase "NHIẾP ẢNH CƯỚI" (vàng đồng, tracking rộng); tiêu đề lớn 72px, ví dụ "Khoảnh khắc một lần, giữ trọn một đời"; dòng mô tả ngắn 1–2 câu; 2 nút: chính "Xem bộ sưu tập" (vàng đồng) + phụ "Đặt lịch tư vấn" (viền trắng).
- Cuộn xuống: mũi tên nhỏ ở đáy, nhấp nháy nhẹ.

### 4.3. Bộ sưu tập — 3 phong cách
- Tiêu đề section: "Bộ sưu tập".
- 3 khối phong cách, mỗi khối gồm: ảnh đại diện lớn (tỉ lệ 16:9 desktop, full-width mobile) + tên phong cách + mô tả 1 câu + nút "Xem thêm":
  1. **Ngoại cảnh** — ảnh cưới ngoài trời, ánh sáng tự nhiên, phong cảnh làm nền.
  2. **Studio** — ảnh trong studio, ánh sáng kiểm soát, nền tối đồng bộ tông trang.
  3. **Truyền thống** — áo dài, lễ nghi, tông ấm, trang trọng.
- Dưới mỗi khối: lưới ảnh nhỏ 3–4 ảnh (tỉ lệ 4:5) để xem trước; bấm ảnh mở lightbox xem full (Dev triển khai lightbox đơn giản: bấm mở, bấm X/ESC đóng, nút qua lại).
- Desktop: 3 phong cách xếp dọc, mỗi khối ảnh trái/chữ phải xen kẽ (khối 2 đảo ngược); mobile: xếp dọc 1 cột.

### 4.4. 3 gói chụp (bảng giá)
- Tiêu đề section: "Gói chụp".
- 3 thẻ ngang hàng desktop (3 cột), dọc mobile; thẻ giữa (gói phổ biến nhất) nổi bật: viền vàng đồng + nhãn "Được chọn nhiều nhất".
- Mỗi thẻ: tên gói, giá (vàng đồng, Playfair Display 32px), thời lượng + số ảnh + quyền lợi (danh sách có dấu tick ✓), nút "Chọn gói này" (thẻ giữa: nút vàng đồng đặc; 2 thẻ còn lại: nút viền).
- Gợi ý tên gói (Dev giữ nguyên cấu trúc, PO chốt tên/giá thật sau): "Cơ bản", "Trọn gói" (nổi bật), "Cao cấp".
- Lưu ý nhỏ dưới bảng: "Giá đã bao gồm chỉnh sửa màu; in ấn tính riêng." (chữ phụ 14px).

### 4.5. Quy trình 4 bước
- Tiêu đề section: "Quy trình làm việc".
- 4 bước xếp ngang desktop (4 cột, nối bằng đường kẻ mờ + mũi tên), dọc mobile (timeline dọc):
  1. **Tư vấn & đặt lịch** — trao đổi ý tưởng, chọn phong cách, chốt ngày.
  2. **Chụp hình** — buổi chụp theo lịch, nhiếp ảnh gia hướng dẫn tạo dáng.
  3. **Chọn & chỉnh sửa** — khách chọn ảnh, studio chỉnh màu, retouch.
  4. **Bàn giao** — giao file gốc + ảnh đã chỉnh, hỗ trợ in ấn.
- Mỗi bước: số thứ tự lớn (Playfair Display, vàng đồng, 48px) + tên bước + mô tả 1–2 câu.

### 4.6. Nhận xét khách hàng
- Tiêu đề section: "Khách hàng nói gì".
- Lưới 3 thẻ nhận xét (desktop 3 cột, mobile 1 cột): mỗi thẻ gồm dấu ngoặc kép lớn vàng đồng, nội dung nhận xét (2–3 câu), tên cặp đôi + ngày chụp (chữ phụ).
- Dùng nhận xét thật của khách khi có; tạm thời Dev dùng placeholder ghi rõ "Nội dung mẫu — thay bằng nhận xét thật trước khi public".

### 4.7. Form liên hệ
- Tiêu đề section: "Liên hệ / Đặt lịch".
- Bố cục 2 cột desktop: trái — thông tin liên hệ (số điện thoại, email, địa chỉ studio, giờ làm việc) + nút gọi/Zalo; phải — form.
- Form gồm: Họ tên* · Số điện thoại* · Ngày dự kiến chụp · Gói quan tâm (dropdown: Cơ bản / Trọn gói / Cao cấp) · Lời nhắn. Nút gửi "Gửi yêu cầu" (vàng đồng, full-width mobile).
- Trường bắt buộc đánh dấu *; lỗi hiển thị chữ đỏ nhạt dưới trường; gửi thành công hiển thị thông báo "Cảm ơn! Studio sẽ liên hệ trong 24h." (Dev: v1 chỉ cần validate phía client + hiển thị thông báo; chưa cần backend gửi mail — ghi rõ trong code TODO).

### 4.8. Footer
- Nền `#1C1C1E`; 3 cột: tên studio + slogan ngắn; menu nhanh; liên hệ + icon mạng xã hội.
- Dòng cuối: "© 2026 — Bản quyền thuộc về studio." (chữ phụ).

## 5. Responsive & hành vi

- Breakpoint: mobile < 768px (1 cột); tablet 768–1023px (2 cột cho lưới ảnh/gói); desktop ≥ 1024px (bố cục đầy đủ, nội dung tối đa 1200px, căn giữa).
- Ảnh: dùng `srcset`/ảnh responsive; lazy-load cho ảnh dưới fold; alt mô tả rõ ràng (SEO + accessibility).
- Hiệu ứng: fade-in nhẹ khi cuộn tới section (không quá 300ms, không làm chậm trang); hover ảnh: phóng nhẹ 1.03 + hiện caption; hover nút: đổi sáng 10%.
- Tương phản: chữ trắng ngà trên nền `#121212` đạt tương phản cao; không dùng chữ xám nhạt dưới 14px.
- Accessibility: mọi nút/form có label; điều hướng bàn phím được; lightbox đóng bằng ESC.

## 6. Ghi chú triển khai cho Dev

1. Làm theo đúng thứ tự section mục 4; không thêm section mới khi chưa hỏi PO.
2. Màu/chữ lấy đúng mã hex và họ font mục 2–3; không tự đổi tông.
3. Ảnh placeholder: dùng ảnh cưới mẫu tông tối/ấm, ghi rõ trong code là placeholder để thay ảnh thật.
4. Tên gói, giá, nhận xét, thông tin liên hệ: dùng nội dung mẫu như trên, đánh dấu TODO để PO chốt số liệu thật trước khi public.
5. Kiểm chứng khi xong: mở ở mobile + desktop, kiểm tra đủ 8 section (header, hero, bộ sưu tập 3 phong cách, 3 gói, 4 bước, nhận xét, form, footer), không lỗi hiển thị, form validate được.
6. Tài liệu này là bản thiết kế duy nhất của TEC-49; thay đổi bố cục/màu/chữ phải cập nhật lại file này.
