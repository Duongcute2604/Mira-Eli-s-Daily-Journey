# 📱 07. UI / HUD

> Thiết kế giao diện, HUD, màn hình điện thoại, journal và ending gallery.
> **Pack này không tồn tại trong bộ `.docx` gốc** — số 07 bị bỏ trống khiến numbering nhảy 06 → 09.
> Viết mới hoàn toàn. Bám theo `09_SYSTEM_VARIABLES.md` mục 09.09 (UI visibility) và `02_GAMEPLAY_SYSTEM.md` 02.05–02.10.

---

## 07.00 — NGUYÊN TẮC GIAO DIỆN

Game này là **visual novel về sự kiệt sức**, không phải RPG về số liệu. Người chơi không được phép mở menu ra và thấy `OVERLOAD = 72`.

| # | Nguyên tắc | Hệ quả thiết kế |
|---|-----------|------------------|
| 1 | **Cảm, không đọc** | Persistent value và Route State **không bao giờ** hiện số. Chỉ hiện qua biểu cảm, hậu quả nội dung, mật độ thông báo. |
| 2 | **UI là công cụ kể chuyện** | Đồng hồ, lịch, tin nhắn không phải đồ trang trí — chúng là nơi người chơi **tự phát hiện** múi giờ và sự kiệt sức. |
| 3 | **Ít chrome** | Không viền dày, không gradient kim loại, không panel thống kê. Khoảng trống là hợp lệ. |
| 4 | **Điều khiển luôn ở chỗ** | Menu, journal, phone mở được bằng 1 phím, không cần rời khỏi dòng chuyện quá lâu. |
| 5 | **Không bao giờ phản hồi sai** | UI không được gợi ý lựa chọn "tốt/bad". Xem 10.05. |

> ⚠️ Nếu người chơi có thể đoán ending bằng cách đếm icon HUD, UI **đang hỏng** → sửa, đừng thêm.

---

## 07.01 — BỐ CỤC MÀN HÌNH

### 07.01.1 — Layout chuẩn (16:9)

```
┌──────────────────────────────────────────────────────────────┐
│  [DAY 12]  [☀ MORNING]              ⏱ 07:20     🔋▓▓▓░        │  ← TOP BAR (mảnh)
│                                                              │
│                    NỘI DUNG CHÍNH                            │
│              (background / CG / sprite)                       │
│                                                              │
│                                                              │
│   ┌────────────────────────────────────────────────────┐     │
│   │  Dương                                         ▾   │     │  ← DIALOGUE BOX
│   │  "Con không biết phải bắt đầu từ đâu."            │     │
│   └────────────────────────────────────────────────────┘     │
│                                                              │
│  [☏]  [✎]  [☰]                        [A]                  │  ← BOTTOM DOCK
└──────────────────────────────────────────────────────────────┘
```

### 07.01.2 — TOP BAR

Thanh trên cùng **chỉ 4 yếu tố**. Tuyệt đối không thêm.

| Yếu tố | Hiển thị | Nguồn | Ghi chú |
|---------|----------|-------|---------|
| Ngày | `DAY 12` chữ | `DAY` | Đếm ngày trong Arc. Reset mỗi chapter lớn. |
| Khung giờ | icon + chữ `MORNING` | `TIME_BLOCK` | Icon: ☀ / 🌤 / 🌆 / 🌙 |
| Đồng hồ | `07:20` | nội bộ | Chỉ hiện ở scene cần (xem 07.03) |
| Năng lượng | icon pin, **không số** | `ENERGY` | 4 mức: đầy / hơi cạn / cạn / gần cạn |

**Màu theo `ENERGY`:** xanh lá → xám → hổ phách → đỏ nhạt. Không nhấp nháy, không đổi màu đột ngột — chuyển mờ trong 1 giây.

### 07.01.3 — BOTTOM DOCK

| Nút | Mở | Phím tắt |
|-----|-----|----------|
| ☏ | Phone | `Q` |
| ✎ | Journal | `W` |
| ☰ | Menu (save/load/options) | `Esc` |
| `A` | Auto-advance | `Space` |

> 🕐 **Đồng hồ Nam** không nằm ở đây — nằm trong app Cuộc gọi. Xem 07.03.

---

## 07.02 — MÀN HÌNH ĐIỆN THOẠI

### 07.02.1 — Cấu trúc

```
┌─────────────────────────────────┐
│  09:41              ▓▓▓░░  78%  │  ← status bar (luôn 78%, không đổi)
├─────────────────────────────────┤
│  ● 2        [Tin nhắn][Lịch]   │
│     [Cuộc gọi][Ngân sách][Ca]   │  ← app grid — chỉ mở app đã mở khoá
├─────────────────────────────────┤
│                                 │
│         NỘI DUNG APP            │
│                                 │
├─────────────────────────────────┤
│         [🏠]                    │  ← về màn hình chính
└─────────────────────────────────┘
```

**Pin cố định 78%** — không bao giờ hao pin, không có chế độ pin yếu. Pin là thứ khiến người chơi lo về nhân vật; ở đây nó chỉ là chrome để màn hình trông như điện thoại.

### 07.02.2 — Màn hình chính (HOME)

- Chỉ hiện **icon app đã mở khoá**. App chưa mở khoá **không hiện placeholder** — tránh gợi ý trước.
- Badge đỏ chỉ dùng cho **tin nhắn chưa đọc có ý nghĩa narrative** (xem 07.05.2).
- Không có app "Cài đặt", không có app "Máy ảnh", không có app mạng xã hội. Giữ màn hình trống để tạo cảm giác **cô đơn**.

### 07.02.3 — App 1: TIN NHẮN

| Yếu tố | Quy tắc |
|---------|---------|
| Danh sách hội thoại | 3 người: **Nam**, **Minh**, **Annika** |
| Bố cục | avatar tròn 32px, tên, tin nhắn cuối, giờ, số tin chưa đọc |
| Mở hội thoại | tin nhắn cuộn lên dần, có thể tua nhanh. Tin cũ **luôn còn**, không xoá. |
| Đã đọc | mờ đi sau 2 ngày trong game. Người chơi **không** được xoá tin — nhân vật không xoá tin vì đó là ký ức. |
| Tin nhắn mới xuất hiện ngoài chương | **có**, đây là cơ chế ambient interaction chính (02.05) |

**Nội dung hội thoại thay đổi theo state:**

| Hội thoại | Điều kiện thay nội dung |
|-----------|------------------------|
| Nam | `ROMANCE_STATE` (3 bản) + `FLAG_*` xem 09.04 |
| Minh | `FAMILY_STATE` (4 bản) |
| Annika | `CAREER_FOCUS` + `REPUTATION` ngưỡng |

> 🎯 **Đây là nơi người chơi học về cả Nam và Minh mà không ai nói trực tiếp.** Không tin nhắn nào được viết như nhiệm vụ; tất cả phải đọc được như người thật nhắn.

### 07.02.4 — App 2: LỊCH

```
┌─────────────────────────────────┐
│  ‹   Tháng 3, 2026      ›      │
├─────────────────────────────────┤
│  T2  T3  T4  T5  T6  T7  T8      │
│   3   4   5   6   7   8   9    │  ← ô trống = không có việc
│   10  11  12 [13] 14  15  16   │  ← hôm nay viền đậm
│   17  18  19  20  21  22  23   │
├─────────────────────────────────┤
│  ▣ 06:00–14:00  Ca sáng        │
│  ▣ 15:00–17:00  Học Minh       │  ← ngày 12
│  ▣ 19:00–21:00  Gọi Nam?       │
└─────────────────────────────────┘
```

| Yếu tố | Quy tắc |
|---------|---------|
| Lịch nghỉ | viết tay kiểu "Nghỉ" — không phải event |
| Ca viện | block xám, dài 8 giờ, đè lên giờ học nếu xung đột |
| Múi giờ Nam | hiện **chỉ khi** lịch có cuộc gọi Nam. Xem 07.03. |
| Mật độ | tăng dần qua từng chương — **đây là kênh thể hiện `OVERLOAD`** (02.08) |

> ⚠️ Khi lịch **kín hoàn toàn**, không hiện cảnh báo. Người chơi tự thấy không còn ô trống. Đó là toàn bộ cơ chế.

### 07.02.5 — App 3: CUỘC GỌI

Đây là **ứng dụng quan trọng nhất** trong game — vì Q1 đã khoá Dương và Nam không bao giờ gặp mặt.

```
┌─────────────────────────────────┐
│  Lịch sử cuộc gọi               │
├─────────────────────────────────┤
│  📞 Nam        12/03  09:12      │  ← đã nhận
│      "Ê, tự nhiên ghê..."       │
│  📵 Nam        11/03  23:40  ⚠   │  ← nhỡ
│      "Không nghe phía bên kia"   │
│  📞 Minh       11/03  20:05      │
│  📵 Sếp Annika 10/03  14:22  ⚠   │
└─────────────────────────────────┘
```

| Yếu tố | Quy tắc |
|---------|---------|
| Nhỡ cuộc gọi | luôn hiện, không xoá. Đây là **hậu quả trì hoãn** — thiếu nó thì múi giờ vô nghĩa. |
| Gọi lại | chỉ gọi lại được nếu khung giờ cho phép (07.03). Bấm ra thông báo nhẹ, không phải màn chặn. |
| Thời lượng | hiển thị **phút** cho cuộc gọi đã nhận: `4 phút`, `12 phút`. Nhìn lại lịch sử = thấy mình đã lỡ bao nhiêu. |
| Cuộc gọi sếp | hiện riêng khối, có tên "Annika Johansson" — nhấn mạnh đây là quan hệ **công việc**, không phải bạn bè |

### 07.02.6 — App 4: NGÂN SỤCH

Mở khoá từ `A1_C01` (bổ sung do Q1 — vì nợ 8 tỷ là bối cảnh xuyên suốt).

| Mục | Hiển thị |
|-----|----------|
| Số dư | `MONEY` hiện số — đây là **ngoại lệ duy nhất** cho quy tắc "không hiện số" (09.09) |
| Nợ | `DEBT` + ngày đến hạn + số tiền còn lại |
| Lịch trả | 3 kỳ đã lên kế hoạch |
| Chi tiêu tháng | 3–4 dòng: **tiền nhà, gửi về nhà, sinh hoạt, để dành** — không phân loại chi tiết |

> ⚠️ **Không** biến app này thành game quản lý tài chính. Không có ô nhập, không phải spreadsheet. Xem 02.10.1.

### 07.02.7 — App 5: CA LÀM

Mở khoá từ `A3_C02`.

| Mục | Nội dung |
|-----|----------|
| Lịch ca tuần | ca sáng 06–14, chiều 14–22 |
| Yêu cầu thi nâng bậc | checklist 3 mục, tiến độ phụ thuộc `CAREER_FOCUS` |
| Yêu cầu của Annika | hiện dần theo `REPUTATION` |

Checklist là **một trong ba chỗ duy nhất** trong game có thanh tiến độ — và nó đo năng lực, không đo sức khoẻ tinh thần.

---

## 07.03 — UI MÚI GIỜ (ĐẶC SẢN CỦA Q1)

Đây là phần UI quan trọng nhất và **hoàn toàn mới**, không có trong bản gốc.

### 07.03.1 — Hai chiếc đồng hồ

Khi mở app **Cuộc gọi** vào khung giờ không thuận lợi, hiện hai đồng hồ cạnh nhau:

```
┌─────────────────────────────────┐
│  Thụy Điển          Việt Nam    │
│     19:40             00:40      │  ← lệch 5h
│      🌆                🌙        │
│                                 │
│  Nam đang ngủ.                 │  ← dòng giải thích, KHÔNG phải cảnh báo
│  Bạn có thể gọi lúc 12:00.     │
└─────────────────────────────────┘
```

| Quy tắc | Chi tiết |
|---------|----------|
| **Không bao giờ** chặn người chơi gọi | Cho phép bấm gọi bất k cứ lúc nào. Hậu quả (nhỡ máy / Nam tắt máy) xử lý bằng nội dung, không bằng UI. |
| Dòng giải thích luôn cho lý do | "Nam đang ngủ", "Nam còn ở lớp", "Dương mệt" — **không** dùng màu đỏ cảnh báo |
| Chỉ hiện khi người chơi chủ động mở app | Không tự nhảy lên. Người chơi phải **tự tìm ra** khung giờ vàng (02.05.1). |
| Đồng hồ VN chỉ hiện từ `A2_C02` | Trước đó Dương chưa nghĩ tới chuyện này → không có UI nào nhắc |

### 07.03.2 — Điều kiện hiển thị

| Khung giờ Thụy Điển | Giờ VN | UI hiển thị |
|---------------------|--------|-------------|
| MORNING 06–11 | 12–17 | Đồng hồ VN hiện, không ghi chú cảnh báo — đây là khung vàng |
| DAY 12–17 | 18–23 | Ghi chú nhẹ: "Nam vừa tan học" |
| EVENING 18–21 | 00–03 | "Nam đang ngủ" |
| NIGHT 22–02 | 05–09 | "Nam vừa thức dậy / Dương kiệt sức" |

### 07.03.3 — Vì sao không phải lý do suông

> Nếu game chỉ chặn cuộc gọi vì múi giờ, người chơi sẽ nghĩ đây là phiền nhiễu thiết kế.
> Vì vậy khung giờ **phải là lợi thế**: `A2_C02` cho người chơi phát hiện MORNING là giờ vàng, và Arc 2 phải được xây để **hy sinh** giờ đó.
> Chi tiết cơ chế: `02_GAMEPLAY_SYSTEM.md` 02.05.1.

---

## 07.04 — JOURNAL / MEMORY LOG

Mở bằng `✎`. Bốn tab.

### 07.04.1 — Tóm tắt chương

Danh sách 31 chương. Chương chưa mở hiện `— — —` (không phải tên bị che, để tránh spoil).

Mỗi chương đã mở ghi 2–4 dòng tóm tắt **bằng giọng Dương**, không phải log hành động.

### 07.04.2 — Ghi chú về nhân vật

Ba thẻ: Nam / Minh / Annika. Mỗi thẻ tích luỹ dòng thông tin theo `FLAG`.

> ⚠️ Chỉ ghi những gì **Dương biết**. Biết từ người khác kể → phải ghi rõ nguồn: *"Nam kể: anh thấy cô ấy cười trong lớp."*
> Đây là chi tiết nhỏ nhưng nó giữ cho journal không biến thành bảng tra cứu.

### 07.04.3 — Lựa chọn quan trọng

Ghi lại 20 choice (`10_CHOICE_BRANCHING.md`) bằng **ngôn ngữ narrative**:

```
A2_C06 — "Con đã nói dối mẹ."
→ Dương nói với Nam rằng mình không mệt.
```

| Sai lầm phải tránh | Làm đúng |
|-------------------|----------|
| "Romance +15, Energy −10" | "Dương nói dối Nam rằng mình không mệt" |
| Hiển thị cờ ✔ / ✗ | Không hiển thị gì — chỉ câu văn |
| Sắp xếp theo ưu tiên | Sắp theo **thứ tự thời gian** |

### 07.04.4 — Mục tiêu hiện tại

1 dòng, hiện ở góc trên journal **và** dưới dialogue box mờ. Không có mũi tên, không có dấu `!`.

---

## 07.05 — HỆ THỐNG THÔNG BÁO

### 07.05.1 — Luật

| Luật | Nội dung |
|------|----------|
| Chỉ dùng khi có ý nghĩa narrative | Không có thông báo "Bạn đã nhận 1 item" |
| Không chặn gameplay | Thông báo trượt qua, không có nút "OK" bắt buộc |
| Số lượng theo `OVERLOAD` | Thấp: 0–1 / chương · Trung bình: 2–3 · Cao: 5–7 / chương |
| Chồng chất khi cao | Notification dồn thành cụm — **đây là biểu hiện trực quan của `OVERLOAD`** |
| Không có notification từ hệ thống | Mọi thông báo đều **từ một người** — báo rằng họ vẫn còn ở đó |

### 07.05.2 — Badge đỏ

- Badge chỉ dùng cho **tin nhắn chưa đọc**.
- Badge cuộc gọi nhỡ **không dùng badge** — nhỡ máy là thứ người ta nhìn thấy trong danh sách, không phải thứ nhỏ nháy đòi hỏi chú ý.
- Số badge **tối đa 9**. Trên 9 hiện `9+`. Chi tiết nhỏ, nhưng giữ badge không bao giờ chiếm nửa màn hình.

---

## 07.06 — DIALOGUE & CHOICE UI

### 07.06.1 — Hộp thoại

| Yếu tố | Quy tắc |
|---------|---------|
| Tên | góc trên trái hộp thoại, chữ nhỏ |
| Chữ | tối đa 2 dòng, tự cuộn |
| Tốc độ chữ | chậm hơn mức người chơi quen — game nặng, không phải game hào hứng |
| Bỏ qua | bấm bất kỳ đâu để hiện hết dòng hiện tại, bấm lần 2 mới sang |
| Portrait | biểu cảm đổi theo 06.03, **không** dùng kiểu pop-in |

### 07.06.2 — Màn hình lựa chọn

```
┌─────────────────────────────────┐
│                                 │
│         (nền tối 60%)          │
│                                 │
│    ┌───────────────────────┐    │
│    │  Con sẽ nói thật.     │    │  ← lựa chọn tốt, tốn nhiều nhất
│    └───────────────────────┘    │
│    ┌───────────────────────┐    │
│    │ Không sao, mẹ lo lắng.│    │
│    └───────────────────────┘    │
│    ┌───────────────────────┐    │
│    │ ...                    │    │  ← im lặng
│    └───────────────────────┘    │
│                                 │
└─────────────────────────────────┘
```

| Luật | Giải thích |
|------|------------|
| Tối đa **3** lựa chọn | 4+ gây tê liệt quyết định |
| Không đánh số, không icon | Số thứ tự tự nhiên = thứ tự người viết muốn |
| Không màu "tốt" / "xấu" | Xem 10.05.7 |
| Lựa chọn tốn tài nguyên | Mọi lựa chọn đều phải có giá — kể cả lựa chọn "im lặng" |
| Không có thanh thời gian | Không có timer trong game |
| Không cho quay lại sau khi chọn | Nhưng **có** cho xem lại trong Journal |

> ⚠️ Lựa chọn phải **dài bằng nhau về độ dài chữ** khi có thể — tránh "lựa chọn dài luôn là lựa chọn sâu" xuất hiện vô tình.

---

## 07.07 — OVERLOAD QUA GIAO DIỆN

`OVERLOAD` **không có thanh, không có số, không có cảnh báo**. Bảng dưới là toàn bộ những gì thay đổi trên UI.

| Mức | Lịch | Thông báo | Màn hình điện thoại | Dialogue | Hue màn hình |
|-----|------|-----------|--------------------|----------|-------------|
| **Thấp** | nhiều ô trống | 0–1 | sạch, icon thưa | self-talk bình thường | chuẩn |
| **Trung bình** | lấp dần | 2–3 | badge tích luỹ | câu ngắn hơn | hơi ấm |
| **Cao** | kín hoàn toàn | 5–7, dồn cụm | badge nhiều, hộp thoại dài | self-talk đổi giọng | ấm dần |
| **Breaking Point** | kín + không ô nghỉ | dồn thành khối | — | objective đơn giản hoá | ấm đậm |

### 07.07.1 — Hue màn hình

| Mức | Overlay |
|-----|---------|
| Thấp | không |
| Trung bình | ấm `#000` 8% |
| Cao | ấm `#1a0d05` 18% |
| Breaking Point | ấm `#2a1005` 30% |

> Overlay phải **tăng dần, không nhảy**. Và **phải hạ về 0** sau `A3_C07` (ba cuộc nói chuyện). Nếu không hạ, game kết thúc trong nước và người chơi không còn tin là có thể thở.

### 07.07.2 — Cấm tuyệt đối

- ❌ Thanh máu
- ❌ Thanh stress
- ❌ Cảnh báo đỏ "Bạn đang quá tải!"
- ❌ Icon đầu lâu / não cháy
- ❌ Hộp thoại bị làm mờ khi `OVERLOAD` cao — người chơi phải **đọc được** dù mệt

---

## 07.08 — ENDING GALLERY

### 07.08.1 — Vị trí

Menu chính → **Nhật ký hành trình**. Dùng lại khung visual của Journal cho nhất quán.

```
┌─────────────────────────────────┐
│  NHẬT KÝ HÀNH TRÌNH            │
├─────────────────────────────────┤
│                                 │
│   ▢     ▢     ▢               │
│   E1    E2    E3               │  ← đã mở: màu + tên
│                                 │
│   ▨     ▢     ▢               │  ← chưa mở: ô trống, KHÔNG ghi "??" 
│   E4    E5    E6               │     (gợi ý có tồn tại nhưng không spoil)
│                                 │
│   ▨     ▢     ▢               │
│   E7    E8    E9               │
│                                 │
│   4 / 9 đã mở                  │
└─────────────────────────────────┘
```

### 07.08.2 — Quy tắc hiển thị

| Yếu tố | Quy tắc |
|---------|----------|
| Ending đã mở | khung CG thumbnail + tên tiếng Anh + tên tiếng Việt |
| Ending chưa mở | ô trống nét đứt, **không** tên, **không** số thứ tự |
| Counter | chỉ đếm "đã mở", không hiện tổng còn lại kiểu gợi ý |
| Nhặt lại | chọn 1 ending → xem lại lời thoại cuối + epilogue, xem thoại nhánh đã chọn |
| Xem lại | **không** cho tua nhánh. Ending là kết quả, không phải trò chơi |

### 07.08.3 — Epilogue

Mỗi ending có **4–6 đoạn epilogue** chọn theo biến tầng 3 (11.05). Gallery cho xem **bản đã xem**, không cho xem trước các bản khác — nếu cho xem, gallery biến thành spoiler máy.

---

## 07.09 — MÀN HÌNH CHÍNH & MENU

```
┌─────────────────────────────────┐
│                                 │
│      HÀNH TRÌNH CỦA           │
│         MIRA ELI               │
│                                 │
│      ▶  Bắt đầu               │
│      ▸  Tiếp tục               │
│      ▸  Nhật ký hành trình      │
│      ▸  Cài đặt                │
│                                 │
│                                 │
│   v1.0 — Dự án học tập         │
└─────────────────────────────────┘
```

### 07.09.1 — Cài đặt

| Mục | Tuỳ chọn |
|-----|----------|
| Tốc độ chữ | Chậm / Vừa / Nhanh / Tức thì |
| Bỏ qua đã đọc | Bật / Tắt |
| Tự động | Bật / Tắt, thời gian dừng |
| Lưu tự động | Bật / Tắt |
| Ngôn ngữ | Tiếng Việt / English (chưa sẵn sàng) |
| Chế độ dễ chịu | **Giảm hiệu ứng quá tải** — xem 07.09.2 |

### 07.09.2 — Chế độ dễ chịu (QUAN TRỌNG)

Game chủ đề `OVERLOAD`. Người chơi nhạy cảm với hiệu ứng nhấp nháy, overlay nóng, âm thanh dồn — **bao gồm cả người đang chơi chính game này để vượt qua stress thật**.

| Khi bật | Thay đổi |
|---------|----------|
| Overlay hue | giữ ở mức Thấp vĩnh viễn |
| V13/V16 | tắt, thay bằng A07 nhẹ hơn |
| Notification | tối đa 2 cùng lúc, không dồn cụm |
| Lịch | không tô đậm khi kín |
| Idle animation | tắt |

> ⚠️ Chế độ này **không làm thay đổi nội dung, số liệu, ending**. Nó chỉ giảm cảm giác khó chịu thị giác/thính giác. Người chơi vẫn chơi đúng game.

---

## 07.10 — ACCESSIBILITY & RESPONSIVE

| Yếu tố | Yêu cầu |
|---------|----------|
| Độ phân giải | thiết kế ở 1920×1080, scale xuống 1280×720 không mất vị trí |
| Tỉ lệ | 16:9 và 16:10. Không hỗ trợ 21:9 bắt buộc |
| Tương phản | chữ dialogue tối thiểu 4.5:1 trên nền tối |
| Cỡ chữ | cho phép tăng 3 mức, dùng chung với cỡ chữ dialogue |
| Tương tác | hỗ trợ chuột + bàn phím; không yêu cầu thao tác chuột chính xác |
| Nền tảng | desktop ưu tiên. Không thiết kế riêng cho mobile — UI hiện tại **quá rộng** cho màn hình dọc |

> 🚫 **Không** làm phiên bản mobile của game này trong giai đoạn hiện tại. Màn hình điện thoại và journal đều giả định không gian rộng và thời gian ngồi lâu — đó là chủ ý thiết kế, không phải hạn chế kỹ thuật.

---

## 07.11 — BẢN DỊCH & BỐI CỮ

| Yếu tố | Quy tắc |
|---------|---------|
| Chuỗi tự dịch được | dialogue, choice, journal, tên app |
| Không tự dịch | tên riêng Thụy Điển giữ nguyên (Annika Johansson), tên tiếng Việt giữ dấu |
| Độ dài chữ | UI phải chịu được **+25% độ dài** so với tiếng Việt mà không tràn |
| Ngày tháng | định dạng theo locale, không hardcode `12/03` |
| Font | cần font hỗ trợ đủ dấu tiếng Việt **và** dấu Thụy Điển (å ä ö, é è) |

---

## 07.12 — SCREEN FLOW

```
MAIN MENU
   │
   ├─▶ GAMEPLAY SCENE
   │      │
   │      ├─▶ DIALOGUE ──▶ CHOICE ──▶ RESOLUTION
   │      │
   │      ├─▶ PHONE ─┬─▶ TIN NHẮN
   │      │          ├─▶ LỊCH
   │      │          ├─▶ CUỘC GỌI  ──▶ (múi giờ) ──▶ CALL SCENE
   │      │          ├─▶ NGÂN SỘCH
   │      │          └─▶ CA LÀM
   │      │
   │      ├─▶ JOURNAL ─┬─▶ TÓM TẮT
   │      │            ├─▶ GHI CHÚ NV
   │      │            ├─▶ LỰA CHỌN
   │      │            └─▶ MỤC TIÊU
   │      │
   │      └─▶ CG / VFX / TRANSITION
   │
   ├─▶ SAVE / LOAD
   ├─▶ ENDING GALLERY ──▶ EPILOGUE REPLAY
   └─▶ OPTIONS
```

---

## 07.13 — TÀI NGUYÊN UI CẦN THIẾT

Chưa có asset nào trong kho hiện tại phục vụ UI. Cần tạo:

| Nhóm | Số lượng | Ghi chú |
|------|----------|---------|
| Icon app | 5 | png 96×96, phong cách tối giản, không nền tròn sáng |
| Icon dock | 4 | ☏ ✎ ☰ A |
| Frame hộp thoại | 1 | dùng cho mọi cảnh, không đổi theo map |
| Overlay hue | 4 mức | png đen 8% / 18% / 30% |
| Frame ô lựa chọn | 3 trạng thái | thường / hover / focus |
| Frame ending gallery | 2 | đã mở / chưa mở |
| Avatar hội thoại | 3 | Nam, Minh, Annika — dùng lại sprite đã có, không cần vẽ mới |
| Màn hình phone | 4 | home / app / keyboard-free list / cuộc gọi đang chạy |
| Font | 1 | phải hỗ trợ tiếng Việt + Thụy Điển |

> 💡 Đây là nhóm asset **rẻ nhất** để tạo nhưng **ảnh hưởng lớn nhất** tới cảm giác game. Ưu tiên làm trước vertical slice.

---

**TIẾP** → `08_ASSET_MANIFEST.md`
**QUAY LẠI** → `CANON_DECISIONS.md`
