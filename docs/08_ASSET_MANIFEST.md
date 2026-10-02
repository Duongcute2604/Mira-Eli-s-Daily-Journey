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

**Ngoài ra:** `tệp ảnh background/__MACOSX/` chứa **15 file rác** (AppleDouble) — không phải 14 như ghi trong tài liệu gốc.

> 🚨 **Kết luận quan trọng:** kho có **105 ảnh dùng được** nhưng thiếu hẳn **một số map cốt lõi**. Chi tiết 08.04.

---

## 08.01 — BACKGROUND

### 08.01.1 — `tệp ảnh background/` — 43 ảnh

| Phân loại | Số | Tên file |
|-----------|----|---------|
| Phòng ngủ | 7 | `bedroom 1` … `bedroom 7` |
| Bếp | 5 | `Kitchen 1`, `kitchen 2` … `kitchen 4` |
| Văn phòng | 5 | `office 1` … `office 5` |
| Đường phố | 4 | `street 1` … `street 4` |
| Tàu hỏa | 4 | `train 1` … `train 3`, `inside train 1` |
| Cửa hàng / quán | 3 | `clothing shop 1`, `restaurant 1`, `mall 1`–`2` |
| Đường hoa anh đào | 2 | `cherry street 1`, `cherry street blur 1` |
| Vườn | 2 | `garden blur 1`, `garden blur 2` |
| Bãi biển | 1 | `dawn beach 1` |
| Onsen | 3 | `onsen 1`, `onsen 3`, `onsen blur 1` |
| Sân ga | 1 | `train station 1` |
| PNG miễn phí | 5 | `FREE_BG_1`, `FREE_BG_2`, `FREE_BG_2_night`, `FREE_BG_2_sunset`, `FREE_BG_3` |

**Kích thước thật:**

| Kích thước | Số | Đánh giá |
|-----------|----|---------|
| **1920×1080** | 41 | ✅ Đúng 16:9, dùng được ngay |
| **1619×1080** | 2 | ⚠️ `bedroom 1.jpg`, `bedroom 2.jpg` — tỉ lệ 1.5, **sẽ méo** trên canvas 16:9 |

> ⚠️ **Xử lý `bedroom 1` / `bedroom 2`:** canvas game là 1920×1080. Đặt 1619×1080 lên sẽ bị kéo ngang. Phải chọn một trong hai:
> (a) crop cắt ngang về 1920 — mất 301px ở cạnh, chấp nhận được vì nội dung phòng ngủ thường ở giữa;
> (b) thêm viền/padding bằng nền trung tính.
> **Không được** để nguyên rồi ép tỉ lệ — sẽ làm méo đồ vật trong phòng.

> 💡 **Điểm tốt:** nhóm `FREE_BG_2` đã có sẵn **3 biến thể** (ngày / hoàng hôn / đêm). Đây là nguồn tài nguyên có sẵn cho hệ thống `TIME_BLOCK` — nên dùng cho M01.

### 08.01.2 — `tệp ảnh background/City/` — 28 ảnh

**Đây là nhóm asset có giá trị nhất trong kho.** Không phải vì đẹp, mà vì nó **đã được dựng sẵn theo khung giờ**.

Tất cả 28 ảnh đều **1920×1080** — đúng chuẩn, không cần xử lý.

| Địa điểm | Day | Afternoon | Night Light | Thiếu |
|-----------|-----|-----------|-------------|-------|
| Downtown 1 | ✅ | ✅ | ✅ | — |
| Downtown 2 | ✅ | ✅ | ✅ | — |
| Downtown 3 | ✅ | ✅ | ✅ | — |
| Neighborhood 1 | ✅ | ❌ | ❌ | **thiếu 2** |
| Neighborhood 2 | ✅ | ❌ | ✅ | **thiếu 1** |
| Neighborhood 3 | ✅ | ✅ | ✅ | — |
| Park 1 | ✅ | ✅ | ✅ | — |
| Park 2 | ❌ | ❌ | ✅ | **thiếu 2** |
| Park 3 | ✅ | ✅ | ✅ | — |
| Playground 3 | ✅ | ❌ | ❌ | **thiếu 2** |
| Sky | ✅ | ✅ | ✅ | — |

**Đọc được từ cấu trúc tên file:** `Downtown 1 Night Light.png` = cùng một góc phố, khung NIGHT.

> 🎯 **Cơ hội thiết kế:** `02_GAMEPLAY_SYSTEM.md` 02.07 định nghĩa 4 khung giờ. `City/` cho ta map ngoài trời **miễn phí** 3/4 biến thể. Đừng vẽ thêm background thành phố — hãy dùng bộ này và chỉ bổ sung 7 ảnh còn thiếu.

**Bổ sung cần thiết (7 ảnh):**

| Thiếu | Tại sao quan trọng |
|-------|-------------------|
| Neighborhood 1 Afternoon | Arc 1 hay dùng Neighborhood 1 |
| Neighborhood 1 Night Light | Arc 2 (phần lớn ban đêm) |
| Neighborhood 2 Afternoon | chuyển khung giờ |
| Park 2 Day + Afternoon | Park 2 giờ chỉ có Night → không dùng được giữa ngày |
| Playground 3 Afternoon + Night | tương tự |

### 08.01.3 — `Spiral Atlas VN House Backgrounds/` — 11 ảnh

Tất cả **1920×1080**. Nội dung:

| File | Nội dung |
|------|----------|
| `entrance.jpg` | cửa ra vào |
| `hallway.jpg` | hành lang |
| `dining.jpg` | phòng ăn |
| `dining_kitchen.jpg` | phòng ăn liền bếp |
| `kitchen.jpg` | bếp |
| `lounge.jpg` | phòng khách |
| `bathroom.jpg` | phòng tắm |
| `master bedroom.jpg` | phòng ngủ chính |
| `single bedroom.jpg` | phòng ngủ đơn |
| `outside1.jpg` | ngoài nhà biến 1 |
| `outside2.jpg` | ngoài nhà biến 2 |

Kèm 2 file văn bản: `license.txt`, `Credits and Information.txt` — **giữ nguyên, không xoá**.

> ⚠️ **Vấn đề phong cách — nghiêm trọng hơn vấn đề license.**
> Nhóm này vẽ kiểu **toon-shaded / cel-shaded**. Nhóm `tệp ảnh background/` (43 ảnh) vẽ kiểu **semi-realistic mềm**. Trộn hai kiểu trong cùng một map nhà sẽ nhìn ra ngay.
>
> **Khuyến nghị:** dùng `Spiral Atlas` cho **M02 (hành lang)** và phần `outside` — là nơi chuyển cảnh, người chơi không soi kỹ. **Không** dùng cho phòng ngủ hoặc bếp nơi người chơi ở lâu, vì sẽ đụng hàng với `bedroom 1–7` và `kitchen 1–4`.

> ⚠️ **Vấn đề chất lượng (ghi trong file gốc của tác giả):**
> `Credits and Information.txt` nói rõ: *"Note: Outside1 and Outside2 do not currently have lines."* — 2 ảnh ngoài nhà **chưa có đường nét**. Về mặt pháp lý OK, về mặt thẩm mỹ thì dễ bị phê phán. Cân nhắc dùng `outside1` thôi, hoặc dùng làm base để vẽ lại.

### 08.01.4 — Bảng ánh xạ Background → Map

Dựa trên `03_MAP_EVENT_FLOW.md`.

| Map | Tên | Ảnh được chỉ định | Tình trạng |
|-----|-----|------------------|-----------|
| **M01** | Nhà Dương — phòng ngủ | `bedroom 3`–`bedroom 7` | ✅ có |
| **M01** | Nhà Dương — bếp | `kitchen 2`–`kitchen 4` | ✅ có |
| **M01** | Nhà Dương — phòng khách | `lounge.jpg` (Spiral) | ⚠️ lệch phong cách |
| **M01** | Nhà Dương — **biến thể ban đêm** | `FREE_BG_2_night.png` | ❌ **thiếu bản riêng cho từng phòng** |
| **M02** | Hành lang | `hallway.jpg` (Spiral) | ✅ có |
| **M02** | Cửa ra vào | `entrance.jpg` (Spiral) | ✅ có |
| **M03** | Đường / khu phố | `street 1`–`4`, `cherry street 1` | ✅ có |
| **M03** | Khu phố (biến giờ) | `City/Neighborhood *` | ✅ có, thiếu 2 ảnh |
| **M04** | **Điểm kết nối** (quán) | `restaurant 1.jpg` | ⚠️ **đang dùng nhầm tạm** |
| **M05** | **Viện dưỡng lão** | `office 1`–`office 5` | ⚠️ **văn phòng ≠ viện dưỡng** |
| **M06** | Phòng họp / phòng sếp | `office 5` | ⚠️ dùng chung với M05 |
| **M07** | **Thư viện / không gian học tập** | — | ❌ **THIẾU HOÀN TOÀN** |
| **M08** | **Sân ga** | `train station 1.jpg` | ⚠️ chỉ 1 góc, không có biến giờ |
| **M08** | Trạm xe buýt | — | ❌ **thiếu** |
| **M09** | Công viên | `City/Park *`, `garden blur *` | ✅ có |
| **M09** | Bãi biển | `dawn beach 1.jpg` | ✅ có |
| **M09** | Onsen | `onsen 1`, `onsen 3` | ✅ có |
| **M10** | Không gian mở cuối cùng | `Sky *.png` | ✅ có |

---

## 08.02 — NHÂN VẬT

### 08.02.1 — `tệp ảnh nhân vật/` — 39 file

| Phân loại | Số | Kích thước |
|-----------|-----|-----------|
| Ảnh nhân vật **dùng được** | 20 | 1024×1536 đến 2048×2048 |
| Tài liệu / bảng tổng hợp | 19 | 800×800 đến 1536×1024 |

**Ảnh dùng được (20):**

| Nhân vật | File | Loại |
|----------|------|-----|
| **Dương** | `Dương.jpg`, `Dương quàn áo thường ngày.jpg`, `Dương khóc.jpg`, `Nhân vật Dương.png`, `Dáng đứng của dương.png` | sprite + biểu cảm |
| **Dương (chibi)** | `chibi Dương.png`, `chibi Dương 3.jpg`, `chuyển động của chibi dương.jpg` | chibi + động |
| **Dương (chuyển động)** | `Chuyển động của dương.jpg`, `09-EVENT_CG_PACK_03_LIFE_WORK_STUDY (bản tóc đen).png` | CG/event |
| **Minh** | `Minh.jpg`, `Nhân vật Minh.png` | sprite |
| **Minh (chibi)** | `chibi minh.png`, `chibi minh 3.jpg`, `chuyển động của chibi minh.jpg` | chibi + động |
| **Minh (chuyển động)** | `Chuyển động của minh.jpg` | CG/event |
| **Nam** | `Nam.jpg`, `Nhân vật Nam.png` | sprite |
| **Nam (chibi)** | `chibi nam.png`, `chibi nam 3.jpg`, `chibi nam ko kính.jpg`, `chuyển động của chibi nam.jpg` | chibi + động |
| **Nam (chuyển động)** | `Chuyển động của nam.jpg` | CG/event |

**Tài liệu tham khảo (19):** `1.1`–`1.8.png`, `Character Sheet cho Nam + Minh (bản lỗi).png`, `Bảng tài nguyên tổng hợp.png`, `cuộc trò chuyện.png`, và 7 ảnh tên tự sinh (`ChatGPT Image …`, `Copilot_…`, `Gemini_Generated_Image_…`).

### 08.02.2 — ⚠️ Ba vấn đề nghiêm trọng

| # | Vấn đề | Hệ quả |
|---|--------|--------|
| **1** | **Có 2 phiên bản tóc Dương** — `09-EVENT_CG_PACK_03_... (bản tóc đen).png` và các ảnh Dương còn lại | Chưa chốt bản chuẩn. Nếu không chốt, sẽ có 2 Dương khác nhau trong cùng game |
| **2** | **`Character Sheet cho Nam + Minh (bản lỗi).png`** — chính tên file ghi "bản lỗi" | Dùng làm chuẩn tham chiếu sẽ **nhân bản cả lỗi**. Phải tìm bản đúng ở `Pack Tổng/01-Character Sheet cho Nam + Minh.png` |
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
| **A3** | **M05 — nội thất viện dưỡng lão** | A3_C02, A3_C05 | Chỉ có `office 1–5` là **văn phòng**. Sảnh, kho thuốc, bếp viện, phòng bệnh, phòng sếp — **không có ảnh nào đúng** |
| **A4** | **Biểu cảm đủ bộ** | 30 CG | F07 cần 3 biến thể · R08 cần 3 · L06 cần 3 composition khác nhau. Hiện có **3** biểu cảm khóc/mệt |

### 08.04.2 — 🟠 Quan trọng

| # | Thiếu | Chặn | Lý do |
|---|-------|-------|-------|
| **B1** | **M04 — quán cà phê** | A2_C04, A2_C06 | Đang dùng `restaurant 1.jpg` tạm — hình bàn ăn, **sai ngữ cảnh** (M04 giờ là điểm kết nối qua màn hình) |
| **B2** | **Trạm xe buýt** | `A1_C07` — Một ngày không ăn | Chương có key moment ở trạm xe buýt, **không có ảnh nào**. Dùng cầu thang máy bay sẽ phá mood |
| **B3** | **M01 — biến thể ban đêm** | Arc 1–2 | Có `FREE_BG_2_night` nhưng chỉ 1 góc. Arc 1–2 chủ yếu diễn vào **ban đêm** |
| **B4** | **Outfit layer** | 13 tổ hợp | Xem 08.02.3 |
| **B5** | **7 ảnh City thiếu biến giờ** | M03, M09 | Xem bảng 08.01.2 |
| **B6** | **Sprite mẹ Dương** | A3_C03, A3_C10 | Có character sheet nhưng chưa có sprite |

### 08.04.3 — 🟡 Nên có

| # | Thiếu | Ghi chú |
|---|-------|---------|
| **C1** | Toàn bộ asset UI | Xem `07_UI_HUD.md` 07.13 — 10 nhóm, **rẻ nhất để tạo, ảnh hưởng lớn nhất** |
| **C2** | Chibi Nam có/không kính | `chibi nam ko kính.png` tồn tại → chắc chắn cần cả 2 phiên bản |
| **C3** | 2 ảnh `outside` của Spiral Atlas chưa có nét | Xem 08.01.3 |
| **C4** | `bedroom 1`/`bedroom 2` crop lại 1920 | Xem 08.01.1 |
| **C5** | 30 đạo cụ | `06-PROPS PACK` có bản vẽ — cần cắt thành file riêng |

### 08.04.4 — Không cần tạo

| Nhóm | Lý do |
|------|-------|
| 28 bảng `Pack Tổng/` | Chỉ là tham khảo |
| 15 file `__MACOSX/` | Rác |
| `.DS_Store` | Rác |
| 7 ảnh tên tự sinh trong `tệp ảnh nhân vật/` | Không xác định được nội dung → giữ ở `refs/`, không dùng |

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

**110 ảnh còn lại** (43 + 28 + 39) **không có file license nào trong kho.**

Tên file cho thấy nhiều nguồn khác nhau: `FREE_BG_*` (gợi ý miễn phí), `ChatGPT Image …`, `Gemini_Generated_Image_…`, `Copilot_…`.

> ⚠️ **Đây là rủi ro thật, không phải cảnh báo hình thức.**
> - Ảnh AI tạo: điều khoản thương mại phụ thuộc từng nền tảng và thời điểm.
> - Ảnh `FREE_BG_*`: chữ "FREE" trong tên **không phải** bằng chứng cấp phép.
> - Tên có khoảng trắng và viết hoa kiểu người dùng tải từ web → rất dễ đến từ asset pack không rõ giấy phép.

**Hành động bắt buộc trước khi phát hành bất kỳ bản nào:**

1. Truy nguồn từng nhóm, lưu lại link + tên tác giả + giấy phép.
2. Với ảnh không tìm được nguồn → **loại khỏi build**, thay bằng ảnh tự vẽ hoặc mua.
3. Cho tới khi xong, **đánh dấu toàn bộ game là dự án học tập, không phát hành.**

> Khuyến nghị thực tế: 28 ảnh `Pack Tổng` và phần lớn `tệp ảnh nhân vật` **nên vẽ lại** bằng AI tạo của chính dự án (có quyền rõ ràng) thay vì truy nguồn từng ảnh. Chất lượng phong cách sẽ đồng nhất hơn là săn tìm giấy phép cho ảnh lệch tông.

---

## 08.06 — QUY ƯỚC ĐẶT TÊN FILE

Tên file hiện tại không dùng được: tiếng Việt có dấu, khoảng trắng, viết hoa không nhất quán, `FREE_BG`, `ChatGPT Image 20_15_55 21 thg 8, 2026`.

| Loại | Quy ước | Ví dụ |
|------|---------|-------|
| Background | `bg_<map>_<room>_<time>.png` | `bg_m01_bedroom_night.png` |
| Nhân vật | `char_<id>_<outfit>_<exp>.png` | `char_duong_casual_tired.png` |
| CG | `cg_<chapter>_<nn>.png` | `cg_a2_c06_01.png` |
| UI | `ui_<element>_<state>.png` | `ui_app_msg_ico.png` |
| VFX | `vfx_<id>_<name>.png` | `vfx_v13_overload.png` |
| Audio | `sfx_<id>_<name>.<ext>` | `sfx_a23_overload_rise.ogg` |

**Quy tắc bắt buộc:**
- Chỉ `a-z`, `0-9`, `_`, `-`.
- Không khoảng trắng. Không dấu. Không ký tự đặc biệt.
- `time ∈ {day, afternoon, night, blank}`.
- Tên phải đọc được **không cần mở file**.

---

## 08.07 — THỨ TỰ ƯU TIÊN TẠO ASSET

Kèm theo `02_GAMEPLAY_SYSTEM.md` 02.13.

| Bước | Làm gì | Tại sao trước |
|------|--------|---------------|
| **1** | Chuẩn hoá tên file + dọn `__MACOSX` | Không tốn công vẽ, làm sạch mọi việc sau |
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
| Ảnh dùng được | **121** |
| Bảng tham khảo | **28** |
| File rác (`__MACOSX`) | **15** + 1 `.DS_Store` |
| Ảnh sai tỉ lệ | **2** (`bedroom 1`, `bedroom 2`) |
| Map cần có | **10** — thiếu hẳn **1**, thiếu nội thất **2** |
| Nhân vật cần có | **5** — thiếu **2** |
| Có license rõ ràng | **11** (CC BY 4.0) |
| **Chưa xác minh license** | **110** ⚠️ |
| Asset chặn tiến độ | **4** |

---

**TIẾP** → `09_SYSTEM_VARIABLES.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
