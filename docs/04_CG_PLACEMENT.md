# ⭐ 04. CG / EVENT PLACEMENT

> 30 CG narrative placement blueprint.
> Ràng buộc tổng quát xem `CANON_DECISIONS.md`. Ánh xạ chapter ↔ map xem `03_MAP_EVENT_FLOW.md`.

---

## 04.00 — MASTER CG STRUCTURE

**30 CG tổng.**

| Nhóm | ID | Arc |
|------|-----|-----|
| Family | `F01`–`F10` | Arc 1 |
| Romance | `R01`–`R10` | Arc 2 |
| Life / Work / Study | `L01`–`L10` | Arc 3 |

Ending sử dụng **Ending Frames / CG Variant** từ 30 CG core hoặc biến thể production — **không** mở rộng thêm một bộ 30 CG mới.

### PLACEMENT TYPE

| Loại | Định nghĩa |
|------|------------|
| **Mandatory** | luôn xuất hiện trong playthrough |
| **Conditional** | phụ thuộc choice/state |
| **Variant** | cùng vị trí narrative nhưng đổi nhân vật, biểu cảm hoặc composition theo route |

### PLACEMENT FLOW

```
MAP EXPLORE → EVENT TRIGGER → DIALOGUE BUILD-UP → CG ENTER
   → OPTIONAL CHOICE → STATE UPDATE → CG EXIT → NEXT EVENT
```

---

## 04.00.1 — ⚠️ THAY ĐỔI BẮT BUỘC DO Q1: CG không được vẽ hai người cùng phòng

> **Bối cảnh:** Dương ở Thụy Điển, Nam ở Việt Nam. **Hai người không gặp mặt.**

6 CG của Arc 2 bản gốc vẽ Dương và Nam cùng khung hình. Điều đó vi phạm setting đã chốt.

| Nguyên tắc | |
|-------------|---|
| ✅ Được | Dương một mình, nhìn màn hình điện thoại, khung hình chia đôi, vật thay thế (tách cà phê, sân ga), khung cửa sổ + đồng hồ |
| ❌ Không | Hai người cùng căn phòng, chạm tay, ngồi cạnh nhau, đi cùng nhau trong khung hình |

**Kỹ thuật thay thế (không tốn thêm CG):**
1. **Split composition** — nửa khung là Dương, nửa là Nam qua màn hình.
2. **Foreground occlusion** — Dương ở foreground, màn hình điện thoại ở background, mờ.
3. **Reverse shot** — cắt giữa hai CG: CG-A Dương ngồi một mình, CG-B góc nhìn qua màn hình (không rõ mặt Nam nếu không muốn thêm asset nhân vật).
4. **Object substitution** — một vật thể ở vị trí Nam thường ngồi: ly cà phê thứ hai, chiếc ghế trống, hành lý.

> 💡 Điểm mạnh của ràng buộc này: **khoảng cách trở thành ngôn ngữ hình ảnh**, thay vì chỉ là lời thoại.

---

## 04.01 — 🏠 ARC 1: FAMILY | F01–F10

### F01 — Một buổi sáng quen thuộc *(Morning Routine)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `P01` / `A1_C01` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Player hoàn thành tương tác buổi sáng; Minh bước vào không gian chung. |
| ⭐ **Type** | **MANDATORY** — Intro CG |
| 🔀 **Condition** | Không. Thiết lập family routine và thói quen gánh trách nhiệm của Dương. |
| ➡️ **After CG** | CG fade về gameplay → nói chuyện với Minh. |

### F02 — Một việc nhỏ chen vào *(A Small Interruption)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C01` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Một việc gia đình cắt ngang lịch của Dương. |
| ⭐ **Type** | **MANDATORY** |
| 🔀 **Condition** | Thiết lập tone `OVERLOAD` sớm. |
| ➡️ **After CG** | Quay lại interaction; player quyết định phản ứng tức thời. |

### F03 — Những việc không tên *(Things Left Unsaid)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C02` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Required dialogue sau khi explore các object liên quan Minh. |
| ⭐ **Type** | **MANDATORY** — Emotional Setup |
| 🔀 **Condition** | Không. Tension setup. |
| ➡️ **After CG** | Free exploration kết thúc → chapter transition. |

### F04 — Cuộc gọi *(Two Directions)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C03` |
| 🗺️ **Map** | `M03` Đường |
| 🎬 **Trigger** | Phone / family conflict xảy ra trong lúc chuyển cảnh. |
| ⭐ **Type** | **CONDITIONAL VARIANT** |
| 🔀 **Condition** | Biến thể dựa trên việc Dương ưu tiên gia đình ngay lập tức hay báo rõ là đang bận. |
| ➡️ **After CG** | Choice result → route-specific short aftermath. |

### F05 — Những kế hoạch riêng *(What Minh Wants)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C04` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Main dialogue đến khoảnh khắc Dương nhận ra mình đã quyết hộ thay Minh. |
| ⭐ **Type** | **MANDATORY** |
| 🔀 **Condition** | Minor `FAMILY_TRUST` tone. |
| ➡️ **After CG** | Dialogue tiếp tục, không route lock cứng. |

### F06 — Những điều không nói *(A Familiar Argument)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C05` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Cinematic escalation của argument. |
| ⭐ **Type** | **MANDATORY** — Conflict CG |
| 🔀 **Condition** | Chuẩn bị cho `A1_C06`; không state lock. |
| ➡️ **After CG** | Immediate continuation sang honest-answer event. |

### F07 — Lần đầu nói thật *(The First Honest Answer)* ⭐
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C06` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Player đến major dialogue choice. |
| ⭐ **Type** | **MANDATORY + EXPRESSION VARIANT** |
| 🔀 **Condition** | `FAMILY_TRUST` / `SELF_AWARENESS` / `FLAG_FAMILY_TRUTH` đổi theo choice. |
| ➡️ **After CG** | CG giữ qua key line → choice → alternate expression → exit. |

> 📌 **CG này cần 3 biến thể biểu cảm** (phản bác / nói thật / im lặng bỏ đi). Xem `08_ASSET_MANIFEST.md` mục expression thiếu.

### F08 — Một ngày không ổn *(After the Silence)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C07` |
| 🗺️ **Map** | `M02` Hành lang / `M03` Đường |
| 🎬 **Trigger** | Dương bước ra ngoài sau conflict và dừng lại. |
| ⭐ **Type** | **CONDITIONAL** |
| 🔀 **Condition** | Tư thế / tone đổi theo kết quả `A1_C06`. |
| ➡️ **After CG** | Reflection event → về nhà. |

### F09 — Người không nói gì *(Letting Someone Help)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C08` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Minh đã tự xử lý một phần trách nhiệm chung. |
| ⭐ **Type** | **MANDATORY + VARIANT** |
| 🔀 **Condition** | Có thể set `FLAG_ACCEPTED_HELP`; `FAMILY_TRUST` đổi. |
| ➡️ **After CG** | Choice aftermath → shared task hoàn thành. |

### F10 — Không phải một mình *(A Different Routine)*
| | |
|---|---|
| 📍 **Chapter** | Arc 1 • `A1_C09` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | **Mirror của F01** khi Dương chuẩn bị rời nhà. |
| ⭐ **Type** | **MANDATORY** — Arc Resolution CG |
| 🔀 **Condition** | Family route sẵn sàng resolve về `GROWTH` / `MIXED` / `UNRESOLVED`. |
| ➡️ **After CG** | Exit home → Arc 2 transition. |

---

## 04.02 — ❤️ ARC 2: ROMANCE | R01–R10

> ⚠️ **Mọi CG trong nhóm này phải tuân thủ 04.00.1 — không vẽ hai người cùng phòng.**

### R01 — Tin nhắn chưa trả lời *(Unread Messages)*
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C01` |
| 🗺️ **Map** | `M03` Đường |
| 🎬 **Trigger** | Player mở điện thoại sau thời gian trì hoãn liên lạc. |
| ⭐ **Type** | **MANDATORY** |
| 🔀 **Condition** | Bối cảnh `ROMANCE_TRUST` sớm; có thể dẫn tới `FLAG_CONTACTED_NAM`. |
| ➡️ **After CG** | Choice response → di chuyển hoặc tiếp tục. |

> **Composition:** Dương nhìn màn hình, background là đường phố — **không** cần vẽ Nam. Dùng thoáng gương mặt Nam trong video call nhỏ nếu có asset.

### R02 — Những múi giờ khác nhau ⭐ **ĐÃ SỬA** *(The Usual Place)*
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C02` |
| 🗺️ **Map** | `M04` Quán cà phê (của **Dương**) |
| 🎬 **Trigger** | Dương ngồi ở quán quen, mở video call. |
| ⭐ **Type** | **MANDATORY** — Relationship Establishment |
| 🔀 **Condition** | Không. Baseline relationship presentation. |
| ➡️ **After CG** | Quay lại gameplay hoặc dialogue tiếp. |

> ⚠️ **Sửa so với bản gốc:** bản gốc vẽ hai người ngồi cùng quán.
> Bản mới: **split composition** — Dương ở quán bên trái, Nam ở quán Việt Nam qua màn hình bên phải.
> **Chi tiết hình ảnh bắt buộc:** hai cốc trên hai bàn khác nhau · đồng hồ tường lệch 5–6 giờ · cửa sổ khác khí hậu · trời sáng bên Dương, trời tối/khuya bên Nam.

### R03 — Minh nhận ra *(Distance in Small Things)*
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C03` |
| 🗺️ **Map** | `M01` Nhà (bản gốc ghi `M08` Transit) |
| 🎬 **Trigger** | Khoảnh khắc chuyển tiếp làm khoảng cách hiện rõ. |
| ⭐ **Type** | **MANDATORY** |
| 🔀 **Condition** | Thiết lập motif khoảng cách. |
| ➡️ **After CG** | Transit sequence → chapter tiếp. |

> ⚠️ **Sửa:** chuyơn này trong `01_STORY.md` là **Minh hỏi về Nam tại nhà**. Bản gốc pack 03/04 gán sai map và nội dung. Lấy `01_STORY.md` làm chuẩn.

### R04 — Kế hoạch gặp nhau ⭐ **ĐÃ SỬA** *(The Question)*
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C04` |
| 🗺️ **Map** | `M04` (điểm kết nối) |
| 🎬 **Trigger** | Nam hỏi trực tiếp Dương muốn gì trong mối quan hệ. |
| ⭐ **Type** | **MANDATORY + DIALOGUE VARIANT** |
| 🔀 **Condition** | Choice đổi `ROMANCE_TRUST` tone nhưng **không** finalize route. |
| ➡️ **After CG** | Choice result dialogue → chapter exit. |

### R05 — Khoảng cách không chỉ tính bằng km *(Different Schedules)*
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C05` |
| 🗺️ **Map** | `M05` Viện dưỡng lão |
| 🎬 **Trigger** | Áp lực công việc và cuộc gọi đến cùng lúc. |
| ⭐ **Type** | **MANDATORY** |
| 🔀 **Condition** | Tăng áp lực `OVERLOAD`. |
| ➡️ **After CG** | Phone interaction → setup conflict. |

> 📍 **Ghi chú asset:** M05 phải là **viện dưỡng lão** (kho thuốc, phòng bệnh nhân), không phải văn phòng. Xem `03_MAP_EVENT_FLOW.md` 03.00.2.

### R06 — Cuộc cãi nhau nhỏ ⭐ **ĐÃ SỬA** *(Not Another Item on the Schedule)*
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C06` |
| 🗺️ **Map** | `M04` / **Phone Event** — cuộc gọi đêm |
| 🎬 **Trigger** | Nam đối diện với Dương về việc bị coi như một việc nữa trong lịch. |
| ⭐ **Type** | **MANDATORY** — Major Conflict CG |
| 🔀 **Condition** | `ROMANCE_TRUST` và `FLAG_ROMANCE_HONESTY` đổi theo choice. |
| ➡️ **After CG** | Choice → route-specific emotional aftermath. |

> ⚠️ **Composition bắt buộc:** Dương ở nhà (foreground), Nam ở Việt Nam qua màn hình. Giọng nói mệt vì đã giữ máy cả buổi chiều — thể hiện bằng **ánh sáng xanh màn hình trên mặt Dương**.

### R07 — Những ngày không có tin nhắn *(Who Reaches Out)*
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C07` |
| 🗺️ **Map** | `M01` Nhà / `M03` Đường |
| 🎬 **Trigger** | Sự im lặng bị phá hoặc bị để nguyên. |
| ⭐ **Type** | **CONDITIONAL** |
| 🔀 **Condition** | Biến thể theo ai chủ động liên lạc và mức trust trước đó. |
| ➡️ **After CG** | Message/call → `A2_C08`. |

### R08 — Nói thật *(What Are You Afraid Of?)* ⭐
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C08` |
| 🗺️ **Map** | `M09` Không gian ngoài yên tĩnh |
| 🎬 **Trigger** | Cuộc trò chuyện thành thật đạt tới mức dễ tổn thương. |
| ⭐ **Type** | **MANDATORY + EXPRESSION VARIANT** |
| 🔀 **Condition** | Tác động lớn lên `SELF_AWARENESS` / `ROMANCE_TRUST`. |
| ➡️ **After CG** | Reflection → final relationship chapter. |

> 📌 Cần **expression variant** cho Dương (khóc / kiềm / mở lòng). Xem `08_ASSET_MANIFEST.md`.

### R09 — Cuộc gọi cuối Arc *(The Shape of Us)* ⭐ **ĐÃ SỬA**
| | |
|---|---|
| 📍 **Chapter** | Arc 2 • `A2_C09` |
| 🗺️ **Map** | `M08` — **hai sân ga ở hai quốc gia** |
| 🎬 **Trigger** | Quyết định cuối về mối quan hệ trước chuyển tiếp. |
| ⭐ **Type** | **MANDATORY + ROUTE VARIANT** |
| 🔀 **Condition** | Resolve `ROMANCE_STATE = ACTIVE / UNCERTAIN / ENDED`. |
| ➡️ **After CG** | Commitment / open future / goodbye sequence. |

> ⚠️ **Composition bắt buộc:** split frame. Bên trái — sân ga tàu Thụy Điển, Dương. Bên phải — sân bay Việt Nam, Nam qua màn hình. **Hai đồng hồ hiển thị hai giờ khác nhau.**

### R10 — Sau câu trả lời *(After the Answer)*
| | |
|---|---|
| 📍 **Chapter** | Arc 2 → Arc 3 Bridge • `A2_C09` End |
| 🗺️ **Map** | `M03` Đường / `M01` Nhà |
| 🎬 **Trigger** | Dương một mình sau quyết định về mối quan hệ. |
| ⭐ **Type** | **CONDITIONAL** — Bridge CG |
| 🔀 **Condition** | Composition/text khác nhau theo `ROMANCE_STATE`. |
| ➡️ **After CG** | Fade sang mở đầu Arc 3. |

---

## 04.03 — 🌱 ARC 3: LIFE / WORK / STUDY | L01–L10

### L01 — Một lịch trình quá đầy *(The Week Ahead)*
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C01` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Dương xem lại một tuần đã chứa quá nhiều cam kết. |
| ⭐ **Type** | **MANDATORY** — Arc Setup |
| 🔀 **Condition** | Thiết lập `OVERLOAD` hiện tại và áp lực ưu tiên. |
| ➡️ **After CG** | Choice approach → `M05`. |

### L02 — Một ca làm khó *(The Opportunity)*
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C02` |
| 🗺️ **Map** | `M06` Phòng sếp Annika |
| 🎬 **Trigger** | Sếp trình bày một cơ hội công việc cụ thể. |
| ⭐ **Type** | **MANDATORY + VARIANT** |
| 🔀 **Condition** | `CAREER_FOCUS` và `FLAG_WORK_OPPORTUNITY` có thể cập nhật. |
| ➡️ **After CG** | Nhận / thương lượng / từ chối. |

> 📍 **Cần asset nhân vật `CHAR_ANNIKA`** — nữ Thụy Điển ~45 tuổi. Xem `08_ASSET_MANIFEST.md`.

### L03 — Minh và con đường riêng *(A Future of Her Own)*
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C03` |
| 🗺️ **Map** | `M01` Nhà |
| 🎬 **Trigger** | Minh nói ra hoặc xác nhận kế hoạch cho tương lai của mình. |
| ⭐ **Type** | **MANDATORY** |
| 🔀 **Condition** | Family presentation đổi; Dương có thể hỗ trợ hoặc kiểm soát. |
| ➡️ **After CG** | Choice → chuẩn bị `FAMILY_STATE`. |

### L04 — Một cuộc gọi quan trọng ⭐ **ĐÃ SỬA** *(What Life Are You Building?)*
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C04` |
| 🗺️ **Map** | **Remote scene** (bỏ hoàn toàn `M04`) |
| 🎬 **Trigger** | Nam hỏi Dương đang hình dung tương lai mình đang xây thế nào. |
| ⭐ **Type** | **CONDITIONAL VARIANT** |
| 🔀 **Condition** | Dialogue/pose phụ thuộc `ROMANCE_STATE` từ Arc 2. |
| ➡️ **After CG** | Future-tone choice → `A3_C05`. |

### L05 — Không thể chọn hết *(Two Important Things)* ⭐
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C05` |
| 🗺️ **Map** | `M05 → M07 → M01` |
| 🎬 **Trigger** | Các cam kết cạnh tranh chạm cùng một khoảnh khắc. |
| ⭐ **Type** | **MANDATORY** — Multi-Location CG |
| 🔀 **Condition** | Tác động lớn lên `CAREER_FOCUS` / `STUDY_FOCUS` / `CONNECTION_FOCUS` / `OVERLOAD`. |
| ➡️ **After CG** | Priority choice → hướng route chủ đạo. |

> 📍 **Ghi chú asset:** `M07` thư viện **chưa có asset** — chặn CG này. Xem `08_ASSET_MANIFEST.md`.

### L06 — Breaking Point ⭐
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C06` |
| 🗺️ **Map** | `M03 → M09` |
| 🎬 **Trigger** | Áp lực narrative đạt đỉnh; Dương cuối cùng đối diện giới hạn. |
| ⭐ **Type** | **MANDATORY** — Major Turning Point CG |
| 🔀 **Condition** | Set `BREAKING_POINT_STATE = AWARE / PUSH_ON / WITHDRAW`. |
| ➡️ **After CG** | Choice → overload presentation đổi. |

> 🎨 **CG này cần 3 biến thể riêng biệt**, không phải expression variant:
> `AWARE` (ngồi xuống) / `PUSH_ON` (đứng lại, tiếp tục) / `WITHDRAW` (bỏ đi). Chúng khác hẳn về composition.

### L07 — Ba cuộc nói chuyện *(What Do You Want?)*
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C07` |
| 🗺️ **Map** | `M09` Không gian ngoài yên tĩnh |
| 🎬 **Trigger** | Dương nhìn lại điều mình muốn, tách khỏi kỳ vọng của người khác. |
| ⭐ **Type** | **MANDATORY** — Introspective CG |
| 🔀 **Condition** | Set personal priority tone: `SELF / CONNECTION / ACHIEVEMENT`. |
| ➡️ **After CG** | Memory callback → route staging. |

### L08 — Cơ hội *(The Next Door)* ⭐
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C08` |
| 🗺️ **Map** | `M06` / `M07` / `M10` (theo route) |
| 🎬 **Trigger** | Một bước đi tiếp theo cụ thể được trình bày qua route-specific staging. |
| ⭐ **Type** | **MANDATORY + ROUTE VARIANT** |
| 🔀 **Condition** | Khoá dominant route candidate: `CAREER / STUDY / BALANCE`. |
| ➡️ **After CG** | Route confirmation → relationship resolution. |

### L09 — Nam không thể chờ mãi ⭐ **ĐÃ SỬA** *(Is There Room for Us?)*
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C09` |
| 🗺️ **Map** | **Cuộc gọi đêm** (bỏ hoàn toàn `M04`/`M08`) |
| 🎬 **Trigger** | Dương quyết định Nam có vị trí xác định trong tương lai phía trước không. |
| ⭐ **Type** | **CONDITIONAL + MAJOR ROUTE VARIANT** |
| 🔀 **Condition** | Final romance state; có thể set `FLAG_COMMIT_TO_NAM` hoặc `FLAG_LET_NAM_GO`. |
| ➡️ **After CG** | Romance epilogue path → `A3_C10`. |

### L10 — Bước đi tiếp theo là của Dương *(The Next Step Is Mine)* ⭐
| | |
|---|---|
| 📍 **Chapter** | Arc 3 • `A3_C10` → `A3_C12` |
| 🗺️ **Map** | `M01 → M08 → M10` |
| 🎬 **Trigger** | Minh rời đi / bước độc lập và bước tiếp theo của Dương được dàn dựng như mirror cuối của game. |
| ⭐ **Type** | **MANDATORY + FINAL ORIENTATION VARIANT** |
| 🔀 **Condition** | Khoá `FAMILY_STATE` và `FINAL_ORIENTATION = CONNECTION / SELF / RECOVERY`. |
| ➡️ **After CG** | Ending Resolver → Ending Group. |

---

## 04.04 — MASTER PLACEMENT TABLE

| CG | Arc | Chapter | Map | Type | Key State |
|----|-----|---------|-----|------|-----------|
| F01 | 1 | `P01`/`A1_C01` | M01 | Mandatory | Setup |
| F02 | 1 | `A1_C01` | M01 | Mandatory | Overload tone |
| F03 | 1 | `A1_C02` | M01 | Mandatory | Family tension |
| F04 | 1 | `A1_C03` | M03 | Conditional | Communication tone |
| F05 | 1 | `A1_C04` | M01 | Mandatory | Family trust tone |
| F06 | 1 | `A1_C05` | M01 | Mandatory | Conflict setup |
| **F07** | 1 | `A1_C06` | M01 | **Major** | Family Trust / Truth |
| F08 | 1 | `A1_C07` | M02/M03 | Conditional | Aftermath |
| F09 | 1 | `A1_C08` | M01 | Variant | Accepted Help |
| F10 | 1 | `A1_C09` | M01 | Resolution | Family State |
| R01 | 2 | `A2_C01` | M03 | Mandatory | Contact |
| R02 | 2 | `A2_C02` | M04 | Mandatory | Baseline + múi giờ |
| R03 | 2 | `A2_C03` | **M01** | Mandatory | Distance *(đã sửa map)* |
| R04 | 2 | `A2_C04` | M04 | Variant | Romance tone |
| R05 | 2 | `A2_C05` | M05 | Mandatory | Overload |
| **R06** | 2 | `A2_C06` | M04/Phone | **Major** | Romance Trust |
| R07 | 2 | `A2_C07` | M01/M03 | Conditional | Contact state |
| **R08** | 2 | `A2_C08` | M09 | **Major** | Honesty |
| R09 | 2 | `A2_C09` | M08 | Route | Romance State |
| R10 | 2→3 | Bridge | M03/M01 | Conditional | Romance aftermath |
| L01 | 3 | `A3_C01` | M01 | Mandatory | Overload setup |
| L02 | 3 | `A3_C02` | M06 | Variant | Career Focus |
| L03 | 3 | `A3_C03` | M01 | Mandatory | Family future |
| L04 | 3 | `A3_C04` | **Remote** | Conditional | Romance state |
| **L05** | 3 | `A3_C05` | M05/M07/M01 | **Major** | Priority |
| **L06** | 3 | `A3_C06` | M03/M09 | **Major** | Breaking Point |
| L07 | 3 | `A3_C07` | M09 | Mandatory | Self/Connection |
| **L08** | 3 | `A3_C08` | M06/M07/M10 | **Route** | Dominant route |
| **L09** | 3 | `A3_C09` | **Remote/night** | **Route** | Romance final |
| L10 | 3 | `A3_C10`–`C12` | M01/M08/M10 | Final | Family + Orientation |

---

## 04.05 — CG TYPE DISTRIBUTION

| Loại | Số lượng |
|------|----------|
| Mandatory Core CG | 19 |
| Mandatory + Variant / Expression | 6 |
| Conditional / Bridge / Route CG | 5 |
| **Tổng CG ID** | **30** |

### IMPORTANT PRODUCTION NOTE

> **"Variant" không nhất thiết nghĩa là vẽ một CG hoàn toàn mới.**
> Nên ưu tiên **cùng background / composition** với thay đổi:
> expression · vị trí nhân vật · lighting · trạng thái điện thoại · overlay.

Mục tiêu: giữ scope sản xuất hợp lý mà vẫn có biến thể.

---

## 04.06 — ENDING CG EXECUTION

Sau L10, Ending Pack quyết định Ending Group.
**Không đánh số thêm CG mới vào bộ 30 core.** Ending sử dụng:

- **Crop / close-up** của L10 với lighting khác.
- **Route-specific variant** của L08 / L09 / L10.
- **Ending illustration riêng** quản lý như *Ending Frame*, **không tính vào CG ID core**.
- **Text/title overlay** và epilogue panel.

### ENDING FRAME MAPPING

| Ending | Ending Frame |
|--------|--------------|
| **E01** True Growth | `L10` + open-space variant |
| **E02** Romance | `L09` commitment variant |
| **E03** Career | `L08` career variant |
| **E04** Study | `L08` study variant |
| **E05** Letting Go | `L09` goodbye variant |
| **E06** Overload | `L06` push-on aftermath |
| **E07** Recovery | `L06` aware + `L10` recovery variant |
| **E08** Burnout | `L06` severe aftermath |
| **E09** Balanced | `L10` neutral continuation variant |

> ✅ Quy tắc này giữ đúng con số **30 CG** mà vẫn đủ 9 ending khác nhau.

---

## 04.07 — CG PRODUCTION CHECKLIST

Mỗi CG phải đáp ứng trước khi vào production:

- [x] Có **unique ID**
- [x] Map tới **chapter/event** cụ thể
- [x] Trạng thái **Mandatory vs Conditional** đã định nghĩa
- [x] **State/flag dependencies** đã xác định
- [x] **Entry trigger** và **exit flow** đã biết
- [x] **Route variants** tái sử dụng asset khi có thể
- [x] **Ending frames** tách khỏi 30 core CG count
- [ ] **Tuân thủ ràng buộc 04.00.1** (không vẽ Dương + Nam cùng phòng)

---

**TIẾP** → `05_VFX_AUDIO_PLACEMENT.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
