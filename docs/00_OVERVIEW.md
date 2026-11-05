# 🎯 00. OVERVIEW

> Hành Trình Của Mira Eli — tổng quan, pitch và mục lục thiết kế.
> **Đọc file này trước.** Nếu chỉ có thời gian đọc một file, hãy đọc file này rồi `CANON_DECISIONS.md`.

---

## 00.01 — PITCH

**Một ngày bình thường của Dương — cô điều dưỡng ở Thụy Điển, gánh nợ 8 tỷ của gia đình, nuôi em gái đang muốn trở thành bác sĩ, và yêu một người ở Việt Nam mà cô không biết cách giữ.**

Game không có quái vật, không có vương quốc, không có đáp án hoàn hảo.
Chỉ có một cô gái, một cái lịch không bao giờ trống, và những ngày bình thường diễn ra liên tục.

> **Chủ đề:** *Trưởng thành không phải giữ được tất cả, mà là biết điều gì quan trọng và biết khi nào cần nhờ người khác.*

**Thể loại:** mô phỏng đời sống + narrative. Web game.
**Nền tảng:** trình duyệt (web).
**Thời lượng một lượt chơi:** 3–5 giờ.
**Số ending:** 9 nhóm, mỗi nhóm có 2–4 biến thể epilogue.

---

## 00.02 — NHÂN VẬT

| NV | Tên | Sinh | Vị trí trong game |
|----|-----|------|--------------------|
| **Dương** | Dương — tên Thụy Điển: **Mira Eli** | 2003 | Nhân vật chính. Điều dưỡng viện dưỡng lão. Gánh nợ gia đình. |
| **Minh** | Minh | 2006 | Em gái, nhập cư từ năm Dương học lớp 9. Mơ ước làm bác sĩ / nhà nghiên cứu. |
| **Nam** | Nam | 2004 | Bạn trai yêu xa 5 năm, ở Việt Nam. SV CNTT, muốn học thạc sĩ để sang Thụy Điển. |
| **Mẹ** | — | — | Đang gánh vác cùng Dương, sức khoẻ không tốt. |
| **Annika** | Annika | ~45 | Sếp nữ người Thụy Điển. Người duy nhất có thể cho Dương thăng chức. |

> ⚠️ **Ràng buộc cứng:** Dương ở Thụy Điển, Nam ở Việt Nam. **Hai người không bao giờ gặp mặt trực tiếp trong game.**
> Mọi tương tác là tin nhắn / cuộc gọi / video call. Khoảng cách đó là chủ đề trung tâm của Arc 2 — đừng phá vỡ nó.

Chi tiết đầy đủ: `CANON_DECISIONS.md` mục 1.

---

## 00.03 — CẤU TRÚC GAME

```
PROLOGUE  (P01)
   ↓
ARC 1 — 🏠 FAMILY            A1_C01 → A1_C09     → FAMILY_STATE
   ↓
ARC 2 — ❤️ ROMANCE           A2_C01 → A2_C09     → ROMANCE_STATE
   ↓
ARC 3 — 🌱 LIFE / WORK / STUDY  A3_C01 → A3_C12  → BREAKING_POINT_STATE
                                                   → PRIORITY_STATE
                                                   → FINAL_ORIENTATION
   ↓
ENDING RESOLVER  →  E01 … E09
```

| Số | Thành phần |
|----|------------|
| Chương | **31** (1 + 9 + 9 + 12) |
| Choice | **20** (xem `10_CHOICE_BRANCHING.md`) |
| Map | **10** (M01–M10) |
| CG | **30** (F/R/L01–10) |
| VFX | **20** (V01–V20) |
| Audio cue | **30** (A01–A30) |
| Object trạng thái | **33** lưu trong save (6 resource + 27 narrative) |

### Ba arc

| Arc | Chủ đề | Câu hỏi trung tâm |
|-----|--------|-------------------|
| Arc 1 — Family | Không phải mọi trách nhiệm đều phải do một mình gánh | Dương có để ai giúp không? |
| Arc 2 — Romance | Yêu một người không có nghĩa là lúc nào cũng biết cách giữ họ ở lại | Dương có dành chỗ thật không? |
| Arc 3 — Life/Work/Study | Không thể giữ tất cả, nhưng có thể chọn cách sống | Dương muốn sống thế nào? |

---

## 00.04 — HỆ THỐNG TRẠNG THÁI (giản lược)

Game có **3 tầng dữ liệu**. Người chơi chỉ nhìn thấy tầng 1.

```
TẦNG 1  RESOURCE          ENERGY · MONEY · DEBT · REPUTATION · DAY · TIME_BLOCK
        ↑ có HUD, phản hồi tức thì, cập nhật liên tục

TẦNG 2  NARRATIVE STATE    7 Persistent + 5 Route State + 15 Flag = 27 object
        ↑ ẩn hoàn toàn. Người chơi CẢM được, không ĐỌC được

TẦNG 3  DERIVED           BALANCE · OPENNESS · RESPONSIBILITY · WORK · STRESS
        ↑ tính tự động, chỉ dùng để viết ngưỡng ending + debug
```

Giá trị khởi tạo, quy tắc cập nhật và ngưỡng ending: `09_SYSTEM_VARIABLES.md`.

**Ba trục ưu tiên cố ý lệch nhau khi bắt đầu:**
`CAREER_FOCUS = 50` · `STUDY_FOCUS = 40` · `CONNECTION_FOCUS = 35`

→ Người chơi phải **tự nhận ra** mình đang bỏ bê kết nối, rồi chủ động tạo khoảng trống.
Không cho sẵn. Đây là ý nghĩa thiết kế, không phải sự bất cẩn.

---

## 00.05 — 9 ENDING

| ID | Tên | Loại |
|----|-----|------|
| E01 | A Life of Her Own | 🌟 True Growth / Self-Directed |
| E02 | Together, Despite the Distance | ❤️ Romance |
| E03 | The Promotion | 💼 Career |
| E04 | The Next Step | 📚 Study / Future Growth |
| E05 | Letting Go | 💔 Honest Separation |
| E06 | The One Who Carries Everything | 🏋️ Overload / Unresolved |
| E07 | Starting Over | 🌱 Recovery / Reset |
| E08 | Too Late to Rest | 🌙 Burnout Consequence |
| E09 | Balanced / Neutral | ☀️ Quiet Continuation |

**Không ending nào phủ nhận toàn bộ lựa chọn trước đó.** Ending tốt không có nghĩa giữ được Nam, công việc và gia đình cùng lúc.
Chi tiết điều kiện và nội dung: `11_ENDING.md`.

---

## 00.06 — MỤC LỤC THIẾT KẾ

| File | Nội dung |
|------|----------|
| **`CANON_DECISIONS.md`** | ⭐ **File luật.** Khi có mâu thuẫn, file này thắng. |
| `00_OVERVIEW.md` | File này — pitch, mục lục. |
| `01_STORY.md` | 31 chương, 3 arc, cảnh báo scene nào là remote. |
| `02_GAMEPLAY_SYSTEM.md` | Core loop, chapter template, interaction, phone, journal, save, build order. |
| `03_MAP_EVENT_FLOW.md` | 10 map M01–M10, trigger, ánh xạ chapter → map. |
| `04_CG_PLACEMENT.md` | 30 CG F/R/L01–10 + ending frame mapping. |
| `05_VFX_AUDIO_PLACEMENT.md` | 20 VFX + 30 audio cue. |
| `06_CHARACTER_STYLE.md` | Style guide nhân vật, outfit layer, expression set. |
| `07_UI_HUD.md` | HUD, màn hình điện thoại, journal, ending gallery. |
| `08_ASSET_MANIFEST.md` | Asset có / thiếu / trạng thái license. |
| `09_SYSTEM_VARIABLES.md` | ⭐ **27 object narrative + 6 resource.** Nguồn chuẩn cho logic trạng thái. |
| `10_CHOICE_BRANCHING.md` | ⭐ **22 choice với delta số cụ thể.** |
| `11_ENDING.md` | 9 ending, resolver, epilogue variant. |
| `12_RULES.md` | **36 luật thi công** — stack, dữ liệu, nội dung, công việc, minigame. |
| `13_QUICKREF.md` | **Bảng tra cứu nhanh** — hằng số, ID, cần gì mở file nào. |

**Thứ tự đọc khi làm việc:**
1. `13_QUICKREF.md` — mở trước, phần lớn câu hỏi dừng ở đây
2. `CANON_DECISIONS.md` → 3. `00_OVERVIEW.md` → 4. `09_SYSTEM_VARIABLES.md` → 5. `10_CHOICE_BRANCHING.md` → 6. pack theo nhiệm vụ
7. `12_RULES.md` — trước khi viết dòng code đầu tiên

---

## 00.07 — TRẠNG THÁI DỰ ÁN

**Chưa có dòng code nào.** Thiết kế mới chốt xong trong `docs/`.

Các bước tiếp theo theo thứ tự ưu tiên:

| # | Việc | Ghi chú |
|---|------|---------|
| 1 | Dọn asset: xoá `__MACOSX`, chuẩn hoá tên file | `todo.md` T1.5 |
| 2 | Viết `CREDITS.md` — bắt buộc vì ảnh Spiral Atlas là CC BY 4.0 | `todo.md` T1.6 |
| 3 | **Prototype vertical slice** `A1_C01 → A1_C06 → A1_C09` | Tài liệu G2 chỉ rõ phải làm slice trước |
| 4 | Bổ sung asset còn thiếu: thư viện (M07), quán cà phê (M04), nội thất viện dưỡng (M05) | Chi tiết ở `08_ASSET_MANIFEST.md` |

> ⚠️ **Chưa được code trước khi asset và license đã xong.** 138/149 ảnh chưa verify license — phát hành công khai lúc này là rủi ro pháp lý.

---

## 00.08 — NGUYÊN TẮC THIẾT KẾ (không được vi phạm)

1. **Không có đáp án hoàn hảo.** Mọi lựa chọn đều tốn một thứ.
2. **Choice tốt phải tốn công.** Lựa chọn tốt nhất không bao giờ là lựa chọn dễ nhất.
3. **Người chơi cảm trạng thái, không đọc trạng thái.** 27 object narrative đều ẩn.
4. **Không khóa ending quá sớm.** Phần lớn route xác định ở Arc 3.
5. **Final scene luôn mirror Prologue** — để người chơi thấy sự thay đổi.
6. **Nam và Minh có quỹ đạo riêng.** Họ không chỉ là phần thưởng/phạt cho lựa chọn của Dương.
7. **Gameplay phục vụ narrative.** Không combat, không grinding, không resource farming.
8. **Dương và Nam không gặp mặt.** Không có ngoại lệ.

---

**TIẾP** → `01_STORY.md`
**ĐỌC LUẬT** → `CANON_DECISIONS.md`
