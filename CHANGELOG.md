# Changelog

## v2.1 — 2026-09-03

- **Structural lock.** Identity lock cũ chỉ đủ cho model *ghép* ảnh. Model *tái tạo*
  (GPT Image) vẽ lại sản phẩm thành một vật trông na ná nhưng sai silhouette, sai
  hoạ tiết lưới, sai số lượng chi tiết. Thêm khối structural lock bắt buộc, ra lệnh
  chép nguyên cấu trúc mà không mô tả bất kỳ giá trị nào, nên không mâu thuẫn với
  ảnh đính kèm.
- `PROMPT SHAPE` bước 1 và `CHECK` cập nhật theo.

## v2.0 — 2026-09-03

- **REF điều khiển toàn bộ bối cảnh.** v1.0 bắt trừu tượng hoá ref ("several potted
  plants" thay vì tả cụ thể), model không thấy ref nên tự bịa ra phòng khác. Nay bắt
  chép 8–15 vật thể, mỗi vật có chất liệu, màu, kích thước, vị trí.
- **Giữ lại graphic device.** v1.0 xếp khiên phát sáng / hào quang / tia sáng chung
  nhóm với logo và chữ rồi xoá sạch. Nay tách bạch: chữ và thương hiệu vẫn xoá,
  graphic device bắt buộc tái tạo. Đổi tên mục `EFFECT OVERLAY` thành `GRAPHIC DEVICE`
  và cho nó chạy tự động khi ref có, không cần người dùng yêu cầu.
- **REF quyết định ánh sáng.** Hai block indoor/outdoor tụt xuống thành fallback.
  Negative tail thành có điều kiện: ref ấm thì bỏ các luật cấm tông ấm, nhưng giữ
  yêu cầu nét và trong.
- **Bỏ luật cấm thảm/rèm quanh máy sưởi** — luật này chặn việc chép đúng ref. Thay
  bằng yêu cầu khoảng cách.
- **Lệnh kiểm tra version.** Nhắn `skill version` cho plugin để biết bản nào đang chạy.
- Thêm `versions/` giữ bản cũ, tag `v1.0` / `v2.0`.

## v1.0

Bản đầu.
