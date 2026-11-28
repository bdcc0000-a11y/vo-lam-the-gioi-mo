# Huyết Ma Tam Quốc — Dàn Trận

Game dàn trận Tam Quốc chơi ngay trên trình duyệt (điện thoại & máy tính), không cần cài đặt, không tài khoản, không quảng cáo, không mua bán trong game.

**Chơi ngay:** https://bdcc0000-a11y.github.io/vo-lam-the-gioi-mo/tam-quoc/

## Nội dung

- **262 danh tướng** (Ngụy / Thục / Ngô / Quần + 102 tướng tự do, gồm 7 danh tướng Xuân Thu hạng SR), mỗi tướng có Võ / Trí / Chỉ huy, chiêu chủ động, bị động, talent riêng và thang binh chủng 5 bậc.
- **80 binh chủng** thuộc 4 hệ Giáo / Kiếm / Giáp / Kỵ, khắc chế lẫn nhau (Giáo > Kỵ > Kiếm > Giáp > Giáo).
- **32 thành** trên bản đồ liên thông; thắng khi thống nhất đủ 32 thành.
- **2 kịch bản:** 🏯 4 màu bem nhau · 183 (4 phe) và ⚔️ Loạn Đổng Trác · 190 (17 thế lực chư hầu theo RTK11).
- **Lịch tháng/năm:** mỗi năm 12 tháng được xáo trộn giữa 4 loại tháng — ⚔️ Chiến tranh, 🏯 Nội chính, 🎭 Kế sách, 🤝 Ngoại giao — mỗi loại tháng mở những hành động và talent riêng.
- **Trận đánh thời gian thực 20 giây:** quân tràn sân theo đội hình, tướng tự tung chiêu sau 3–5 đòn thường, đơn đấu / tranh biện đóng băng toàn trận, lệnh giữa trận (Tổng công / Cố thủ / Săn tướng), thế trận (Đột phá / Phòng thủ). Thành chỉ mất khi quân thủ bị quét sạch hoặc toàn bộ tướng thủ gục; phe nào còn ≤20% quân sẽ tự thua.
- **Nội chính:** nông nghiệp / thương nghiệp / dân số từng thành, lương thực toàn phe, 5 loại công trình × 3 cấp, chiêu mộ tướng tự do bằng điểm Chỉ Huy, hệ thống tù binh (thả / chém / giam chờ chiêu hàng / vượt ngục / giải cứu).
- **44 talent** theo 4 mảng (Nội chính / Kế sách / Ngoại giao / Chiến tranh), tối đa 3 lần dùng mỗi tháng.
- **Chuỗi sự kiện lịch sử:** 12 sự kiện kịch bản 183 (Khăn Vàng 184 → Tào Phi soán Hán 220) và 6 sự kiện kịch bản 190, mỗi sự kiện 2 lựa chọn với hệ quả số học thật, không có lựa chọn "đúng tuyệt đối".
- **Lớp giữ chân:** hộp "Tháng sau đáng chờ", Album sưu tầm 262 tướng + wishlist + pity tướng tự do, kịch tính trận đấu (MVP, danh hiệu trận, chuỗi thắng 🔥), nhiệm vụ ngày, 19 thành tựu xuyên ván, Sử sách 20 ván gần nhất, 3 độ khó mở khóa dần.
- **Âm thanh:** toàn bộ là bản ghi thật (vũ khí, giáp, trống, tiếng reo hò xung trận) qua reverb; nhạc nền tắt mặc định, bật trong nút âm thanh.

## Cách chơi nhanh

1. Chọn kịch bản và một thế lực ở màn hình đầu (chạm thẻ tướng SR ở băng chuyền để ghim wishlist tối đa 3 người).
2. Chạm vào thành để mở menu cạnh thành: xem tướng, tuyển quân, phát triển, xây công trình, dùng talent, điều tướng (chỉ tới thành có đường qua đất nhà).
3. Tháng Chiến tranh: bấm ⚔️ WAR ở thành của mình, chọn thành địch kề, chọn số quân mang theo và đội hình từng tướng rồi Xuất trận.
4. Bấm **Sang tháng ➜** để qua tháng; để ý dải lịch 12 tháng và cảnh báo lương thực ⚠️.

Tiến trình tự lưu trong trình duyệt (localStorage), mỗi thiết bị một save riêng.

## Cấu trúc mã nguồn

| File | Vai trò |
|---|---|
| `index.html` | Toàn bộ game: giao diện, bản đồ, trận đánh, AI, sự kiện, âm thanh (2 khối script nội tuyến) |
| `heroes.js` | Dữ liệu 262 tướng |
| `troops.js` | Dữ liệu 80 binh chủng |
| `assets/heroes/` | 262 ảnh tướng (280×280 PNG trong suốt) |
| `assets/troops/` | 80 ảnh lính |
| `assets/fx/` | 82 ảnh hiệu ứng chiêu |
| `assets/sfx/` | 33 mẫu âm thanh thật (mỗi mẫu có .ogg + .mp3) |
| `tests/smoke.js` | Kiểm thử khói: ván mới → chuẩn bị → trận → AI → lưu |
| `tests/sim.js` | Mô phỏng cân bằng: `curve` (đường cong thắng), `games` (AI đấu AI), `eco` (kinh tế) |
| `tests/events.js` | Kiểm tra cân bằng 17 sự kiện: AI tham lam không chọn một phía quá 70% |
| `tests/hooks.js` | Kiểm tra hộp "Tháng sau đáng chờ": tháng trống < 15% |
| `tests/savesize.js` | Đo dung lượng save sau 60 tháng |

Chạy kiểm thử: `node tests/smoke.js` (phải in ALL PASS).

## Ghi chú kỹ thuật

- Mọi hằng số gameplay mới nằm trong đối tượng `TUNING` ở đầu script 1 của `index.html`.
- Save dùng khóa `huyetma_tq_v1`, phiên bản save = 2, tự di trú khi nạp save cũ; dữ liệu xuyên ván (thành tựu, sử sách, số liệu) nằm ở khóa riêng `huyetma_tq_meta_v1`.
- Game chạy hoàn toàn ngoại tuyến sau lần tải đầu (mọi tài nguyên cùng thư mục, không gọi API ngoài).
