# 🌅 11. ENDING

> 9 ending group + resolution blueprint.
> Nguồn: `01_STORY.md` (chương) · `09_SYSTEM_VARIABLES.md` (state) · `10_CHOICE_BRANCHING.md` (delta).
> Điều kiện dưới đây là **blueprint logic**; ngưỡng số cụ thể cần tinh chỉnh khi balancing gameplay.

---

## 11.00 — ENDING OVERVIEW

**Tổng: 9 Ending Groups.**

| Nguyên tắc | |
|-------------|---|
| Không phân loại đơn giản thành Good / Bad | Mỗi ending phản ánh **một cách Dương ưu tiên** và đối diện với giới hạn. |
| Ending Group quyết định bởi | `PRIORITY_STATE` + `BREAKING_POINT_STATE` + `FINAL_ORIENTATION` |
| `ROMANCE_STATE` + `FAMILY_STATE` | tạo **biến thể epilogue**, không khoá toàn bộ ending |
| Growth Ending | khi Dương lựa chọn **có ý thức** và chấp nhận hậu quả |

### MASTER ENDING FLOW

```
ARC 1 → FAMILY_STATE
ARC 2 → ROMANCE_STATE
ARC 3 → PRIORITY_STATE + BREAKING_POINT_STATE
A3_C11 → FINAL_ORIENTATION
A3_C12 → (không choice, chỉ phản chiếu hậu quả)
   ↓
ENDING RESOLVER
   ↓
ENDING GROUP + NAM VARIANT + MINH VARIANT
```

---

## 11.01 — ENDING RESOLVER ORDER

| STEP | Việc |
|------|------|
| **1** | Check `OVERLOAD` và `BREAKING_POINT_STATE` |
| **2** | Resolve dominant `PRIORITY_STATE` |
| **3** | Read `FINAL_ORIENTATION` |
| **4** | Apply `ROMANCE_STATE` / `FLAG_COMMIT_TO_NAM` |
| **5** | Apply `FAMILY_STATE` / `FLAG_LET_MINH_GO` |
| **6** | Select final scene và epilogue variant |

> **Priority rule:** một route Overload nghiêm trọng có thể **override** các priority khác.
> Sau đó mới xét Career / Study / Connection / Balance.

### 11.01.1 — Pseudo-code resolver

```
// STEP 1 — Overload override
if OVERLOAD >= 85 and BREAKING_POINT_STATE == PUSH_ON:
    if ENERGY <= 10 or OVERLOAD >= 95:   → E08
    else:                                  → E06

// STEP 2 — Recovery override
if BREAKING_POINT_STATE == AWARE and FINAL_ORIENTATION == RECOVERY:
    → E07

// STEP 3 — Priority route
if PRIORITY_STATE == CAREER:    → E03
if PRIORITY_STATE == STUDY:     → E04
if PRIORITY_STATE == BALANCE and FINAL_ORIENTATION in {SELF, CONNECTION}:
    → E01

// STEP 4 — Connection route
if PRIORITY_STATE == CONNECTION and ROMANCE_STATE == ACTIVE
   and FLAG_COMMIT_TO_NAM:      → E02

// STEP 5 — Closure
if ROMANCE_STATE == ENDED or FLAG_LET_NAM_GO:
    → E05

// STEP 6 — Fallback
→ E09
```

> ⚠️ **Thứ tự này có chủ đích:** overload và recovery kiểm trước, vì chúng nói về **trạng thái tâm lý**;
> priority nói về **hướng đi**. Một người có thể chọn hướng đi rất rõ ràng nhưng vẫn kiệt sức — và người đó
> không thuộc về E03/E04.

### 11.01.2 — Ngưỡng số tham chiếu (từ `STORY_BIBLE`, dùng để test)

| Kiểm tra | Điều kiện | Ending |
|----------|-----------|--------|
| Overload nghiêm trọng | `STRESS >= 95` ∧ `ENERGY <= 10` | **E08** |
| Gánh hết | `RESPONSIBILITY >= 85` ∧ `OPENNESS < 40` | **E06** |
| Buông | `ROMANCE < 40` ∨ `FLAG_LET_NAM_GO` | **E05** |
| Trưởng thành | `BALANCE >= 75` ∧ `OPENNESS >= 70` ∧ `STRESS < 65` ∧ `FAMILY >= 65` ∧ (`WORK >= 60` ∨ `STUDY >= 60`) | **E01** |
| Tình yêu | `ROMANCE >= 85` ∧ `TRUST >= 75` ∧ `FLAG_COMMIT_TO_NAM` ∧ `STRESS < 80` | **E02** |
| Sự nghiệp | `WORK >= 90` ∧ `FLAG_WORK_OPPORTUNITY` ∧ `STRESS < 85` | **E03** |
| Học tập | `STUDY >= 90` ∧ `FAMILY >= 65` | **E04** |
| Bắt đầu lại | `SELF_AWARENESS >= 60` ∧ `BREAKING_POINT_STATE = AWARE` | **E07** |
| Trung tính | không thỏa ending nào ưu tiên | **E09** |

> ⚠️ Đây là **logic blueprint**, không phải bản cân bằng cuối.
> **Mục tiêu thiết kế:** không ending nào đạt 100% xác suất, không ending nào dưới 2%.

---

## 11.02 — 9 ENDING

---

### 🌟 E01 — A Life of Her Own

| | |
|---|---|
| 🎭 **Type** | True Growth / Self-Directed |
| 🎯 **Core meaning** | Dương không chọn hoàn hảo. Cô chọn một cuộc sống mình **có thể chịu trách nhiệm**, biết giới hạn và vẫn giữ kết nối với người quan trọng. |

**🔓 Entry conditions**
- `PRIORITY_STATE = BALANCE` hoặc self-directed path
- `SELF_AWARENESS` cao
- `BREAKING_POINT_STATE = AWARE` hoặc recovery-oriented
- `OVERLOAD` không ở trạng thái nghiêm trọng
- `FINAL_ORIENTATION = SELF` hoặc `CONNECTION` theo hướng lành mạnh

**🎬 Ending scene**
Dương bắt đầu một ngày mới với lịch không còn bị lấp kín.
Cô tự quyết một việc cho tương lai nhưng **không xoá toàn bộ** không gian dành cho người khác.
Một việc nhỏ giống Prologue xuất hiện.
Lần này Dương **không phản ứng tự động**; cô dừng lại và chọn điều mình thật sự cần làm.

**❤️ Nam — epilogue state**
| `ROMANCE_STATE` | Kết quả |
|------------------|---------|
| `ACTIVE` | Nam vẫn hiện diện như **một phần cuộc sống**, không phải phần thưởng của ending. |
| `UNCERTAIN` | Hai người vẫn giữ liên lạc, tương lai mở. |
| `ENDED` | Dương nhớ nhưng không quay lại chỉ vì sợ cô đơn. |

**🏠 Minh — epilogue state**
| `FAMILY_STATE` | Kết quả |
|------------------|---------|
| `GROWTH` | Minh tự bước trên con đường riêng và Dương hỗ trợ **đúng lúc**. |
| `MIXED` / `UNRESOLVED` | Vẫn còn va chạm, nhưng Dương bắt đầu thay đổi cách đối thoại. |

**⭐ Final image / line**
> **Mirror Prologue:** thay vì nói *"Chắc vẫn kịp"*, Dương nhìn lịch, mỉm cười và **chủ động để lại một khoảng trống**.

**🌿 Variants**
- Connection Variant — có cuộc gọi/tin nhắn từ Nam.
- Solo Variant — Dương tự bắt đầu một ngày mới.
- Family Variant — Minh rời nhà cho chặng đường riêng.

**🎨 Ending frame** → `L10` + open-space variant.

---

### ❤️ E02 — Together, Despite the Distance

| | |
|---|---|
| 🎭 **Type** | Romance Ending |
| 🎯 **Core meaning** | Dương và Nam **không giải quyết mọi khó khăn**; họ quyết định **cùng giải quyết** chúng. |

**🔓 Entry conditions**
- `ROMANCE_STATE = ACTIVE`
- `FLAG_COMMIT_TO_NAM = TRUE`
- `CONNECTION_FOCUS` cao hoặc `FINAL_ORIENTATION = CONNECTION`
- Không bị Overload severe override

**🎬 Ending scene**
Dương và Nam nói về **một kế hoạch cụ thể** thay vì những lời hứa mơ hồ.
Cả hai thừa nhận vẫn sẽ có những ngày không liên lạc đúng giờ.
Điều thay đổi là họ biết cách nói **trước khi** sự im lặng trở thành khoảng cách.
Cảnh kết tập trung vào một cuộc gọi dài — đủ để **thấy** kế hoạch được thực hiện.

> ⚠️ **Bổ sung do Q1:** vì hai người không gặp mặt, "kế hoạch gặp nhau" của E02 là
> **học thạc sĩ + visa + ngày bay** — một kế hoạch có thật, kéo dài, và cần cả hai giữ.
> Đây là ending khó nhất về mặt viết vì phải **không** biến nó thành "mọi thứ sẽ ổn".

**❤️ Nam — epilogue state**
`ACTIVE`, có cam kết rõ ràng nhưng vẫn giữ cuộc sống riêng.

**🏠 Minh — epilogue state**
| `FAMILY_STATE` | Kết quả |
|------------------|---------|
| `GROWTH` | Minh chứng kiến Dương **không còn bỏ quên bản thân** để giữ tình yêu. |

**⭐ Final image / line**
> Khoảng cách vẫn tồn tại trên bản đồ, nhưng **không còn là điều duy nhất nối hai người**.

**🌿 Variants**
- Family Growth Variant — Minh ủng hộ mối quan hệ.
- Busy Life Variant — hai người vẫn phải sắp xếp thời gian thực tế.
- Time-Zone Variant — kế hoạch còn bị múi giờ làm khó. Xem `02_GAMEPLAY_SYSTEM.md` 02.05.1.

**🎨 Ending frame** → `L09` commitment variant.

---

### 💼 E03 — The Promotion

| | |
|---|---|
| 🎭 **Type** | Career Ending |
| 🎯 **Core meaning** | Dương chọn một cơ hội nghề nghiệp quan trọng và **chấp nhận cái giá** của việc ưu tiên nó. |

**🔓 Entry conditions**
- `PRIORITY_STATE = CAREER`
- `CAREER_FOCUS` là trục nổi bật
- `FLAG_WORK_OPPORTUNITY = TRUE`
- `FINAL_ORIENTATION = SELF` hoặc `CONNECTION` nhưng Career vẫn dominant
- `BREAKING_POINT_STATE` không phải `PUSH_ON` severe

**🎬 Ending scene**
Dương bước vào vai trò hoặc cơ hội mới.
Cô nhìn thấy thành quả nhưng **không giả vờ** rằng mọi thứ khác không bị ảnh hưởng.
Một khoảnh khắc yên tĩnh cho thấy cô tự hỏi thành công này sẽ thay đổi cuộc sống thế nào.
Kết thúc bằng việc Dương bước vào không gian công việc mới với **chủ động rõ ràng**.

> 💰 **Bổ sung do Q1:** `FLAG_DEBT_CLEARED` / `FLAG_FINANCIAL_RISK` quyết định hậu quả tài chính:
> đây là lúc **thăng chức** tăng lương (480k → 940k → 1.1M/ngày) nhưng vẫn chưa trả hết 8 tỷ.
> E03 **không** phải "thoát nợ" — nó là "bước đi tiếp, chậm hơn".

**❤️ Nam — epilogue state**
| `ROMANCE_STATE` | Kết quả |
|------------------|---------|
| `ACTIVE` | Nam chúc mừng nhưng hai người **phải thương lượng lại** khoảng cách/thời gian. |
| `UNCERTAIN` | Một lời chúc ngắn, tương lai chưa khoá. |
| `ENDED` | Thành công **không xoá hoàn toàn** sự mất mát. |

**🏠 Minh — epilogue state**
| `FAMILY_STATE` | Kết quả |
|------------------|---------|
| `GROWTH` | Minh tự hào nhưng **không còn phụ thuộc** vào Dương. |

**⭐ Final image / line**
> Dương đứng trước một cánh cửa/cơ hội mới và **tự bước vào**.

**🌿 Variants**
- Connected Career — thành công nhưng vẫn giữ được kết nối.
- Lonely Success — thành công cao nhưng ít kết nối hơn.
- Debt-Cleared Variant — nếu `FLAG_DEBT_CLEARED`, thêm một dòng về việc tự trả xong nợ.

**🎨 Ending frame** → `L08` career variant.

---

### 📚 E04 — The Next Step

| | |
|---|---|
| 🎭 **Type** | Study / Future Growth Ending |
| 🎯 **Core meaning** | Dương chọn **đầu tư vào bước ngoặt dài hạn** thay vì chỉ chạy theo áp lực hiện tại. |

**🔓 Entry conditions**
- `PRIORITY_STATE = STUDY`
- `STUDY_FOCUS` cao
- `FLAG_STUDY_ROUTE = TRUE`
- `FINAL_ORIENTATION = SELF` hoặc `RECOVERY`

**🎬 Ending scene**
Dương chuẩn bị cho một môi trường mới: lớp học, chương trình, kỳ thi hoặc hành trình phát triển.
Cô **không biết hết** tương lai sẽ ra sao.
Điều khác với đầu game: cô **không cần biết hết trước khi bước tiếp**.
Cảnh cuối là Dương bắt đầu hành trình học tập mới.

> 📚 **Bổ sung do Q1:** đây cũng là ending gắn với **ước mơ của Minh** — em muốn làm bác sĩ.
> Nếu `FAMILY_STATE = GROWTH`, hai chị em cùng bước vào hai con đường khác nhau.
> Đó là lý do `STUDY_FOCUS` của Dương có ý nghĩa chứ không chỉ là sự nghiệp cá nhân.

**❤️ Nam — epilogue state**
`ACTIVE`/`UNCERTAIN` → Nam vẫn có thể **đồng hành từ xa** (hỗ trợ học tập, tài liệu, lịch).

**🏠 Minh — epilogue state**
| `FAMILY_STATE` | Kết quả |
|------------------|---------|
| `GROWTH` | Minh và Dương **đều bước vào chặng mới song song**. |

**⭐ Final image / line**
> Hai con đường khác nhau cùng mở ra phía trước.

**🌿 Variants**
- Romance Support Variant.
- Sibling Parallel Growth Variant.
- Nam-Masters-Also-Moving Variant — Nam cũng bắt đầu hồ sơ thạc sĩ: **hai người cùng đi, hai hướng khác nhau**.

**🎨 Ending frame** → `L08` study variant.

---

### 💔 E05 — Letting Go

| | |
|---|---|
| 🎭 **Type** | Honest Separation |
| 🎯 **Core meaning** | Buông một người **không nhất thiết là thất bại** — nếu cả hai đã nói thật về điều mình có và không thể cho nhau. |

**🔓 Entry conditions**
- `ROMANCE_STATE = ENDED` hoặc `FLAG_LET_NAM_GO = TRUE`
- `ROMANCE_TRUST` / `FLAG_ROMANCE_HONESTY` không quá thấp — **chia tay xảy ra sau đối thoại thật**
- `FINAL_ORIENTATION = SELF` hoặc `RECOVERY`

**🎬 Ending scene**
Dương và Nam có một cuộc trò chuyện bình tĩnh.
**Không có ai là phản diện.**
Họ thừa nhận những điều đã từng quan trọng.
Họ chia tay với **một sự rõ ràng** mà trước đây cả hai thiếu.

**❤️ Nam — epilogue state**
Nam tiếp tục con đường riêng. Ký ức vẫn tồn tại nhưng **không kéo Dương quay lại**.

**🏠 Minh — epilogue state**
| `FAMILY_STATE` | Kết quả |
|------------------|---------|
| `GROWTH` | Minh trở thành người thấy rõ Dương đang học cách buông. |

**⭐ Final image / line**
> Dương cất điện thoại, bước ra ngoài và **không quay lại ngay**.

**🌿 Variants**
- Soft Goodbye — vẫn giữ thiện cảm.
- Clean Break — không liên lạc thêm, nhưng không oán trách.
- Nam-First Variant — Nam quyết định sang Thụy Điển trước; Dương chọn để anh đi.

**🎨 Ending frame** → `L09` goodbye variant.

> ⚠️ **Rủi ro thiết kế:** E05 dễ trở thành "phần thưởng cho việc chọn thành thật".
> Nó chỉ đúng nếu `FLAG_ROMANCE_HONESTY` đã được set từ trước — nếu không, đây là **hậu quả**, không phải kết quả.

---

### 🏋️ E06 — The One Who Carries Everything

| | |
|---|---|
| 🎭 **Type** | Overload / Unresolved |
| 🎯 **Core meaning** | Dương tiếp tục tin rằng mọi thứ chỉ an toàn khi **cô tự gánh**. |

**🔓 Entry conditions**
- `PRIORITY_STATE = OVERLOAD`
- `OVERLOAD` cao
- `BREAKING_POINT_STATE = PUSH_ON`
- `SELF_AWARENESS` thấp hoặc Dương liên tục từ chối hỗ trợ

**🎬 Ending scene**
Dương hoàn thành **rất nhiều** việc.
Tin nhắn, lịch và nhiệm vụ đều được xử lý.
**Không có khoảnh khắc chiến thắng thực sự.**
Kết thúc là Dương tiếp tục bước sang một ngày khác với chiếc lịch vẫn kín.

**❤️ Nam — epilogue state**
| `ROMANCE_STATE` | Kết quả |
|------------------|---------|
| `ACTIVE` | Nam vẫn còn nhưng **khoảng cách cảm xúc lớn**. |
| `UNCERTAIN` | Sự im lặng tiếp tục. |
| `ENDED` | Nam chỉ còn trong ký ức. |

**🏠 Minh — epilogue state**
| `FAMILY_STATE` | Kết quả |
|------------------|---------|
| `UNRESOLVED` | Minh vẫn thấy Dương mệt nhưng Dương **chưa chịu thay đổi**. |

**⭐ Final image / line**
> Dương nói một phiên bản tối của câu Prologue: ***"Chắc... vẫn kịp."***

**🌿 Variants**
- Family Strain Variant.
- Romance Distance Variant.
- Solo Overload Variant.

**🎨 Ending frame** → `L06` push-on aftermath.

---

### 🌱 E07 — Starting Over

| | |
|---|---|
| 🎭 **Type** | Recovery / Reset |
| 🎯 **Core meaning** | Dương **không chọn tăng tốc**. Cô chọn dừng lại đủ lâu để xây lại nhịp sống. |

**🔓 Entry conditions**
- `FLAG_CHOSE_BALANCE = TRUE` hoặc recovery path
- `BREAKING_POINT_STATE = AWARE`
- `FINAL_ORIENTATION = RECOVERY`
- `OVERLOAD` đã được nhận diện và giảm

**🎬 Ending scene**
Dương chủ động bỏ hoặc hoãn một số thứ.
Cô có **một ngày không cần chứng minh năng suất**.
Cuộc sống chưa hoàn hảo nhưng bắt đầu có **nhịp thở**.
Kết thúc bằng một hành động nhỏ mang tính khởi đầu.

**❤️ Nam — epilogue state**
| `ROMANCE_STATE` | Kết quả |
|------------------|---------|
| `ACTIVE` | Nam tôn trọng quyết định giảm nhịp; hai người học cách kết nối khác đi. |
| `ENDED` | Dương hồi phục mà **không biến việc quay lại thành mục tiêu**. |

**🏠 Minh — epilogue state**
| `FAMILY_STATE` | Kết quả |
|------------------|---------|
| `GROWTH` | Minh không cần Dương gánh hộ, nhưng **vẫn ở cạnh khi được cần**. |

**⭐ Final image / line**
> Một căn phòng yên tĩnh, ánh sáng buổi sáng, **lịch có khoảng trống**.

**🌿 Variants**
- Romance Recovery Variant.
- Solo Recovery Variant.
- Family Recovery Variant.

**🎨 Ending frame** → `L06` aware + `L10` recovery variant.

---

### 🌙 E08 — Too Late to Rest

| | |
|---|---|
| 🎭 **Type** | Burnout Consequence |
| 🎯 **Core meaning** | **Đây không phải hình phạt vì Dương chăm chỉ.** Đây là hậu quả của việc liên tục bỏ qua tín hiệu rằng mình đã quá giới hạn. |

**🔓 Entry conditions**
- `OVERLOAD` rất cao (`STRESS >= 95`)
- `BREAKING_POINT_STATE = PUSH_ON` hoặc `WITHDRAW` kéo dài
- `ENERGY <= 10`
- Dương tiếp tục chọn làm tất cả **sau** Breaking Point

**🎬 Ending scene**
Dương cuối cùng **buộc phải** dừng.
Không phải vì cô đã chọn nghỉ, mà vì **không thể tiếp tục cùng nhịp cũ**.
Những việc từng nghĩ không thể giao cho ai vẫn phải được người khác xử lý.
Cảnh kết **mở**, không khẳng định Dương đã hồi phục.

**❤️ Nam — epilogue state**
| `ROMANCE_STATE` | Kết quả |
|------------------|---------|
| `ACTIVE` | Nam cố liên lạc nhưng **không thể thay Dương quyết định nghỉ**. |
| `ENDED` | Sự cô đơn rõ hơn. |

**🏠 Minh — epilogue state**
Minh chứng kiến giới hạn của Dương và **có thể trở thành người chủ động giúp đỡ**.

**⭐ Final image / line**
> Dương nhìn một lịch trống lần đầu tiên, nhưng lần này **không phải do cô chủ động tạo ra nó**.

**🌿 Variants**
- Support Present Variant.
- Isolation Variant.

**🎨 Ending frame** → `L06` severe aftermath.

---

### ☀️ E09 — Balanced / Neutral

| | |
|---|---|
| 🎭 **Type** | Quiet Continuation |
| 🎯 **Core meaning** | Không có bước ngoặt cực lớn. Dương tìm được **một cách tiếp tục** tương đối ổn định, dù vẫn còn nhiều điều chưa giải quyết. |

**🔓 Entry conditions**
- Không có route dominant cực mạnh
- `OVERLOAD` ở mức kiểm soát
- `FINAL_ORIENTATION` không đủ mạnh để vào ending đặc biệt khác
- Family/Romance ở trạng thái `MIXED` hoặc `UNCERTAIN`

**🎬 Ending scene**
Một ngày bình thường diễn ra.
Dương vẫn bận, vẫn có việc và vẫn có lúc chậm trễ.
Khác biệt là cô **nhận ra điều đó sớm hơn và điều chỉnh**.
**Không có câu trả lời cuối cùng.**

**❤️ Nam — epilogue state**
`ACTIVE`/`UNCERTAIN` → Nam xuất hiện như **một kết nối đang tiếp tục được xây**.

**🏠 Minh — epilogue state**
Minh tiếp tục trưởng thành và Dương **dần học cách không quản lý hộ**.

**⭐ Final image / line**
> **Mirror Prologue:** Dương nhìn lịch và **xoá đi một việc không cần thiết**.

**🌿 Variants**
- Romance Neutral Variant.
- Family Neutral Variant.
- Solo Neutral Variant.

**🎨 Ending frame** → `L10` neutral continuation variant.

---

## 11.03 — ENDING FLOWCHART

```
PROLOGUE
   ↓
ARC 1 — FAMILY
   ↓
FAMILY_STATE (GROWTH / MIXED / UNRESOLVED)
   ↓
ARC 2 — ROMANCE
   ↓
ROMANCE_STATE (ACTIVE / UNCERTAIN / ENDED)
   ↓
ARC 3 — LIFE / WORK / STUDY
   ↓
CHECK OVERLOAD
   ├── Severe + PUSH_ON → E06 / E08
   └── Controlled
   ↓
PRIORITY_STATE
   ├── CAREER     → E03
   ├── STUDY      → E04
   ├── CONNECTION + ACTIVE → E02
   ├── BALANCE    → E01 / E07 / E09
   └── Other/Mixed → E09
   ↓
ROMANCE ENDED + Honest Recovery → E05
   ↓
FAMILY_STATE + ROMANCE_STATE
   ↓
EPILOGUE VARIANT
```

---

## 11.04 — ENDING PRIORITY MATRIX

| Thứ tự | Nhóm | Ending |
|--------|------|--------|
| **Highest Override** | Burnout — severe overload + collapse/withdraw | **E08** |
| **Second Override** | Overload + persistent push-on | **E06** |
| **Route Endings** | Career / Study / Romance | **E03 / E04 / E02** |
| **Growth Endings** | Self-directed / Recovery | **E01 / E07** |
| **Relationship Closure** | Honest separation | **E05** |
| **Fallback** | Không route rõ | **E09** |

---

## 11.05 — EPILOGUE VARIANT SYSTEM

| Thành phần | Định nghĩa |
|------------|------------|
| **ENDING GROUP** | cuộc sống Dương chọn hoặc rơi vào |
| **NAM VARIANT** | trạng thái tình cảm sau ending (`ROMANCE_STATE` + `FLAG_COMMIT_TO_NAM`) |
| **MINH VARIANT** | trạng thái gia đình và mức độ trưởng thành độc lập (`FAMILY_STATE` + `FLAG_LET_MINH_GO`) |

> Nhờ hệ này, **cùng một Ending Group có thể có 2–4 epilogue khác nhau**
> mà không cần tạo quá nhiều ending hoàn toàn tách biệt.

**Số epilogue thực thi được:**

| Ending | Nam variant | Minh variant | Tổng |
|--------|-------------|-------------|------|
| E01 | 3 | 2 | 6 |
| E02 | 1 | 2 | 2 |
| E03 | 3 | 2 | 6 |
| E04 | 3 | 2 | 6 |
| E05 | 2 | 2 | 4 |
| E06 | 3 | 2 | 6 |
| E07 | 2 | 2 | 4 |
| E08 | 2 | 2 | 4 |
| E09 | 2 | 2 | 4 |
| **Tổng** | **21** | **18** | **~42 epilogue** |

> ⚠️ Đây là **con số lý thuyết**. Trong thực tế nên cắt bớt — chọn **1 Nam variant chính + 1 neutral**
> cho mỗi ending, giữ các variant đặc biệt cho E01/E03/E06. Mục tiêu thực tế: **20–24 epilogue**.

---

## 11.06 — ENDING DESIGN PRINCIPLES

1. **Không ending nào phủ nhận toàn bộ lựa chọn trước đó.**
2. **Ending tốt không đồng nghĩa** giữ được Nam, công việc hay gia đình cùng lúc.
3. **Ending xấu không cần bi kịch hoá** — đôi khi chỉ là Dương chưa học được điều mình cần học.
4. **Final scene luôn mirror Prologue** để người chơi thấy sự thay đổi.
5. **Nam và Minh có quỹ đạo riêng** trong epilogue — không chỉ là phần thưởng/phạt.
6. **Không có ending nào phủ định giá trị của cả một Arc.** Dương vẫn thông minh, vẫn có năng lực ở mọi kết thúc.

---

## 11.07 — TESTING CHECKLIST

Khi prototype, chạy các kịch bản sau và xác nhận đúng ending:

| # | Kịch bản | Kỳ vọng |
|---|----------|---------|
| 1 | Chọn A ở hầu hết major choice, không nhận overload | E06 |
| 2 | Chọn D ở `CH_A3_05`, B ở `CH_A3_06`, push tới cuối | **E08** |
| 3 | `CH_A3_06` = A (AWARE), `CH_A3_08` = C (balance), `CH_A3_11` = C (recovery) | E07 |
| 4 | `CH_A3_08` = C (balance), `CH_A3_11` = B (self), family GROWTH | E01 |
| 5 | `CH_A3_08` = A (career), `CH_A3_11` = B (self) | E03 |
| 6 | `CH_A3_08` = B (study), `CH_A3_11` = B (self), family GROWTH | E04 |
| 7 | `CH_A3_04` = A, `CH_A3_09` = A, `CH_A3_11` = A (connection) | E02 |
| 8 | `CH_A2_08` = A (honesty), `CH_A3_09` = C (let go) | E05 |
| 9 | Không chọn route nào rõ, `OVERLOAD` ~55 | E09 |

> 🎯 Sau khi cân bằng: **mỗi ending phải đạt được bằng ≥ 2 kịch bản tự nhiên**,
> và **không ending nào đạt 100%**.

---

**TIẾP** → Quay lại `00_OVERVIEW.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
