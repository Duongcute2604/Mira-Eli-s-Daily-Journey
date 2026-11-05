# 📏 12. RULES — LUẬT THI CÔNG

> `CANON_DECISIONS.md` là luật **nội dung** (game phải kể gì). File này là luật **cách làm** (làm thế nào).
> Khi hai bên xung đột: nội dung do CANON quyết, cách làm do file này quyết.
> Tra nhanh trong lúc code: `13_QUICKREF.md`.

**Hiệu lực:** 05/11/2026
**Tổng: 36 luật** = A5 · B4 · C3 · D5 · E3 · F2 · G3 · H1 · L4 · M6

---

## 12.00 — CÁCH DÙNG

- Luật chỉ được **thêm hoặc thay thế**, không xoá (H1). Luật bị thay giữ nguyên số, ghi `[thay bởi D-0xx]`.
- Luật nào vi phạm mà không có lý do ghi lại thì coi như bug, không phải "linh hoạt".
- Số nào trong file này cũng phải sinh từ script hoặc đo thật, không ước lượng.

---

## 12.01 — A · KỸ THUẬT CODE

| Mã | Luật | Quy định |
|----|------|----------|
| **A1** | Stack | TypeScript + Vite. **Không game engine.** UI bằng DOM/CSS. Chỉ thêm PixiJS khi một hiệu ứng cụ thể không làm được bằng CSS — và khi đó chỉ trong một module. |
| **A2** | Cấu trúc | `src/engine` · `src/ui` · `src/content` · `public/assets` · `tools`. Không quá 3 tầng thư mục. Mỗi file một việc. |
| **A3** | Đặt tên | File `kebab-case.ts` · type `PascalCase` · hàm `camelCase` · hằng `SCREAMING_SNAKE`. **Cấm đổi ID nội dung**: `A1_C01`, `CH_A1_06`, `M04`, `V16`, `A23` giữ đúng như docs. |
| **A4** | Lỗi & log | Một hàm `log(level, msg)` duy nhất, bật bằng `?debug=1`. Thiếu asset → `throw` kèm ID. Cấm `console.log` rải rác, cấm fallback im lặng. |
| **A5** | Ngân sách | JS ≤ 150 KB gzip · ảnh nạp mỗi chương ≤ 6 MB · chữ hiện < 16 ms · chuyển cảnh ≤ 600 ms · không nạp trước toàn bộ 82 background. |

### A2 — cây thư mục chuẩn

```
src/
  engine/     runner.ts  state.ts  save.ts  grade.ts  timed-task.ts  log.ts  types.ts
  ui/         dialogue.ts  choice.ts  phone.ts  journal.ts  bg.ts
  content/    a1_c01.json  …  a3_c12.json
public/
  assets/     bg/  char/  cg/  audio/
tools/        smoke.ts  match-style.mjs  optimize-webp.mjs
```

---

## 12.02 — B · DỮ LIỆU

| Mã | Luật | Quy định |
|----|------|----------|
| **B1** | Định dạng thoại | JSON thuần, một file mỗi chương. Không Ink, không YAML — cần 0 thư viện parse. Schema ở dưới. |
| **B2** | ID nội dung | File = ID chương viết thường (`a1_c06.json`) · scene = `a1_c06_s02`. Dòng thoại **không có ID**, tính theo vị trí — thêm/xoá dòng không phá save. |
| **B3** | Save | Một key `medj.save`, không tách nhỏ. Chỉ lưu 6 resource + 27 object. **Không lưu** object dẫn xuất (BALANCE, OPENNESS, STRESS…). |
| **B4** | Migration | Đọc save → nếu `v` cũ thì chạy `migrate()`. Parse lỗi → copy sang `medj.save.bak`, báo người chơi, bắt đầu lượt mới. **Cấm xoá save im lặng.** |

### B1 — schema chương

```ts
type Line    = { who: Who; text: string; expr?: string; vfx?: string; sfx?: string }
type Scene   = { id: string; bg: string; scale?: number; x?: number; y?: number;
                 lines: Line[]; choice?: string; minigame?: string }
type Chapter = { id: string; title: string; scenes: Scene[] }
type Who     = "DUONG" | "MINH" | "NAM" | "ANNIKA" | "MOTHER" | "NARR"
```

`scale / x / y` là **góc máy** (luật G3 + L5): cùng một background cho nhiều khung.

### B3 — save schema

```ts
type Save = {
  v: 1
  chapter: string; scene: string
  energy: number; money: number; debt: number; reputation: number
  day: number; timeBlock: "MORNING" | "DAY" | "EVENING" | "NIGHT"
  state: Record<string, number>   // 7 persistent + 5 route, đúng tên trong 09
  flags: string[]                 // 15 FLAG_*
  ts: number
}
```

---

## 12.03 — C · NỘI DUNG

| Mã | Luật | Quy định |
|----|------|----------|
| **C1** | Quy cách scene | Một scene = một địa điểm + một nhịp hội thoại, 8–20 dòng. Mỗi khung ≤ 3 dòng, ≤ 120 ký tự/dòng. Kết scene phải đổi ≥ 1 state hoặc ≥ 1 thông tin. |
| **C2** | Duyệt | Đọc thành tiếng một lần, rồi kiểm 5 điểm: ai nói · biểu cảm có trong bộ · bg tồn tại · VFX/audio ID tồn tại · ID khớp docs. |
| **C3** | Giọng văn | Tự thoại dùng "mình". Cấm câu kể thay cảm xúc người chơi ("Dương rất buồn"). Tối đa một dấu `!` mỗi scene. |

---

## 12.04 — D · CÔNG VIỆC

| Mã | Luật | Quy định |
|----|------|----------|
| **D1** | Nhánh & commit | `main` luôn chạy được. Làm trên `feat/…`. Commit `feat｜fix｜docs｜content｜art: mô tả ≤ 60 ký tự`. Mỗi commit phải build được. |
| **D2** | .gitignore | `node_modules` · `dist` · `.DS_Store` · `__MACOSX` · `*.log` · `refs/`. Tên asset phải khớp chuẩn trước khi commit. |
| **D3** | Sao lưu | Push cuối mỗi buổi. Tag cuối mỗi phase: `p0`, `slice`, `p3`. Không làm quá một buổi mà không push. |
| **D4** | Xong là gì | Chỉ đánh `[x]` khi đã qua smoke (L3) và đã đóng băng (L1). |
| **D5** | **Chốt là ghi và đẩy** | Mỗi lần hai bên chốt một phương án: ghi vào file luật **ngay trong lượt đó**, rồi commit + push. Quyết định chỉ nằm trong chat thì coi như chưa có. Không gộp nhiều ngày rồi đẩy một lần. |

---

## 12.05 — E · QUY MÔ

| Mã | Luật | Quy định |
|----|------|----------|
| **E1** | Ngân sách giờ | Ghi khoảng, không ghi số: slice 3–6 tuần · Phase 3 6–10 tuần · Phase 4 8–16 tuần. Đây là dự báo để cắt, không phải cam kết. |
| **E2** | Thứ tự cắt | Cắt từ trên xuống: 42 epilogue → 20 · CG 30 → 12 · ending 9 → 6 · audio 30 → 15 · phone system → đơn giản · minigame 3 → 2 → 1 · **cuối cùng mới cắt chương**. |
| **E3** | Điều kiện bỏ | Task vượt 2× ước lượng → cắt về bản tối thiểu trong một buổi. Vẫn không xong → bỏ, ghi `lessons.md`. Không kéo dài. |

---

## 12.06 — F · KIỂM CHỨNG

| Mã | Luật | Quy định |
|----|------|----------|
| **F1** | Chương đạt | Chơi trọn không lỗi console · save → reload → đúng scene · mọi ID tham chiếu tồn tại · chuyển cảnh ≤ 600 ms · 3 người chơi không phải hỏi cách chơi. |
| **F2** | Playtest | 3 người, im lặng, ghi chỗ dừng > 5 giây. Hỏi 3 câu: bạn nghĩ Dương đang cảm thấy gì · có muốn chọn khác không · chỗ nào chán. |

---

## 12.07 — G · HÌNH ẢNH

| Mã | Luật | Quy định |
|----|------|----------|
| **G1** | Spec asset | bg 1920×1080 WebP ≤ 250 KB · sprite PNG/WebP có alpha, cao 900–1080 px, neo chân giữa–dưới · CG 1920×1080 · tên `bg_` `char_` `cg_` + số. |
| **G2** | Credit | Asset mới phải có dòng trong `CREDITS.md` cùng commit. Không rõ nguồn → không dùng, không ngoại lệ. |
| **G3** | **Một mốc phong cách** | Mốc là **Họ C — 3D painterly** (`bg_city_*`). Mọi ảnh mới phải so với 3 ảnh mốc trong `assets/bg/_anchor/`. Lệch họ → chạy `tools/match-style.mjs` hoặc loại. |

### G3 — ba họ đang có trong kho

| Họ | Số ảnh | Đặc điểm | Xử lý |
|----|--------|----------|-------|
| **A — toon Blender** (`bg_sa_*`) | 11 | Mảng phẳng, bóng mềm, gần sprite nhất | Giữ. Đủ gần mốc để dùng không cần chỉnh |
| **B — ảnh thật** (`bg_bedroom_*`, `bg_kitchen_*`, `bg_office_*`, `bg_street_*`…) | 43 | Chi tiết cao, tương phản mạnh | Giữ, nhưng **grade về C** trước khi build |
| **C — 3D painterly** (`bg_city_*`) | 28 | Mềm, mờ xa, ít chi tiết vặt, có sẵn 3 khung giờ | **Mốc.** Không chỉnh |

### G3 — quy trình thêm background mới

1. **License trước, phong cách sau.** Không rõ nguồn → dừng.
2. **Thử mức 0/1 trước** (L5): viết lại cảnh, hoặc tái dùng map + đổi góc máy. Phần lớn cảnh mới không cần ảnh mới.
3. Mở ảnh ứng viên **cạnh 3 ảnh mốc ở 100%**, không so với trí nhớ.
4. **Kiểm tra 5 giây:** nhìn 5 giây, chỉ ra được ảnh nào là ảnh mới → loại.
5. Năm tiêu chí: góc máy ngang tầm mắt (~1,2 m), phối cảnh một điểm tụ · không người, không chữ · một nguồn sáng chính, không bóng cứng · chừa trống giữa hoặc nửa phải cho sprite · không có vùng đen tuyệt đối.
6. `tools/match-style.mjs` → WebP q80 → đặt vào cảnh thật, chụp màn hình cạnh cảnh liền trước. Giật → chưa đạt.

---

## 12.08 — H · SỬA LUẬT

| Mã | Luật | Quy định |
|----|------|----------|
| **H1** | Mẫu quyết định | Mọi thay đổi luật ghi một dòng vào `CANON_DECISIONS.md` §5: `D-0xx ｜ ngày ｜ nội dung ｜ thay D-0xx ｜ lý do ｜ file ảnh hưởng`. Sửa mọi file liên quan trong cùng commit. |

---

## 12.09 — L · LUẬT CỦA NGƯỜI LÀM

| Mã | Luật | Quy định |
|----|------|----------|
| **L1** | Đóng băng | Tính năng xong → test 3 lần (mở mới · reload · save-load) → ghi ✅ vào bảng trạng thái → **không refactor nữa**. Chỉ sửa khi chính nó lỗi. |
| **L2** | Cô lập | Mỗi tính năng là một module, chỉ nói với ngoài qua interface trong `engine/types.ts`. Cấm import chéo giữa các module `ui/*`. |
| **L3** | Smoke test | `tools/smoke.ts`, chạy `npm run smoke`, 10 kiểm tra, không framework. Phải xanh trước khi đóng băng; đỏ thì không được đánh `[x]`. |
| **L4** | Gọn | 0 dependency ngoài vite + typescript · không abstraction trước lần lặp thứ 3 · file ≤ 200 dòng · hàm ≤ 40 dòng · dữ liệu ở JSON, code chỉ chạy dữ liệu · **cấm viết tắt tên biến**. |
| **L5** | Rẻ trước, đắt sau | Thứ tự bắt buộc khi cần một cảnh mới: viết lại cảnh để không cần nền mới → tái dùng map + đổi góc máy → lấy từ cùng nguồn/pipeline → ảnh ngoài + grade → tự dựng. Không được nhảy cóc. |

---

## 12.10 — M · MINIGAME

Quyết định 05/11/2026: **giữ minigame**, nhưng phải rẻ và phải phục vụ chủ đề. Minigame là chỗ dễ làm hỏng một game kể chuyện nhất — vì nó thêm một cổng kỹ năng không liên quan tới câu chuyện.

| Mã | Luật | Quy định |
|----|------|----------|
| **M1** | Kích thước | Mỗi minigame ≤ 60 giây, một màn hình. Không hướng dẫn riêng — lần chơi đầu tự dạy bằng 3 giây mở đầu (thấy mục tiêu + đồng hồ). |
| **M2** | Không thua cứng | Thất bại **không bắt chơi lại**. Nó đổi state (`REPUTATION −`, `OVERLOAD +`) rồi kể tiếp. Đúng nguyên tắc game không có game over. |
| **M3** | Phải có luận điểm | Mỗi minigame phải chứng minh **một câu** về chủ đề, ghi ở đầu file dữ liệu. Không viết được câu đó → bỏ minigame. |
| **M4** | Có bản dự phòng | Mỗi minigame có một choice tương đương về state. Game phải chạy được khi thiếu minigame. Đây là điều kiện để cắt được ở Phase 3. |
| **M5** | Một hệ, ba bộ dữ liệu | Dùng chung `engine/timed-task.ts`. Đúng lần lặp thứ 3 nên được trừu tượng hoá: một hệ, ba file JSON. Không viết ba mini-engine. |
| **M6** | Không có trong slice | `A1_C01 → A1_C09` **không** có minigame. Minigame bắt đầu từ Arc 2 trở đi. Phase 2 giữ sạch và rẻ. |

### M — ba minigame đề xuất (chờ chốt)

| ID | Tên | Chương | Luận điểm (M3) | Cơ chế |
|----|-----|--------|----------------|--------|
| **MG1** | Chia thuốc | `A3_C02` | *Ưu tiên là thứ duy nhất còn lại khi không đủ thời gian* | 5 bệnh nhân, 5 loại thuốc, đồng hồ chạy; chọn sai thứ tự làm `REPUTATION −` |
| **MG2** | Bữa tối | Arc 2 (chương chốt sau) | *Nấu cho hai người, ăn một mình* | Hai bếp; nấu thêm phần cho Minh thì lỡ giờ gọi Nam → `FAMILY_TRUST +` hoặc `ROMANCE_TRUST +`, không cả hai |
| **MG3** | Ca đêm | `A3_C??` | *Không cứu được tất cả, chỉ cứu được người mình chọn* | Chuỗi 3 quyết định có đồng hồ, không phản xạ |

Nếu thiếu thời gian, theo E2: cắt MG3 trước, rồi MG2. MG1 giữ vì nó đã có sẵn trong `03_MAP_EVENT_FLOW` (`A3_C02`) và là minigame gắn chặt nghề nghiệp nhất.

---

## 12.11 — BẢNG TRẠNG THÁI TÍNH NĂNG

Điền khi đóng băng (L1). Không có dòng nào ở đây thì chưa có tính năng nào xong.

| Tính năng | Module | Smoke | Freeze | Ngày |
|-----------|--------|-------|--------|------|
| — | — | — | — | — |
