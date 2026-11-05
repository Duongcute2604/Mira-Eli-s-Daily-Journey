# 🔀 10. CHOICE & BRANCHING

> 22 choice, tách riêng khỏi Story Pack. Chuyển ở đây là con số cụ thể, không phải mô tả định tính.
> Ràng buộc tổng quát xem `CANON_DECISIONS.md`.

---

## 10.00 — TỔNG QUAN

**Choice không xuất hiện ở mọi chapter.** Ưu tiên những khoảnh khắc thật sự thể hiện cách Dương sống và đối diện với người khác.

| Loại | Tác động | Dùng ở |
|------|----------|---------|
| **Minor Choice** | Đổi tone cảm xúc, câu thoại | Không khóa route |
| **Relationship Choice** | Đổi trạng thái quan hệ | Đầu Arc 1, Arc 2 |
| **Route Choice** | Ảnh hưởng hướng kết thúc | Arc 3 |

**Luật thiết kế:**
- Không có đáp án tốt tuyệt đối. Lựa chọn thể hiện **ưu tiên** và **cái giá phải trả**.
- Không nên có quá nhiều **fake choice** — lựa chọn quan trọng phải có hậu quả nhìn thấy được.
- **Không khóa ending quá sớm**: phần lớn route xác định ở Arc 3.
- Choice quan trọng nhất: `A1_C06`, `A2_C06`, `A2_C08`, `A2_C09`, `A3_C05`–`A3_C11`.

### Luồng phân nhánh tổng thể

```
MINOR CHOICE          → CHARACTER TONE
RELATIONSHIP CHOICE   → FAMILY_STATE / ROMANCE_STATE
ROUTE CHOICE          → PRIORITY_STATE
FINAL DECISION        → FINAL_ORIENTATION → ENDING GROUP
```

### Quy ước ghi delta

| Ký hiệu | Nghĩa |
|---------|--------|
| `FT` | `FAMILY_TRUST` |
| `RT` | `ROMANCE_TRUST` |
| `SA` | `SELF_AWARENESS` |
| `OL` | `OVERLOAD` |
| `CF` | `CAREER_FOCUS` |
| `SF` | `STUDY_FOCUS` |
| `NF` | `CONNECTION_FOCUS` |
| `EN` | `ENERGY` (resource) |
| `RE` | `REPUTATION` (resource) |

---

## 10.01 — ARC 1: 🏠 FAMILY

### CH_A1_01 — 📍 A1_C01 — Một buổi sáng quen thuộc
> **Tình huống:** Minh hỏi có cần giúp việc đang dang dở không.

| | Lựa chọn | Delta | Hiệu ứng tức thì |
|---|----------|-------|------------------|
| **A** | "Không sao, để chị làm." | `FT +5`, `OL +5`, `SA −3`, `EN −5` | Củng cố thói quen tự gánh |
| **B** | "Ừ, em làm giúp chị phần này." | `FT +10`, `SA +3`, `OL −5`, set `FLAG_SHARED_WORK` | Mở sớm hướng hợp tác |

🌱 **Dài hạn:** đổi tone Family, chưa khóa route.
💡 Đây là **choice đầu tiên** — chọn A thì mọi thứ về sau khó hơn, nhưng người chơi vẫn cảm thấy bình thường. **Đó là chủ đích.**

---

### CH_A1_03 — 📍 A1_C03 — Cuộc gọi
> **Tình huống:** Việc gia đình xuất hiện cùng lúc với tin nhắn của Nam. Dương ưu tiên gì?

| | Lựa chọn | Delta | Hiệu ứng tức thì |
|---|----------|-------|------------------|
| **A** | Xử lý ngay việc gia đình | `FT +5`, `RT −8`, `OL +5` | Nam tiếp tục chờ |
| **B** | Báo rõ cho Nam mình đang bận | `RT +10`, `SA +3`, `NF +5` | Không biến sự im lặng thành câu trả lời |

🌱 **Dài hạn:** ảnh hưởng `ROMANCE_STATE` đầu Arc 2.
💡 Chọn B là lần đầu Dương **cố chủ động không phải ai**. `SA +3` có chủ đích — đây là hạt giống nhỏ.

---

### CH_A1_06 — 📍 A1_C06 — Lần đầu nói thật ⭐ **MAJOR**
> **Tình huống:** Minh nói: *"Chị không cho ai cơ hội giúp chị cả."*

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Phản bác — *"Chị làm vì mọi người thôi."* | `FT −12`, `OL +8`, `SA −8` |
| **B** | Nói thật — thừa nhận mình mệt và sợ không xử lý hết | `FT +18`, `SA +15`, `OL +10`, set `FLAG_FAMILY_TRUTH` |
| **C** | Im lặng rồi bỏ đi | `FT −8`, `OL +3`, `SA +2` |

🌱 **Dài hạn:** choice lớn của Arc 1, quyết định `FAMILY_STATE` trước Arc 3.
⚠️ Lưu ý: **chọn B vẫn tăng `OVERLOAD`** — nói thật không phải là giải quyết xong. Người chơi phải **nói thật nhiều lần** trước khi `OVERLOAD` giảm thật.

---

### CH_A1_08 — 📍 A1_C08 — Người không nói gì
> **Tình huống:** Minh đã xử lý xong một việc Dương thường gánh.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Cảm ơn và để Minh tiếp tục | `FT +15`, `SA +12`, `OL −8`, set `FLAG_ACCEPTED_HELP` |
| **B** | Kiểm tra lại và làm lại | `FT −10`, `SA −5`, `OL +5` |

🌱 **Dài hạn:** ảnh hưởng cách Minh nói chuyện ở A3_C03.

---

### CH_A1_09 — 📍 A1_C09 — Không phải một mình
> **Tình huống:** Một việc quen thuộc lại xuất hiện — y hệt A1_C01.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Tự làm ngay | `FT +5`, `OL +8`, `SA −3` |
| **B** | Hỏi Minh và chia việc | `FT +18`, `SA +10`, `OL −10`, `NF +5`, set `FLAG_SHARED_WORK` |

🌱 **Dài hạn:** xác lập `FAMILY_STATE`. Dùng ở A3_C03, A3_C07, A3_C10 và Ending.
⭐ **Mirror A1_C01** — nếu người chơi chọn A ở A1_C01 và B ở A1_C09, đó là bước tiến thật sự, mạnh hơn là chọn B cả hai.

---

## 10.02 — ARC 2: ❤️ ROMANCE

> ⚠️ **Nam luôn ở Việt Nam.** Mọi scene là tin nhắn / call / video call.

### CH_A2_01 — 📍 A2_C01 — Tin nhắn chưa trả lời
> **Tình huống:** Dương thấy nhiều tin nhắn chưa trả lời của Nam.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Nhắn một câu ngắn: *"Xin lỗi, chị bận."* | `RT +5`, `NF +3` |
| **B** | Gọi cho Nam | `RT +12`, `NF +8`, `SA +3`, set `FLAG_CONTACTED_NAM`, `EN −5` |
| **C** | Để tối rồi nói | `RT −10`, `OL +5`, `NF −5` |

🌱 **Dài hạn:** định tone Romance đầu Arc.

---

### CH_A2_04 — 📍 A2_C04 — Kế hoạch gặp nhau
> **Tình huống:** Video call. Nam hỏi: *"Nếu khó khăn, chị vẫn muốn gặp em chứ?"*

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | "Có, chị muốn." | `RT +12`, `NF +8` |
| **B** | "Chị không biết." | `RT +8`, `SA +8` |
| **C** | Chuyển sang nói về trở ngại | `RT −5`, `SA −5`, `OL +5` |

🌱 **Dài hạn:** ảnh hưởng nội dung A2_C08.
💡 B là choice hay nhất cho nhân vật: trung thực mà chưa chắc chắn.

---

### CH_A2_06 — 📍 A2_C06 — Cuộc cãi nhau nhỏ ⭐ **MAJOR**
> **Tình huống:** Nam nói anh không muốn chỉ là một mục trong lịch.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Nói thật: Dương sợ không đủ cho mọi thứ | `RT +15`, `SA +12`, set `FLAG_ROMANCE_HONESTY`, `EN −5` |
| **B** | Giải thích rằng Dương đang rất bận | `RT −5`, `SA −3` |
| **C** | Kết thúc cuộc gọi | `RT −15`, `OL +5`, `NF −8` |

🌱 **Dài hạn:** quyết định trạng thái Romance giữa Arc.
⚠️ `ROMANCE_STATE` **không khóa** ở đây. Phải đợi A2_C09.

---

### CH_A2_07 — 📍 A2_C07 — Những ngày không có tin nhắn
> **Tình huống:** Sau nhiều ngày im lặng.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Chủ động nhắn | `RT +12`, `SA +8`, `NF +8`, set `FLAG_CONTACTED_NAM` |
| **B** | Chờ Nam liên lạc | `RT −5`, `NF −5` |

🌱 **Dài hạn:** ảnh hưởng mức độ chủ động của Dương ở A2_C09.
💡 Đây là choice **đắt nhất về mặt tinh thần** trong Arc 2: nhận rủi ro bị từ chối.

---

### CH_A2_08 — 📍 A2_C08 — Nói thật ⭐ **MAJOR**
> **Tình huống:** Nam hỏi Dương thực sự sợ điều gì.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Nói rõ nỗi sợ | `RT +18`, `SA +15`, set `FLAG_ROMANCE_HONESTY` |
| **B** | Chỉ nói "chị sẽ cố" | `RT +5` |
| **C** | Thừa nhận chưa biết mình muốn gì | `RT +10`, `SA +12`, `NF +5` |

🌱 **Dài hạn:** ảnh hưởng trực tiếp A2_C09 và A3_C04.

---

### CH_A2_09 — 📍 A2_C09 — Cuộc gọi cuối Arc ⭐ **ROUTE**
> **Tình huống:** Dương và Nam thống nhất điều gì?
> *Bối cảnh sau Q1: Dương ở sân ga tàu Thụy Điển, Nam ở sân bay Việt Nam — hai bờ gọi nhau.*

| | Lựa chọn | Delta | Kết quả |
|---|----------|-------|---------|
| **A** | Cùng cố gắng tiếp tục | `RT +15`, `NF +12` | `ROMANCE_STATE = ACTIVE` |
| **B** | Cho nhau thời gian | `RT +5`, `SA +5` | `ROMANCE_STATE = UNCERTAIN` |
| **C** | Dừng lại trong sự thành thật | `SA +15`, `OL +10` | `ROMANCE_STATE = ENDED`, set `FLAG_LET_NAM_GO` |

🌱 **Dài hạn:** route state ảnh hưởng **toàn bộ** sự xuất hiện của Nam ở Arc 3.

---

## 10.03 — ARC 3: 🌱 LIFE / WORK / STUDY

### CH_A3_01 — 📍 A3_C01 — Một lịch trình quá đầy
> **Tình huống:** Dương nhìn lịch kín của tuần.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Cố giữ toàn bộ kế hoạch | `OL +12`, `EN −20`, `SA −5` |
| **B** | Bỏ một số việc | `OL −10`, `SA +5` |
| **C** | Xin hỗ trợ / sắp xếp lại | `OL −15`, `SA +10`, `FT +8`, `NF +8` |

🌱 **Dài hạn:** ảnh hưởng cách `BREAKING_POINT` được xây dựng.
⚠️ Chọn A **gần như chốt ending E06/E08 ngay tại đây**. Đó là chủ đích — người chơi phải hiểu hậu quả.

---

### CH_A3_02 — 📍 A3_C02 — Một ca làm khó
> **Tình huống:** Sếp Annika đưa ra cơ hội thăng chức, cần thêm thời gian.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Nhận ngay | `CF +18`, `OL +10`, `EN −25`, `NF −8`, set `FLAG_WORK_OPPORTUNITY` |
| **B** | Thương lượng giới hạn | `CF +10`, `SA +8`, `OL −5`, set `FLAG_WORK_OPPORTUNITY` |
| **C** | Từ chối | `CF −10`, `NF +10`, `OL −8`, `EN +10` |

🌱 **Dài hạn:** dùng ở A3_C08 và Ending.
💡 B là lựa chọn **trưởng thành nhất**: không phải từ chối ước mơ, cũng không phải ôm hết.

---

### CH_A3_03 — 📍 A3_C03 — Minh và con đường riêng
> **Tình huống:** Minh nói muốn tự xử lý phần chuẩn bị cho tương lai.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Tôn trọng và hỗ trợ khi được hỏi | `FT +15`, `SF +8`, `SA +10`, `OL −8` |
| **B** | Vẫn cố chuẩn bị mọi thứ | `FT −10`, `OL +12`, `SF +10`, `SA −5` |

🌱 **Dài hạn:** ảnh hưởng A3_C10.
💡 B là **cái bẫy thật sự của nhân vật**: nó làm Minh có thành tích nhưng **làm hỏng quan hệ**. Không có lựa chọn nào "vừa đẹp vừa đúng".

---

### CH_A3_04 — 📍 A3_C04 — Một cuộc gọi quan trọng
> **Tình huống:** Nam hỏi Dương đang xây dựng cuộc sống nào.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Có chỗ cho tình yêu | `RT +12`, `NF +15`, set `FLAG_COMMIT_TO_NAM` |
| **B** | Chưa biết, nhưng muốn tìm câu trả lời | `RT +8`, `SA +12` |
| **C** | Tạm né tránh | `RT −8`, `SA −5`, `OL +5` |

🌱 **Dài hạn:** đối chiếu ở A3_C09.

---

### CH_A3_05 — 📍 A3_C05 — Không thể chọn hết ⭐ **ROUTE LỚN**
> **Tình huống:** Hai việc quan trọng trùng thời điểm.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Công việc / cơ hội | `CF +22`, `OL +12`, `NF −8`, `SF −5` |
| **B** | Học tập / tương lai dài hạn | `SF +22`, `OL +8`, `NF −5`, `CF −8` |
| **C** | Người thân / quan hệ | `NF +22`, `FT +8`, `RT +8`, `CF −10`, `SF −5` |
| **D** | Cố làm cả hai | `OL +22`, `EN −30`, `SA −8` |

🌱 **Dài hạn:** một trong các trục ending chính.
⚠️ **D là lựa chọn thu hút người chơi** — ai cũng thích "làm hết". Nó là đầu vào của E08.

---

### CH_A3_06 — 📍 A3_C06 — Breaking Point ⭐ **MAJOR**
> **Tình huống:** Dương không theo kịp nhịp cũ nữa.

| | Lựa chọn | Delta | Kết quả |
|---|----------|-------|---------|
| **A** | Dừng lại và nói mình không ổn | `SA +20`, `OL −20`, set `FLAG_ADMITTED_OVERLOAD`, `BREAKING_POINT_STATE = AWARE` | Mở recovery path |
| **B** | Cố làm tiếp | `OL +18`, `SA −8`, `BREAKING_POINT_STATE = PUSH_ON` | Nguy cơ E08 |
| **C** | Biến mất một thời gian | `OL −5`, `NF −15`, `FT −10`, `SA +5`, `BREAKING_POINT_STATE = WITHDRAW` | Quan hệ bị ảnh hưởng |

🌱 **Dài hạn:** quyết định tone hậu Breaking Point.

---

### CH_A3_07 — 📍 A3_C07 — Ba cuộc nói chuyện
> **Tình huống:** Sau ba cuộc nói chuyện, Dương tự hỏi mình muốn gì.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | "Chị muốn sống theo cách của mình." | `SA +15`, `CF +10`, `SF +5`, `NF −5` |
| **B** | "Chị muốn giữ người quan trọng." | `NF +18`, `RT +10`, `FT +8`, `CF −8` |
| **C** | "Chị muốn đi xa hơn trong công việc/học tập." | `CF +12`, `SF +12`, `SA +8`, `NF −10` |

🌱 **Dài hạn:** đối chiếu với hành động ở A3_C08–11.
💡 Đây là choice **duy nhất** Dương trả lời cho chính mình, không phải cho ai.

---

### CH_A3_08 — 📍 A3_C08 — Cơ hội ⭐ **ROUTE LỚN NHẤT**
> **Tình huống:** Cơ hội mới — công việc, học tập, hoặc nhịp sống bền vững.

| | Lựa chọn | Delta | Kết quả |
|---|----------|-------|---------|
| **A** | Theo đuổi cơ hội nghề nghiệp | `CF +20`, `OL +10`, set `FLAG_WORK_OPPORTUNITY` | Candidate E03 |
| **B** | Theo đuổi học tập / bước ngoặt mới | `SF +20`, `FT +10`, set `FLAG_STUDY_ROUTE` | Candidate E04 |
| **C** | Chọn nhịp sống bền vững hơn | `OL −20`, `SA +12`, `NF +10`, set `FLAG_CHOSE_BALANCE` | Candidate E01 / E07 |

🌱 **Dài hạn:** khóa nhóm ending ưu tiên, nhưng vẫn kết hợp `ROMANCE_STATE` / `FAMILY_STATE`.

---

### CH_A3_09 — 📍 A3_C09 — Nam không thể chờ mãi ⭐ **ROUTE**
> **Tình huống:** Nam hỏi tương lai có chỗ cho cả hai không.

| | Lựa chọn | Delta | Kết quả |
|---|----------|-------|---------|
| **A** | "Có. Chị muốn cùng xây nó." | `RT +15`, `NF +12`, `SA +8`, set `FLAG_COMMIT_TO_NAM` | Romance `ACTIVE` |
| **B** | "Chị muốn, nhưng không thể hứa ngay." | `RT +8`, `SA +10` | `UNCERTAIN` |
| **C** | "Có lẽ chúng ta nên buông." | `SA +15`, `NF −15`, set `FLAG_LET_NAM_GO` | Ending **E05** |

🌱 **Dài hạn:** quyết định biến thể ending tình cảm.

---

### CH_A3_10 — 📍 A3_C10 — Ngày Minh bước đi
> **Tình huống:** Minh bước vào chặng mới — đại học của em.

| | Lựa chọn | Delta |
|---|----------|-------|
| **A** | Đồng hành rồi để Minh tự bước | `FT +20`, `SA +12`, `NF +10`, `OL −12`, set `FLAG_LET_MINH_GO` |
| **B** | Tiếp tục cố kiểm soát mọi thứ | `FT −10`, `OL +12`, `SA −5` |

🌱 **Dài hạn:** khóa `FAMILY_STATE` cuối cùng.

---

### CH_A3_11 — 📍 A3_C11 — Quyết định của Dương ⭐ **FINAL**
> **Tình huống:** Dương định nghĩa bước tiếp theo của chính mình.

| | Lựa chọn | Delta | `FINAL_ORIENTATION` |
|---|----------|-------|---------------------|
| **A** | "Đi tiếp cùng những người mình chọn." | `NF +15`, `FT +8` | `CONNECTION` |
| **B** | "Đi tiếp trên con đường mình chọn." | `CF +10`, `SF +10`, `SA +10` | `SELF` |
| **C** | "Mình cần dừng lại trước." | `OL −20`, `SA +15`, `EN +20` | `RECOVERY` |

🌱 **Dài hạn:** Resolver kết hợp orientation + Romance + Family + Priority để gọi Ending.

---

## 10.04 — CẤU TRÚC PHÂN NHÁNH

```
ARC 1 → FAMILY_STATE
       GROWTH / MIXED / UNRESOLVED

ARC 2 → ROMANCE_STATE
       ACTIVE / UNCERTAIN / ENDED

ARC 3 → PRIORITY_STATE
       CAREER / STUDY / CONNECTION / BALANCE / OVERLOAD

FINAL → FINAL_ORIENTATION
       CONNECTION / SELF / RECOVERY

ENDING RESOLVER
```

### Ma trận ánh xạ ending

| Điều kiện | Ending |
|-----------|--------|
| Romance `ACTIVE` + cam kết + `FINAL = CONNECTION` | E02 |
| `CAREER`/`STUDY` + `FINAL = SELF` | E03 / E04 |
| `BALANCE` + Family `GROWTH` + `RECOVERY`/`SELF` | E01 hoặc E09 |
| `ENDED` + `FINAL` thành thật | E05 |
| `OVERLOAD` + từ chối dừng | E08 / E06 |
| `AWARE` + `RECOVERY` | E07 |
| Còn lại | E09 |

⚠️ `FAMILY_UNRESOLVED` hoặc `ROMANCE_UNCERTAIN` **không nhất thiết tạo ending xấu** — chúng tạo **biến thể epilogue**.

---

## 10.05 — LUẬT THIẾT KẾ CHOICE

1. **Minor Choice** → đổi tone, câu thoại, phản ứng ngắn. Không set flag.
2. **Relationship Choice** → đổi cách nhân vật nói và hành động ở chapter sau.
3. **Route Choice** → chỉ dùng ở turning point lớn (A1_C06, A2_C06, A2_C09, A3_C05, A3_C06, A3_C08, A3_C09, A3_C11).
4. **Không quá nhiều fake choice.** Lựa chọn quan trọng phải có hậu quả nhìn thấy được.
5. **Không khóa ending quá sớm.** Phần lớn route xác định ở Arc 3.
6. **Choice luôn tốn tài nguyên.** Mọi lựa chọn đều có `ENERGY` hoặc một trục focus bị hy sinh. Không có lựa chọn "miễn phí".
7. **Choice tốt phải tốn công.** Choice tốt nhất (`SA +`, `OL −`) không bao giờ là choice dễ nhất.

---

**TIẾP** → `11_ENDING.md`
**QUAY LẠI** → `CANON_DECISIONS.md`