# 🗂️ 13. QUICKREF — TRA CỨU NHANH

> Mở file này **trước** khi code. Chỉ mở pack trong `docs/` khi bảng dưới đây bảo phải mở.
> Mục đích: không phải đọc lại 17 file mỗi lần vào code.
> **Luật:** file này chỉ ghi số **đã chốt**. Số đang tranh chấp ghi rõ "chưa chốt", không đoán.

---

## 13.00 — HẰNG SỐ ĐÃ CHỐT

| Hằng số | Giá trị | Ghi chú |
|---------|---------|---------|
| Canvas | **1920×1080**, scale 1280×720 | `07_UI_HUD` |
| Chương | **31** = P01 + 9 + 9 + 12 | P01, A1_C01–C09, A2_C01–C09, A3_C01–C12 |
| Choice | **22** (Arc 1: 5 · Arc 2: 6 · Arc 3: 11) | Chốt D-001, 05/11/2026 |
| Lựa chọn tối đa | **4** mỗi màn | Chốt D-002 |
| Ending | **9** nhóm · **42** epilogue | `11_ENDING` |
| Object narrative | **27** = 7 persistent + 5 route + 15 flag | `09_SYSTEM_VARIABLES` |
| Resource | **6** = ENERGY, MONEY, DEBT, REPUTATION, DAY, TIME_BLOCK | `CANON` §2 |
| Time block | **4** = MORNING · DAY · EVENING · NIGHT |  |
| Map | **10** = M01–M10 | `03_MAP_EVENT_FLOW` |
| CG / VFX / Audio | **30 / 20 / 30** | `04`, `05` |
| Background | **82** ảnh = 43 họ B + 28 họ C + 11 họ A | `08_ASSET_MANIFEST` |
| Mốc phong cách | **Họ C — 3D painterly** | Chốt D-003 |
| Minigame | **3** (MG1–MG3), bắt đầu từ Arc 2 | Chốt D-004 |
| Lượt chơi | 3–5 giờ | `00_OVERVIEW` |

---

## 13.01 — ID

| Thực thể | Dạng | Ví dụ |
|----------|------|-------|
| Chương | `P01` · `A[arc]_C[2 số]` | `A1_C06` |
| Choice | `CH_A[arc]_[2 số]` | `CH_A3_05` |
| Map | `M01`–`M10` | `M04` |
| CG | `F`/`R`/`L` **01–10** | `R07` |
| VFX | `V01`–`V20` | `V16` |
| Audio | `A01`–`A30` | `A23` |
| Flag | `FLAG_*` | `FLAG_ACCEPTED_HELP` |
| Minigame | `MG1`–`MG3` | `MG1` |
| Scene (code) | `{chapter}_sNN` | `a1_c06_s02` |
| File nội dung | `{chapter}.json` | `a1_c06.json` |
| Asset | `bg_` · `char_` · `cg_` | `bg_city_downtown_01_day` |

---

## 13.02 — CẦN BIẾT GÌ → MỞ ĐÚNG MỘT FILE

| Câu hỏi | File |
|---------|------|
| Chương này ở map nào, làm gì, vào ra sao | `03_MAP_EVENT_FLOW` |
| Choice này đổi biến nào, bao nhiêu điểm | `10_CHOICE_BRANCHING` |
| Biến nào tồn tại, khoảng, giá trị khởi tạo | `09_SYSTEM_VARIABLES` |
| Điều kiện ra ending nào | `11_ENDING` |
| Cảnh này dùng CG nào | `04_CG_PLACEMENT` |
| Cảnh này có VFX / audio gì | `05_VFX_AUDIO_PLACEMENT` |
| Màn hình có thành phần gì | `07_UI_HUD` |
| Asset này có chưa, tên gì, license | `08_ASSET_MANIFEST` |
| Nhân vật mặc gì, biểu cảm nào | `06_CHARACTER_STYLE` |
| Hai tài liệu nói khác nhau, ai thắng | `CANON_DECISIONS` |
| Viết code thế nào cho đúng luật | `12_RULES` |
| Đang ở đâu, làm gì tiếp | `todo.md` + board #11–13 |

---

## 13.03 — 36 LUẬT, BẢN MỘT DÒNG

**A · Kỹ thuật** — A1 TS+Vite, không engine · A2 5 thư mục · A3 tên + ID cấm đổi · A4 một hàm log · A5 JS ≤ 150 KB, ảnh ≤ 6 MB/chương
**B · Dữ liệu** — B1 JSON/chương · B2 ID, dòng không có ID · B3 một key save · B4 migrate, cấm xoá save im lặng
**C · Nội dung** — C1 scene 8–20 dòng, ≤ 120 ký tự · C2 duyệt 5 điểm · C3 giọng văn
**D · Công việc** — D1 nhánh + commit · D2 .gitignore · D3 push cuối buổi + tag · D4 xong = smoke + freeze · D5 chốt là ghi và đẩy ngay
**E · Quy mô** — E1 ngân sách khoảng · E2 thứ tự cắt · E3 vượt 2× thì cắt
**F · Kiểm chứng** — F1 chương đạt · F2 playtest 3 người
**G · Hình ảnh** — G1 spec asset · G2 credit cùng commit · G3 mốc phong cách + quy trình 6 bước
**H · Sửa luật** — H1 mẫu quyết định D-0xx
**L · Người làm** — L1 đóng băng · L2 cô lập module · L3 smoke 10 kiểm tra · L4 gọn · L5 rẻ trước đắt sau
**M · Minigame** — M1 ≤ 60 giây · M2 không thua cứng · M3 phải có luận điểm · M4 có bản dự phòng · M5 một hệ ba bộ dữ liệu · M6 không có trong slice

---

## 13.04 — BỐN QUYẾT ĐỊNH 05/11/2026

| Mã | Quyết định | Thay cho |
|----|-----------|----------|
| **D-001** | Choice = **22**, sửa mọi chỗ ghi 20 | Con số 20 ở `00`, `01`, `09`, `10`, `todo` |
| **D-002** | Lựa chọn tối đa = **4** | "tối đa 3" ở `07_UI_HUD` 07.06.2 |
| **D-003** | Mốc phong cách = **Họ C** | Ghi chú "Spiral Atlas khác phong cách" ở `08` |
| **D-004** | **Giữ minigame**, 3 cái, từ Arc 2 | Core loop không có minigame ở `02` |
| **D-005** | **Chốt là ghi và đẩy** — mỗi quyết định thành một commit + push trong cùng lượt | Chỉ push cuối buổi ở D3 |

---

## 13.05 — CHECKLIST TRƯỚC KHI CODE MỘT BUỔI

1. Việc hôm nay là **một** tính năng, đã ghi ở `todo.md` chưa?
2. Tính năng này thuộc module nào (A2)? Nó cần nói với module khác qua interface nào (L2)?
3. Dữ liệu của nó nằm ở JSON nào (B1)? ID đã đúng chuẩn chưa (13.01)?
4. `npm run smoke` đang xanh không? Đỏ thì sửa trước, không thêm gì.
5. Cuối buổi: test 3 lần → đóng băng (L1) → push (D3) → ghi 3 dòng vào `todo.md`.

---

## 13.06 — TRẠNG THÁI

**Đang ở:** cuối Phase 1 (thiết kế xong), **trước Phase 2** (chưa có dòng code nào).

**Chưa xong và biết là chưa xong:**

| Việc | Chặn cái gì | Ghi ở |
|------|-------------|-------|
| Chốt chương cho MG2, MG3 | Phase 3 | `12_RULES` §12.10 |
| 3 ảnh mốc vào `assets/bg/_anchor/` | G3 | `12_RULES` §12.07 |
| Định dạng `.docx` → chỉ đọc, không sửa | — | `CANON` §4 |
| Thư mục `src/` và `package.json` chưa tồn tại | mọi thứ | — |
