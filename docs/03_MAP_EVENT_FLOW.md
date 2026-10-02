# 🗺️ 03. MAP / EVENT FLOW

> Chapter-to-Map Narrative Flow.
> 10 map core, tái sử dụng nhiều lần bằng cách đổi thời gian, object state, dialogue, VFX và event trigger.
> **Mục tiêu:** giảm scope nhưng vẫn tạo cảm giác cuộc sống thay đổi theo từng Arc.

---

## 03.00 — MASTER MAP LIST

| Map | Tên | Vai trò | Tái dùng |
|-----|-----|---------|----------|
| **M01** | Nhà Dương / Living Space | Family hub, reflection, Minh events | Rất nhiều |
| **M02** | Hành lang / Cửa ra vào | Transition, departure, return, khoảng lặng | Nhiều |
| **M03** | Đường / Khu phố | Walking transition, gọi điện, ambient reflection | Rất nhiều |
| **M04** | **Quán cà phê / Điểm hẹn** | ⚠️ Đã đổi thành **điểm gọi video** — xem 03.00.1 | Nhiều |
| **M05** | Nơi làm việc — **viện dưỡng lão** | Work pressure, sếp, career choices | Nhiều |
| **M06** | Phòng họp / Khu riêng của sếp | High-pressure dialogue, cơ hội | Ít |
| **M07** | Không gian học tập / Thư viện | Study route, lên kế hoạch tương lai | Ít |
| **M08** | Sân ga / Trạm giao thông | Distance, departure, reunion, route transition | Nhiều |
| **M09** | Không gian ngoài yên tĩnh / Công viên | Reflection, recovery, nói thật | Nhiều |
| **M10** | Không gian mở cuối cùng | Final chapter và ending staging | Ít |

### MAP REUSE RULE

- **Base geometry giữ ổn định.**
- **Time block** thay đổi: Morning / Day / Evening / Night.
- **Object states** thay đổi theo Event Flags.
- **Dialogue nodes** thay đổi theo Family / Romance / Priority State.
- Một số chapter chỉ dùng một phần map hoặc một cinematic sub-area.

---

## 03.00.1 — ⚠️ THAY ĐỔI BẮT BUỘC DO Q1: M04 và M08

> **Bối cảnh:** Dương ở Thụy Điển, Nam ở Việt Nam. **Hai người không gặp mặt.**

Bản gốc dùng M04 (Café) và M08 (Transit) làm **nơi hai người gặp nhau**. Cấu trúc đó không tồn tại được trong setting đã chốt. Dưới đây là cách giữ map, đổi bản chất scene.

### M04 — từ "nơi gặp mặt" thành "nơi kết nối"

| Yếu tố | Bản gốc | Bản đã sửa |
|---------|----------|------------|
| Dương ở đâu | M04 cùng Nam | M04 quán cà phê gần nhà (Thụy Điển), buổi chiều |
| Nam ở đâu | M04 cùng Dương | **Phía bên kia màn hình** — quán quen ở Việt Nam, cùng khung giờ hoặc gần khuya |
| CG thể hiện | hai người cùng khung hình | **Chia đôi khung hình** hoặc Dương nhìn màn hình điện thoại |
| Yếu tố mới | — | **Múi giờ** — chi tiết cơ chế ở `02_GAMEPLAY_SYSTEM.md` 02.05.1 |

**Kết quả:** M04 vẫn là "không gian thân quen" nhưng giờ nó là **không gian của Dương một mình**, nơi cô chọn ngồi để nói chuyện với người đang ở rất xa. Vật dụng trong cảnh (tách cà phê, bàn ghế) trở thành **vật thay thế cho sự hiện diện** — thứ Dương nhìn thay cho Nam.

### M08 — từ "sân ga chia tay" thành "hai sân ga"

| Yếu tố | Bản gốc | Bản đã sửa |
|---------|----------|------------|
| Bối cảnh | hai người đứng cùng sân ga | Dương ở **sân ga tàu Thụy Điển**, Nam ở **sân bay Việt Nam** |
| Lời chia tay | trực tiếp | **qua điện thoại**, hai bên nhìn chuyến tàu/chuyến bay riêng |
| Yếu tố mới | — | **Đồng hồ ngược nhau** — hai màn hình hiển thị hai giờ khác nhau |

**Kết quả:** Sự chia tay vẫn xảy ra, nhưng đau hơn — hai người cùng chờ, cùng nhìn một hành trình không thuộc về nhau.

### Danh sách chương bị ảnh hưởng

| Chương | Bản gốc | Bản đã sửa |
|--------|----------|------------|
| `A2_C02` | gặp ở quán cà phê | Dương ngồi ở quán gần nhà, **gọi video** cho Nam ở quán bên Việt Nam |
| `A2_C04` | gặp, Nam hỏi trực tiếp | **Video call dài** — câu hỏi giữ nguyên |
| `A2_C06` | xung đột tại quán | **Xung đột qua điện thoại** — Dương bật/tắt máy |
| `A2_C09` | chia tay ở sân ga | **Hai sân ga ở hai quốc gia**, gọi nhau lúc chia tay |
| `A3_C04` | café hoặc remote | Chuyển hẳn sang **remote scene** |
| `A3_C09` | ngưỡng cửa quan hệ tại M04/M08 | **Cuộc gọi đêm** — đúng chủ đề "Nam không thể chờ mãi" |

> Chi tiết nội dung từng chương: `01_STORY.md`.

### 03.00.2 — Bổ sung do Q1: M05 là viện dưỡng lão, không phải văn phòng

Bản gốc gọi M05 là "Workplace" chung chung và dùng asset `office 1–5` (văn phòng).
Với setting đã chốt, M05 phải là **viện dưỡng lão**: sảnh chính, hành lang, kho thuốc, bếp, phòng bệnh nhân, phòng sếp.
→ Xem danh sách asset cần bổ sung tại `08_ASSET_MANIFEST.md`.

**Nội thất bắt buộc của M05 (theo setting):**

| Khu vực | Dùng cho chương |
|---------|-----------------|
| Sảnh chính | routine mở đầu ca |
| Kho thuốc | `A2_C05`, `A3_C02` — cơ hội nghề nghiệp |
| Phòng bệnh nhân | `A3_C02`, minigame đưa thuốc |
| Phòng sếp Annika | `A3_C02` — cơ hội thăng chức |
| Hành lang viện | `A1_C07`, `A3_C06` — kiệt sức |
| Bếp viện | `A2_C05` — sinh hoạt ăn uống |

---

## 03.01 — PROLOGUE + ARC 1: 🏠 FAMILY

> Tên chương chuẩn theo `01_STORY.md`. Tên tiếng Anh trong ngoặc là bản nháp trong tài liệu gốc, giữ lại để đối chiếu.

### `P01` — Một ngày bình thường
| | |
|---|---|
| 🗺️ **Map** | `M01 → M02 → M03` |
| 🚪 **Entry** | Bắt đầu tại M01, buổi sáng. |
| 🎯 **Objective** | Hoàn thành routine và rời nhà. |
| 🔎 **Key interactions** | Calendar/schedule (giới thiệu workload) · Phone (tin nhắn đầu tiên) · Minh (dialogue ngắn) · Door (exit trigger) |
| 🎬 **Event flow** | Player kiểm tra lịch → một việc gia đình chen vào kế hoạch → Dương tự xử lý thay vì hỏi người khác → rời M01 → M02 → M03 |
| 🔀 **Choice / State** | Không có route choice lớn; thiết lập tone `OVERLOAD` và thói quen tự gánh. |
| ➡️ **Exit** | Transition sang `A1_C01`. |

### `A1_C01` — Một buổi sáng quen thuộc
| | |
|---|---|
| 🗺️ **Map** | `M01` |
| 🚪 **Entry** | Buổi sáng, khu bếp / phòng khách. |
| 🎯 **Objective** | Chuẩn bị cho ngày mới và nói chuyện với Minh. |
| 🔎 **Key interactions** | Minh · một việc dang dở · Phone · Calendar |
| 🎬 **Event flow** | Optional interaction xây bối cảnh → required talk với Minh → Minh đề nghị giúp → story event kết thúc routine |
| 🔀 **Choice / State** | Minor: tự làm / nhờ Minh → `CH_A1_01`, có thể set `FLAG_SHARED_WORK` |
| ➡️ **Exit** | `M01 → M03` hoặc time transition. |

### `A1_C02` — Những việc không tên *(Things Left Unsaid)*
| | |
|---|---|
| 🗺️ **Map** | `M01` |
| 🚪 **Entry** | Buổi tối, vừa về nhà. |
| 🎯 **Objective** | Tìm hiểu điều Minh đang tránh nói. |
| 🔎 **Key interactions** | Cửa phòng Minh · vật dụng chung / kỷ niệm · bàn bếp |
| 🎬 **Event flow** | Free explore ngắn → object interaction mở self-talk → talk trigger → conversation |
| 🔀 **Choice / State** | Không khóa state; xây tension. **Không giải quyết hoàn toàn mâu thuẫn.** |
| ➡️ **Exit** | Kết thúc tại M01, transition sang ngày sau. |

### `A1_C03` — Cuộc gọi *(Two Directions)*
| | |
|---|---|
| 🗺️ **Map** | `M03 → M01` |
| 🚪 **Entry** | Buổi tối, trên đường về. |
| 🎯 **Objective** | Quyết định cách phản hồi khi việc gia đình và Nam cùng xuất hiện. |
| 🔎 **Key interactions** | Phone · travel point về nhà · ambient thought interaction |
| 🎬 **Event flow** | Notification từ Nam → family task xuất hiện → player về nhà → short event giải quyết ưu tiên tức thời |
| 🔀 **Choice / State** | `CH_A1_03` — xử lý gia đình ngay / báo Nam rõ mình bận |
| ➡️ **Exit** | Thiết lập tone giao tiếp ban đầu → `A1_C04`. |

### `A1_C04` — Những kế hoạch riêng *(What Minh Wants)*
| | |
|---|---|
| 🗺️ **Map** | `M01` |
| 🚪 **Entry** | Buổi chiều tại nhà. |
| 🎯 **Objective** | Thực sự lắng nghe điều Minh muốn. |
| 🔎 **Key interactions** | Minh · vật dụng cá nhân · Calendar |
| 🎬 **Event flow** | Optional context → required dialogue → Dương nhận ra mình thường **giả định** điều tốt nhất cho Minh mà không hỏi |
| 🔀 **Choice / State** | Minor dialogue tone. |
| ➡️ **Exit** | Transition sang `A1_C05`. |

### `A1_C05` — Những điều không nói *(A Familiar Argument)*
| | |
|---|---|
| 🗺️ **Map** | `M01` |
| 🚪 **Entry** | Ban đêm, tension đã có sẵn. |
| 🎯 **Objective** | Hoàn thành cuộc nói chuyện trước khi rời scene. |
| 🔎 **Key interactions** | Minh · cửa ra vào **khoá cho tới khi event kết thúc** |
| 🎬 **Event flow** | Talk bắt đầu bình tĩnh → thói quen cũ lộ ra → argument leo thang → player mất free control trong cinematic beat |
| 🔀 **Choice / State** | Không route lock; setup cho `A1_C06`. |
| ➡️ **Exit** | Immediate continuation. |

### `A1_C06` — Lần đầu nói thật ⭐
| | |
|---|---|
| 🗺️ **Map** | `M01` |
| 🚪 **Entry** | Cùng vị trí, ngay sau argument. |
| 🎯 **Objective** | Đối diện trực tiếp với lời nói của Minh. |
| 🔎 **Key interactions** | Minh · optional reflection object sau event |
| 🎬 **Event flow** | Main dialogue → Choice UI → option result dialogue → conditional aftermath |
| 🔀 **Choice / State** | **Major** — `CH_A1_06`. Cập nhật `FAMILY_TRUST`, `SELF_AWARENESS`, `FLAG_FAMILY_TRUTH`. |
| ➡️ **Exit** | Unlock `A1_C07`. |

### `A1_C07` — Một ngày không ổn
| | |
|---|---|
| 🗺️ **Map** | `M02 → M03` |
| 🚪 **Entry** | Ngoài nhà, buổi tối. |
| 🎯 **Objective** | Cho Dương một khoảng cách vật lý để suy nghĩ. |
| 🔎 **Key interactions** | Phone · ghế / điểm yên tĩnh · cửa quay lại |
| 🎬 **Event flow** | Free walk → optional phone message → reflection trigger → quyết định quay lại / tiến tới |
| 🔀 **Choice / State** | Tone only; có thể tham chiếu kết quả `A1_C06`. |
| ➡️ **Exit** | Return `M01`. |

> 📍 **Ghi chú asset:** key moment của chương là *"Dương ngồi ở trạm xe buýt"*. Chưa có asset trạm xe buýt — xem `08_ASSET_MANIFEST.md`.

### `A1_C08` — Người không nói gì
| | |
|---|---|
| 🗺️ **Map** | `M01` |
| 🚪 **Entry** | Ban ngày, việc thực tế tại nhà. |
| 🎯 **Objective** | Hoàn thành một việc cùng Minh. |
| 🔎 **Key interactions** | Task object · Minh · Calendar |
| 🎬 **Event flow** | Minh đã chủ động xử lý một phần → Dương phản ứng → player kiểm tra kết quả → dialogue đóng scene |
| 🔀 **Choice / State** | `CH_A1_08` — cảm ơn và để Minh tiếp tục / kiểm tra và làm lại. Có thể set `FLAG_ACCEPTED_HELP`. |
| ➡️ **Exit** | Unlock `A1_C09`. |

### `A1_C09` — Không phải một mình
| | |
|---|---|
| 🗺️ **Map** | `M01 → M02` |
| 🚪 **Entry** | Buổi sáng, mirror với `A1_C01`. |
| 🎯 **Objective** | Chuẩn bị rời nhà theo cách mới. |
| 🔎 **Key interactions** | Calendar · Minh · Door |
| 🎬 **Event flow** | Routine interaction → vấn đề cũ quay lại → **final Arc 1 choice** → exit cinematic |
| 🔀 **Choice / State** | **Major** — `CH_A1_09`. → **resolve `FAMILY_STATE`** |
| ➡️ **Exit** | Exit `M02` → Arc 2. |

---

## 03.02 — ARC 2: ❤️ ROMANCE

> ⚠️ **Nam luôn ở Việt Nam.** Mọi scene là tin nhắn / call / video call. M04 và M08 dùng như **điểm kết nối**, không phải nơi gặp — xem 03.00.1.

### `A2_C01` — Tin nhắn chưa trả lời
| | |
|---|---|
| 🗺️ **Map** | `M03 → M04` |
| 🚪 **Entry** | Đường, chiều muộn. |
| 🎯 **Objective** | Kiểm tra các tin nhắn của Nam. |
| 🔎 **Key interactions** | Phone · transit point · optional reflection point |
| 🎬 **Event flow** | Đọc tin nhắn → choice response → di chuyển đến điểm kết nối hoặc tiếp tục route |
| 🔀 **Choice / State** | `CH_A2_01` — nhắn ngắn / gọi / trì hoãn. Có thể set `FLAG_CONTACTED_NAM`. |
| ➡️ **Exit** | `M04` hoặc time transition. |

### `A2_C02` — Những múi giờ khác nhau ⭐ **ĐÃ SỬA**
| | |
|---|---|
| 🗺️ **Map** | `M04` (**quán cà phê của Dương**, Thụy Điển — Nam ở phía bên kia màn hình) |
| 🚪 **Entry** | Buổi chiều tại Thụy Điển. Ở Việt Nam đã khuya. |
| 🎯 **Objective** | Nói chuyện bình thường — và phát hiện vấn đề múi giờ. |
| 🔎 **Key interactions** | Điện thoại / video call · vật dụng trên bàn · Phone UI |
| 🎬 **Event flow** | Optional talk → main dialogue → **sự lệch giữa điều nói và điều tránh** → lộ ra chênh lệch 5–6 giờ |
| 🔀 **Choice / State** | Tone-based. Đây là chương **giới thiệu cơ chế múi giờ** cho người chơi. |
| ➡️ **Exit** | Kết thúc cuộc gọi → `M03`. |

### `A2_C03` — Minh nhận ra *(Distance in Small Things)*
| | |
|---|---|
| 🗺️ **Map** | `M01` → `M03` |
| 🚪 **Entry** | Nhà. |
| 🎯 **Objective** | Đối diện với việc Minh nhận ra Dương đang né tránh. |
| 🔎 **Key interactions** | Minh · Phone |
| 🎬 **Event flow** | Minh hỏi về Nam → Dương giảm nhẹ vấn đề → Minh không ép, chỉ hỏi "chị có ổn không" → Dương thừa nhận không biết làm sao giữ mọi thứ |
| 🔀 **Choice / State** | No major choice. |
| ➡️ **Exit** | Dương nhận cuộc gọi từ Nam → `A2_C04`. |

### `A2_C04` — Kế hoạch gặp nhau ⭐ **ĐÃ SỬA**
| | |
|---|---|
| 🗺️ **Map** | `M04` (điểm kết nối) |
| 🚪 **Entry** | Buổi tối, yên tĩnh. |
| 🎯 **Objective** | Trả lời câu hỏi của Nam về mong muốn gặp nhau. |
| 🔎 **Key interactions** | Điện thoại / video call · exit sau dialogue |
| 🎬 **Event flow** | Conversation bắt đầu → câu hỏi đến → choice → phản ứng tức thời khác nhau theo lựa chọn |
| 🔀 **Choice / State** | `CH_A2_04` — Có / Chị không biết / Tránh. Đổi tone Romance. |
| ➡️ **Exit** | Unlock `A2_C05`. |

### `A2_C05` — Khoảng cách không chỉ tính bằng km
| | |
|---|---|
| 🗺️ **Map** | `M05 → M03` |
| 🚪 **Entry** | Từ viện dưỡng ra đường. |
| 🎯 **Objective** | Hoàn thành work beat trong khi communication pressure tăng. |
| 🔎 **Key interactions** | Bàn làm việc · tin nhắn/nhiệm vụ từ sếp · Phone |
| 🎬 **Event flow** | Work interaction → notification cắt ngang → player thoát sau nhiệm vụ |
| 🔀 **Choice / State** | Optional response ảnh hưởng dialogue nhưng không route. |
| ➡️ **Exit** | Dẫn tới conflict. |

### `A2_C06` — Cuộc cãi nhau nhỏ ⭐ **ĐÃ SỬA**
| | |
|---|---|
| 🗺️ **Map** | `M04` / **Phone Event** — cuộc gọi đêm |
| 🚪 **Entry** | Riêng tư, hai đầu sợ ở hai quốc gia. |
| 🎯 **Objective** | Đối diện với lời phàn nàn rằng Nam không muốn chỉ là một mục trong lịch. |
| 🔎 **Key interactions** | Điện thoại · phone interface |
| 🎬 **Event flow** | Main dialogue → conflict escalation → choice UI → aftermath khác nhau |
| 🔀 **Choice / State** | **Major** — `CH_A2_06`. Cập nhật `ROMANCE_TRUST` + `FLAG_ROMANCE_HONESTY`. |
| ➡️ **Exit** | Unlock `A2_C07`. |

### `A2_C07` — Những ngày không có tin nhắn
| | |
|---|---|
| 🗺️ **Map** | `M01 → M03` |
| 🚪 **Entry** | Nhà rồi ra đường. |
| 🎯 **Objective** | Quyết định có chủ động phá im lặng hay không. |
| 🔎 **Key interactions** | Phone · điểm yên tĩnh |
| 🎬 **Event flow** | Đọc sự im lặng / missed message → choice → conditional message event |
| 🔀 **Choice / State** | `CH_A2_07` — chủ động nhắn / chờ Nam. |
| ➡️ **Exit** | Đổi tone vào `A2_C08`. |

### `A2_C08` — Nói thật
| | |
|---|---|
| 🗺️ **Map** | `M09` |
| 🚪 **Entry** | Không gian ngoài yên tĩnh, ban đêm. |
| 🎯 **Objective** | Trả lời câu hỏi về điều Dương thật sự sợ. |
| 🔎 **Key interactions** | Điện thoại · ghế / điểm nhìn · ambient object |
| 🎬 **Event flow** | Đi tới điểm yên tĩnh → main dialogue → choice → reflection sau cuộc trò chuyện |
| 🔀 **Choice / State** | **Major** — `CH_A2_08` (honesty choice). |
| ➡️ **Exit** | Dẫn thẳng sang `A2_C09`. |

### `A2_C09` — Cuộc gọi cuối Arc ⭐ **ĐÃ SỬA**
| | |
|---|---|
| 🗺️ **Map** | `M08` → `M03` (**hai sân ga ở hai quốc gia**) |
| 🚪 **Entry** | Ngưỡng cửa / chia tay. |
| 🎯 **Objective** | Xác định trạng thái mối quan hệ khi Arc kết thúc. |
| 🔎 **Key interactions** | Điện thoại · transit trigger · **hai màn hình hiển thị hai giờ khác nhau** |
| 🎬 **Event flow** | Final conversation → choice UI → goodbye / commitment riêng theo branch → departure |
| 🔀 **Choice / State** | **Route** — `CH_A2_09`. → **resolve `ROMANCE_STATE`** |
| ➡️ **Exit** | Transition sang Arc 3. |

---

## 03.03 — ARC 3: 🌱 LIFE / WORK / STUDY

### `A3_C01` — Một lịch trình quá đầy
| | |
|---|---|
| 🗺️ **Map** | `M01 → M05` |
| 🚪 **Entry** | Buổi sáng tại nhà, rồi đi làm. |
| 🎯 **Objective** | Đánh giá lịch tuần và chọn cách bắt đầu. |
| 🔎 **Key interactions** | Calendar · Phone · Door/travel |
| 🎬 **Event flow** | Inspect schedule → choice về cách tiếp cận → di chuyển tới nơi làm/học |
| 🔀 **Choice / State** | `CH_A3_01` — giữ hết / bỏ bớt / xin hỗ trợ. Thiết lập tone Arc 3. |
| ➡️ **Exit** | Branch presentation vào `A3_C02`. |

### `A3_C02` — Một ca làm khó
| | |
|---|---|
| 🗺️ **Map** | `M05 → M06` (kho thuốc → phòng sếp Annika) |
| 🚪 **Entry** | Khu họp của viện dưỡng. |
| 🎯 **Objective** | Đối diện cơ hội công việc mới. |
| 🔎 **Key interactions** | Sếp Annika · bàn làm việc · hồ sơ cuộc họp |
| 🎬 **Event flow** | Work objective → dialogue với sếp → cơ hội được trình bày → choice |
| 🔀 **Choice / State** | `CH_A3_02` — nhận / thương lượng giới hạn / từ chối. Cập nhật `CAREER_FOCUS` + `FLAG_WORK_OPPORTUNITY`. |
| ➡️ **Exit** | Exit tới `M03`. |

### `A3_C03` — Minh và con đường riêng
| | |
|---|---|
| 🗺️ **Map** | `M01` |
| 🚪 **Entry** | Nhà. |
| 🎯 **Objective** | Lắng nghe kế hoạch riêng của Minh. |
| 🔎 **Key interactions** | Minh · vật dụng cá nhân đại diện cho bước tiếp theo |
| 🎬 **Event flow** | Explore → talk → choice response |
| 🔀 **Choice / State** | `CH_A3_03` — tôn trọng và hỗ trợ / kiểm soát và chuẩn bị sẵn mọi thứ |
| ➡️ **Exit** | Cập nhật presentation gia đình. |

### `A3_C04` — Một cuộc gọi quan trọng ⭐ **ĐÃ SỬA**
| | |
|---|---|
| 🗺️ **Map** | **`M04` → chuyển hẳn sang remote scene** (bỏ hoàn toàn café) |
| 🚪 **Entry** | Phòng Dương, ban đêm — hai đầu sợ. |
| 🎯 **Objective** | Trả lời câu hỏi về tương lai. |
| 🔎 **Key interactions** | Điện thoại · ambient interaction |
| 🎬 **Event flow** | Conversation → choice → conditional reaction |
| 🔀 **Choice / State** | `CH_A3_04` — có chỗ cho tình yêu / đang tìm / né tránh |
| ➡️ **Exit** | Thiết lập tone Romance Future → `A3_C05`. |

### `A3_C05` — Không thể chọn hết ⭐
| | |
|---|---|
| 🗺️ **Map** | `M05 → M07 → M01` (montage nhiều ngày) |
| 🚪 **Entry** | Multi-location. |
| 🎯 **Objective** | Chọn ưu tiên khi các việc quan trọng trùng thời điểm. |
| 🔎 **Key interactions** | Work trigger · tài liệu học tập · family/phone trigger |
| 🎬 **Event flow** | Player nhận các trigger cạnh tranh nhau → **objective list cố ý xung đột** → choice giải quyết ưu tiên |
| 🔀 **Choice / State** | **Route lớn** — `CH_A3_05`. Định hướng `PRIORITY_STATE`. |
| ➡️ **Exit** | Đi tới breaking point. |

> 📍 **Ghi chú asset:** `M07` (thư viện) **chưa có asset nào** — xem `08_ASSET_MANIFEST.md`.

### `A3_C06` — Breaking Point ⭐
| | |
|---|---|
| 🗺️ **Map** | `M05 → M03 → M09` (viện dưỡng → trạm xe buýt → công viên yên tĩnh) |
| 🚪 **Entry** | Quá tải trên đường, chuyển tới không gian yên tĩnh. |
| 🎯 **Objective** | Tìm một nơi để Dương đối diện với giới hạn. |
| 🔎 **Key interactions** | Phone notifications · Calendar overlay · điểm yên tĩnh |
| 🎬 **Event flow** | Áp lực giác quan tăng → **controls/objectives đơn giản hoá** → main reflection event → choice |
| 🔀 **Choice / State** | **Major** — `CH_A3_06`. → **set `BREAKING_POINT_STATE`** |
| ➡️ **Exit** | Quyết định cách trình bày overload về sau. |

### `A3_C07` — Ba cuộc nói chuyện
| | |
|---|---|
| 🗺️ **Map** | `M09` |
| 🚪 **Entry** | Không gian yên tĩnh, chiều muộn. |
| 🎯 **Objective** | Tự trả lời câu hỏi trung tâm của game. |
| 🔎 **Key interactions** | Điểm reflection · Phone (optional) |
| 🎬 **Event flow** | Đi bộ → memory callbacks → choice UI |
| 🔀 **Choice / State** | `CH_A3_07` — Bản thân / Kết nối / Thành tựu |
| ➡️ **Exit** | Thiết lập tone Personal Priority. |

### `A3_C08` — Cơ hội ⭐
| | |
|---|---|
| 🗺️ **Map** | `M06` / `M07` / `M10` (**theo route**) |
| 🚪 **Entry** | Route-specific staging. |
| 🎯 **Objective** | Chọn bước đi cụ thể tiếp theo. |
| 🔎 **Key interactions** | Cơ hội việc làm **HOẶC** tài liệu học tập **HOẶC** open-space route trigger |
| 🎬 **Event flow** | Conditional map entry dựa trên state trước đó → main choice → route confirmation |
| 🔀 **Choice / State** | **Route lớn nhất** — `CH_A3_08`. Career / Study / Sustainable balance. **Khóa dominant route candidate.** |
| ➡️ **Exit** | → relationship resolution. |

### `A3_C09` — Nam không thể chờ mãi ⭐ **ĐÃ SỬA**
| | |
|---|---|
| 🗺️ **Map** | **Cuộc gọi đêm** (bỏ hoàn toàn ngưỡng cửa tại M04/M08) |
| 🚪 **Entry** | Đêm, hai đầu. Dương ở nhà, Nam ở phòng làm việc. |
| 🎯 **Objective** | Xác định Nam có vị trí nào trong tương lai Dương đang chọn. |
| 🔎 **Key interactions** | Điện thoại |
| 🎬 **Event flow** | Conversation → choice → branch-specific result |
| 🔀 **Choice / State** | **Route** — `CH_A3_09`. Có thể set `FLAG_COMMIT_TO_NAM` hoặc `FLAG_LET_NAM_GO`. **Resolve Romance Final State.** |
| ➡️ **Exit** | Romance epilogue path → `A3_C10`. |

### `A3_C10` — Ngày Minh bước đi
| | |
|---|---|
| 🗺️ **Map** | `M01 → M08` |
| 🚪 **Entry** | Nhà rồi ra khởi hành / sân ga. |
| 🎯 **Objective** | Đồng hành với Minh nhưng không sống thay Minh. |
| 🔎 **Key interactions** | Minh · túi / cửa / transit trigger |
| 🎬 **Event flow** | Preparation interactions → dialogue → choice → departure hoặc đi cùng một đoạn |
| 🔀 **Choice / State** | `CH_A3_10` — hỗ trợ và buông / tiếp tục kiểm soát. **Khóa Family Final State.** |
| ➡️ **Exit** | Dương có khoảng trống nghĩ về mình. |

### `A3_C11` — Quyết định của Dương ⭐
| | |
|---|---|
| 🗺️ **Map** | `M10` |
| 🚪 **Entry** | Không gian mở, ngưỡng cửa cuối. |
| 🎯 **Objective** | Định nghĩa bước tiếp theo. |
| 🔎 **Key interactions** | **Một** central trigger; minimal optional reflection objects. |
| 🎬 **Event flow** | Callback visuals/lines → final choice UI → **state lock** → walk forward trigger |
| 🔀 **Choice / State** | **Final** — `CH_A3_11`. → **set `FINAL_ORIENTATION`** |
| ➡️ **Exit** | Ending Resolver → Ending Scene. |

### `A3_C12` — Một ngày sau đó *(bổ sung — xem `todo.md` mục 7.1 mâu thuẫn 11)*

> Chương này tồn tại trong `01_STORY.md` và `09_SYSTEM_VARIABLES.md` (resolver chạy **sau A3_C12**) nhưng bản gốc pack 03 bỏ sót. Bổ sung lại để 3 tài liệu khớp nhau.

| | |
|---|---|
| 🗺️ **Map** | `M10` + route-specific map |
| 🚪 **Entry** | Tùy route đã chọn. |
| 🎯 **Objective** | Cho thấy hậu quả đời thường của lựa chọn. Không có twist mới. |
| 🔎 **Key interactions** | Chỉ interaction cần thiết cho route hiện tại. |
| 🎬 **Event flow** | Montage một ngày bình thường → **hành động nhỏ phản chiếu Prologue** → closing beat |
| 🔀 **Choice / State** | **KHÔNG có choice.** Chỉ đọc state để chọn biến thể hình ảnh và dòng thoại. |
| ➡️ **Exit** | Ending Resolver → Ending Group. |

---

## 03.04 — EVENT TRIGGER TYPES

| Loại | Định nghĩa |
|------|------------|
| **AREA_TRIGGER** | player enters a zone |
| **INTERACT_TRIGGER** | player interacts with required object/NPC |
| **STATE_TRIGGER** | event appears only khi value/flag condition met |
| **TIME_TRIGGER** | event starts sau chapter time transition |
| **CHOICE_TRIGGER** | immediate branch sau option selected |
| **CHAIN_TRIGGER** | event B bắt đầu tự động sau event A |

---

## 03.05 — MAP STATE EXAMPLES

### M01 — NHÀ

| Arc | Trạng thái map |
|-----|----------------|
| **Arc 1** | family tension và routine objects |
| **Arc 2** | phone/silence và return-home reflection |
| **Arc 3** | schedule pressure, tương lai của Minh, buông tay |

> ⚠️ Hiện chỉ có **phiên bản sáng**. Arc 1–2 diễn chủ yếu buổi tối → cần night variant. Xem `08_ASSET_MANIFEST.md`.

### M04 — ĐIỂM KẾT NỐI (quán cà phê của Dương)

| Giai đoạn | Trạng thái |
|-----------|------------|
| **Đầu Arc 2** | quen thuộc, thoải mái — Dương gọi Nam từ đây |
| **Giữa Arc 2** | khoảng cách trở nên **hiện thực trong dialogue** |
| **Cuối Arc 3** | không còn là nơi gặp; là nơi Dương ngồi một mình giữa hai cuộc gọi |

> ⚠️ Hiện **chưa có asset quán cà phê** — đang dùng `restaurant 1` làm tạm. Xem `08_ASSET_MANIFEST.md`.

### M08 — SÂN GA / GIAO THÔNG

| Giai đoạn | Trạng thái |
|-----------|------------|
| **Arc 2** | khoảng cách vật lý: hai bên ở hai quốc gia, cùng chờ một chuyến đi |
| **Arc 3** | Minh khởi hành; Dương đưa đến rồi để Minh đi tiếp |

### M09 — KHÔNG GIAN NGOÀI YÊN TĨNH

| Chương | Công dụng |
|--------|-----------|
| `A2_C08` | sự thành thật cảm xúc với Nam |
| `A3_C06` | Breaking Point |
| `A3_C07` | tự phản chiếu có callback |

---

## 03.06 — MASTER EVENT FLOW

```
CHAPTER START
   ↓
MAP LOAD
   ↓
INTRO EVENT
   ↓
FREE EXPLORE
   ↓
REQUIRED INTERACTION(S)
   ↓
MAIN STORY EVENT
   ↓
CHOICE? ── NO ──→ TRANSITION
   │ YES
   ↓
STATE / FLAG UPDATE
   ↓
CONDITIONAL AFTERMATH
   ↓
CHAPTER COMPLETE
   ↓
NEXT MAP / TIME BLOCK
```

---

## 03.07 — PRODUCTION PRIORITY

| Tier | Map |
|------|-----|
| **Tier 1** | `M01` Home · `M03` Street · `M04` Café · `M05` Viện dưỡng · `M09` Quiet Outdoor · `M10` Final Space |
| **Tier 2** | `M02` Corridor · `M06` Meeting Area · `M07` Study Space · `M08` Transit Hub |

**Nguyên tắc:**
1. Build **reusable object states** trước khi tạo chapter-specific geometry.
2. Prototype **một vertical slice trước**: `A1_C01 → A1_C06 → A1_C09`.
3. Rồi mới prototype một romance route và một Arc 3 route trước khi sản xuất hết chương.

---

**TIẾP** → `04_CG_PLACEMENT.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
