# ⚙️ 09. SYSTEM / VARIABLES

> Nguồn chuẩn cho toàn bộ logic trạng thái. Mọi pack khác tham chiếu file này.
> Ràng buộc tổng quát xem `CANON_DECISIONS.md`.

**Tổng: 27 object narrative** = 7 Persistent + 5 Route State + 15 Flag

---

## 09.00 — TỔNG QUAN

```
CHOICE → RESOURCE Δ → VALUE Δ / FLAG SET → ARC STATE → FINAL ORIENTATION → ENDING RESOLVER
```

**Nguyên tắc cốt lõi:**
- Thiết kế ưu tiên **Narrative State** hơn nhồi chỉ số.
- Phần lớn biến **chạy ẩn**. Không có thanh điểm nào trên HUD cho 7 persistent value.
- Mỗi choice quan trọng đổi **một hoặc nhiều** state.
- Ending Resolver đọc state cuối Arc 3 để chọn Ending Group + biến thể epilogue.
- `RESOURCE` (ENERGY / MONEY / DEBT) là **cơ chế**, tách riêng vì nó có phản hồi tức thì cho người chơi.

### Sơ đồ tầng

```
┌─ TẦNG 1 RESOURCE ────────────────────────────────┐
│  ENERGY   MONEY   DEBT   REPUTATION   DAY   TIME   │
│  → có HUD, cập nhật liên tục, phản hồi tức thì   │
└────────────────────────────────────────────────────┘
                      ↕ chuyển đổi ở choice
┌─ TẦNG 2 NARRATIVE STATE (27) ────────────────────┐
│  7 Persistent  ·  5 Route State  ·  15 Flag       │
│  → ẩn, người chơi cảm nhận qua dialogue/VFX       │
└────────────────────────────────────────────────────┘
                      ↓ tính tự động
┌─ TẦNG 3 DERIVED ─────────────────────────────────┐
│  BALANCE  OPENNESS  RESPONSIBILITY  WORK  STRESS   │
│  → chỉ để viết ngưỡng ending + debug, không lưu   │
└────────────────────────────────────────────────────┘
```

---

## 09.01 — TẦNG 1: RESOURCE

| Biến | Kiểu | Khoảng | Hiển thị |
|------|------|--------|----------|
| `ENERGY` | int | 0–100 | HUD dạng biểu tượng (không phải số) |
| `MONEY` | int (VND) | ≥ 0 | HUD dạng tiền |
| `DEBT` | int (VND) | ≥ 0 | Menu tài chính / Journal |
| `REPUTATION` | int | 0–100 | Ẩn. Lộ qua lời sếp + kỳ thi nâng bậc |
| `DAY` | int | ≥ 1 | HUD góc màn hình |
| `TIME_BLOCK` | enum | `MORNING` `DAY` `EVENING` `NIGHT` | HUD |

### 09.01.1 — ENERGY

| Δ | Nguyên nhân |
|---|-----------|
| −25 | Ca trực viện dưỡng (ngày) |
| −10 | Học / ôn bài |
| −15 | Nấu ăn + dọn dẹp cho Minh |
| −5 | Nói chuyện với Nam |
| +30 | Ngủ đủ một đêm (chuyển NIGHT → MORNING) |
| +20 | Nghỉ giữa ca |
| +10 | Ăn uống đúng bữa |
| +15 | Tắt điện thoại, đi dạo một mình |

**Quy tắc:** `ENERGY < 20` → khóa choice hưởng lợi ở `PRIORITY`, tự thoại đổi sang kiểu mệt, idle animation chậm.
`ENERGY == 0` → buộc chuyển time block hoặc mất 1 ngày nghỉ (tự động).

### 09.01.2 — DEBT & MONEY

```
Ban đầu:  DEBT = 8_000_000_000    MONEY = 12_000_000
```

**Lương theo chức vị** (VND / ngày):

| Chức vị | Lương/ngày | Yêu cầu `REPUTATION` | Cách lên |
|----------|-----------|----------------------|----------|
| Điều dưỡng (tân binh) | 480.000 | — | Vào game |
| Điều dưỡng (đã xét) | 620.000 | 55 | Sau 20 ngày |
| Điều dưỡng cao | 780.000 | 70 | Thi nâng bậc 1 buổi |
| Chuyên viên | 940.000 | 82 | Thi nâng bậc 2 buổi |
| Trưởng ca | 1.100.000 | 92 | Thi nâng bậc 3 buổi |

> Số liệu tạm — cần cân bằng lại khi prototype. Nguyên tắc: **lương KHÔNG đủ để trả hết nợ trong một lượt chơi ngắn.** Nợ phải là mục tiêu dài hạn, không phải thứ giải quyết xong.
> Ước tính: mức lương cao nhất trả hết 8 tỷ cần ~**200 ngày làm việc liên tục**. Đó là con số có chủ đích.

**Chi phí cố định / ngày:**

| Khoản | VND |
|-------|-----|
| Sinh hoạt (3 người + Dương) | 250.000 |
| Hỗ trợ học tập Minh (nếu đang học) | 300.000 |
| Đi lại | 40.000 |

**Trả nợ:** người chơi chọn mức trả mỗi ngày. Trả càng nhiều càng nhanh hết nợ → nhưng càng ít tiền cho học tập/ăn uống → `ENERGY` giảm.
Đây là **cơ chế xung đột trung tâm** — thay cho việc "chỉ số Tài chính" của G1.

**Sự kiện tài chính:**

| Điều kiện | Kết quả |
|-----------|---------|
| `DEBT <= 0` | set `FLAG_DEBT_CLEARED`, mở ending có hậu về tài chính |
| `MONEY < 0` liên tục 14 ngày | set `FLAG_FINANCIAL_RISK`, `ENERGY` tụt thêm mỗi ngày, khóa ending E01/E02 |
| Trả trễ ≥ 1 lần | `REPUTATION −5`, sếp hỏi thăm → choice phụ |

### 09.01.3 — REPUTATION

| Δ | Nguyên nhân |
|---|--------|
| +5 | Hoàn thành ca trực không lỗi |
| +10 | Giữ được ca tình huống khẩn (bệnh nhân lên cơn / chạy trốn) |
| +15 | Đỗ kỳ thi nâng bậc |
| −10 | Phát thuốc sai cho bệnh nhân |
| −5 | Đến trễ, nghỉ không phép |
| −15 | Bệnh nhân xảy ra chuyện nghiêm trọng dưới sự trực của Dương |

`REPUTATION >= 55` → mở đường lên điều dưỡng đã xét → tăng lương.

---

## 09.02 — TẦNG 2: 7 PERSISTENT VALUES

Tất cả: `Integer`, `0–100`, **Hidden**.

### FAMILY_TRUST
- **Ý nghĩa:** Mức độ Dương và Minh tin tưởng, chia sẻ và cho nhau quyền tự quyết.
- **Dùng bởi:** choice Arc 1; A3_C03, A3_C10; Ending dòng Family.
- **Khởi tạo:** 45
- **Ảnh hưởng tới:** lời thoại Minh (02.09 Level 1–2), CG biến thể, `FAMILY_STATE`.

### ROMANCE_TRUST
- **Ý nghĩa:** Chất lượng tin tưởng và giao tiếp giữa Dương và Nam.
- **Dùng bởi:** choice Arc 2; A3_C04, A3_C09; Ending dòng Romance.
- **Khởi tạo:** 55
- **Ảnh hưởng tới:** nội dung tin nhắn, giọng Nam trong call, `ROMANCE_STATE`.

### SELF_AWARENESS
- **Ý nghĩa:** Khả năng Dương nhận ra giới hạn, nhu cầu và cảm xúc thật của bản thân.
- **Dùng bởi:** A1_C06 trở đi; A3_C06–A3_C11; ending tăng trưởng.
- **Khởi tạo:** 25
- **Lưu ý:** giá trị thấp nhất trong 7 biến. Tăng nó là **hành trình chính** của game.

### OVERLOAD
- **Ý nghĩa:** Mức độ Dương đang cố ôm quá nhiều trách nhiệm cùng lúc.
- **Dùng bởi:** Arc 1–3; Breaking Point; ending quá tải.
- **Khởi tạo:** 55
- **Hiển thị:** **không** có thanh số. Cảm nhận qua V06/V13/V15/V16, lịch kín dần, notification dày thêm, self-talk thay đổi, idle mệt hơn.

### CAREER_FOCUS
- **Ý nghĩa:** Mức độ Dương ưu tiên cơ hội và phát triển công việc.
- **Dùng bởi:** A3_C02, A3_C05, A3_C08.
- **Khởi tạo:** 50

### STUDY_FOCUS
- **Ý nghĩa:** Mức độ Dương ưu tiên học tập / bước ngoặt tương lai (bao gồm việc giúp Minh học).
- **Dùng bởi:** A3_C05, A3_C08; cột "Học tập" của ending.
- **Khởi tạo:** 40

### CONNECTION_FOCUS
- **Ý nghĩa:** Mức độ Dương ưu tiên giữ kết nối với Nam, Minh, mẹ.
- **Dùng bởi:** A1_C09, A2_C06–C09, A3_C05–C11.
- **Khởi tạo:** 35

### 09.02.1 — Quy tắc khởi đầu lệch lệch

> Ba trục `CAREER_FOCUS(50) / STUDY_FOCUS(40) / CONNECTION_FOCUS(35)` **không cân bằng**.
> `CONNECTION_FOCUS` thấp nhất → game buộc người chơi **tự nhận ra mình đang bỏ bê kết nối**,
> rồi chủ động nâng nó lên. Đây là ý nghĩa thiết kế, không phải sự bất cẩn.

---

## 09.03 — TẦNG 2: 5 ROUTE STATES

### FAMILY_STATE — Enum
`GROWTH` / `MIXED` / `UNRESOLVED`

**Quy tắc phân giải** (chạy sau A1_C09):

| Kết quả | Điều kiện |
|---------|-----------|
| `GROWTH` | `FAMILY_TRUST >= 65` **VÀ** `FLAG_FAMILY_TRUTH` **VÀ** ít nhất 1 trong {`FLAG_SHARED_WORK`, `FLAG_ACCEPTED_HELP`, `FLAG_LET_MINH_GO`} |
| `MIXED` | `FAMILY_TRUST` 40–64 **HOẶC** có flag mâu thuẫn (vd: nói thật nhưng vẫn kiểm soát ở A3_C03) |
| `UNRESOLVED` | `FAMILY_TRUST < 40` **HOẶC** `FLAG_FAMILY_TRUTH` chưa bật **VÀ** Dương vẫn gánh thay |

`FAMILY_STATE` **chưa khóa vĩnh viễn** — có thể nâng lên ở A3_C10 nếu `FLAG_LET_MINH_GO`.

### ROMANCE_STATE — Enum
`ACTIVE` / `UNCERTAIN` / `ENDED`

| Kết quả | Điều kiện |
|---------|-----------|
| `ACTIVE` | A2_C09 chọn tiếp tục **HOẶC** A3_C09 chọn cam kết |
| `UNCERTAIN` | Hai người còn nói chuyện nhưng chưa cam kết rõ (A2_C09 = "cho nhau thời gian") |
| `ENDED` | `FLAG_LET_NAM_GO = true` **HOẶC** A2_C09 chọn "dừng lại trong sự thành thật" |

### PRIORITY_STATE — Enum
`CAREER` / `STUDY` / `CONNECTION` / `BALANCE` / `OVERLOAD`

| Kết quả | Điều kiện |
|---------|-----------|
| `CAREER` | `CAREER_FOCUS` là trục cao nhất **VÀ** `FLAG_WORK_OPPORTUNITY` |
| `STUDY` | `STUDY_FOCUS` là trục cao nhất **VÀ** `FLAG_STUDY_ROUTE` |
| `CONNECTION` | `CONNECTION_FOCUS` cao **VÀ** `FINAL_ORIENTATION = CONNECTION` |
| `BALANCE` | `FLAG_CHOSE_BALANCE` **VÀ** `OVERLOAD` đã kiểm soát (`OVERLOAD <= 55`) |
| `OVERLOAD` | `OVERLOAD >= 75` **VÀ** `BREAKING_POINT_STATE = PUSH_ON` |

> **Ưu tiên khi trùng:** `OVERLOAD` > `CAREER` > `STUDY` > `CONNECTION` > `BALANCE`.
> Nếu `OVERLOAD >= 75` thì không cần xét trục khác — người chơi đã chọn gánh hết.

### FINAL_ORIENTATION — Enum
`CONNECTION` / `SELF` / `RECOVERY`

Chốt tại A3_C11. Đây là câu trả lời cho câu hỏi *"Mình muốn sống như thế nào?"*

### BREAKING_POINT_STATE — Enum
`AWARE` / `PUSH_ON` / `WITHDRAW`

Chốt tại A3_C06. Quyết định toàn bộ cách trình bày về sau.

| Giá trị | Nghĩa |
|---------|-------|
| `AWARE` | Dương dừng lại và nói thật. Mở recovery path |
| `PUSH_ON` | Dương cố tiếp. Mở cảnh báo nghiêm trọng |
| `WITHDRAW` | Dương biến mất một thời gian. Quan hệ bị ảnh hưởng |

---

## 09.04 — TẦNG 2: 15 EVENT FLAGS

| Flag | Nghĩa | Set tại |
|------|-------|---------|
| `FLAG_SHARED_WORK` | Dương chọn chia việc với Minh | A1_C01 / A1_C09 |
| `FLAG_FAMILY_TRUTH` | Dương nói thật với Minh | A1_C06 |
| `FLAG_ACCEPTED_HELP` | Dương chấp nhận sự giúp đỡ | A1_C08 |
| `FLAG_CONTACTED_NAM` | Dương chủ động liên lạc lại với Nam | A2_C01 / A2_C07 |
| `FLAG_ROMANCE_HONESTY` | Dương nói thật về nỗi sợ và giới hạn | A2_C06 / A2_C08 |
| `FLAG_COMMIT_TO_NAM` | Dương xác nhận muốn xây tương lai cùng Nam | A2_C09 / A3_C09 |
| `FLAG_LET_NAM_GO` | Dương và Nam kết thúc trong sự thành thật | A2_C09 / A3_C09 |
| `FLAG_WORK_OPPORTUNITY` | Dương nhận hoặc theo đuổi cơ hội công việc | A3_C02 / A3_C08 |
| `FLAG_STUDY_ROUTE` | Dương chọn hướng học tập / bước ngoặt mới | A3_C05 / A3_C08 |
| `FLAG_CHOSE_BALANCE` | Dương chủ động giảm tải, chọn nhịp sống bền vững | A3_C01 / A3_C08 |
| `FLAG_ADMITTED_OVERLOAD` | Dương thừa nhận mình không ổn | A3_C06 |
| `FLAG_LET_MINH_GO` | Dương đồng hành nhưng để Minh tự bước | A3_C10 |
| `FLAG_DEBT_CLEARED` | Gia đình trả hết nợ | *(bổ sung từ G1)* tự động khi `DEBT <= 0` |
| `FLAG_FINANCIAL_RISK` | Không trả nợ 14 ngày liên tiếp | *(bổ sung từ G1)* tự động |
| `FLAG_SKILL_UP` | Dương đỗ kỳ thi nâng bậc thành công | *(bổ sung từ G1)* A3_C02 / E03 |

---

## 09.05 — TRIỆU LƯỜNG THAY ĐỔI

Không phải choice nào cũng ± giống nhau. Ba mức:

| Mức | Δ | Dùng cho |
|-----|---|----------|
| **Minor** | ±5 | Đổi tone câu thoại, phản ứng |
| **Major emotional** | ±10 đến ±20 | Turning point của quan hệ hoặc self-awareness |
| **Route-defining** | Δ lớn **+ set Flag** | Quyết định hướng |

**Ví dụ — A2_C06 "Cuộc cãi nhau nhỏ":**

| Chọn | Delta |
|------|-------|
| A — Nói thật | `ROMANCE_TRUST +15`, `SELF_AWARENESS +10`, set `FLAG_ROMANCE_HONESTY` |
| B — Giải thích là bận | `ROMANCE_TRUST −5` |
| C — Kết thúc cuộc gọi | `ROMANCE_TRUST −15`, `OVERLOAD +5` |

> `ROMANCE_STATE` **không** khóa ở A2_C06. Phải đợi A2_C09.

**Danh sách delta đầy đủ của cả 22 choice:** xem `10_CHOICE_BRANCHING.md`.

---

## 09.06 — ARC STATE RESOLUTION

Thứ tự chạy:

```
Sau A1_C09  → resolve FAMILY_STATE
Sau A2_C09  → resolve ROMANCE_STATE
Sau A3_C06  → set BREAKING_POINT_STATE
Sau A3_C08  → resolve PRIORITY_STATE
Sau A3_C11  → set FINAL_ORIENTATION
Sau A3_C12  → ENDING RESOLVER
```

---

## 09.07 — ENDING RESOLVER

### Thứ tự ưu tiên

> Mục đích: tránh một choice nhỏ vô tình khóa toàn bộ ending.

```
BƯỚC 1 — OVERLOAD & BREAKING_POINT_STATE
           nếu nghiêm trọng → khóa luôn, bỏ qua bước 2-3
BƯỚC 2 — PRIORITY_STATE (trục chủ đạo)
BƯỚC 3 — FINAL_ORIENTATION
BƯỚC 4 — ROMANCE_STATE / FLAG_COMMIT_TO_NAM
BƯỚC 5 — FAMILY_STATE / FLAG_LET_MINH_GO
BƯỚC 6 — chọn ending scene + biến thể epilogue
```

### Ví dụ ánh xạ

| Điều kiện | Kết quả |
|-----------|---------|
| `OVERLOAD` rất cao + `PUSH_ON` | E08 / E06 |
| `BALANCE` + `SELF`/`RECOVERY` + Family `GROWTH` | E01 hoặc E09 |
| `CAREER` + `SELF` | E03 |
| `STUDY` + `SELF` | E04 |
| `CONNECTION` + `ACTIVE` + `FLAG_COMMIT_TO_NAM` | E02 |
| `ENDED` + honesty/self-awareness cao | E05 |

---

## 09.08 — NGƯỠNG SỐ CHO TESTING

Đây là ngưỡng để viết test tự động. **Cân bằng tay khi prototype.**

| Kiểm tra | Điều kiện | Kỳ vọng |
|----------|-----------|---------|
| Overload nghiêm trọng | `STRESS >= 95` ∧ `ENERGY <= 10` ∧ ít ngày nghỉ | ending **E08** |
| Gánh hết | `RESPONSIBILITY >= 85` ∧ `OPENNESS < 40` | ending **E06** |
| Buông | `ROMANCE < 40` ∨ `FLAG_LET_NAM_GO` | ending **E05** |
| Trưởng thành | `BALANCE >= 75` ∧ `OPENNESS >= 70` ∧ `STRESS < 65` ∧ `FAMILY >= 65` ∧ (`WORK >= 60` ∨ `STUDY >= 60`) | ending **E01** |
| Tình yêu | `ROMANCE >= 85` ∧ `TRUST >= 75` ∧ `FLAG_COMMIT_TO_NAM` ∧ `STRESS < 80` | ending **E02** |
| Sự nghiệp | `WORK >= 90` ∧ `FLAG_WORK_OPPORTUNITY` ∧ `STRESS < 85` | ending **E03** |
| Học tập | `STUDY >= 90` ∧ `FAMILY >= 65` | ending **E04** |
| Bắt đầu lại | `SELF_AWARENESS >= 60` ∧ `BREAKING_POINT_STATE = AWARE` | ending **E07** |
| Trung tính | không thỏa ending nào ưu tiên | ending **E09** |

> ⚠️ Đây là **logic blueprint**, không phải bản cân bằng cuối. Khi prototype, đo tỉ lệ chơi thật rồi chỉnh.
> Mục tiêu thiết kế: **không ending nào đạt 100% xác suất** và **không ending nào dưới 2%**.

---

## 09.09 — UI VISIBILITY

| Biến | Hiển thị? | Nếu không thì thể hiện bằng |
|------|-----------|---------------------------|
| 7 Persistent Value | ❌ Ẩn hoàn toàn | Dialogue, biểu cảm, CG variant |
| 5 Route State | ❌ Ẩn hoàn toàn | Nội dung thay đổi ở 02.09 |
| 15 Flag | ❌ Ẩn | Callback dialogue, object state |
| `ENERGY` | ✅ HUD | Icon, không hiện số |
| `MONEY` / `DEBT` | ✅ HUD / Journal | Số tiền |
| `DAY` / `TIME_BLOCK` | ✅ HUD | Chữ + biểu tượng |
| `REPUTATION` | ❌ Ẩn | Lời sếp + kỳ thi |
| `OVERLOAD` | ⚠️ gián tiếp | V06/V13/V15/V16, lịch kín, notification dày, self-talk, idle |

**Nguyên tắc:** người chơi phải **cảm** được `PRIORITY_STATE`, không **đọc** được nó.
Chi tiết UI: `07_UI_HUD.md`.

---

## 09.10 — TÓM TẮT DỮ LIỆU

| Nhóm | Số lượng |
|------|----------|
| Resource (Tầng 1) | 6 |
| Persistent Values (Tầng 2) | 7 |
| Route States (Tầng 2) | 5 |
| Event Flags (Tầng 2) | 15 |
| Derived (Tầng 3) | 10 |
| **Tổng object lưu trong save** | **33** |

---

**TIẾP** → `10_CHOICE_BRANCHING.md` (chi tiết delta của 22 choice)
**QUAY LẠI** → `CANON_DECISIONS.md`