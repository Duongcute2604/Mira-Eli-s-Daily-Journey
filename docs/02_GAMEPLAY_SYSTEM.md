# 🎮 02. GAMEPLAY / SYSTEM

> Biến Story, Choice, Variables và Ending thành cấu trúc gameplay có thể triển khai.
> **Nguyên tắc:** gameplay phục vụ trải nghiệm narrative. Không tạo hệ thống phức tạp không cần thiết.
> Ràng buộc tổng quát xem `CANON_DECISIONS.md`.

---

## 02.00 — CORE GAME LOOP

```
START / LOAD
   ↓
ENTER CHAPTER
   ↓
EXPLORE MAP / LOCATION
   ↓
INTERACT WITH OBJECTS / CHARACTERS
   ↓
UNLOCK STORY EVENT
   ↓
DIALOGUE / EVENT SCENE
   ↓
PLAYER CHOICE (nếu có)
   ↓
MINIGAME (nếu có — từ Arc 2 trở đi, xem 12_RULES §12.10)
   ↓
UPDATE VALUES / FLAGS
   ↓
UNLOCK NEXT EVENT OR CHAPTER
   ↓
SAVE / JOURNAL UPDATE
   ↓
NEXT CHAPTER
```

**Nguyên tắc thiết kế:**
- Gameplay chính: **Exploration + Interaction + Dialogue + Choice**.
- Không combat, không grinding, không resource farming.
- Không phải chapter nào cũng có choice lớn.
- Khám phá dùng để xây bối cảnh, cảm xúc và mở event; Choice dùng để thay đổi trạng thái narrative.
- Gameplay loop phải **ngắn, rõ, lặp lại dễ hiểu**.

**Minigame (D-004):** 3 cái — MG1 chia thuốc, MG2 bữa tối, MG3 ca đêm. Thuộc Tầng 1 RESOURCE, cập nhật ngay. Mỗi cái ≤ 60 giây, một màn hình, **không thua cứng**, và **có bản dự phòng bằng choice**. Không có minigame trong vertical slice. Chi tiết: `12_RULES.md` §12.10.

---

## 02.01 — PLAYER FLOW

### PHASE 1 — ARRIVAL
- Người chơi spawn tại map/chapter.
- Hiển thị objective ngắn: đi đâu hoặc nói chuyện với ai.
- Cho phép tương tác một số object để hiểu bối cảnh.

### PHASE 2 — EXPLORATION
- Đi bộ giữa các điểm quan trọng.
- Tương tác với NPC chính, điện thoại, bàn làm việc, lịch, vật dụng cá nhân.
- Một số interaction chỉ là **flavour**; một số **unlock Story Event**.

### PHASE 3 — STORY TRIGGER
- Chạm trigger area hoặc hoàn thành điều kiện.
- Gameplay chuyển sang Event / Dialogue Scene.
- Control có thể bị giới hạn tuỳ cinematic.

### PHASE 4 — CHOICE
- Nếu scene có choice: pause dialogue flow.
- Hiển thị **2–4 option**.
- Player chọn một hướng.
- System cập nhật Value / Flag / Route State.

### PHASE 5 — RESOLUTION
- Scene kết thúc.
- Objective mới hoặc chapter complete.
- Journal/log cập nhật thông tin quan trọng.
- Cho phép save.

---

## 02.02 — CORE INTERACTION SYSTEM

### A. TALK INTERACTION
Dùng cho Dương ↔ Minh, Dương ↔ Nam (qua thiết bị) và NPC phụ.

| Loại | Mục đích |
|------|----------|
| **Main Dialogue** | đẩy story |
| **Optional Dialogue** | xây tính cách / bối cảnh |
| **Conditional Dialogue** | thay đổi theo Family/Romance State hoặc Flag |

> ⚠️ Dương ↔ Nam **không bao giờ** là talk interaction trực tiếp. Nó đi qua Phone system (02.05).

### B. OBJECT INTERACTION

| Object | Vai trò |
|--------|---------|
| **Phone** | tin nhắn, cuộc gọi, missed call |
| **Calendar / Schedule** | thể hiện workload và áp lực |
| **Desk / Work Items** | bối cảnh công việc |
| **Personal Objects** | flavour và memory trigger |
| **Door / Travel Point** | chuyển location hoặc bắt event |

### C. EVENT INTERACTION
```
Interact → kiểm tra condition → gọi Event Scene
```
- Event có thể là **one-time**, **repeatable** hoặc **conditional**.
- Event hoàn thành sẽ set Event Flag hoặc unlock next chapter.

---

## 02.03 — CHAPTER GAMEPLAY TEMPLATE

Mỗi chapter dùng **một template nhất quán** để production dễ quản lý.

| # | Bước | Nội dung |
|---|------|----------|
| 1 | **Chapter Intro** | location + thời gian + mục tiêu |
| 2 | **Free Explore** | 2–5 điểm tương tác chính |
| 3 | **Required Interaction** | điều kiện để story tiếp tục |
| 4 | **Main Event** | dialogue / cinematic |
| 5 | **Choice** | nếu chapter có choice |
| 6 | **State Update** | value / flag / route |
| 7 | **Transition Event** | mở chapter tiếp theo |

### Ví dụ — `A1_C06` Lần đầu nói thật

| Bước | Nội dung |
|------|----------|
| Intro | Dương và Minh ở phòng khách. Buổi tối. |
| Explore | Không gian nhỏ, vài object phản ánh căng thẳng. |
| Required Trigger | Nói chuyện với Minh. |
| Main Event | Cuộc đối thoại chính. |
| Choice | Phản bác / Nói thật / Bỏ đi → `CH_A1_06` |
| State Update | `FAMILY_TRUST`, `SELF_AWARENESS`, `FLAG_FAMILY_TRUTH` |
| Transition | Dương rời scene hoặc ở lại; mở `A1_C07`. |

---

## 02.04 — OBJECTIVE SYSTEM

Objective phải **ngắn và diegetic**, tránh checklist quá game-like.

| Loại | Định nghĩa |
|------|------------|
| **Primary Objective** | việc cần làm để tiến story |
| **Context Objective** | nhắc nhẹ bối cảnh |
| **Optional Objective** | tương tác thêm để hiểu nhân vật |

**Ví dụ hợp lệ:**
> *"Nói chuyện với Minh."* · *"Kiểm tra điện thoại."* · *"Về nhà."* · *"Xem lại lịch hôm nay."* · *"Tìm một khoảng yên tĩnh."*

**Không khuyến nghị:**
> *"Collect 10 items"* · *"Defeat enemies"* · bất kỳ nhiệm vụ lặp lại nào không phục vụ narrative.

---

## 02.05 — PHONE SYSTEM

Điện thoại là gameplay object quan trọng nhất của game — vì Q1 đã khoá Dương và Nam không gặp mặt, **phone là toàn bộ Arc 2**.

| Chức năng | Vai trò |
|-----------|---------|
| **Messages** | đọc tin nhắn và lịch sử hội thoại |
| **Calls** | trigger event hoặc optional call |
| **Missed Calls** | phản ánh hậu quả của việc trì hoãn |
| **Calendar** | workload, event, áp lực |
| **Notifications** | chỉ dùng khi có ý nghĩa narrative |

### PHONE RULE

- Không mô phỏng smartphone đầy đủ. Chỉ có app/menu phục vụ story.
- Một số message thay đổi theo `ROMANCE_STATE` hoặc event flags.
- Phone tạo **ambient interaction** giữa các story beat.

### 02.05.1 — Cơ chế múi giờ (bổ sung do Q1)

Đây là cơ chế **mới sinh ra** từ việc giữ setting G1, không có trong bản gốc G2.

```
Thụy Điển (CET/CEST)  =  Việt Nam (ICT) − 5 hoặc − 6 giờ
```

| Khung giờ Thụy Điển | Ở Việt Nam là | Dương có thể gọi Nam? |
|--------------------|---------------|------------------------|
| MORNING 06–11 | 12–17 (chiều) | ✅ rất dễ — giờ vàng của cả hai |
| DAY 12–17 | 18–23 (tối) | ⚠️ tạm được, Nam mệt |
| EVENING 18–21 | 00–03 (khuya) | ❌ Nam ngủ |
| NIGHT 22–02 | 05–09 (sáng) | ⚠️ Dương kiệt sức, Nam mới dậy |

**Cách dùng trong game (không dùng như lý do suông):**

1. **Lợi thế** — `MORNING` ở Thụy Điển là khung duy nhất cả hai đều tỉnh. Game phải cho người chơi **tìm ra** khung này.
2. **Nghịch lý** — khung "hợp lý nhất" thường bị chiếm hết bởi ca viện dưỡng và học của Minh.
3. **Hệ quả** — người chơi phải *hy sinh* một khung giờ để giữ mối quan hệ. Đó là lựa chọn, không phải sự cố.
4. **Arc 2 → Arc 3** — Nam học thạc sĩ để sang Thụy Điển: múi giờ **biến mất**, nhưng còn thứ khác xuất hiện (visa, chi phí, thời gian). Không phải "vấn đề được giải quyết" — là vấn đề đổi hình dạng.

> 💡 Thiết kế: cho người chơi **phát hiện** múi giờ ở `A2_C02` thay vì được nói trước. Sai lệch giờ là cú va chạm tự nhiên nhất trong game này.

### 02.05.2 — Danh sách app

| App | Chức năng | Mở khoá |
|-----|-----------|---------|
| **Tin nhắn** | lịch sử chat với Nam / Minh / sếp Annika | từ đầu |
| **Lịch** | lịch ngày / tuần, workload | từ đầu |
| **Cuộc gọi** | danh sách cuộc gọi, missed call | từ đầu |
| **Ngân sách** | `MONEY`, `DEBT`, lịch trả nợ | từ `A1_C01` (bổ sung do Q1) |
| **Ca làm** | lịch ca viện dưỡng, yêu cầu thi nâng bậc | từ `A3_C02` |

---

## 02.06 — JOURNAL / MEMORY LOG

| Mục | Nội dung |
|-----|----------|
| **Story Summary** | tóm tắt chapter đã hoàn thành |
| **Character Notes** | thông tin Dương biết về Nam/Minh |
| **Important Choices** | lưu quyết định bằng **ngôn ngữ narrative**, không hiển thị điểm số |
| **Current Direction** | objective hiện tại |

**Mục tiêu:** giúp người chơi quay lại sau khi nghỉ.
**Không phải:** biến game thành spreadsheet.

> ⚠️ Journal **không** hiển thị `OVERLOAD`, `SELF_AWARENESS` hay bất kỳ persistent value nào. Xem 02.08.

---

## 02.07 — TIME & TRANSITION SYSTEM

Time blocks: `MORNING` / `DAY` / `EVENING` / `NIGHT`.
Không cần đồng hồ real-time. Story Event có thể chuyển time block trực tiếp.
Chapter kết thúc thường dẫn đến time/location transition.

| Khung giờ | Công dụng narrative |
|----------|---------------------|
| **Morning** | routine, family, expectation |
| **Day** | work/study pressure |
| **Evening** | transition, fatigue, missed communication |
| **Night** | intimacy, reflection, important calls |

**Bổ sung do Q1:** khung giờ còn quyết định **an toàn liên lạc với Nam** (02.05.1). `NIGHT` là khung thân mật nhưng cũng là khung Nam đã ngủ.

---

## 02.08 — OVERLOAD PRESENTATION SYSTEM

`OVERLOAD` **không** phải một thanh chỉ số. Nó phải được **cảm nhận qua gameplay**.

| Mức | Biểu hiện |
|-----|-----------|
| **Thấp** | ambience sạch, ít layer, UI/phone bình tĩnh, lịch còn khoảng trống |
| **Trung bình** | notification xuất hiện nhiều hơn, work cue dày, lịch kín |
| **Cao** | V13/V16 + A23/A24 tăng cường; lịch kín hoàn toàn; self-talk đổi; idle chậm; thông tin dày đặc |
| **Breaking Point** | objective đơn giản hoá để nhấn mạnh việc Dương không còn xử lý được |

**Kênh truyền tải cụ thể:**
- VFX: V06 / V13 / V15 / V16
- Audio: A07 / A23 / A24
- Lịch: mật độ ngày tăng dần qua từng chương
- Notification: tần suất và chồng chất
- **Self-talk**: câu tự thoại của Dương đổi theo trạng thái
- **Idle animation**: mệt hơn

> ⚠️ Không dùng V13/V16/A23/A24 **liên tục** — người chơi sẽ mất khả năng cảm nhận. Đó là lý do `OVERLOAD` chạy ẩn.

Chi tiết thực thi: `05_VFX_AUDIO_PLACEMENT.md`.

---

## 02.09 — CONDITIONAL CONTENT SYSTEM

Cùng một map hoặc scene có thể thay đổi theo State mà **không cần tạo map mới**.

| State | Ảnh hưởng |
|-------|-----------|
| `FAMILY_STATE` | lời thoại của Minh, interaction tại nhà |
| `ROMANCE_STATE` | tin nhắn, cuộc gọi, sự hiện diện của Nam |
| `OVERLOAD` | self-talk, schedule, ambient presentation |
| `PRIORITY_STATE` | objective và event trong Arc 3 |
| **Event Flags** | callback dialogue và object state |

### CONTENT LEVELS

| Level | Loại nội dung | Chi phí sản xuất |
|-------|---------------|------------------|
| **1** | Dialogue line replacement | rẻ |
| **2** | Optional interaction thay đổi | trung bình |
| **3** | Short event variant | đắt |
| **4** | Full route scene / ending | rất đắt |

> 🎯 Mục tiêu sản xuất: **80% nội dung ở Level 1–2.** Level 3–4 dành riêng cho turning point.

---

## 02.10 — SAVE / LOAD SYSTEM

| Loại | Quy tắc |
|------|---------|
| **Auto Save** | khi chapter/event quan trọng hoàn thành |
| **Manual Save** | tại chapter hub hoặc menu |
| **Choice Lock** | choice quan trọng không được đổi sau khi đã confirm trong cùng playthrough |
| **Load Previous** | cho phép người chơi quay lại save cũ nếu muốn khám phá route khác |

**Danh sách phải lưu (33 object):**

| Nhóm | Số lượng |
|------|----------|
| Resource (Tầng 1) | 6 |
| Persistent Values | 7 |
| Route States | 5 |
| Event Flags | 15 |
| **Tổng** | **33** |

Chi tiết: `09_SYSTEM_VARIABLES.md`.

### 02.10.1 — Quyết định về "mô phỏng tài chính"

G1 nói game mô phỏng tài chính. G2 nói "không cần resource farming".
→ **Giữ cả hai, theo cách sau:**

| Giữ (từ G2) | Bỏ (từ G1) |
|-------------|------------|
| Không có grinding | Không phải spreadsheet tài chính |
| Không farm tiền để hết nợ trong 1 lượt | Không có thanh "Tài chính" trên HUD |
| Quyết định chi tiêu **có hậu quả** | Không có mini-game quản lý ngân sách |

`DEBT` tồn tại và thay đổi theo lựa chọn của người chơi, nhưng nó là **áp lực nền**, không phải mục tiêu tối ưu hoá. Một lượt chơi ngắn **không** trả hết 8 tỷ — đó là con số có chủ đích.

---

## 02.11 — ENDING EXECUTION FLOW

```
FINAL CHAPTER COMPLETE
   ↓
LOCK FINAL VALUES
   ↓
CHECK OVERLOAD / BREAKING_POINT_STATE
   ↓
RESOLVE PRIORITY_STATE
   ↓
CHECK FINAL_ORIENTATION
   ↓
APPLY ROMANCE VARIANT
   ↓
APPLY FAMILY VARIANT
   ↓
PLAY ENDING SCENE
   ↓
EPILOGUE
   ↓
ENDING TITLE / CREDITS
   ↓
UNLOCK ENDING IN GALLERY
```

Chi tiết 9 ending: `11_ENDING.md`.

---

## 02.12 — RECOMMENDED SYSTEM PRIORITY

| Mức | Hệ thống |
|-----|----------|
| **Must Have** | Dialogue System |
| **Must Have** | Choice System |
| **Must Have** | Narrative Variables / Flags |
| **Must Have** | Interaction System |
| **Must Have** | Chapter / Event Trigger System |
| **Should Have** | Phone System |
| **Should Have** | Journal / Story Log |
| **Should Have** | Conditional Dialogue / Object States |
| **Nice to Have** | Ending Gallery, Chapter Select sau khi hoàn thành |

---

## 02.13 — PRODUCTION BUILD ORDER

> ⚠️ Build **đúng thứ tự này.** Mỗi bước phải chạy được trước khi bắt đầu bước sau.

| STEP | Hệ thống | Phải chứng minh được |
|------|----------|---------------------|
| **1** | Player movement + camera | đi được trong map, camera theo |
| **2** | Interaction prompt + object interaction | bấm được object, hiện prompt |
| **3** | Dialogue và event system | hộp thoại chạy, event trigger được |
| **4** | Choice UI | chọn được, ghi lại lựa chọn |
| **5** | Variables / flags / route states | delta số chạy đúng như `10_CHOICE_BRANCHING.md` |
| **6** | Chapter progression | chạy hết `A1_C01 → A1_C09` |
| **7** | Phone + Journal | đọc/nhắn/gọi được, journal cập nhật |
| **8** | Conditional content | Level 1–2 đổi theo state |
| **9** | Save/load | load lại giữ nguyên 33 object |
| **10** | Ending resolver + gallery | chạy ra đúng 1 trong 9 ending |

### 02.13.1 — Vertical slice bắt buộc

Trước khi làm hết 31 chương, prototype **`A1_C01 → A1_C06 → A1_C09`**.

Lý do: đây là cung đủ để kiểm chứng toàn bộ hệ thống mà vẫn nhỏ:

| Cần kiểm chứng | Chương đại diện |
|----------------|-----------------|
| Routine + Minor choice | `A1_C01` |
| Major choice + State update + Flag | `A1_C06` |
| Route resolution (`FAMILY_STATE`) | `A1_C09` |

Nếu slice này không cho cảm giác đúng, làm thêm 28 chương cũng vô nghĩa.

---

## 02.14 — FINAL GAMEPLAY LOOP

```
EXPLORE → INTERACT → DISCOVER → TALK → CHOOSE → CONSEQUENCE → REFLECT → MOVE FORWARD
```

---

**TIẾP** → `03_MAP_EVENT_FLOW.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
