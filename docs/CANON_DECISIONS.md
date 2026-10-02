# CANON DECISIONS — Hành Trình Của Mira Eli

> **File này là luật chơi của thiết kế.** Khi có mâu thuẫn giữa các file, file này thắng.
> Mọi thay đổi từ đây trở đi phải cập nhật file này trước.

**Ngày chốt:** 02/10/2026
**Trạng thái:** Đã khóa. Thiết kế chính thức bắt đầu từ đây.

---

## 1. PREMISE — Setting chính thức

Dương và gia đình **sang Thụy Điển từ năm Dương học lớp 9**, cùng mẹ và em gái Minh.
Gia đình phá sản vì bố mẹ Dương vỡ nợ. Khoản nợ còn lại **8 tỷ VND** do Dương gánh.
Sau khi tốt nghiệp lớp 12, Dương **đi làm điều dưỡng tại viện dưỡng lão** để trả nợ và nuôi Minh.

| Nhân vật | Năm sinh | Quốc tịch | Vị trí |
|----------|----------|-----------|--------|
| **Dương** / Mira Eli | 2003 | VN → SE (nhập cư) | Điều dưỡng viện dưỡng lão. Muốn học đại học để thăng chức |
| **Minh** | 2006 | VN → SE (nhập cư từ lớp 6) | Em gái. Mơ ước trở thành bác sĩ / nhà nghiên cứu |
| **Nam** | 2004 | Việt Nam | SV CNTT. Yêu xa 5 năm. Mục tiêu: học thạc sĩ ở Thụy Điển để sang gặp Dương |
| **Mẹ** | — | VN → SE | Đang gánh vác cùng Dương, sức khỏe không tốt |
| **Sếp (Annika)** | ~45 | Thụy Điển | Nữ, người Thụy Điển, trực tiếp chỉ đạo Dương. Tốt bụng nhưng lười, hay vắng mặt. Là người duy nhất có thể cho Dương thăng chức (phải đỗ kỳ thi nâng bậc 1–2 buổi) |

### 1.1. Ràng buộc cứng do setting

> ⚠️ **Dương ở Thụy Điển. Nam ở Việt Nam. KHÔNG BAO GIỜ gặp mặt trực tiếp trong game.**

Mọi scene có Nam đều là: **điện thoại / tin nhắn / video call / nhìn qua màn hình**.
Không có bất kỳ CG nào hai người cùng ở một căn phòng.
Cái "khoảng cách" là chủ đề trung tâm của Arc 2 — đừng phá vỡ nó.

### 1.2. Chi tiết bổ sung từ thiết kế G1 (được giữ lại)

- **Ca làm:** mỗi ca có 2–5 đồng nghiệp nữa. Sếp thường vắng mặt để đi du lịch hoặc "ốm".
- **Minigame tại viện (2–3 cái):** đưa thuốc cho bệnh nhân, nấu ăn, và xử lý tình huống khẩn — bệnh nhân lên cơn, bệnh nhân đột ngột qua đời, bệnh nhân không chịu ăn/uống thuốc, bệnh nhân chạy trốn đi lạc.
- **Viện dưỡng lão có:** sảnh chính, hành lang, kho thuốc, bếp, phòng bệnh nhân, phòng sếp, và **nhà bệnh nhân** (Dương đôi khi phải đưa thuốc/giao đồ ăn tại nhà).
- **Đời sống:** Dương từng lớp 9 vừa học vừa làm. Giờ cô vẫn chưa quyết được: đi học đại học hay dồn tiền trả nợ nuôi Minh đi học.
- **Đồng nghiệp gần nhà** thỉnh thoảng lái đón Dương đi làm khi cô trễ.

---

## 2. HỆ THỐNG CHỈ SỐ — 3 tầng

Không phải mọi biến đều cùng cấp. Chia làm 3 tầng để không trộn lẫn mục đích.

```
TẦNG 1 — RESOURCE (cơ chế chơi)      cập nhật liên tục, có trong HUD
TẦNG 2 — NARRATIVE STATE (24 object) ← CHUẨN. cập nhật ở choice
TẦNG 3 — DERIVED (chỉ để test)      tính tự động, không lưu
```

### TẦNG 1 — Resource (khôi phục từ thiết kế G1)

Q1 giữ lại nợ 8 tỷ → cần lớp tài chính. Nhưng nó là **cơ chế**, không phải narrative state.

| Biến | Kiểu | Khoảng | Ý nghĩa |
|------|------|--------|---------|
| `ENERGY` | int | 0–100 | Thể lực. Dưới 20 → dialogue tự thoại thay đổi, idle mệt |
| `MONEY` | int (VND) | không trần | Tiền mặt hiện có |
| `DEBT` | int (VND) | ≥0 | Dư nợ gia đình. Bắt đầu 8.000.000.000 |
| `REPUTATION` | int | 0–100 | Uy tín nghề nghiệp tại viện. Quyết định được thăng chức |
| `DAY` | int | ≥1 | Ngày hiện tại |
| `TIME_BLOCK` | enum | MORNING / DAY / EVENING / NIGHT | Khung giờ |

**Luồng tiền mỗi ngày:**
```
MONEY += lương (theo ca + chức vị + REPUTATION)
MONEY -= sinh hoạt
MONEY -= học phí Minh (nếu đang học)
MONEY -= trả nợ (nếu người chơi chọn)
DEBT  -= khoản đã trả
```
Khi `DEBT == 0` → mở cờ `FLAG_DEBT_CLEARED` → mở cửa ending có hậu về tài chính.
Khi `MONEY < 0` → 2 tuần không trả được → `FLAG_FINANCIAL_RISK`, ảnh hưởng ending.

### TẦNG 2 — Narrative State (24 object, CHUẨN)

Lấy nguyên vẹn từ `09_SYSTEM_VARIABLES`. **Đây là bản chuẩn duy nhất.**

**7 Persistent Values** (0–100, ẩn — không hiện thanh HUD):

| Biến | Ý nghĩa |
|------|---------|
| `FAMILY_TRUST` | Dương và Minh tin tưỡng, chia sẻ, cho quyền tự quyết |
| `ROMANCE_TRUST` | Chất lượng giao tiếp giữa Dương và Nam |
| `SELF_AWARENESS` | Dương nhận ra giới hạn và cảm xúc thật của bản thân |
| `OVERLOAD` | Mức độ Dương đang ôm quá nhiều |
| `CAREER_FOCUS` | Ưu tiên cơ hội nghề nghiệp |
| `STUDY_FOCUS` | Ưu tiên học tập / bước ngoặt tương lai |
| `CONNECTION_FOCUS` | Ưu tiên giữ kết nối với người quan trọng |

**5 Route States** (enum):

| Biến | Giá trị |
|------|---------|
| `FAMILY_STATE` | `GROWTH` / `MIXED` / `UNRESOLVED` |
| `ROMANCE_STATE` | `ACTIVE` / `UNCERTAIN` / `ENDED` |
| `PRIORITY_STATE` | `CAREER` / `STUDY` / `CONNECTION` / `BALANCE` / `OVERLOAD` |
| `FINAL_ORIENTATION` | `CONNECTION` / `SELF` / `RECOVERY` |
| `BREAKING_POINT_STATE` | `AWARE` / `PUSH_ON` / `WITHDRAW` |

**12 Event Flags** (boolean): `FLAG_SHARED_WORK`, `FLAG_FAMILY_TRUTH`, `FLAG_ACCEPTED_HELP`,
`FLAG_CONTACTED_NAM`, `FLAG_ROMANCE_HONESTY`, `FLAG_COMMIT_TO_NAM`, `FLAG_WORK_OPPORTUNITY`,
`FLAG_STUDY_ROUTE`, `FLAG_CHOSE_BALANCE`, `FLAG_ADMITTED_OVERLOAD`, `FLAG_LET_MINH_GO`,
`FLAG_LET_NAM_GO`

**+ 3 flag bổ sung do Q1** (khôi phục từ G1): `FLAG_DEBT_CLEARED`, `FLAG_FINANCIAL_RISK`, `FLAG_SKILL_UP`
→ **Tổng: 27 object.**

### TẦNG 3 — Derived (tính tự động, chỉ để viết ngưỡng ending + debug)

Ánh xạ 10 biến của `STORY_BIBLE` vào hệ mới. **Không lưu, không chỉnh tay.**

| Biến cũ | Công thức từ tầng 1 + 2 |
|---------|------------------------|
| `FAMILY` | `= FAMILY_TRUST` |
| `ROMANCE` | `= ROMANCE_TRUST` |
| `TRUST` | `= ROMANCE_TRUST` (trùng ý nghĩa, giữ alias để đọc ngưỡng cũ) |
| `OPENNESS` | `= round(0.6 × SELF_AWARENESS + 0.4 × (100 − OVERLOAD))` |
| `RESPONSIBILITY` | `= round(0.7 × OVERLOAD + 0.3 × (100 − SELF_AWARENESS))` |
| `WORK` | `= round(0.7 × CAREER_FOCUS + 0.3 × REPUTATION)` |
| `STUDY` | `= STUDY_FOCUS` |
| `BALANCE` | `= round((100 − OVERLOAD) / 2 + 50 − abs(max(FOCUS) − avg(FOCUS)) / 2)` |
| `STRESS` | `= OVERLOAD` |
| `ENERGY_D` | `= TẦNG1.ENERGY` |

**Ý nghĩa của `BALANCE`:** cao khi overload thấp **và** người chơi không dồn hết vào một trục.
Dồn 100 vào một trục cũng bị trừ — đúng chủ đề "không thể chọn hết".

### 2.1. Giá trị khởi tạo (tại P01, trước khi người chơi chọn gì)

| Tầng 2 | Giá trị | Lý do |
|---------|---------|--------|
| `FAMILY_TRUST` | 45 | Dương gánh hết, Minh chưa được hỏi ý kiến |
| `ROMANCE_TRUST` | 55 | Yêu 5 năm, còn tốt — nhưng Dương trì hoãn nhiều |
| `SELF_AWARENESS` | 25 | Cô chưa thừa nhận là mình kiệt sức |
| `OVERLOAD` | 55 | Đã quá tải trước khi game bắt đầu |
| `CAREER_FOCUS` | 50 | Viện dưỡng là nguồn thu nhập duy nhất |
| `STUDY_FOCUS` | 40 | Ước mơ có nhưng bị hoãn |
| `CONNECTION_FOCUS` | 35 | Cô luôn đẩy việc khác lên trước |

| Tầng 1 | Giá trị |
|---------|---------|
| `ENERGY` | 65 |
| `MONEY` | 12.000.000 VND |
| `DEBT` | 8.000.000.000 VND |
| `REPUTATION` | 40 |
| `DAY` | 1 |

> Chọn `OVERLOAD` khởi đầu 55 (không phải 50) và `CONNECTION_FOCUS` 35 (không phải 40) là **cố ý**.
> Người chơi phải **tự tạo ra** khoảng trống cho Nam và Minh. Không cho sẵn.

---

## 3. SỬA MÂU THUẪN — bảng tra

| Mâu thuẫn | Cách sửa |
|-----------|----------|
| 6 chương cho Dương gặp Nam trực tiếp | Đổi thành phone / video call. Chi tiết từng chương xem `todo.md` mục 6.1 |
| Minh sang Thụy Điển "từ lớp 6" | Chốt: **Dương + mẹ + Minh cùng sang năm Dương học lớp 9**. Minh sinh 2006 nên năm đó 13 tuổi ≈ lớp 7. Viết lại mọi chỗ nói "từ lớp 6" |
| Pack thiếu số 06/07/08 | Đã viết: `06_CHARACTER_STYLE.md`, `07_UI_HUD.md`, `08_ASSET_MANIFEST.md` |
| 4 ending (G1) vs 9 ending (G2) | **9 ending E01–E09.** Chi tiết ở `11_ENDING.md` |
| 4 chỉ số (G1) vs 24 biến (G2) | **24 biến + 3 flag = 27.** Tầng 1 Resource tách riêng |
| Minh mơ làm bác sĩ (chỉ có ở G1) | Giữ. Ước mơ này là lý do `STUDY_FOCUS` của Dương có ý nghĩa |
| Sếp là nữ Thụy Điển 45 tuổi (chỉ G1) | Giữ. Nhân vật `CHAR_ANNIKA` |
| "Game mô phỏng tài chính" (G1) vs "không resource farming" (G2) | **Giữ cả hai:** không có *grinding*, nhưng có **quyết định chi tiêu có hậu quả**. Xem `02_GAMEPLAY_SYSTEM.md` mục 2.10 |

---

## 4. CẤU TRÚC THƯ MỤC

```
docs/
  CANON_DECISIONS.md        ← file này. LUẬT.
  00_OVERVIEW.md            ← mục lục, pitch, tóm tắt
  01_STORY.md               ← 31 chương
  02_GAMEPLAY_SYSTEM.md     ← core loop, chapter template, build order
  03_MAP_EVENT_FLOW.md      ← 10 map, trigger
  04_CG_PLACEMENT.md        ← 30 CG
  05_VFX_AUDIO_PLACEMENT.md ← 20 VFX + 30 audio
  06_CHARACTER_STYLE.md     ← style guide + outfit layer
  07_UI_HUD.md              ← HUD, điện thoại, journal
  08_ASSET_MANIFEST.md      ← asset có / thiếu / license
  09_SYSTEM_VARIABLES.md    ← 27 object (canonical)
  10_CHOICE_BRANCHING.md    ← 20 choice + delta số
  11_ENDING.md              ← 9 ending + resolver
```

Nguồn gốc `.docx` giữ nguyên trong `Cốt truyện/` làm tham khảo, **không sửa trong đó nữa** — chỉ sửa bản `.md`.