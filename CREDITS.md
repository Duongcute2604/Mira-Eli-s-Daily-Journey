# CREDITS — Hành Trình Của Mira Eli

> File ghi công bắt buộc về nguồn gốc và giấy phép của mọi tài nguyên trong dự án.
> Xem `docs/08_ASSET_MANIFEST.md` mục 08.05 để biết vì sao file này bắt buộc phải tồn tại.

---

## ⚠️ TRẠNG THÁI PHÁT HÀNH

| | |
|---|---|
| **Phiên bản hiện tại** | Dự án học tập — **không phát hành công khai** |
| **Lý do** | 138 / 149 ảnh **chưa xác minh được giấy phép** (xem 08.05.2) |
| **Điều kiện để phát hành** | Truy nguồn được mọi ảnh dùng trong build, hoặc thay bằng ảnh tự tạo |

> 🚨 Chưa hoàn tất phần xác minh license cho 138 ảnh còn lại.
> File này hiện **chưa đủ** để phát hành. Không được bỏ qua mục này.

---

## 1. GIẤY PHÉP BẮT BUỘC — CC BY 4.0

### Spiral Atlas Visual Novel House Backgrounds

| | |
|---|---|
| **Tác giả** | Spiral Atlas |
| **Năm** | 2023 |
| **Tên tác phẩm** | Spiral Atlas Visual Novel House Backgrounds |
| **Giấy phép** | Creative Commons Attribution 4.0 International (CC BY 4.0) |

**Liên kết bắt buộc:**
- Giấy phép: <https://creativecommons.org/licenses/by/4.0/>
- Credit gốc của tác giả: <https://spiralatlas.github.io/credits/>

**Các file sử dụng (11 ảnh):**

| File trong dự án | Nội dung |
|------------------|----------|
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_entrance.jpg` | Cửa ra vào |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_hallway.jpg` | Hành lang |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_dining.jpg` | Phòng ăn |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_dining_kitchen.jpg` | Phòng ăn liền bếp |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_kitchen.jpg` | Bếp |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_lounge.jpg` | Phòng khách |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_bathroom.jpg` | Phòng tắm |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_master_bedroom.jpg` | Phòng ngủ chính |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_single_bedroom.jpg` | Phòng ngủ đơn |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_outside_01.jpg` | Ngoài nhà — biến 1 |
| `tệp ảnh background/Spiral Atlas VN House Backgrounds/bg_sa_outside_02.jpg` | Ngoài nhà — biến 2 |

**Có sửa đổi gì không?**
> Ảnh **được đổi tên** sang quy ước của dự án ngày 02/10/2026 (tiền tố `bg_sa_`).
> Nội dung hình ảnh **không bị chỉnh sửa**. Nếu sau này có crop / tô màu / thay đổi kích thước,
> **phải cập nhật dòng này** — CC BY 4.0 yêu cầu khai báo mọi thay đổi.

**Ghi chú thêm do tác giả (trích nguyên văn từ `Credits and Information.txt`):**
> *"These images were created in Blender and Clip Studio Paint, mostly using models from
> Sketchfab and Blenderkit."*

Tác giả cũng ghi rõ 2 ảnh `outside` **chưa có đường nét** — dùng nguyên trạng.

---

## 2. ASSET CHƯA XÁC MINH ĐƯỢC

**138 ảnh** trong kho hiện **không có thông tin giấy phép nào**. Chi tiết theo nhóm:

| Nhóm | Số | Ghi chú |
|------|----|---------|
| `tệp ảnh background/` | 43 | 38 `.jpg` + 5 `.png`. Tên cũ `FREE_BG_*` **không phải** bằng chứng cấp phép |
| `tệp ảnh background/City/` | 28 | Không rõ nguồn |
| `tệp ảnh nhân vật/` | 39 | Có tên file như `ChatGPT Image …`, `Gemini_Generated_Image_…`, `Copilot_…` |
| `Pack Tổng/` | 28 | Bảng tổng hợp tham khảo — **không đưa vào build** |

**Hành động bắt buộc trước khi phát hành:**
1. Truy nguồn từng nhóm: lưu link, tên tác giả, loại giấy phép.
2. Ảnh nào không tìm được nguồn → **loại khỏi build**, thay bằng ảnh tự vẽ hoặc mua.
3. Cập nhật lại file này và mục "Trạng thái phát hành" ở trên.

---

## 3. NỘI DUNG GỐC

### Kịch bản và thiết kế

| | |
|---|---|
| **Tác giả kịch bản** | *(bổ sung)* |
| **Thiết kế game** | *(bổ sung)* |
| **Ngôn ngữ** | Tiếng Việt |

Tài liệu thiết kế gốc nằm ở `Cốt truyện/` (11 file `.docx`).
Bản markdown đã chuẩn hoá nằm ở `docs/`.

### Công cụ

| Công cụ | Dùng để |
|---------|---------|
| *(bổ sung)* | |

---

## 4. GHI CHÚ

| | |
|---|---|
| **Ngày cập nhật** | 02/10/2026 |
| **Phiên bản tài liệu** | 1.0 |
| **Người chịu trách nhiệm** | *(bổ sung)* |

> File này phải được cập nhật **mỗi khi** thêm asset mới vào build.
> Asset có tiền tố `bg_sa_` **luôn** yêu cầu ghi credit — xem mục 1.
