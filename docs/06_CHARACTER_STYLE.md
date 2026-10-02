# 🎭 06. CHARACTER STYLE

> Style guide nhân vật, outfit layer và bộ biểu cảm.
> **Pack này không tồn tại trong bộ `.docx` gốc** — số 06 bị bỏ trống khiến numbering nhảy 05 → 09.
> Viết mới hoàn toàn dựa trên asset thực tế trong `tệp ảnh nhân vật/` và `Pack Tổng/`.
> Ràng buộc nhân vật: `CANON_DECISIONS.md` mục 1.

---

## 06.00 — TẠI SAO PACK NÀY CẦN THIẾT

| Nguồn | Nói gì | Thiếu gì |
|-------|--------|----------|
| `01_STORY` | Dương, Minh, Nam — năm sinh, tính cách, mối quan hệ | Không có mô tả hình ảnh |
| `Pack Tổng/01-*` | Có character sheet cho Dương, Nam, Minh | Sheet vẽ kiểu **tĩnh**, không có quy tắc thay đổi |
| `Pack Tổng/02-Expression Pack` | Có bộ biểu cảm | Không có danh sách biểu cảm **bắt buộc theo từng cảnh** |
| `Pack Tổng/15-CHARACTER EXPANSION` | Có Minh, mẹ Dương, sếp | Chưa có outfit theo context |

**Không có pack này, artist sẽ tự quyết** → mỗi người vẽ một kiểu → không nhất quán.

---

## 06.01 — HỒ SƠ NHÂN VẬT

### CHAR_DUONG — Dương / Mira Eli

| | |
|---|---|
| **Sinh** | 2003 |
| **Tuổi tại P01** | 20 (lớp 12, vừa tốt nghiệp) |
| **Quốc tịch** | VN → Thụy Điển (nhập cư năm lớp 9) |
| **Nghề** | Điều dưỡng tại viện dưỡng lão |
| **Vai trò** | Nhân vật chính — người chơi điều khiển |

**Ngoại hình (theo character sheet):**
- Tóc đen dài. Có **hai phiên bản tóc** trong asset: bản tóc đen và bản thay đổi — phải chốt một bản chuẩn.
- Tỉ lệ sprite ngực–đùi, phù hợp game visual novel.
- Dung điệu mặc định: **hơi mệt, không buồn cười nhiều** — đây là biểu hiện của `OVERLOAD` khởi đầu 55.

**Tính cách (nhất quán xuyên game):**
| Đặc điểm | Biểu hiện | Phản ví dụ |
|-----------|-----------|------------|
| Có trách nhiệm đến mức gánh hết | Tự làm thay Minh trước khi hỏi | Không bao giờ "quên" |
| Nói thật rất khó | Trả lời bằng logic khi bị hỏi cảm xúc | Không nói dối, chỉ tránh |
| Có ý thức về giới hạn nhưng không thừa nhận | `SELF_AWARENESS = 25` | Không phải người không hiểu |
| Tốt, nhưng mệt | Giúp không cần hỏi | Không phải lạnh lùng |

**Giới hạn bắt buộc của nhân vật:**
- ❌ Không bao giờ hoàn giải mọi thứ.
- ❌ Không bao giờ làm việc hấp dẫn trừ khi nói thật về giới hạn.
- ❌ Không "đột nhiên tỏ ra mạnh mẽ" ở Arc 3 nếu chưa tăng `SELF_AWARENESS`.

---

### CHAR_MINH — Minh

| | |
|---|---|
| **Sinh** | 2006 |
| **Tuổi tại P01** | 17 (đang lớp 11–12) |
| **Quốc tịch** | VN → Thụy Điển (cùng đợt nhập cư) |
| **Ước mơ** | Bác sĩ hoặc nhà nghiên cứu |
| **Vai trò** | Em gái — **người nhìn thấy điều Dương né** |

**Ngoại hình:** nhỏ hơn Dương rõ rệt. Asset có chibi riêng (`chibi minh.png`) và chibi 2048×2048.

**Tính cách:**
- Không phản đối mạnh — vì vậy thói quen của Dương trông "bình thường" và không ai sửa.
- **Đặt câu hỏi thay vì ra lệnh.** Đây là vũ khí của Minh trong game.
- Khi Dương gánh hết, Minh không đánh — Minh **quan sát và ghi nhớ**.

**Cung cáo trong `FAMILY_STATE`:**
| Giá trị | Minh trông thế nào |
|----------|-------------------|
| `GROWTH` | Nói thẳng hơn, tự quyết nhiều hơn |
| `MIXED` | Vẫn hỏi nhưng bắt đầu giữ ý riêng |
| `UNRESOLVED` | Vẫn ngoan nhưng **ít nói với Dương hơn** |

---

### CHAR_NAM — Nam

| | |
|---|---|
| **Sinh** | 2004 |
| **Tuổi tại P01** | 19 (SV năm 2–3) |
| **Quốc tịch** | Việt Nam |
| **Nghề** | Sinh viên CNTT |
| **Mục tiêu** | Học thạc sĩ ở Thụy Điển để sang gặp Dương |
| **Vai trò** | Bạn trai yêu xa 5 năm — **chỉ qua điện thoại** |

**Ngoại hình:** asset có `chibi nam.png` và `chibi nam ko kính.png` (bản không đeo kính) — phải chốt một bản.

**Tính cách:**
- **Kiên nhẫn đến mức nguy hiểm.** Anh giữ máy cả buổi chiều chờ khung giờ của Dương.
- Không oán trách. Anh đặt câu hỏi, rồi chờ.
- **Không phải người cứu vãn.** Không xuất hiện đúng lúc, không giải quyết vấn đề từ xa.
  → Nếu Nam "cứu" được Dương bằng điện thoại, chủ đề game sập.

**Cung cấp trong `ROMANCE_STATE`:**
| Giá trị | Giọng / cách hiển thị |
|----------|----------------------|
| `ACTIVE` | Nói chuyện tự nhiên, ít phòng thủ |
| `UNCERTAIN` | Nhiều câu hỏi hơn, chậm hơn |
| `ENDED` | Vẫn lịch sự, nhưng **không còn gọi chủ động** |

---

### CHAR_MOTHER — Mẹ Dương

| | |
|---|---|
| **Quốc tịch** | VN → Thụy Điển |
| **Vai trò** | Đang gánh vác cùng Dương, sức khoẻ không tốt |
| **Asset** | `Pack Tổng/15-Character sheet Mẹ Dương.png` (1380×1140) |

**Tính cách:**
- Không phải người để Dương gánh thêm. Sức kho�é kém là lý do Dương phải chịu thêm.
- **Không được biến thành nạn nhân.** Cô ấy vẫn là người mẹ, vẫn có ý kiến.
- Hiện diện qua điện thoại/đường dây nếu scene cần; không cần sprite thường trực.

---

### CHAR_ANNIKA — Sếp Annika

| | |
|---|---|
| **Tuổi** | ~45 |
| **Quốc tịch** | Thụy Điển |
| **Vai trò** | Nữ trưởng ca. **Người duy nhất có thể cho Dương thăng chức.** |
| **Asset** | `Pack Tổng/15-Character sheet Sếp của Dương.png` (1536×1024) |

**Tính cách — ba điểm, cả ba đều có chủ đích:**
1. **Tốt bụng nhưng lười** — không phải kiểu ác ý, mà kiểu không kiểm tra.
2. **Hay vắng mặt** — đi du lịch hoặc "ốm". Đây là lý do Dương phải tự xoay xở.
3. **Nói tiếng Thụy Điển / dùng tiếng Anh** — nhắc nhở liên tục rằng Dương là người nhập cư.
   → Đây là nguồn áp lực **duy nhất không đến từ chính Dương**, và là nguồn áp lực dễ khiến người chơi thù ghét sếp.
   → Đó là chủ ý: sếp không hoàn toàn đúng, nhưng cũng không phải kẻ xấu.

**Vai trò cơ chế:**
- Sếp **không thể** thăng chức Dương miễn phí. Phải đỗ kỳ thi nâng bậc 1–2 buổi.
- `REPUTATION >= 55` mới mở đường lên điều dưỡng đã xét.

---

## 06.02 — OUTFIT LAYER

> ⚠️ **Asset hiện tại KHÔNG có layer.** Tất cả nhân vật là ảnh phẳng 1 file.
> Bảng dưới là **spec yêu cầu**, chưa phải thứ đang có.

### 06.02.1 — Layer stack

```
CHAR_{id}_base_{expression}.png     ← thân + mặt
CHAR_{id}_hair_{color}.png          ← tóc (che khuôn mặt một phần)
CHAR_{id}_outfit_{id}.png           ← áo khoác ngoài
CHAR_{id}_bottom_{id}.png           ← quần / váy
CHAR_{id}_prop_{id}.png             ← phụ kiện (kính, khăn, túi)
```

### 06.02.2 — Outfit cần cho từng nhân vật

#### CHAR_DUONG — 5 outfit

| ID | Outfit | Dùng ở | Ghi chú |
|----|--------|---------|---------|
| `DUO_WORK` | Đồng phục/đồng phục điều dưỡng viện dưỡng | `A2_C05`, `A3_C01`–`A3_C06` | Không có mũ/bảo hiểm — hợp setting Thụy Điển |
| `DUO_HOME` | Đồ ở nhà | Arc 1, `A3_C03`, `A3_C10`, `A3_C11` | **Mặc định nhiều nhất** |
| `DUO_OUT` | Đồ ra ngoài / đi gặp sếp | `A2_C02`, `A3_C02`, `A3_C08` | |
| `DUO_NIGHT` | Đồ ngủ / đồ sau ca đêm | `A1_C07`, `A2_C06`, `A3_C06` | Cần cho `ENERGY < 20` idle |
| `DUO_STUDY` | Đồ học tập | `A3_C05`, `A3_C08` route Study | |

> 💡 Nếu không đủ budget cho 5 outfit, **bắt buộc giữ 3**: `DUO_WORK`, `DUO_HOME`, `DUO_NIGHT`.
> Vì Arc 1–2 diễn chủ yếu ở nhà ban đêm, thiếu `DUO_NIGHT` sẽ phá tone ngay.

#### CHAR_MINH — 3 outfit

| ID | Outfit | Dùng ở | Ghi chú |
|----|--------|---------|---------|
| `MIN_HOME` | Đồ ở nhà / đi học | Arc 1, Arc 3 | Mặc đồ sơ mi học sinh — nhắc nhở Dương về chuyện đi học |
| `MIN_STUDY` | Đồ đi học thật | `A3_C03`, `A3_C10` | Khoảnh khắc Minh bước ra khỏi nhà |
| `MIN_OUT` | Đồ đi chơi / du lịch | `A3_C10` departure | |

#### CHAR_NAM — 3 outfit

| ID | Outfit | Dùng ở | Ghi chú |
|----|--------|---------|---------|
| `NAM_HOME` | Đồ ở nhà | A2_C01, A2_C07 | Việt Nam — khác hoàn toàn Dương |
| `NAM_CAMPUS` | Đồ đi học | A1_C04, A2_C04, A2_C08, A3_C09 | **Outfit phổ biến nhất** — anh luôn ở trường |
| `NAM_WORK` | Đồ đi làm thêm | A2_C09, A3_C04 | Phản ánh anh đang cố gồng |

> ⚠️ **Bắt buộc:** Dương và Nam phải **khác nhau rõ về màu và kiểu** ở mọi outfit.
> Hai người không gặp mặt — nếu trông giống nhau, người chơi sẽ nhầm khung hình.

#### CHAR_ANNIKA — 2 outfit

| ID | Outfit | Dùng ở | Ghi chú |
|----|--------|---------|---------|
| `ANN_WORK` | Công nghiệp Thụy Điển — chuyên nghiệp, lạnh | `A3_C02` | Cố ý khác "ấm" với vai trò tốt bụng |
| `ANN_CASUAL` | Đồ casual khi đi du lịch / vắng mặt | Có thể xuất hiện 1 lần | Nhắc Dương: sếp vắng mặt không phải vì bệnh |

---

## 06.03 — BỘ BIỂU CẢM

> Asset có `Pack Tổng/02-Expression Pack for Dương, Nam, and Minh.png` nhưng **chưa rõ có đủ các biểu cảm dưới đây không.**

### 06.03.1 — Bộ biểu cảm chuẩn (bắt buộc cho cả 3 NV chính)

| ID | Biểu cảm | Dùng khi |
|----|---------|---------|
| `EX_NEUTRAL` | Trung tính, mệt nhẹ | **Mặc định toàn game** |
| `EX_TIRED` | Mệt rõ — mí mắt, vai | `ENERGY < 20`, `OVERLOAD > 70` |
| `EX_SMILE_SOFT` | Cười nhẹ, thật | Sau A1_C08, A3_C10 |
| `EX_SMILE_BRIGHT` | Cười rõ | Chỉ khi `SELF_AWARENESS` cao — hiếm, phải kiếm |
| `EX_WORRY` | Lo | `OVERLOAD` cao, sắp hết tiền |
| `EX_SAD` | Buồn, im | `ROMANCE_TRUST` thấp, `A2_C09` |
| `EX_ANGRY` | Giận (nhỏ) | `A1_C05`, `A2_C06` |
| `EX_CRY` | Khóc / nghẹn | `F07`, `R08`, `A3_C09` |
| `EX_SURPRISE` | Ngỡ ngàng | Mới gặp / tin bất ngờ |
| `EX_DETERMINED` | Quyết tâm | `A1_C09`, `A3_C06` chọn A, `A3_C08` |
| `EX_DRAINED` | Kiệt sức | `E06`, `E08` |
| `EX_PEACEFUL` | Bình yên | `E01`, `E07`, `E09` |

### 06.03.2 — Biểu cảm bắt buộc theo CG cụ thể

| CG | Cần biểu cảm |
|----|------------|
| **F07** — Lần đầu nói thật | `EX_DETERMINED` (nói thật) / `EX_ANGRY` (phản bác) / `EX_SAD` (bỏ đi) → **3 biến thể** |
| **R08** — Nói thật | `EX_CRY` / `EX_SURPRISE` / `EX_NEUTRAL` → **3 biến thể** |
| **L06** — Breaking Point | **3 composition khác nhau**, không chỉ khác biểu cảm: ngồi xuống / đứng lại / bỏ đi |

### 06.03.3 — Minh: biểu cảm riêng

| ID | Biểu cảm | Dùng khi |
|----|---------|---------|
| `MIN_NEUTRAL` | Trung tính | Mặc định |
| `MIN_QUIET` | Nhỏ giọng, nhìn xuống | `FAMILY_STATE = UNRESOLVED` |
| `MIN_HURT` | Bị tổn thương, nhưng không khóc | `A1_C06` |
| `MIN_FIRM` | Kiên định, đã lớn | `A3_C10`, `FAMILY_STATE = GROWTH` |
| `MIN_HOPE` | Hy vọng, mắt sáng | Khi nói về ước mơ bác sĩ — `A3_C03` |

### 06.03.4 — Nam: biểu cảm riêng

| ID | Biểu cảm | Dùng khi |
|----|---------|---------|
| `NAM_NEUTRAL` | Trung tính, ấm | Mặc định |
| `NAM_PATIENT` | Kiên nhẫn, mỉm cười nhẹ | Chờ Dương, `A2_C06` |
| `NAM_TIRED_WAIT` | Mệt vì chờ quá lâu | `A2_C06` — **biểu cảm quan trọng nhất của Nam** |
| `NAM_HURT` | Tổn thương nhưng giấu | `A2_C09` chọn C, `A3_C09` |
| `NAM_OPEN` | Thành thật, mở lòng | `A2_C08` |

> ⚠️ `NAM_TIRED_WAIT` là biểu cảm **nâng ending lên** của cả Arc 2.
> Nếu Nam luôn tỏ ra vui khi chờ, người chơi sẽ không bao giờ thấy sự bất công của khoảng cách.
> Đây là lý do setting "không gặp mặt" **không phải hình phạt** mà là công cụ kể chuyện.

---

## 06.04 — QUY TẮC VẼ NHẤT QUÁN

1. **Tỉ lệ không đổi.** Mọi frame cùng nhân vật phải giữ cùng tỉ lệ và đường chân đất.
2. **Ánh sáng theo map, không theo mood.** Dương trong nhà ban đêm vẫn phải khớp `A06` ambience — nếu sprite sáng rõ hơn background thì sai.
3. **Không vẽ biểu cảm mới trong game.** Chỉ dùng 12 biểu cảm chuẩn + biến thể đã liệt kê. Nếu cần thêm → cập nhật file này trước.
4. **Dương không bao giờ đeo kính.** Chỉ Nam có kính (và asset có 2 bản nam có/không kính — chốt một).
5. **Màu tóc:** chốt một bản cho Dương. Asset có "bản tóc đen" và bản gốc — phải so sánh và bỏ bản thừa.
6. **Không thêm nhân vật có tên mới ngoài 5 người đã chốt.** NPC vô danh thì được.

---

## 06.05 — CHIẾN LƯỢC KHI BUDGET HẠN CHẾ

Nếu không đủ tiền/thời gian cho đủ outfit và 12 biểu cảm:

| Ưu tiên | Nội dung | Lý do |
|---------|----------|-------|
| **1** | `DUO_HOME` + `DUO_WORK` | 2 outfit phủ 70% game |
| **2** | `EX_NEUTRAL`, `EX_TIRED`, `EX_SAD`, `EX_DETERMINED` | 4 biểu cảm phủ 80% tình huống |
| **3** | `MIN_HOME` + `NAM_CAMPUS` | Minh và Nam phải nhận diện được |
| **4** | 3 biến thể F07 | CG turning point đầu tiên, người chơi nhớ lâu nhất |
| **5** | `CHAR_ANNIKA` | Không có sếp thì A3_C02 không diễn được |

> ❌ **Không hy sinh:** `CHAR_NAM` nói chuyện được. Không có Nam thì game mất 1/3 nội dung.

---

**TIẾP** → `07_UI_HUD.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
