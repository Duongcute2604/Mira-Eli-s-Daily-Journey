# TODO — Hành Trình Của Mira Eli

> Ngày audit: 02/10/2026
> Trạng thái: **Phase 0 — Design complete, chưa có code**

---

## 0. QUY TRÌNH (áp dụng từ bước này trở đi)

Mỗi task mới phải đi qua 6 bước, không bỏ bước nào:

1. Viết kế hoạch cụ thể vào `todo.md` (mục tiêu phải đo được)
2. Kiểm tra lại kế hoạch
3. Làm xong mục nào đánh dấu mục đó `[x]`
4. Mỗi thay đổi phải có giải thích rõ ràng
5. Ghi kết quả vào `todo.md`
6. Tổng kết bài học vào `lessons.md`

Nguyên lý: **Tối giản** — chỉ đổi cái cần thiết. **Triệt để** — giải quyết tận gốc, không vá tạm. **Vô hình** — sửa đúng chỗ, không phát sinh lỗi mới.

---

## 1. KẾT QUẢ AUDIT LẦN 1 — ĐỌC TOÀN BỘ TÀI LIỆU

### 1.1. Phạm vi đã đọc

| # | File | Dòng | Nội dung |
|---|------|------|----------|
| 1 | `README.md` | 134 | Intro game, 3 nhân vật trung tâm, tôn vinh cá nhân |
| 2 | `Cốt truyện/Cốt truyện Hành Trình Của Mira Eli.docx` | 481 | **Thiết kế G1** — pitch gốc, premise Thụy Điển, nợ 8 tỷ |
| 3 | `Cốt truyện/Hanh_Trinh_Cua_Mira_Eli_Tong_Hop_Du_An.docx` | 243 | **Thiết kế G1** — tổng hợp ý tưởng web game, 4 chỉ số, 15 background |
| 4 | `Cốt truyện/01_STORY_PACK.docx` | 590 | **Thiết kế G2** — 31 chương, 3 arc |
| 5 | `Cốt truyện/02_GAMEPLAY_SYSTEM_IMPLEMENTATION_PACK.docx` | 223 | **G2** — core loop, chapter template, build order |
| 6 | `Cốt truyện/03_MAP_EVENT_FLOW_PACK.docx` | 684 | **G2** — 10 map (M01–M10), trigger, chapter→map |
| 7 | `Cốt truyện/04_CG_EVENT_PLACEMENT_PACK.docx` | 667 | **G2** — 30 CG (F/R/L01–10) |
| 8 | `Cốt truyện/05_VFX_AUDIO_EVENT_PLACEMENT_PACK.docx` | 661 | **G2** — 20 VFX + 30 audio cue |
| 9 | `Cốt truyện/09_SYSTEM_VARIABLES_PACK.docx` | 242 | **G2** — 24 object narrative state |
| 10 | `Cốt truyện/10_CHOICE_BRANCHING_PACK.docx` | 407 | **G2** — 20 choice |
| 11 | `Cốt truyện/11_ENDING_PACK.docx` | 312 | **G2** — 9 ending E01–E09 + resolver |
| 12 | `Cốt truyện/GAME_FLOW_STORY_FLOW_DETAILED_STORY_BIBLE.docx` | 538 | **G2-bien thể** — 10 stat + ngưỡng ending số |
| 13 | `tệp ảnh background/.../license.txt` | — | CC BY 4.0 (Spiral Atlas) |
| 14 | `tệp ảnh background/.../Credits and Information.txt` | — | Nguồn ảnh: Blender + Clip Studio |

**Tổng: 11 file .docx + 2 file .txt + 149 file ảnh đã kiểm kê metadata.**
Phương pháp đọc: giải nén `word/document.xml` bằng .NET `System.IO.Compression`, giữ `<w:p>` → newline, `<w:tab>/<w:tc>` → tab, bỏ tag, decode entity.

- [x] Đọc hết tài liệu
- [x] Kiểm kê asset (149 ảnh, đo kích thước thật)
- [x] Đối chiếu tài liệu ↔ asset
- [x] Phát hiện mâu thuẫn nội bộ

---

## 2. TÓM TẮT DỰ ÁN

**Tên:** Hành Trình Của Mira Eli / Mira-Eli's Daily Journey
**Thể loại:** Mô phỏng đời sống + narrative (web game / đồ án)
**Chủ đề:** Không có quái vật, không có vương quốc, không có đáp án hoàn hảo — chỉ có người và những ngày bình thường.

**Nhân vật chính:**

| NV | Tên thật | Sinh | Vị trí |
|----|----------|------|--------|
| Dương (Mira Eli) | Dương, QĐ bị đổi tên khi nhập cư | 2003 | Nữ chính — điều dưỡng, gánh vác, giữ mọi thứ |
| Nam | Nam | 2004 | Bạn trai yêu xa, SV CNTT, muốn học thạc sĩ để sang Thụy Điển |
| Minh | Minh | 2006 | Em gái, mơ ước trở thành bác sĩ/nhà nghiên cứu |

**Chủ đề trung tâm:** *"Trưởng thành không phải giữ được tất cả, mà là biết điều gì quan trọng và biết khi nào cần nhờ người khác."*

**Master flow:** `PROLOGUE → ARC 1: FAMILY → ARC 2: ROMANCE → ARC 3: LIFE/WORK/STUDY → FINAL REFLECTION → ENDINGS`

---

## 3. HỆ THỐNG GHI CHÚ

### 3.1. Có 2 thế hệ thiết kế cùng tồn tại (⚠️ VẤN ĐỀ LỚN NHẤT)

| | **G1 (2 file cũ)** | **G2 (9 file Pack)** |
|---|---|---|
| Triết lý | Mô phỏng đời sống, quản lý chỉ số | Narrative-first, chỉ số ẩn |
| Chỉ số | 4 cái, hiện HUD: Sức khỏe, Tài chính, Học tập, Tình cảm | 7 Persistent + 5 Route State + 12 Flag = **24 object, không hiện HUD** |
| Ending | 4 (có hậu / trung tính / tiêu cực / đặc biệt) | 9 (E01–E09) |
| Setting | Thụy Điển, nợ 8 tỷ, viện dưỡng lão, sếp nữ 45 tuổi, minigame y tế | Không còn Thụy Điển/nợ 8 tỷ/viện dưỡng trong lore. Tập trung **overload / gánh vác / giao tiếp** |
| Bối cảnh | Chưa quy chiếu | M01–M10 tái sử dụng, 4 time block |
| Gameplay | Explore + quản lý tài chính + 2–3 minigame | Chỉ Explore → Interact → Dialogue → Choice |

**Kết luận:** G2 là bản thiết kế **chất lượng cao hơn nhiều** (có ID chuẩn, có trigger, có resolver, có priority matrix) nhưng **đã thay đổi hoàn toàn premise gốc**. G1 chứa toàn bộ setting hấp dẫn mà G2 đã bỏ.

### 3.2. Có 3 bộ stat model khác nhau ⚠️

| Nguồn | Số biến | Tên biến |
|-------|---------|----------|
| G1 (`Hanh_Trinh...Tong_Hop`) | 4 | Sức khỏe, Tài chính, Học tập, Tình cảm |
| **G2 canonical** (`09_SYSTEM_VARIABLES`) | 24 | 7 Persistent: `FAMILY_TRUST, ROMANCE_TRUST, SELF_AWARENESS, OVERLOAD, CAREER_FOCUS, STUDY_FOCUS, CONNECTION_FOCUS` + 5 Route State: `FAMILY_STATE, ROMANCE_STATE, PRIORITY_STATE, FINAL_ORIENTATION, BREAKING_POINT_STATE` + 12 Flag: `FLAG_SHARED_WORK, FLAG_FAMILY_TRUTH, FLAG_ACCEPTED_HELP, FLAG_CONTACTED_NAM, FLAG_ROMANCE_HONESTY, FLAG_COMMIT_TO_NAM, FLAG_WORK_OPPORTUNITY, FLAG_STUDY_ROUTE, FLAG_CHOSE_BALANCE, FLAG_ADMITTED_OVERLOAD, FLAG_LET_MINH_GO, FLAG_LET_NAM_GO` |
| G2-biến thể (`STORY_BIBLE`) | 18 | `FAMILY, ROMANCE, TRUST, OPENNESS, RESPONSIBILITY, WORK, STUDY, BALANCE, STRESS, ENERGY` + 8 flag |

→ **Phải chọn 1.** Đề xuất: lấy `09_SYSTEM_VARIABLES` làm canonical (nó có quy tắc cập nhật + resolver + UI visibility), map `STORY_BIBLE` vào làm delta cụ thể.

### 3.3. Ending resolver (đã có ngưỡng số ở STORY_BIBLE)

```
E08 Too Late to Rest    : STRESS>=95 AND ENERGY<=10 AND REST_HISTORY thấp
E06 Carries Everything  : RESPONSIBILITY>=85 AND OPENNESS<40 AND REST thấp
E05 Letting Go          : ROMANCE<40 OR SEPARATION=TRUE
E01 A Life of Her Own   : BALANCE>=75 AND OPENNESS>=70 AND STRESS<65 AND FAMILY>=65 AND (WORK>=60 OR STUDY>=60)
E02 Together Despite...  : ROMANCE>=85 AND TRUST>=75 AND COMMITMENT=TRUE AND STRESS<80
E03 The Promotion       : WORK>=90 AND CAREER_CHOICE=TRUE AND STRESS<85
E04 The Next Step       : STUDY>=90 AND FAMILY>=65
E07 Starting Over       : SELF_ROUTE=TRUE AND OPENNESS>=60
E09 Balanced / Neutral  : fallback
```

Priority: `E08 > E06 > E05 > E01 > E02 > E03 > E04 > E07 > E09`

---

## 4. KIỂM KÊ ASSET (đo thật, không ước lượng)

**Tổng: 149 file ảnh.**

| Nhóm | Số lượng | Ghi chú |
|------|----------|---------|
| Background 16:9 chuẩn 1920×1080 | 80 | Đạt chuẩn đề xuất 1920×1080 |
| Background tỉ lệ 1.5 | 34 | `bedroom 1`, `bedroom 2` (1619×1080) lệch chuẩn |
| Ảnh nhân vật | 22 | Đa dạng kích thước, cần chuẩn hoá |
| Ảnh trong `Pack Tổng/` | 32 | Bảng tổng hợp tham khảo |

### 4.1. Ánh xạ Background ↔ 10 Map

| Map | Yêu cầu | Asset khả dụng | Hạng |
|-----|----------|-----------------|------|
| M01 | Home / Living | `bedroom 3–7`, Spiral Atlas: `lounge, kitchen, dining, dining_kitchen, master bedroom, single bedroom, bathroom` | ✅ dư |
| M02 | Corridor / Entrance | Spiral Atlas: `hallway, entrance` | ✅ đủ |
| M03 | Street / Neighborhood | `street 1–4`, `cherry street 1`, `City/Neighborhood 1–3` (Day/Afternoon/Night) | ✅ dư |
| M04 | **Café / Meeting** | `restaurant 1`, `mall 1–2`, `clothing shop 1` | ⚠️ **không có quán cà phê** |
| M05 | **Workplace (viện dưỡng)** | `office 1–5` | ⚠️ **lệch ngữ cảnh** — là văn phòng, không phải viện dưỡng |
| M06 | Office Meeting | `office 1–5` | ✅ đủ |
| M07 | **Study / Library** | *(không có)* | ❌ **THIẾU HOÀN TOÀN** |
| M08 | Transit Hub | `train station 1`, `inside train 1`, `train 1–3` | ✅ đủ |
| M09 | Quiet Outdoor | `City/Park 1–3`, `garden blur 1–2`, `dawn beach 1`, `onsen 1–3` | ✅ dư |
| M10 | Final Open Space | `City/Sky Day Day, Sky Afternoon Day, Sky Night Day` | ✅ đủ |

### 4.2. Asset còn thiếu (theo mức ưu tiên)

| # | Thiếu | Ai cần | Mức độ |
|---|-------|--------|--------|
| 1 | **Thư viện / lớp học / trường đại học** (M07) | A3_C05, A3_C08, L05, L08, V14, A22, A27 | 🔴 **chặn** — 7 hạng mục phụ thuộc |
| 2 | **Quán cà phê** (M04) | A2_C02, A2_C04, A2_C06, L04, L09, V09, A11, A15 | 🔴 cao — trọng tâm Arc 2 |
| 3 | **Nội thất viện dưỡng lão**: phòng bệnh, kho thuốc, sảnh (M05) | A3_C02, L02, A19, A21, nhân vật sếp | 🟠 cao — nếu giữ setting gốc |
| 4 | **Trạm xe buýt** | A1_C07 key moment ("Dương ngồi ở trạm xe buýt") | 🟡 trung bình |
| 5 | **Biến thể night cho M01 (nhà)** | Arc 1–2 chủ yếu diễn buổi tối; nhà hiện chỉ có 1 phiên bản sáng | 🟠 cao |
| 6 | **Outfit layer cho Dương / Nam / Minh** | 02 docs yêu cầu hệ layer (base + tóc + áo + quần + phụ kiện) | 🟠 cao |
| 7 | **Expression đủ bộ** | 04 pack cần "expression variant" cho F07, R08 | 🟡 trung bình |
| 8 | **Cánh cửa sếp / nhân vật phụ** | A3_C02, A21 | 🟡 trung bình |

---

## 5. VẤN ĐỀ PHÁP LÝ & BẢN QUYỀN

| # | Vấn đề | Trạng thái | Hành động |
|---|--------|------------|-----------|
| 1 | **Spiral Atlas — CC BY 4.0** | Đã có `license.txt` | ⚠️ **BẮT BUỘC ghi credit** trong game credits + README: tên, nguồn, link license, ghi rõ đã chỉnh sửa |
| 2 | Thư mục `__MACOSX` chứa file rác | `.DS_Store`, `._*.jpg` (14 file) | Xóa — rác từ macOS |
| 3 | **149 ảnh còn lại chưa rõ license** | `FREE_BG_*`, `City/*`, `bedroom/street/kitchen/office/mall/train...` | ❌ **Chưa verify.** Phải truy nguồn trước khi phát hành công khai |
| 4 | Tên file chưa chuẩn hoá | `FREE_BG_1.png`, `bedroom 3.jpg`, `01.1.png` | Cần đổi theo convention `bg_home_livingroom.png` / `char_duong_base.png` |

---

## 6. QUYẾT ĐỊNH ĐÃ CHỐT — 02/10/2026

| # | Câu hỏi | Quyết định |
|---|---------|-----------|
| Q1 | Premise | **Giữ setting G1** (Thụy Điển, nợ 8 tỷ, viện dưỡng lão, sếp nữ 45 tuổi, Minh mơ làm bác sĩ, Nam học thạc sĩ), **bổ sung làm bối cảnh cho G2** |
| Q2 | Bộ chỉ số | **24 biến của `09_SYSTEM_VARIABLES` làm chuẩn.** 10 biến `STORY_BIBLE` hạ xuống thành *delta cụ thể cho từng choice*, dùng làm ngưỡng số cho ending resolver |
| Q3 | Bước tiếp theo | **Viết lại toàn bộ 11 pack `.docx` → `.md`**, sửa mâu thuẫn, bổ sung pack 06/07/08 còn thiếu |

### 6.1. Hệ quả của Q1 — sửa 6 chương "gặp trực tiếp Nam"

Dương ở Thụy Điển, Nam ở Việt Nam, yêu xa 5 năm → **không thể ngồi cùng phòng**.
M04 Café và M08 Transit phải đổi bản chất:

| Chương | Bản gốc | Bản sửa |
|--------|----------|----------|
| A2_C02 | Dương và Nam gặp ở quán cà phê | Dương ngồi ở quán cà phê gần nhà, **gọi video** cho Nam đang ở quán cà phê bên Việt Nam |
| A2_C04 | Gặp mặt, Nam hỏi trực tiếp | **Video call dài** — câu hỏi vẫn giữ nguyên |
| A2_C06 | Xung đột tại quán | **Xung đột qua điện thoại**, Dương bật/tắt máy |
| A2_C09 | Chia tay ở sân ga | Dương ở **sân ga tàu Thụy Điển**, Nam ở **sân bay/ga Việt Nam** — hai bờ gọi nhau lúc chia tay |
| A3_C04 | Café hoặc remote | Chuyển hẳn sang **remote scene** |
| A3_C09 | Ngưỡng cửa quan hệ tại M04/M08 | Chuyển sang **cuộc gọi đêm** — đúng chủ đề "Nam không thể chờ mãi" |

**Bổ sung mới (do Q1 sinh ra):** cần cơ chế `TIME_ZONE` — giờ Thụy Điển chậm hơn Việt Nam 5–6 giờ → sinh ra "múi giờ khác nhau" (A2_C02) một cách **tự nhiên và giàu sắc thái** thay vì là lý do suông.

### 6.2. Phase 1 — trạng thái

- [x] **T1.1** Chốt PREMISE ✅
- [x] **T1.2** Chốt bộ STAT ✅
- [x] **T1.3** Chốt bộ ENDING ✅ (9 ending E01–E09, ngưỡng lấy từ STORY_BIBLE)
- [x] **T1.4** Viết lại 11 pack ra `.md` ✅ **13/13**
- [x] **T1.5** Xoá `__MACOSX`, chuẩn hoá tên file asset ✅
- [x] **T1.6** Bổ sung `CREDITS.md` cho toàn bộ asset ✅

---

## 7. KẾ HOẠCH TRIỂN KHAI

### Phase 1 — Chuyển thiết kế sang .md ✅ **HOÀN THÀNH 02/10/2026**

- [x] T1.1 / T1.2 / T1.3 — chốt quyết định
- [x] T1.4a `docs/CANON_DECISIONS.md` — bản ghi quyết định + giá trị khởi tạo biến
- [x] T1.4b `docs/00_OVERVIEW.md` — mục lục + pitch + 8 nguyên tắc thiết kế
- [x] T1.4c `docs/01_STORY.md` — 31 chương, sửa 6 chương Nam
- [x] T1.4d `docs/09_SYSTEM_VARIABLES.md` — 27 object (canonical) + delta STORY_BIBLE + ngưỡng ending
- [x] T1.4e `docs/10_CHOICE_BRANCHING.md` — 20 choice + delta số cụ thể
- [x] T1.4f `docs/02_GAMEPLAY_SYSTEM.md` — core loop, chapter template, phone + múi giờ, save, build order
- [x] T1.4g `docs/03_MAP_EVENT_FLOW.md` — 10 map, sửa M04/M08 long-distance, thêm A3_C12
- [x] T1.4h `docs/04_CG_PLACEMENT.md` — 30 CG, sửa R02/R04/R06/R09/L04/L09 theo long-distance, sửa R03 về map M01
- [x] T1.4i `docs/05_VFX_AUDIO_PLACEMENT.md` — 20 VFX + 30 audio + audio riêng cho khoảng cách
- [x] T1.4j `docs/11_ENDING.md` — 9 ending + pseudo-code resolver + 42 epilogue + 9 kịch bản test
- [x] T1.4k `docs/06_CHARACTER_STYLE.md` — **pack bị thiếu**
- [x] T1.4l `docs/07_UI_HUD.md` — **pack bị thiếu**
- [x] T1.4m `docs/08_ASSET_MANIFEST.md` — **pack bị thiếu**, liệt kê asset thiếu
- [x] T1.5 dọn `__MACOSX` + chuẩn hoá tên file
- [x] T1.6 `CREDITS.md`

### Phase 2 — Vertical Slice (đúng theo `03.07` và `02.13`)

Tài liệu G2 đã chỉ rõ: **prototype một vertical slice trước — `A1_C01 → A1_C06 → A1_C09`**

- [ ] **T2.1** Chọn stack web (khuyến nghị: TypeScript + Phaser 3 hoặc PixiJS — sprite sheet + scene management có sẵn)
- [ ] **T2.2** STEP 1 — Player movement + camera
- [ ] **T2.3** STEP 2 — Interaction prompt + object interaction
- [ ] **T2.4** STEP 3 — Dialogue + event system
- [ ] **T2.5** STEP 4 — Choice UI
- [ ] **T2.6** STEP 5 — Variables / flags / route states
- [ ] **T2.7** STEP 6 — Chapter progression (đủ A1_C01 → A1_C09)
- [ ] **T2.8** Kiểm thử: chạy thật, log sạch, load save hoạt động

### Phase 3 — Mở rộng

- [ ] **T3.1** Thêm 1 route Romance (A2) — verify romance state machine
- [ ] **T3.2** Thêm 1 route Arc 3 (A3) — verify priority state + breaking point
- [ ] **T3.3** Ending resolver + ending gallery
- [ ] **T3.4** Phone system + Journal
- [ ] **T3.5** Conditional content (4 mức Level 1–4)
- [ ] **T3.6** Bổ sung asset còn thiếu (M04, M07, M05, night variant)
- [ ] **T3.7** Cân bằng ngưỡng ending — test đủ 9 ending khả di

### Phase 4 — Hoàn thiện

- [ ] **T4.1** Đủ 30 CG + 20 VFX + 30 audio
- [ ] **T4.2** Save/load đầy đủ
- [ ] **T4.3** Credits + màn hình kết thúc
- [ ] **T4.4** Viết README kỹ thuật + hướng dẫn build

---

## 7. MÂU THUẪN CẦN GIẢI QUYẾT

| # | Mâu thuẫn | Nơi | Mức |
|---|-----------|-----|-----|
| 1 | **Premise**: G1 nói Thụy Điển + nợ 8 tỷ; G2 không còn | README + G1 vs G2 packs | 🔴 |
| 2 | **Số chỉ số**: 4 vs 10 vs 24 | G1 / STORY_BIBLE / 09_PACK | 🔴 |
| 3 | **Số ending**: 4 vs 9 | G1 vs 11_PACK | 🔴 |
| 4 | **Gameplay**: G1 có quản lý tài chính + minigame; G2 nói "không cần resource farming" | G1 vs 02_PACK | 🔴 |
| 5 | **Thiếu pack 06, 07, 08** — numbering nhảy 05 → 09 | Tên file | 🟠 |
| 6 | **Năm Minh sang Thụy Điển**: "từ lớp 6" vs Dương "từ lớp 9" | `Cốt truyện...docx` dòng 5 và 53 | 🟠 |
| 7 | **Tuổi Minh**: sinh 2006 (lớp 6 năm 2020 = 13–14 tuổi ✓ hợp lý), nhưng G1 lại đồng nhất với "lớp 6" trong khi Dương lớp 9 | như trên | 🟠 |
| 8 | **Minh ước mơ làm bác sĩ** (G1) — G2 không đề cập | G1 vs G2 | 🟡 |
| 9 | **Nam chưa bao giờ gặp Dương trực tiếp?** G2 có `M04 Café` với scene gặp mặt → mâu thuẫn với "yêu xa" | G1 vs 03_PACK | 🟠 |
| 10 | **Tên chương lệch nhau giữa pack 01 và pack 03/04** | `01_STORY` vs `03_MAP_EVENT_FLOW` | 🔴 |
| 11 | **Pack 03 chỉ có A3_C01–C11, thiếu A3_C12** | `01_STORY` có A3_C12 "Một ngày sau đó" | 🟠 |

> ⚠️ Điểm 9 nghiêm trọng: G2 đặt nhiều scene **gặp trực tiếp** Nam ở M04 Café (A2_C02, A2_C04, A2_C06, A3_C04, A3_C09) và M08 Transit (A2_C09). Nhưng premise G1 nói Dương ở Thụy Điển, Nam ở Việt Nam, yêu xa 5 năm. **Hai bên không thể gặp mặt.** Phải giải quyết: hoặc bỏ các scene gặp mặt, hoặc đổi premise.

### 7.1. Chi tiết mâu thuẫn 10 và 11 — phát hiện khi đối chiếu lúc viết `03_MAP_EVENT_FLOW`

**Mâu thuẫn 10 — tên chương lệch.** Pack 03 và pack 04 dùng **tên tiếng Anh làm bản nháp**, lệch với tên tiếng Việt chuẩn trong pack 01:

| ID | Pack 01 (CHUẨN) | Pack 03/04 (bản nháp) |
|----|----------------|------------------------|
| A1_C02 | Những việc không tên | Things Left Unsaid |
| A1_C03 | Cuộc gọi | Two Directions |
| A1_C04 | Những kế hoạch riêng | What Minh Wants |
| A1_C05 | Những điều không nói | A Familiar Argument |
| A2_C03 | Minh nhận ra | Distance in Small Things |
| A3_C11 | Quyết định của Dương | The Next Step Is Mine |

→ **Sửa:** lấy tên trong `01_STORY.md` làm chuẩn. Pack 03/04 trong bản `.md` mới sẽ ghi tên chuẩn, kèm tên tiếng Anh trong ngoặc để giữ liên kết với bản gốc.

**Mâu thuẫn 11 — thiếu chương.** Pack 03 kết thúc ở `A3_C11` rồi sang `FINAL`. Nhưng `01_STORY.md` có thêm `A3_C12 — Một ngày sau đó` (lập luận: 31 chương = 1 + 9 + 9 + 12), và `09_SYSTEM_VARIABLES` chạy resolver "sau A3_C12".
→ **Sửa:** thêm `A3_C12` vào `03_MAP_EVENT_FLOW.md` là chương montage không choice, map `M10 + route map`, chỉ phản chiếu hậu quả.

---

## 8. NHẬT KÝ KẾT QUẢ

**2026-10-02 — Hoàn thành audit toàn bộ tài liệu + asset.**

Kết quả:
- Đọc 11/11 file .docx (5.048 dòng text sau trích xuất)
- Kiểm kê 149 file ảnh, đo kích thước thật bằng .NET `System.Drawing`
- Xác định 9 mâu thuẫn thiết kế, 8 asset thiếu, 4 vấn đề pháp lý
- Đề xuất chia 4 phase triển khai

Chưa viết dòng code nào. Đúng theo nguyên tắc "Lập kế hoạch trước khi code" — hiện đang ở Phase 1 (chốt thiết kế), chưa nên code vì 3 blocker (premise, stat, ending) chưa giải quyết.

**2026-10-02 — Hoàn thành Phase 1: 13 pack `.md` + dọn asset + `CREDITS.md`.**

Viết mới / viết lại:
| Kết quả | Chi tiết |
|---------|----------|
| 13 file `.md` trong `docs/` | 11 pack từ `.docx` + 3 pack bị thiếu (06/07/08) + `CANON_DECISIONS.md` |
| 31 chương | `01_STORY.md`, trong đó 6 chương sửa theo Q1 |
| 20 choice | `10_CHOICE_BRANCHING.md`, mỗi choice có delta số cụ thể |
| 33 object lưu save | `09_SYSTEM_VARIABLES.md` (27 object Tầng 1–2 + 6 derived) |
| 9 ending | `11_ENDING.md`, có pseudo-code resolver + 9 kịch bản test |
| 30 CG / 20 VFX / 30 audio | `04_` + `05_` |
| 10 map | `03_MAP_EVENT_FLOW.md`, sửa M04/M05/M08, thêm A3_C12 |

Dọn asset:
| Việc | Kết quả |
|------|---------|
| Xoá file rác | **16** (15 `__MACOSX` + 1 `.DS_Store`) |
| Chuẩn hoá tên file | **105** — git nhận `R100` (rename thuần, không đổi nội dung) |
| Giữ nguyên | 44 ảnh tham khảo + 2 file license Spiral Atlas |
| `CREDITS.md` | Tạo mới — bắt buộc vì 11 ảnh CC BY 4.0 |

Số liệu kho (đo trực tiếp, không chép tài liệu gốc):
- **149** ảnh = **105 dùng được** + **44 tham khảo**
- **138** ảnh chưa xác minh được license ⚠️
- **4** asset chặn tiến độ: M07 thư viện, CHAR_ANNIKA, M05 viện dưỡng lão, bộ biểu cảm

Bài học xem `lessons.md` (L001–L017).