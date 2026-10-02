# ✨ 05. VFX / AUDIO PLACEMENT

> 20 VFX + 30 audio placement blueprint.
> VFX/Audio **không thay thế** narrative event; chúng nhấn nhịp cảm xúc, chuyển cảnh, overload, intimacy và route consequence.

---

## 05.00 — MASTER FLOW

```
GAMEPLAY → EVENT BUILD-UP → VFX / AUDIO CUE → DIALOGUE / CG
   → CHOICE → STATE UPDATE → CONDITIONAL AFTERMATH
```

### ASSET DISTRIBUTION

| Nhóm | Số lượng |
|------|----------|
| **VFX** | 20 — ambient, transition, emotion, overload, UI/phone, ending |
| **Audio** | 30 — ambience, interaction, phone, emotional stinger, transition, ending |

> **Ưu tiên reuse** theo Map State và Event State thay vì tạo asset chỉ dùng một lần.

---

## 05.01 — ✨ VFX PLACEMENT | V01–V20

### V01 — Morning Light
| | |
|---|---|
| 📍 **Chapter/Map** | `P01` / `A1_C01` • M01 Nhà |
| ▶️ **Trigger** | Chapter intro |
| 🎭 **Purpose** | Routine, warmth trước áp lực |
| 🔀 **Condition** | Always |
| ➡️ **After** | Fade về gameplay bình thường. |

### V02 — Calendar Focus Pulse
| | |
|---|---|
| 📍 **Chapter/Map** | `P01` / `A1_C01` / `A3_C01` • M01 Nhà |
| ▶️ **Trigger** | Inspect schedule |
| 🎭 **Purpose** | Hiển thị mật độ workload |
| 🔀 **Condition** | Always; **mạnh hơn khi `OVERLOAD` cao** |
| ➡️ **After** | Quay lại interaction. |

### V03 — Phone Notification Pop
| | |
|---|---|
| 📍 **Chapter/Map** | `A1_C03` / `A2_C01` / `A2_C05` • M03 / M05 |
| ▶️ **Trigger** | Message/call đến |
| 🎭 **Purpose** | Cắt ngang sự chú ý **không bằng hard cut** |
| 🔀 **Condition** | Conditional theo message flag |
| ➡️ **After** | Phone interaction. |

### V04 — Street Transition Sweep
| | |
|---|---|
| 📍 **Chapter/Map** | `P01` / `A1_C03` / `A2_C03` • M03 |
| ▶️ **Trigger** | Location/time transition |
| 🎭 **Purpose** | Giữ nhịp di chuyển |
| 🔀 **Condition** | Always |
| ➡️ **After** | Load beat kế tiếp. |

### V05 — Warm Home Window Dust
| | |
|---|---|
| 📍 **Chapter/Map** | `A1_C02` / `A1_C04` / `A1_C09` • M01 |
| ▶️ **Trigger** | Cảnh gia đình yên tĩnh |
| 🎭 **Purpose** | Nostalgia và đời sống thường |
| 🔀 **Condition** | Always; **intensity đổi theo `FAMILY_STATE`** |
| ➡️ **After** | Dialogue/event. |

### V06 — Argument Edge Distortion
| | |
|---|---|
| 📍 **Chapter/Map** | `A1_C05`–`A1_C06` • M01 |
| ▶️ **Trigger** | Conflict leo thang |
| 🎭 **Purpose** | Báo hiệu áp lực cảm xúc |
| 🔀 **Condition** | **Mandatory** tại đỉnh conflict |
| ➡️ **After** | CG / choice entry. |

### V07 — Silence Fade
| | |
|---|---|
| 📍 **Chapter/Map** | `A1_C07` • M02 → M03 |
| ▶️ **Trigger** | Dương rời đi sau conflict |
| 🎭 **Purpose** | Tạo **khoảng trống cảm xúc** |
| 🔀 **Condition** | Biến thể theo kết quả `A1_C06` |
| ➡️ **After** | Reflection gameplay. |

### V08 — Shared Task Spark
| | |
|---|---|
| 📍 **Chapter/Map** | `A1_C08` • M01 |
| ▶️ **Trigger** | Minh giúp hoàn thành việc |
| 🎭 **Purpose** | Giải quyết tích cực nhỏ |
| 🔀 **Condition** | **Chỉ khi help được chấp nhận** |
| ➡️ **After** | `FLAG_ACCEPTED_HELP` aftermath. |

### V09 — Café Steam / Soft Focus
| | |
|---|---|
| 📍 **Chapter/Map** | `A2_C02` / `A2_C04` • M04 |
| ▶️ **Trigger** | Conversation bắt đầu |
| 🎭 **Purpose** | Intimacy và không gian thân quen |
| 🔀 **Condition** | Always; **giảm độ ấm khi căng thẳng tăng** |
| ➡️ **After** | Dialogue. |

> ⚠️ **Bổ sung do Q1:** hơi nước cà phê giờ thuộc về **không gian của Dương một mình** — nó thay cho sự hiện diện của Nam.

### V10 — Transit Motion Blur
| | |
|---|---|
| 📍 **Chapter/Map** | `A2_C03` / `A2_C09` / `A3_C10` • M08 |
| ▶️ **Trigger** | Departure/arrival |
| 🎭 **Purpose** | Khoảng cách vật lý và chuyển tiếp |
| 🔀 **Condition** | Route variant |
| ➡️ **After** | Next chapter / route state. |

### V11 — Message Silence Pulse
| | |
|---|---|
| 📍 **Chapter/Map** | `A2_C06`–`A2_C07` • M01 / M03 / Phone |
| ▶️ **Trigger** | Không liên lạc được |
| 🎭 **Purpose** | Làm cho **sự vắng mặt trở nên cảm nhận được** |
| 🔀 **Condition** | `ROMANCE_TRUST` thấp hoặc trả lời chậm |
| ➡️ **After** | Contact decision. |

### V12 — Night Reflection Particles
| | |
|---|---|
| 📍 **Chapter/Map** | `A2_C08` / `A3_C07` • M09 |
| ▶️ **Trigger** | Sự thành thật / tự phản chiếu trong im lặng |
| 🎭 **Purpose** | Chậm lại trọng tâm cảm xúc |
| 🔀 **Condition** | Always |
| ➡️ **After** | Choice/reflection. |

### V13 — Work Screen Glitch
| | |
|---|---|
| 📍 **Chapter/Map** | `A2_C05` / `A3_C02` / `A3_C05` • M05 / M06 |
| ▶️ **Trigger** | Áp lực công việc tăng đột ngột |
| 🎭 **Purpose** | Hiển thị các yêu cầu cạnh tranh |
| 🔀 **Condition** | **Intensity scales theo `OVERLOAD`** |
| ➡️ **After** | Choice/event. |

### V14 — Study Page / Light Drift
| | |
|---|---|
| 📍 **Chapter/Map** | `A3_C05` / `A3_C08` • M07 |
| ▶️ **Trigger** | Cân nhắc study route |
| 🎭 **Purpose** | Khả năng tương lai và sự tập trung |
| 🔀 **Condition** | STUDY route hoặc interaction liên quan |
| ➡️ **After** | Route confirmation. |

### V15 — Priority Split Overlay
| | |
|---|---|
| 📍 **Chapter/Map** | `A3_C05` • M05 → M07 → M01 |
| ▶️ **Trigger** | Các cam kết cạnh tranh |
| 🎭 **Purpose** | Làm cho **nhiều yêu cầu hiện thành cùng lúc** |
| 🔀 **Condition** | **Mandatory** tại đỉnh conflict |
| ➡️ **After** | Major priority choice. |

### V16 — Overload Distortion
| | |
|---|---|
| 📍 **Chapter/Map** | `A3_C06` • M03 → M09 |
| ▶️ **Trigger** | Breaking Point |
| 🎭 **Purpose** | **Core overload presentation** |
| 🔀 **Condition** | Intensity theo `OVERLOAD`; mạnh nhất khi `PUSH_ON` |
| ➡️ **After** | Breaking Point choice. |

### V17 — Memory Callback Fade
| | |
|---|---|
| 📍 **Chapter/Map** | `A3_C07` / `A3_C11` / `A3_C12` • M09 / M10 |
| ▶️ **Trigger** | Cảnh quá khứ vang lại trong quyết định hiện tại |
| 🎭 **Purpose** | Nối lựa chọn với sự trưởng thành |
| 🔀 **Condition** | Conditional theo major flags |
| ➡️ **After** | Final orientation. |

### V18 — Open Space Wind / Light
| | |
|---|---|
| 📍 **Chapter/Map** | `A3_C11` / `E01` / `E07` / `E09` • M10 |
| ▶️ **Trigger** | Bước cuối |
| 🎭 **Purpose** | Cảm giác không gian và khả năng |
| 🔀 **Condition** | Variant theo `FINAL_ORIENTATION` |
| ➡️ **After** | Ending frame. |

### V19 — Route Door Highlight
| | |
|---|---|
| 📍 **Chapter/Map** | `A3_C08` • M06 / M07 / M10 |
| ▶️ **Trigger** | Lựa chọn tương lai cụ thể trở nên khả dụng |
| 🎭 **Purpose** | Làm rõ route **không gây UI overload** |
| 🔀 **Condition** | Career / Study / Balance conditional |
| ➡️ **After** | Route lock. |

### V20 — Ending Dissolve
| | |
|---|---|
| 📍 **Chapter/Map** | Final • Ending-specific |
| ▶️ **Trigger** | Final image / title transition |
| 🎭 **Purpose** | Đóng lại narrative route |
| 🔀 **Condition** | All endings; tone/intensity variant |
| ➡️ **After** | Ending title → credits. |

---

## 05.02 — 🔊 AUDIO PLACEMENT | A01–A30

### A01 — Home Morning Ambience
`P01` / `A1_C01` • M01 · Trigger: map load · **Thiết lập đời sống thường** · Always · Loop dưới routine.

### A02 — Kettle / Kitchen Detail
`A1_C01` • M01 · Trigger: object interaction · **Texture gia đình** · Optional interaction · Quay lại ambience.

### A03 — Calendar Tap / UI Tick
`P01` / `A3_C01` • M01 · Trigger: inspect schedule · **Feedback workload** · Always · Có thể layer với V02.

### A04 — Phone Notification
`A1_C03` / `A2_C01` / `A2_C05` • M03 / M05 · Trigger: message đến · **Cắt ngang sự chú ý** · Conditional · → Phone UI.

### A05 — Footsteps Transition
`P01` / `A1_C03` / `A2_C03` • M02 / M03 / M08 · Trigger: travel · **Giữ liên tục vật lý** · Always · Crossfade ambience.

### A06 — Home Night Ambience
`A1_C02` / `A1_C05` / `A1_C06` • M01 · Trigger: evening scene · **Tạo tension qua sự tĩnh** · Always · Giảm density trước key lines.

> 📍 Cần asset **night variant cho M01** — hiện chỉ có background sáng. Xem `08_ASSET_MANIFEST.md`.

### A07 — Dialogue Tension Bed
`A1_C05`–`A1_C06` • M01 · Trigger: argument leo thang · **Hỗ trợ conflict không lấn át VO** · Mandatory · Dừng trước choice.

### A08 — Silence / Room Tone
`A1_C06`–`A1_C07` • M01 → M02 · Trigger: sau honest answer · **Để hậu quả thở** · Always; duration variant → Reflection.

### A09 — Soft Resolve Motif
`A1_C08`–`A1_C09` • M01 · Trigger: acceptance/help · **Báo hiệu tiến bộ nhỏ** · `FLAG_ACCEPTED_HELP` hoặc family outcome tích cực → Arc transition.

### A10 — Street Day Ambience
`A2_C01` / `A2_C07` • M03 · Trigger: explore street · **Kết nối trung tính** · Always → Crossfade.

### A11 — Café Ambience
`A2_C02` / `A2_C04` / `A3_C04` • M04 · Trigger: map load · **Không gian chung quen thuộc** · Always; giảm density cho dialogue nghiêm túc → Conversation.

### A12 — Cup / Table Detail
`A2_C02` / `A2_C04` • M04 · Trigger: object/gesture · **Neo trữu tượng vào cảnh** · Optional/scene cue.

> ⚠️ **Bổ sung do Q1:** tiếng **ly đặt xuống** thay cho khoảng trống mà Nam đáng lẽ ngồi. Đây là detail âm thanh — rẻ hơn CG nhưng đắng hơn nhiều.

### A13 — Transit Announcement / Rail
`A2_C03` / `A2_C09` / `A3_C10` • M08 · Trigger: departure · **Đại diện cho khoảng cách và di chuyển** · Always trong transit scenes → Transition.

### A14 — Message Sent / Unsent Cue
`A2_C01` / `A2_C07` • Phone · Trigger: player contact choice · **Làm lựa chọn liên lạc trở nên cụ thể** · Conditional.

### A15 — Romance Tension Motif
`A2_C04`–`A2_C06` • M04 / Phone · Trigger: question/conflict · **Tăng khoảng cách cảm xúc** · State-sensitive · Kết thúc tại major choice.

### A16 — Night Outdoor Ambience
`A2_C08` • M09 · Trigger: map load · **Tạo riêng tư và mở** · Always → Under dialogue.

### A17 — Honesty Stinger
`A2_C08` / `A3_C07` • M09 · Trigger: Dương trả lời thành thật · **Đánh dấu sự dễ tổn thương** · Chỉ ở honest/major emotional option → Fade sau câu.

### A18 — Goodbye / Departure Motif
`A2_C09` / `E05` • M08 · Trigger: relationship closure · **Đóng khung chia ly mà không tạo phản diện** · ENDED route / goodbye scene.

### A19 — Workplace Ambience
`A2_C05` / `A3_C02` / `A3_C05` • M05 · Trigger: map load · **Áp lực hằng ngày** · Always → Layers với work cues.

> 📍 Ambience M05 phải là **bệnh viện/viện dưỡng** (máy monitor, bước chân trong hành lang), không phải văn phòng.

### A20 — Keyboard / Work Detail
`A2_C05` / `A3_C02` • M05 / M06 · Trigger: task interaction · **Nhịp làm việc xúc giác** · Optional/required.

### A21 — Boss Opportunity Stinger
`A3_C02` • M06 · Trigger: cơ hội được tiết lộ · **Đánh dấu turning point** · Always → Choice UI.

### A22 — Study Space Ambience
`A3_C05` / `A3_C08` • M07 · Trigger: map load · **Tập trung và lên kế hoạch tương lai** · Study route/scene → Under interaction.

### A23 — Priority Pressure Layer
`A3_C05` • Multi-map · Trigger: competing demands peak · **Quá tải thính giác của nghĩa vụ** · Mandatory; mix intensity theo state → Major choice.

### A24 — Overload Low Frequency
`A3_C06` • M03 → M09 · Trigger: Breaking Point bắt đầu · **Báo hiệu áp lực nhận thức** · Intensity scales `OVERLOAD` · Dừng hoặc resolve sau choice.

### A25 — Breath / Recovery Cue
`A3_C06` / `E07` • M09 · Trigger: Dương dừng lại và thừa nhận giới hạn · **Tạo khoảng trống sau áp lực** · `AWARE` / `RECOVERY` → Reflection.

### A26 — Memory Echo
`A3_C07` / `A3_C11` / `A3_C12` • M09 / M10 · Trigger: callback lựa chọn quá khứ · **Nối lịch sử narrative** · Conditional by flags → Final choice.

### A27 — Route Confirmation Motif
`A3_C08` • M06 / M07 / M10 · Trigger: Career/Study/Balance locked · **Xác nhận hướng đi** · Route-specific variant → Next scene.

### A28 — Family Departure Motif
`A3_C10` • M01 → M08 · Trigger: Minh tiến gần độc lập · **Hỗ trợ đắng đoản** · Family route variant → Final chapter.

### A29 — Final Open Theme
`A3_C11` / `A3_C12` / `E01` / `E02` / `E03` / `E04` / `E09` • M10 / Ending · Trigger: final orientation · **Giải quyết hoặc mở tương lai** · Ending-group variant → Ending title.

### A30 — Credits / Afterimage
Final • Ending · Trigger: credits begin · **Để lại dư âm cảm xúc sau hình ảnh cuối** · All endings, variant arrangement → Credits/menu.

---

## 05.03 — MASTER EVENT PLACEMENT SUMMARY

| Segment | VFX | Audio | Map chính | Chức năng narrative |
|---------|-----|-------|-----------|---------------------|
| **Prologue** | V01–V04 | A01–A05 | M01–M03 | Routine + workload setup |
| **Arc 1 Early** | V05 | A06 | M01 | Family context |
| **Arc 1 Conflict** | V06–V08 | A07–A09 | M01–M03 | Conflict → silence → small growth |
| **Arc 2 Early** | V09–V10 | A10–A14 | M03–M08 | Connection + distance |
| **Arc 2 Conflict** | V11 | A15 | M01 / M04 | Communication breakdown |
| **Arc 2 Honesty** | V12 | A16–A18 | M09 / M08 | Vulnerability + route resolution |
| **Arc 3 Work/Study** | V13–V15 | A19–A23 | M05–M07 | Competing futures |
| **Breaking Point** | V16 | A24–A25 | M03–M09 | Overload consequence |
| **Final Choice** | V17–V19 | A26–A29 | M09–M10 | Memory + direction |
| **Ending** | V20 | A29–A30 | Ending | Resolution + credits |

---

## 05.04 — STATE-DRIVEN PRESENTATION RULES

| State | Thay đổi |
|-------|----------|
| `OVERLOAD` thấp | ambience sạch, ít layer, UI/phone bình tĩnh |
| `OVERLOAD` trung bình | notification, work cue và pressure layer xuất hiện **dày hơn** |
| `OVERLOAD` cao | V13/V16 + A23/A24 tăng cường độ — **không dùng liên tục** để tránh gây mệt |
| `FAMILY_STATE` | đổi **warmth** của M01, V05 và các resolve/departure cue |
| `ROMANCE_STATE` | đổi V11, A15, A17, A18 và tone của A29 |
| `FINAL_ORIENTATION` | quyết định biến thể V18/V20 và A29/A30 |

> ⚠️ **Nguyên tắc sử dụng:** nếu `OVERLOAD` cao, V13/V16/A23/A24 phải **được nghỉ** giữa các chương.
> Hiệu ứng liên tục trở thành nền và người chơi ngừng cảm nhận được — đúng thứ ta muốn tránh.

---

## 05.05 — IMPLEMENTATION RULES

1. **Ambient audio loop theo Map State**, không restart mỗi khi player quay camera.
2. **One-shot VFX chỉ kích hoạt qua event flag** để tránh lặp.
3. **CG event nên có audio ducking** — ambience giảm nhẹ, dialogue/cue quan trọng được ưu tiên.
4. **Choice screen:** giữ room tone hoặc low music bed. Tránh silence tuyệt đối trừ khi đó là dụng ý.
5. **State-driven variant ưu tiên thay mix/intensity** trước khi tạo asset hoàn toàn mới.
6. **VFX và audio IDs phải được gọi từ Event Table / Chapter Data**, không hard-code trực tiếp trong scene.

---

## 05.06 — PRODUCTION PRIORITY

| Tier | VFX | Audio |
|------|-----|-------|
| **Tier 1** | V01, V02, V03, V06, V09, V13, V16, V18, V20 | A01, A04, A06, A07, A11, A15, A19, A23, A24, A29 |
| **Tier 2** | V04, V05, V10, V12, V15, V17 | A03, A08, A09, A13, A16, A17, A21, A25, A26, A28, A30 |
| **Tier 3** | *remaining polish / ambient detail assets* | |

### Prototype sequence

> **`A1_C05 → A1_C06 → A1_C07`** — kiểm chứng **tension** presentation (V06, V07, A07, A08).
> **`A3_C05 → A3_C06`** — kiểm chứng **overload** presentation (V13, V15, V16, A23, A24).

Hai đoạn này quyết định toàn bộ cảm giác "nặng" của game. Phải chạy trước khi làm phần còn lại.

---

## 05.07 — FINAL CHECKLIST

- [x] 20/20 VFX mapped to a concrete chapter/event
- [x] 30/30 audio cues mapped to a concrete chapter/event
- [x] Mỗi major CG turning point có ít nhất một supporting presentation cue
- [x] State-driven variations đã xác định
- [x] Ambient reuse được ưu tiên
- [x] Ending cues map tới Ending Group và epilogue tone

---

## 05.08 — BỔ SUNG DO Q1: audio cho khoảng cách

Cơ chế múi giờ (`02_GAMEPLAY_SYSTEM.md` 02.05.1) cần **hỗ trợ bằng âm thanh** mới có tác dụng:

| Công cụ | Cách dùng |
|----------|-----------|
| **A04 biến thể "giờ bên kia"** | Khi Dương mở call mà Nam chưa thức — chuông reo mãi rồi tắt. Người chơi **nghe** ra sự chênh lệch giờ trước khi hiểu. |
| **A11 layer "quán bên kia"** | Khi split frame mở, ambience của quán Việt Nam lọt vào nhẹ ở bên phải. Chứng minh Nam ở nơi khác. |
| **A13 announcement song ngôn ngữ khác** | Thông báo ga Thụy Điển và sân bay Việt Nam phải **khác nhau về ngôn ngữ**. Đây là cue mạnh nhất cho `R09`. |
| **A17 stinger "khung giờ trượt"** | Khi Dương nói thật, đồng hồ tường lệch nửa giây — nhỏ thôi, nhưng cảm được. |

> 🎯 Nguyên tắc: **đừng giải thích khoảng cách bằng lời thoại — cho người chơi nghe và nhìn thấy nó.**

---

**TIẾP** → `06_CHARACTER_STYLE.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
