# 📦 08. ASSET MANIFEST

> Kiểm kê toàn bộ asset trong kho, đo kích thước thật, chỉ ra cái thiếu và cái không dùng được.
> **Pack này không tồn tại trong bộ `.docx` gốc** — số 08 bị bỏ trống khiến numbering nhảy 07 → 09.
> Mọi con số trong tài liệu này là **kết quả đo trực tiếp trên file**, không chép từ tài liệu gốc.

> 📅 **Ngày kiểm kê:** 02/10/2026
> 🧰 **Công cụ đo:** đếm file trực tiếp + đọc header kích thước ảnh (`System.Drawing`)

---

## 08.00 — TÓM TẮT

| Nhóm | Vị trí | Số ảnh | Dùng được? |
|------|---------|---------|-----------|
| **Background — gốc** | `tệp ảnh background/` | 43 | ✅ 43 — nhưng 2 file sai tỉ lệ |
| **Background — City** | `tệp ảnh background/City/` | 28 | ✅ 28 — có sẵn biến thể theo khung giờ |
| **Background — Spiral Atlas** | `tệp ảnh background/Spiral Atlas VN House Backgrounds/` | 11 | ⚠️ Có — nhưng **khác phong cách** + **bắt buộc ghi credit** |
| **Nhân vật** | `tệp ảnh nhân vật/` | 39 | ⚠️ 23 dùng được / 16 tài liệu tham khảo |
| **Bảng tổng hợp** | `Pack Tổng/` | 28 | ❌ **Không** — đây là bảng tham khảo, không phải asset game |
| | **TỔNG** | **149** | **105 dùng được + 44 tham khảo** |

**Ngoài ra:** `tệp ảnh background/__MACOSX/` chứa **15 file rác** (AppleDouble) + 1 file `.DS_Store` — **đã xoá ngày 02/10/2026**. (Tài liệu gốc ghi 14, thực tế là 15.)

> 🚨 **Kết luận quan trọng:** kho có **105 ảnh dùng được** nhưng thiếu hẳn **một số map cốt lõi**. Chi tiết 08.04.

---

## 08.01 — BACKGROUND

### 08.01.1 — `tệp ảnh background/` — 43 ảnh

| Phân loại | Số | Tên file (sau khi chuẩn hoá) |
|-----------|----|---------|
| Phòng ngủ | 7 | `bg_bedroom_01` … `bg_bedroom_07` |
| Bếp | 4 | `bg_kitchen_01` … `bg_kitchen_04` |
| Văn phòng | 5 | `bg_office_01` … `bg_office_05` |
| Đường phố | 4 | `bg_street_01` … `bg_street_04` |
| Tàu hỏa | 4 | `bg_train_01`–`03`, `bg_train_interior_01` |
| Cửa hàng / quán | 3 | `bg_clothing_shop_01`, `bg_restaurant_01`, `bg_mall_01`–`02` |
| Đường hoa anh đào | 2 | `bg_cherry_street_01`, `bg_cherry_street_blur_01` |
| Vườn | 2 | `bg_garden_blur_01`, `bg_garden_blur_02` |
| Bãi biển | 1 | `bg_dawn_beach_01` |
| Onsen | 3 | `bg_onsen_01`, `bg_onsen_03`, `bg_onsen_blur_01` |
| Cửa hàng biến blur | 1 | `bg_clothing_shop_blur_01` |
| Sân ga | 1 | `bg_train_station_01` |
| PNG "miễn phí" | 5 | `bg_free_01`, `bg_free_02`, `bg_free_02_night`, `bg_free_02_sunset`, `bg_free_03` |

> Tổng: 7 + 4 + 5 + 4 + 4 + 3 + 2 + 2 + 1 + 3 + 1 + 1 + 5 = **43** ✅

**Kích thước thật:**

| Kích thước | Số | Đánh giá |
|-----------|----|---------|
| **1920×1080** | 41 | ✅ Đúng 16:9, dùng được ngay |
| **1619×1080** | 2 | ⚠️ `bg_bedroom_01.jpg`, `bg_bedroom_02.jpg` — tỉ lệ 1.5, **sẽ méo** trên canvas 16:9 |

> ⚠️ **Xử lý `bg_bedroom_01` / `bg_bedroom_02`:** canvas game là 1920×1080. Đặt 1619×1080 lên sẽ bị kéo ngang. Phải chọn một trong hai:
> (a) crop cắt ngang về 1920 — mất 301px ở cạnh, chấp nhận được vì nội dung phòng ngủ thường ở giữa;
> (b) thêm viền/padding bằng nền trung tính.
> **Không được** để nguyên rồi ép tỉ lệ — sẽ làm méo đồ vật trong phòng.

> 💡 **Điểm tốt:** nhóm `bg_free_02*` đã có sẵn **3 biến thể** (ngày / hoàng hôn / đêm). Đây là nguồn tài nguyên có sẵn cho hệ thống `TIME_BLOCK` — nên dùng cho M01.

### 08.01.2 — `tệp ảnh background/City/` — 28 ảnh

**Đây là nhóm asset có giá trị nhất trong kho.** Không phải vì đẹp, mà vì nó **đã được dựng sẵn theo khung giờ**.

Tất cả 28 ảnh đều **1920×1080** — đúng chuẩn, không cần xử lý.

| Địa điểm | File ngày | File chiều | File đêm | Thiếu |
|-----------|-----------|------------|----------|-------|
| Downtown 1 | `_01_day` ✅ | `_01_afternoon` ✅ | `_01_night` ✅ | — |
| Downtown 2 | `_02_day` ✅ | `_02_afternoon` ✅ | `_02_night` ✅ | — |
| Downtown 3 | `_03_day` ✅ | `_03_afternoon` ✅ | `_03_night` ✅ | — |
| Neighborhood 1 | `_01_day` ✅ | ❌ | ❌ | **thiếu 2** |
| Neighborhood 2 | `_02_day` ✅ | ❌ | `_02_night` ✅ | **thiếu 1** |
| Neighborhood 3 | `_03_day` ✅ | `_03_afternoon` ✅ | `_03_night` ✅ | — |
| Park 1 | `_01_day` ✅ | `_01_afternoon` ✅ | `_01_night` ✅ | — |
| Park 2 | ❌ | ❌ | `_02_night` ✅ | **thiếu 2** |
| Park 3 | `_03_day` ✅ | `_03_afternoon` ✅ | `_03_night` ✅ | — |
| Playground 3 | `_03_day` ✅ | ❌ | ❌ | **thiếu 2** |
| Sky | `bg_city_sky_day.png` ✅ | `bg_city_sky_afternoon.png` ✅ | `bg_city_sky_night.png` ✅ | — |

**Đọc được từ cấu trúc tên file:** `bg_city_downtown_01_night.png` = cùng một góc phố với `bg_city_downtown_01_day.png`, chỉ khác khung NIGHT.

> 🎯 **Cơ hội thiết kế:** `02_GAMEPLAY_SYSTEM.md` 02.07 định nghĩa 4 khung giờ. `City/` cho ta map ngoài trời **miễn phí** 3/4 biến thể. Đừng vẽ thêm background thành phố — hãy dùng bộ này và chỉ bổ sung 7 ảnh còn thiếu.

**Bổ sung cần thiết (7 ảnh):**

| File cần bổ sung | Tại sao quan trọng |
|-------|-------------------|
| `bg_city_neighborhood_01_afternoon.png` | Arc 1 hay dùng Neighborhood 1 |
| `bg_city_neighborhood_01_night.png` | Arc 2 (phần lớn ban đêm) |
| `bg_city_neighborhood_02_afternoon.png` | chuyển khung giờ |
| `bg_city_park_02_day.png` + `_afternoon` | Park 2 chỉ có Night → không dùng được giữa ngày |
| `bg_city_playground_03_afternoon.png` + `_night` | tương tự |

### 08.01.3 — `Spiral Atlas VN House Backgrounds/` — 11 ảnh

Tất cả **1920×1080**. Toàn bộ được đổi tên có tiền tố **`bg_sa_`** — `sa` = Spiral Atlas, nhắc bắt buộc phải ghi credit. Xem 08.05.1.

| File mới | Nội dung |
|------|----------|
| `bg_sa_entrance.jpg` | cửa ra vào |
| `bg_sa_hallway.jpg` | hành lang |
| `bg_sa_dining.jpg` | phòng ăn |
| `bg_sa_dining_kitchen.jpg` | phòng ăn liền bếp |
| `bg_sa_kitchen.jpg` | bếp |
| `bg_sa_lounge.jpg` | phòng khách |
| `bg_sa_bathroom.jpg` | phòng tắm |
| `bg_sa_master_bedroom.jpg` | phòng ngủ chính |
| `bg_sa_single_bedroom.jpg` | phòng ngủ đơn |
| `bg_sa_outside_01.jpg` | ngoài nhà biến 1 |
| `bg_sa_outside_02.jpg` | ngoài nhà biến 2 |

Kèm 2 file văn bản: `license.txt`, `Credits and Information.txt` — **giữ nguyên, không xoá, không đổi tên** (chúng là chứng cứ license).

> ⚠️ **Vấn đề phong cách — nghiêm trọng hơn vấn đề license.**
> Nhóm này vẽ kiểu **toon-shaded / cel-shaded**. Nhóm `tệp ảnh background/` (43 ảnh) vẽ kiểu **semi-realistic mềm**. Trộn hai kiểu trong cùng một map nhà sẽ nhìn ra ngay.
>
> **Khuyến nghị:** dùng `bg_sa_*` cho **M02 (hành lang)** và phần `outside` — là nơi chuyển cảnh, người chơi không soi kỹ. **Không** dùng cho phòng ngủ hoặc bếp nơi người chơi ở lâu, vì sẽ đụng hàng với `bg_bedroom_*` và `bg_kitchen_*`.

> ⚠️ **Vấn đề chất lượng (ghi trong file gốc của tác giả):**
> `Credits and Information.txt` nói rõ: *"Note: Outside1 and Outside2 do not currently have lines."* — `bg_sa_outside_01.jpg` và `bg_sa_outside_02.jpg` **chưa có đường nét**. Về mặt pháp lý OK, về mặt thẩm mỹ thì dễ bị phê phán. Cân nhắc chỉ dùng `_01`, hoặc dùng làm base để vẽ lại.

### 08.01.4 — Bảng ánh xạ Background → Map

Dựa trên `03_MAP_EVENT_FLOW.md`.

| Map | Tên | Ảnh được chỉ định | Tình trạng |
|-----|-----|------------------|-----------|
| **M01** | Nhà Dương — phòng ngủ | `bg_bedroom_03`–`07` | ✅ có |
| **M01** | Nhà Dương — bếp | `bg_kitchen_02`–`04` | ✅ có |
| **M01** | Nhà Dương — phòng khách | `bg_sa_lounge.jpg` | ⚠️ lệch phong cách |
| **M01** | Nhà Dương — **biến thể ban đêm** | `bg_free_02_night.png` | ❌ **thiếu bản riêng cho từng phòng** |
| **M02** | Hành lang | `bg_sa_hallway.jpg` | ✅ có |
| **M02** | Cửa ra vào | `bg_sa_entrance.jpg` | ✅ có |
| **M03** | Đường / khu phố | `bg_street_01`–`04`, `bg_cherry_street_01` | ✅ có |
| **M03** | Khu phố (biến giờ) | `bg_city_neighborhood_*` | ✅ có, thiếu 2 ảnh |
| **M04** | **Điểm kết nối** (quán) | `bg_restaurant_01.jpg` | ⚠️ **đang dùng nhầm tạm** |
| **M05** | **Viện dưỡng lão** | `bg_office_01`–`05` | ⚠️ **văn phòng ≠ viện dưỡng** |
| **M06** | Phòng hợp / phòng sếp | `bg_office_05.jpg` | ⚠️ dùng chung với M05 |
| **M07** | **Thư viện / không gian học tập** | — | ❌ **THIẾU HOÀN TOÀN** |
| **M08** | **Sân ga** | `bg_train_station_01.jpg` | ⚠️ chỉ 1 góc, không có biến giờ |
| **M08** | Trạm xe buýt | — | ❌ **thiếu** |
| **M09** | Công viên | `bg_city_park_*`, `bg_garden_blur_*` | ✅ có |
| **M09** | Bãi biển | `bg_dawn_beach_01.jpg` | ✅ có |
| **M09** | Onsen | `bg_onsen_01`, `bg_onsen_03` | ✅ có |
| **M10** | Không gian mở cuối cùng | `bg_city_sky_*.png` | ✅ có |

---

## 08.02 — NHÂN VẬT

### 08.02.1 — `tệp ảnh nhân vật/` — 39 file

| Phân loại | Số | Kích thước |
|-----------|-----|-----------|
| Ảnh nhân vật **dùng được** | **23** | 1024×1536 đến 2048×2048 |
| Tài liệu / ảnh chưa xác định | **16** | 800×800 đến 1536×1024 |

**Ảnh dùng được (23) — sau khi đổi tên:**

| Nhân vật | File | Loại |
|----------|------|-----|
| **Dương** | `char_duong_base.jpg`, `char_duong_daily_outfit.png`, `char_duong_crying.jpg`, `char_duong_standing.png`, `char_duong_sheet.png` | sprite + biểu cảm |
| **Dương (chibi)** | `char_duong_chibi_01.png`, `char_duong_chibi_02.jpg`, `char_duong_chibi_anim.jpg` | chibi + động |
| **Dương (chuyển động)** | `char_duong_anim.jpg`, `char_duong_cg_pack03_blackhair.png` | CG/event |
| **Minh** | `char_minh_base.jpg`, `char_minh_sheet.png` | sprite |
| **Minh (chibi)** | `char_minh_chibi_01.png`, `char_minh_chibi_02.jpg`, `char_minh_chibi_anim.jpg` | chibi + động |
| **Minh (chuyển động)** | `char_minh_anim.jpg` | CG/event |
| **Nam** | `char_nam_base.jpg`, `char_nam_sheet.png` | sprite |
| **Nam (chibi)** | `char_nam_chibi_01.png`, `char_nam_chibi_02.jpg`, `char_nam_chibi_noglasses.png`, `char_nam_chibi_anim.jpg` | chibi + động |
| **Nam (chuyển động)** | `char_nam_anim.jpg` | CG/event |

**Tài liệu / ảnh chưa xác định (16) — giữ nguyên tên, không đưa vào build:**

| Nhóm | Số | File |
|------|----|------|
| Bảng số | 8 | `1.1.png` – `1.8.png` |
| Character sheet | 1 | `Character Sheet cho Nam + Minh( bản lỗi).png` |
| Bảng tổng hợp | 1 | `Bảng tài nguyên tổng hợp.png` |
| Minh họa hội thoại | 1 | `cuộc trò chuyện.png` |
| Ảnh tên tự sinh | 5 | `ChatGPT Image …` ×2, `Copilot_…`, `Gemini_Generated_Image_…` ×2 |

> ⚠️ 5 ảnh tên tự sinh **không xác định được nội dung** vì tên file không mang thông tin. Không dùng vào game cho tới khi mở ra kiểm tra. Nếu là nhân vật → chuyển sang nhóm dùng được và đổi tên.

### 08.02.2 — ⚠️ Ba vấn đề nghiêm trọng

| # | Vấn đề | Hệ quả |
|---|--------|--------|
| **1** | **Có 2 phiên bản tóc Dương** — `char_duong_cg_pack03_blackhair.png` và các ảnh Dương còn lại | Chưa chốt bản chuẩn. Nếu không chốt, sẽ có 2 Dương khác nhau trong cùng game |
| **2** | **`Character Sheet cho Nam + Minh( bản lỗi).png`** — chính tên file ghi "bản lỗi" | Dùng làm chuẩn tham chiếu sẽ **nhân bản cả lỗi**. Phải tìm bản đúng ở `Pack Tổng/01-Character Sheet cho Nam + Minh.png` |
| **3** | **Không có Annika** | Nhân vật có vai trò chuyển Arc 3 (`A3_C02`, `A3_C05`, `A3_C11`) nhưng **chưa có ảnh nào** |

> 🚨 Vấn đề #2 nguy hiểm vì "bản lỗi" là tên file do người khác đặt — ai đó **đã nhìn thấy lỗi này**. Phải mở 2 bản so sánh trước khi chốt.

### 08.02.3 — Thiếu về nhân vật

Theo `06_CHARACTER_STYLE.md`:

| Thiếu | Số lượng | Mức độ |
|-------|----------|--------|
| `CHAR_ANNIKA` | 1 nhân vật | **Chặn** A3_C05 / A3_C11 |
| Mẹ Dương — sprite | 1 | `A3_C03`, `A3_C10` |
| Outfit layer Dương | 5 | áo ngủ, đồ viện dưỡng, đồ thường, đồ nghiêm túc, đồ ở nhà Minh |
| Outfit layer Minh | 3 | |
| Outfit layer Nam | 3 | |
| Outfit layer Annika | 2 | |
| Biểu cảm đủ bộ | xem 06.03 | **Chặn** 30 CG |

---

## 08.03 — `Pack Tổng/` — 28 ẢNH **KHÔNG PHẢI ASSET GAME**

### 08.03.1 — Kết luận

Cả 28 ảnh trong `Pack Tổng/` là **bảng tổng hợp tham khảo** — bảng gộp nhiều thiết kế vào một ảnh.

| Kích thước | Số | Ý nghĩa |
|-----------|----|---------|
| 1536×1024 | 25 | khung bảng tổng hợp |
| 1402×1122 | 1 | |
| 1380×1140 | 1 | |
| 1086×1448 | 1 | |

**Không ảnh nào trong 28 ảnh này là asset có thể cắt ra dùng thẳng.**

### 08.03.2 — Nhưng chúng có giá trị lớn

Đây là **nguồn thiết kế quan trọng nhất trong kho**. Phải đọc và giữ, dù không dùng được trong game.

| File | Nội dung thiết kế |
|------|-----------------|
| `00-tổng hợp bản rõ nét hơn.png` | tổng hợp toàn bộ |
| `01-Bảng thiết kế nhân vật dương.png` | thiết kế Dương |
| `01-Character Sheet riêng chỉ dành cho Dương.png` | sheet Dương riêng |
| `01-Character Sheet cho Nam + Minh.png` | **bản ĐÚNG** (đối chiếu file "bản lỗi" trong `tệp ảnh nhân vật/`) |
| `02-Expression Pack…` | bộ biểu cảm |
| `04-Animation Pack.png` | hướng animation |
| `05-background.png` | hướng background |
| `06-PROPS PACK – 30 đạo cụ.png` | 30 đạo cụ |
| `07-UI GAME PACK – …` | hướng UI |
| `08-icon park -.png` | icon |
| `09-EVENT_CG_PACK_01_FAMILY.png` | CG Arc 1 |
| `09-EVENT_CG_PACK_02_ROMANCE.png` | CG Arc 2 |
| `09-EVENT_CG_PACK_03_LIFE_WORK_STUDY.png` | CG Arc 3 |
| `10-MAP PACK1.png` / `10-MAP PACK2.png` | hướng map |
| `11-VFX EFFECT PACK — TỔNG HỢP.png` | hướng VFX |
| `12-AUDIO PACK.png` | hướng audio |
| `13-Title Menu Pack` ×5 | 5 phương án menu |
| `14-GAMEPLAY SYSTEM PACK.png` | hướng hệ thống |
| `15-CHARACTER EXPANSION PACK.png` | Minh, mẹ, sếp |
| `15-Character sheet Minh/Mẹ Dương/Sếp của Dương.png` | sheet bổ sung |
| `UI GAME PACK … bản 1.png` | UI bản 1 |

> ⚠️ **Trùng lặp cần dọn:** có **2 bản UI** (`07-UI GAME PACK` và `UI GAME PACK … bản 1`) và **5 bản Title Menu** cùng chủ đề. Cần chốt 1 mỗi loại, xoá hoặc chuyển sang `refs/` các bản còn lại.

### 08.03.3 — Đề xuất tổ chức lại

```
assets/
  bg/          ← background dùng được, đã chuẩn hoá tên
  char/        ← sprite nhân vật dùng được
  cg/          ← CG tách từ Pack Tổng (sau khi cắt)
  ui/          ← icon, frame (sau khi tạo mới)
refs/          ← 28 bảng Pack Tổng — KHÔNG đưa vào build
```

> 🚨 Không bao giờ đóng gói `refs/` vào bản build. 28 ảnh 1536×1024 ≈ 40–60 MB không dùng.

---

## 08.04 — ASSET CÒN THIẾU

Xếp theo mức độ chặn. **Không tạo gì cả trong danh sách này cho tới khi thoát khỏi Phase 1.**

### 08.04.1 — 🔴 Chặn (không có thì không làm được chương)

| # | Thiếu | Chặn | Lý do |
|---|-------|-------|-------|
| **A1** | **M07 — không gian học tập / thư viện** | L05, L08, V14, A22 | ❌ **Thiếu hoàn toàn — 0 ảnh.** Là route STUDY của Arc 3. Không có thì nhánh E04 không dựng được. |
| **A2** | **`CHAR_ANNIKA`** | A3_C05, A3_C11 | Nhân vật quyết định 2 route lớn mà chưa có ảnh nào |
| **A3** | **M05 — nội thất viện dưỡng lão** | A3_C02, A3_C05 | Chỉ có `bg_office_01`–`bg_office_05` là **văn phòng**. Sảnh, kho thuốc, bếp viện, phòng bệnh, phòng sếp — **không có ảnh nào đúng** |
| **A4** | **Biểu cảm đủ bộ** | 30 CG | F07 cần 3 biến thể · R08 cần 3 · L06 cần 3 composition khác nhau. Hiện có **3** biểu cảm khóc/mệt |

### 08.04.2 — 🟠 Quan trọng

| # | Thiếu | Chặn | Lý do |
|---|-------|-------|-------|
| **B1** | **M04 — quán cà phê** | A2_C04, A2_C06 | Đang dùng `bg_restaurant_01.jpg` tạm — hình bàn ăn, **sai ngữ cảnh** (M04 giờ là điểm kết nối qua màn hình) |
| **B2** | **Trạm xe buýt** | `A1_C07` — Một ngày không ăn | Chương có key moment ở trạm xe buýt, **không có ảnh nào**. Dùng cầu thang máy bay sẽ phá mood |
| **B3** | **M01 — biến thể ban đêm** | Arc 1–2 | Có `bg_free_02_night.png` nhưng chỉ 1 góc. Arc 1–2 chủ yếu diễn vào **ban đêm** |
| **B4** | **Outfit layer** | 13 tổ hợp | Xem 08.02.3 |
| **B5** | **7 ảnh City thiếu biến giờ** | M03, M09 | Xem bảng 08.01.2 |
| **B6** | **Sprite mẹ Dương** | A3_C03, A3_C10 | Có character sheet nhưng chưa có sprite |

### 08.04.3 — 🟡 Nên có

| # | Thiếu | Ghi chú |
|---|-------|---------|
| **C1** | Toàn bộ asset UI | Xem `07_UI_HUD.md` 07.13 — 10 nhóm, **rẻ nhất để tạo, ảnh hưởng lớn nhất** |
| **C2** | Chibi Nam có/không kính | `char_nam_chibi_noglasses.png` tồn tại → chắc chắn cần cả 2 phiên bản |
| **C3** | 2 ảnh `outside` của Spiral Atlas chưa có nét | Xem 08.01.3 |
| **C4** | `bg_bedroom_01`/`02` crop lại 1920 | Xem 08.01.1 |
| **C5** | 30 đạo cụ | `Pack Tổng/06-PROPS PACK` có bản vẽ — cần cắt thành file riêng |

### 08.04.4 — Không cần tạo

| Nhóm | Số | Lý do |
|------|----|-------|
| 28 bảng `Pack Tổng/` | 28 | Chỉ là tham khảo |
| 15 file `__MACOSX/` + 1 `.DS_Store` | 16 | **Đã xoá 02/10/2026** |
| 16 ảnh tài liệu trong `tệp ảnh nhân vật/` | 16 | Không phải asset game — giữ nguyên tên để đối chiếu |

---

## 08.05 — VẤN ĐỀ PHÁP LÝ

### 08.05.1 — 🔴 BẮT BUỘC GHI CREDIT

**11 ảnh Spiral Atlas** được cấp phép **CC BY 4.0**. Điều kiện bắt buộc:

> *Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made.*

| Nội dung | Giá trị |
|----------|--------|
| Tên tác giả | **Spiral Atlas** |
| Năm | **2023** |
| Tên tác giả trang | Spiral Atlas Visual Novel House Backgrounds |
| Link license | `https://creativecommons.org/licenses/by/4.0/` |
| Link credit gốc | `https://spiralatlas.github.io/credits/` |
| Có sửa đổi không? | **Phải ghi rõ** — nếu crop/méo/tint thì ghi "đã chỉnh sửa kích thước/tô màu" |

**→ Bắt buộc tạo `CREDITS.md` ở gốc dự án.** Không có file này là **vi phạm giấy phép**.

### 08.05.2 — 🟠 CHƯA XÁC MINH ĐƯỢC

**138 ảnh còn lại** (149 − 11 ảnh Spiral Atlas) **không có file license nào trong kho.**
Trong đó **94 ảnh dùng được** (43 + 28 + 23) và **44 ảnh tham khảo** (28 + 16).

Tên file cho thấy nhiều nguồn khác nhau: `bg_free_*` (gợi ý miễn phí), `ChatGPT Image …`, `Gemini_Generated_Image_…`, `Copilot_…`.

> ⚠️ **Đây là rủi ro thật, không phải cảnh báo hình thức.**
> - Ảnh AI tạo: điều khoản thương mại phụ thuộc từng nền tảng và thời điểm.
> - Ảnh `bg_free_*`: chữ "free" trong tên **không phải** bằng chứng cấp phép.
> - Tên có khoảng trắng và viết hoa kiểu người dùng tải từ web → rất dễ đến từ asset pack không rõ giấy phép.

**Hành động bắt buộc trước khi phát hành bất kỳ bản nào:**

1. Truy nguồn từng nhóm, lưu lại link + tên tác giả + giấy phép.
2. Với ảnh không tìm được nguồn → **loại khỏi build**, thay bằng ảnh tự vẽ hoặc mua.
3. Cho tới khi xong, **đánh dấu toàn bộ game là dự án học tập, không phát hành.**

> Khuyến nghị thực tế: 28 ảnh `Pack Tổng` và phần lớn `tệp ảnh nhân vật` **nên vẽ lại** bằng AI tạo của chính dự án (có quyền rõ ràng) thay vì truy nguồn từng ảnh. Chất lượng phong cách sẽ đồng nhất hơn là săn tìm giấy phép cho ảnh lệch tông.

---

## 08.06 — QUY ƯỚC ĐẶT TÊN FILE

Tên file cũ không dùng được: tiếng Việt có dấu, khoảng trắng, viết hoa không nhất quán, `FREE_BG`, `ChatGPT Image 20_15_55 21 thg 8, 2026`.

> ✅ **Đã áp dụng ngày 02/10/2026.** 105 asset đã được đổi sang quy ước dưới đây — xem bảng đầy đủ ở **08.09**.
> 44 ảnh tham khảo (`Pack Tổng/` + 16 ảnh trong `tệp ảnh nhân vật/`) **giữ nguyên tên** để còn đối chiếu được với tài liệu gốc.

| Loại | Quy ước | Ví dụ |
|------|---------|-------|
| Background | `bg_<theme>_<nn>[_<time>].<ext>` | `bg_bedroom_03.jpg` · `bg_city_downtown_01_night.png` |
| Background CC BY | `bg_sa_<room>.jpg` | `bg_sa_hallway.jpg` |
| Nhân vật | `char_<id>_<variant>.<ext>` | `char_duong_base.jpg` |
| CG | `cg_<chapter>_<nn>.png` | `cg_a2_c06_01.png` |
| UI | `ui_<element>_<state>.png` | `ui_app_msg_ico.png` |
| VFX | `vfx_<id>_<name>.png` | `vfx_v13_overload.png` |
| Audio | `sfx_<id>_<name>.<ext>` | `sfx_a23_overload_rise.ogg` |

**Quy tắc bắt buộc:**
- Chỉ `a-z`, `0-9`, `_`, `-`.
- Không khoảng trắng. Không dấu. Không ký tự đặc biệt.
- `time ∈ {day, afternoon, night, sunset}`.
- Tiền tố `bg_sa_` = **bắt buộc ghi credit CC BY 4.0**. Xem 08.05.1.
- Tên phải đọc được **không cần mở file**.

> 💡 Vì sao chưa gán `m01`, `m02`… vào tên? Vì **chưa ai xác nhận** ảnh nào thuộc map nào — đó là quyết định của người làm game, không phải suy ra từ tên file cũ. Khi map được chốt, chuyển `bg_<theme>` → `bg_<map>_<room>` bằng một lệnh đổi tên hàng loạt.

---

## 08.07 — THỨ TỰ ƯU TIÊN TẠO ASSET

Kèm theo `02_GAMEPLAY_SYSTEM.md` 02.13.

| Bước | Làm gì | Tại sao trước |
|------|--------|---------------|
| **1** | ~~Chuẩn hoá tên file + dọn `__MACOSX`~~ **✅ xong 02/10** | Không tốn công vẽ, làm sạch mọi việc sau |
| **2** | Tạo `CREDITS.md` | Bắt buộc pháp lý, tốn 15 phút |
| **3** | Asset UI (10 nhóm trong 07.13) | Rẻ nhất, ảnh hưởng lớn nhất |
| **4** | Bổ sung 7 ảnh City còn thiếu | Hoàn thiện hệ thống khung giờ |
| **5** | Vẽ `CHAR_ANNIKA` | Chặn 2 route lớn |
| **6** | Vẽ **M07 thư viện** | Chặn route STUDY — thiếu cả map |
| **7** | Vẽ **M05 viện dưỡng lão** (5 phòng) | Chặn Arc 3 hoàn toàn |
| **8** | Vẽ M04 quán + trạm xe buýt | Chặn 3 chapter |
| **9** | Bổ sung biến thể ban đêm M01 | Arc 1–2 |
| **10** | Outfit layer + biểu cảm đủ bộ | 30 CG |

> 🎯 **Vertical slice chỉ cần bước 1–4.** Đủ để dựng `A1_C01` → `A1_C06` và kiểm chứng toàn bộ hệ thống mà chưa cần vẽ gì mới ngoài UI.

---

## 08.08 — SỐ LIỆU TỔNG KẾT

| Chỉ số | Giá trị |
|--------|---------|
| Tổng số file ảnh trong kho | **149** |
| Ảnh dùng được | **105** (82 background + 23 nhân vật) |
| Ảnh tham khảo | **44** (28 `Pack Tổng` + 16 tài liệu) |
| File rác | **16** — **đã xoá 02/10/2026** |
| Đã đổi tên chuẩn | **105** — git nhận `R100` |
| Ảnh sai tỉ lệ | **2** (`bg_bedroom_01`, `bg_bedroom_02`) |
| Map cần có | **10** — thiếu hẳn **1** (M07), thiếu nội thất **2** (M04, M05) |
| Nhân vật cần có | **5** — thiếu **2** (Annika, mẹ Dương) |
| Có license rõ ràng | **11** (CC BY 4.0) |
| **Chưa xác minh license** | **138** ⚠️ |
| Asset chặn tiến độ | **4** |

## 08.09 — PHỤ LỤC: BẢNG ĐỔI TÊN FILE

Toàn bộ 105 asset đã được đổi tên ngày **02/10/2026**. Bảng dưới giữ lại tên cũ để nhận ra asset khi đối chiếu với tài liệu gốc hoặc Pack Tổng/.

> Git ghi nhận **105/105 là R100** — đổi tên thuần, không thay đổi nội dung ảnh.

### tệp ảnh background — 82 file

| Tên cũ | Tên mới |
|--------|---------|
| `Downtown 1 Afternoon.png` | `bg_city_downtown_01_afternoon.png` |
| `Downtown 1 Day.png` | `bg_city_downtown_01_day.png` |
| `Downtown 1 Night Light.png` | `bg_city_downtown_01_night.png` |
| `Downtown 2 Afternoon.png` | `bg_city_downtown_02_afternoon.png` |
| `Downtown 2 Day.png` | `bg_city_downtown_02_day.png` |
| `Downtown 2 Night Light.png` | `bg_city_downtown_02_night.png` |
| `Downtown 3 Afternoon.png` | `bg_city_downtown_03_afternoon.png` |
| `Downtown 3 Day.png` | `bg_city_downtown_03_day.png` |
| `Downtown 3 Night Light.png` | `bg_city_downtown_03_night.png` |
| `Neighborhood 1 Afternoon.png` | `bg_city_neighborhood_01_afternoon.png` |
| `Neighborhood 1 Day.png` | `bg_city_neighborhood_01_day.png` |
| `Neighborhood 2 Afternoon.png` | `bg_city_neighborhood_02_afternoon.png` |
| `Neighborhood 2 Day.png` | `bg_city_neighborhood_02_day.png` |
| `Neighborhood 2 Night Light.png` | `bg_city_neighborhood_02_night.png` |
| `Neighborhood 3 Afternoon.png` | `bg_city_neighborhood_03_afternoon.png` |
| `Neighborhood 3 Day.png` | `bg_city_neighborhood_03_day.png` |
| `Neighborhood 3 Night Light.png` | `bg_city_neighborhood_03_night.png` |
| `Park 1 Afternoon.png` | `bg_city_park_01_afternoon.png` |
| `Park 1 Day.png` | `bg_city_park_01_day.png` |
| `Park 1 Night Light.png` | `bg_city_park_01_night.png` |
| `Park 2 Night Light.png` | `bg_city_park_02_night.png` |
| `Park 3 Afternoon.png` | `bg_city_park_03_afternoon.png` |
| `Park 3 Day.png` | `bg_city_park_03_day.png` |
| `Park 3 Night Light.png` | `bg_city_park_03_night.png` |
| `Playground 3 Day.png` | `bg_city_playground_03_day.png` |
| `Sky Afternoon Day.png` | `bg_city_sky_afternoon.png` |
| `Sky Day Day.png` | `bg_city_sky_day.png` |
| `Sky Night Day.png` | `bg_city_sky_night.png` |
| `bedroom 1.jpg` | `bg_bedroom_01.jpg` |
| `bedroom 2.jpg` | `bg_bedroom_02.jpg` |
| `bedroom 3.jpg` | `bg_bedroom_03.jpg` |
| `bedroom 4.jpg` | `bg_bedroom_04.jpg` |
| `bedroom 5.jpg` | `bg_bedroom_05.jpg` |
| `bedroom 6.jpg` | `bg_bedroom_06.jpg` |
| `bedroom 7.jpg` | `bg_bedroom_07.jpg` |
| `Kitchen 1.jpg` | `bg_kitchen_01.jpg` |
| `kitchen 2.jpg` | `bg_kitchen_02.jpg` |
| `kitchen 3.jpg` | `bg_kitchen_03.jpg` |
| `kitchen 4.jpg` | `bg_kitchen_04.jpg` |
| `office 1.jpg` | `bg_office_01.jpg` |
| `office 2.jpg` | `bg_office_02.jpg` |
| `office 3.jpg` | `bg_office_03.jpg` |
| `office 4.jpg` | `bg_office_04.jpg` |
| `office 5.jpg` | `bg_office_05.jpg` |
| `street 1.jpg` | `bg_street_01.jpg` |
| `street 2.jpg` | `bg_street_02.jpg` |
| `street 3.jpg` | `bg_street_03.jpg` |
| `street 4.jpg` | `bg_street_04.jpg` |
| `train 1.jpg` | `bg_train_01.jpg` |
| `train 2.jpg` | `bg_train_02.jpg` |
| `train 3.jpg` | `bg_train_03.jpg` |
| `inside train 1.jpg` | `bg_train_interior_01.jpg` |
| `clothing shop 1.jpg` | `bg_clothing_shop_01.jpg` |
| `clothing shop blur 1.jpg` | `bg_clothing_shop_blur_01.jpg` |
| `restaurant 1.jpg` | `bg_restaurant_01.jpg` |
| `mall 1.jpg` | `bg_mall_01.jpg` |
| `mall 2.jpg` | `bg_mall_02.jpg` |
| `cherry street 1.jpg` | `bg_cherry_street_01.jpg` |
| `cherry street blur 1.jpg` | `bg_cherry_street_blur_01.jpg` |
| `garden blur 1.jpg` | `bg_garden_blur_01.jpg` |
| `garden blur 2.jpg` | `bg_garden_blur_02.jpg` |
| `dawn beach 1.jpg` | `bg_dawn_beach_01.jpg` |
| `onsen 1.jpg` | `bg_onsen_01.jpg` |
| `onsen 3.jpg` | `bg_onsen_03.jpg` |
| `onsen blur 1.jpg` | `bg_onsen_blur_01.jpg` |
| `train station 1.jpg` | `bg_train_station_01.jpg` |
| `FREE_BG_1.png` | `bg_free_01.png` |
| `FREE_BG_2.png` | `bg_free_02.png` |
| `FREE_BG_2_night.png` | `bg_free_02_night.png` |
| `FREE_BG_2_sunset.png` | `bg_free_02_sunset.png` |
| `FREE_BG_3.png` | `bg_free_03.png` |
| `entrance.jpg` | `bg_sa_entrance.jpg` |
| `hallway.jpg` | `bg_sa_hallway.jpg` |
| `dining.jpg` | `bg_sa_dining.jpg` |
| `dining_kitchen.jpg` | `bg_sa_dining_kitchen.jpg` |
| `kitchen.jpg` | `bg_sa_kitchen.jpg` |
| `lounge.jpg` | `bg_sa_lounge.jpg` |
| `bathroom.jpg` | `bg_sa_bathroom.jpg` |
| `master bedroom.jpg` | `bg_sa_master_bedroom.jpg` |
| `single bedroom.jpg` | `bg_sa_single_bedroom.jpg` |
| `outside1.jpg` | `bg_sa_outside_01.jpg` |
| `outside2.jpg` | `bg_sa_outside_02.jpg` |

### tệp ảnh nhân vật — 23 file

| Tên cũ | Tên mới |
|--------|---------|
| `Dương.jpg` | `char_duong_base.jpg` |
| `Dương quàn áo thường ngày.png` | `char_duong_daily_outfit.png` |
| `Dương khóc.jpg` | `char_duong_crying.jpg` |
| `Dáng đứng của dương.png` | `char_duong_standing.png` |
| `chibi Dương.png` | `char_duong_chibi_01.png` |
| `chibi Dương 3.jpg` | `char_duong_chibi_02.jpg` |
| `chuyển động của chibi dương.jpg` | `char_duong_chibi_anim.jpg` |
| `Chuyển động của dương.jpg` | `char_duong_anim.jpg` |
| `Minh.jpg` | `char_minh_base.jpg` |
| `chibi minh.png` | `char_minh_chibi_01.png` |
| `chibi minh 3.jpg` | `char_minh_chibi_02.jpg` |
| `chuyển động của chibi minh.jpg` | `char_minh_chibi_anim.jpg` |
| `Chuyển động của minh.jpg` | `char_minh_anim.jpg` |
| `Nam.jpg` | `char_nam_base.jpg` |
| `chibi nam.png` | `char_nam_chibi_01.png` |
| `chibi nam 3.jpg` | `char_nam_chibi_02.jpg` |
| `chibi nam ko kính.png` | `char_nam_chibi_noglasses.png` |
| `chuyển động của chibi nam.jpg` | `char_nam_chibi_anim.jpg` |
| `Chuyển động của nam.jpg` | `char_nam_anim.jpg` |
| `Nhân vật Dương.png` | `char_duong_sheet.png` |
| `Nhân vật Minh.png` | `char_minh_sheet.png` |
| `Nhân vật Nam.png` | `char_nam_sheet.png` |
| `09-EVENT_CG_PACK_03_LIFE_WORK_STUDY (bản tóc đen).png` | `char_duong_cg_pack03_blackhair.png` |

---

**TIẾP** → `09_SYSTEM_VARIABLES.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
