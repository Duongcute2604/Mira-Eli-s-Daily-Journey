# LESSONS — Hành Trình Của Mira Eli

> Ghi lại sau **mỗi lỗi**. Sai ở đâu, vì sao sai, lần sau tránh thế nào.

---

## L001 — Không có tài liệu .md nào trong repo
**Ngày:** 2026-10-02
**Sai:** 11 file thiết kế quan trọng nhất của cả game đều nằm rải rác trong `.docx` ở thư mục `Cốt truyện/`. Không có `todo.md`, không có `lessons.md`, không có mã nguồn.
**Vì sao sai:** File `.docx` là file nhị phânn zip — AI và script đọc rất bất tiện, khó grep, khó diff, không review được trong PR. Định dạng này **không phù hợp làm nguồn thiết kế cho dự án phần mềm**.
**Lần sau tránh:** Ngay khi có thiết kế, viết ra `.md`. `.docx` chỉ dùng để xuất bản cho người đọc, không dùng làm bản gốc.
**Đã làm:** Tạo `todo.md` + `lessons.md` ngay sau audit đầu tiên.

---

## L002 — Design docs bị nhân bản qua nhiều thế hệ, tạo 3 bộ stat khác nhau
**Ngày:** 2026-10-02
**Sai:** Cùng một game nhưng tồn tại song song:
- G1 (2 file .docx cũ): 4 chỉ số, 4 ending, premise Thụy Điển + nợ 8 tỷ
- G2 (9 file Pack mới): 24 object, 9 ending, premise hoàn toàn khác
- STORY_BIBLE: 10 stat riêng + ngưỡng ending bằng số

Ba bộ này **không tương thích với nhau**. Nếu code theo file nào cũng sẽ sai.
**Vì sao sai:** Mỗi lần sửa thiết kế đã viết một file mới thay vì cập nhật file cũ. File cũ không bị xóa nên gây hiểu nhầm.
**Lần sau tránh:** Mỗi thay đổi thiết kế lớn → **ghi đè có version** (`STORY_v2.md`), và **xoá/xếp file cũ vào `_archive/`** ngay, đừng để chung chỗ.
**Đã làm:** `todo.md` mục 3.1, 3.2, 7 liệt kê đầy đủ và đánh dấu 🔴.

---

## L003 — Thiết kế mâu thuẫn với premise gốc
**Ngày:** 2026-10-02
**Sai:** G2 đặt các scene **gặp trực tiếp** Nam ở M04 Café và M08 Transit (A2_C02, A2_C04, A2_C06, A2_C09, A3_C04, A3_C09 — tức là **6 chương**). Nhưng premise là Dương ở Thụy Điển, Nam ở Việt Nam, yêu xa 5 năm. Hai người **không thể gặp mặt**.
**Vì sao sai:** Khi tách "narrative" khỏi "setting", tác giả đã vô tình viết lại premise mà không nhận ra. G2 cũng xóa mất nợ 8 tỷ và bối cảnh viện dưỡng lão — nhưng README vẫn mô tả như cũ.
**Lần sau tránh:** Trước khi viết scene, **luôn đặt câu hỏi "nhân vật có mặt ở đây được không, theo setting không?"**. Đọc `README` làm chuẩn setting, và **mọi thay đổi setting phải cập nhật cả README**.

---

## L004 — Đánh số pack bị lỗ hổng
**Ngày:** 2026-10-02
**Sai:** Pack đánh số nhảy từ `05` sang `09`. Thiếu `06`, `07`, `08`.
**Vì sao sai:** `09_SYSTEM_VARIABLES` có ghi *"phần đó sẽ map sang TITLE / MENU / UI PACK"* → 06/07/08 nhiều khả năng là **TITLE/MENU pack, UI pack, và một pack gì đó chưa viết**.
**Lần sau tránh:** **Không để lỗ trống trong numbering.** Nếu pack chưa viết thì đánh số `06_TODO` thay vì nhảy số.
**Đã làm:** Ghi vào `todo.md` mục 7 #5.

---

## L005 — Đọc file .docx cần tool, không mở trực tiếp được
**Ngày:** 2026-10-02
**Sai:** Ban đầu thử `read` trực tiếp file `.docx` → lỗi.
**Vì sao sai:** `.docx` là file ZIP chứa XML. Cần giải nén `word/document.xml` rồi bóc tag mới lấy được text sạch.
**Lần sau tránh:** Khi cần đọc hàng loạt tài liệu văn phòng, viết script trích xuất một lần rồi đọc file text. Giữ script trong `tools/` để dùng lại.
**Đã làm:** Đã viết và chạy script PowerShell giải nén + bóc tag + decode entity. Xử lý được 11/11 file, 5.048 dòng.

---

## L006 — Không kiểm tra license của asset đã tải về
**Ngày:** 2026-10-02
**Sai:** 149 ảnh trong repo, **chỉ có 10 ảnh** (Spiral Atlas) có file `license.txt` kèm theo. 139 ảnh còn lại không có bất kỳ thông tin nguồn hay license nào.
**Vì sao sai:** Tên file kiểu `FREE_BG_1.png` **không phải bằng chứng có quyền sử dụng**. "Free" nhiều khi chỉ nghĩa là "miễn phí tải" chứ vẫn yêu cầu credit hoặc cấm thương mại.
**Lần sau tránh:** Mỗi lần tải asset → **ghi luôn file `SOURCE.md` cạnh folder** gồm: tên tác giả, link gốc, license, ngày tải. Khi phát hành game, đây là dữ liệu để làm màn hình Credits.
**Đã làm:** Ghi vào `todo.md` mục 5, đánh dấu Spiral Atlas = CC BY 4.0 bắt buộc ghi credit, 139 ảnh = chưa verify.

---

## L007 — Tên file asset chưa chuẩn hoá
**Ngày:** 2026-10-02
**Sai:** `FREE_BG_1.png`, `bedroom 3.jpg`, `01.1.png`, `chibi Dương.png`, `Copilot_20260821_095258.png`, `ChatGPT Image 20_15_55 21 thg 8, 2026.png`...
**Vì sao sai:** Tài liệu thiết kế yêu cầu tên thống nhất (`bg_home_livingroom.png`, `char_duong_base.png`) để code load được bằng key từ config. Tên hiện tại vừa có dấu tiếng Việt, vừa có khoảng trắng, vừa mang tên tool AI — không group được theo loại.
**Lần sau tránh:** Ngay khi bắt đầu dự án asset: chốt convention tên file **trước**, ví dụ `<loại>_<chủ thể>_<biến thể>.<ext>`. Rồi viết script đổi tên hàng loạt.
**Đã làm:** Ghi vào `todo.md` mục 5 #4.

---

## L008 — File rác từ macOS
**Ngày:** 2026-10-02
**Sai:** Thư mục `__MACOSX` chứa 14 file rác: `.DS_Store`, `._.DS_Store`, `._bathroom.jpg`... (file AppleDouble rỗng ~120–600 byte).
**Vì sao sai:** Kéo thả folder từ macOS xong copy cả nguyên folder ẩn.
**Lần sau tránh:** Copy asset trên macOS dùng `rsync` hoặc `ditto` không kèm resource fork, hoặc thêm `.gitignore` cho `__MACOSX` và `.DS_Store`.
**Đã làm:** Ghi vào `todo.md` mục 5 #2.

---

## L009 — Bỏ qua kiểm tra kích thước thật của asset
**Ngày:** 2026-10-02
**Sai:** Tài liệu khuyến nghị background 16:9 1920×1080. Nếu chỉ nhìn tên file thì tưởng mọi thứ đã chuẩn.
**Vì sao sai:** Đo thật mới biết: 80 ảnh đúng chuẩn, nhưng `bedroom 1.jpg` / `bedroom 2.jpg` là **1619×1080** (tỉ lệ 1.5, không phải 1.78) → đặt lên canvas 16:9 sẽ bị méo hoặc để viền đen. Ngoài ra 22 ảnh nhân vật có tỉ lệ từ 0.67 đến 1.25 — không thể dùng chung một anchor chân.
**Lần sau tránh:** **Luôn đo metadata ảnh bằng script** (`System.Drawing` trên Windows) trước khi lên kế hoạch ghép cảnh. Đừng tin tên file.
**Đã làm:** Đã đo toàn bộ 149 ảnh, phân loại theo tỉ lệ và độ phân giải.

---

## L010 — Tài liệu thiết kế tốt nhưng thiếu ngưỡng số khả thi
**Ngày:** 2026-10-02
**Sai:** `11_ENDING_PACK` và `09_SYSTEM_VARIABLES` mô tả ending bằng ngôn ngữ định tính ("SELF_AWARENESS cao", "OVERLOAD cao") — **không có ngưỡng số**. Chỉ có `STORY_BIBLE` mới cho ngưỡng cụ thể (`STRESS>=95`, `BALANCE>=75`...).
**Vì sao sai:** Ngưỡng định tính không test được. Không có số thì không biết ending nào mở được, không cân bằng nổi.
**Lần sau tránh:** Mọi điều kiện ending phải có **con số cụ thể + nguồn tham chiếu**. `11_ENDING_PACK` đã tự ghi chú: *"ngưỡng điểm cụ thể có thể tinh chỉnh khi balancing gameplay"* — cần ghi vào `todo.md` như một task cụ thể, không để mơ hồ.
**Đã làm:** `todo.md` mục 3.3 đã gom đủ 8 ngưỡng số từ STORY_BIBLE, và mục 6 Phase 3 có task cân bằng.

---

## L011 — Dừng lại đúng lúc
**Ngày:** 2026-10-02
**Sai (suy nghĩ):** Bản năng muốn bắt tay dựng game luôn — chọn stack, khởi tạo repo, viết dialogue system.
**Vì sao dừng:** Có 3 blocker chưa giải quyết mà chỉ người tác giả mới quyết được:
1. Giữ hay bỏ setting Thụy Điển + nợ 8 tỷ + viện dưỡng lão?
2. Dùng bộ stat nào (4 / 10 / 24)?
3. 4 ending hay 9 ending?
Nếu code trước khi chốt, xong phải viết lại từ đầu — đúng nghĩa "vá tạm tạo nợ kỹ thuật".
**Lần sau tránh:** Tuân thủ nguyên tắc: **lập kế hoạch trước, chỉ "xong" khi có bằng chứng**. Hỏi câu hỏi quyết định trước khi sinh code.
**Đã làm:** Dừng ở Phase 1, viết 3 câu hỏi vào `todo.md`, chờ trả lời.

---

## TEMPLATE — dùng lại cho các task sau

```
### L0XX — <tên lỗi/sai sót>
**Ngày:** YYYY-MM-DD
**Sai gì:** mô tả cụ thể, có số liệu
**Vì sao sai:** nguyên nhân gốc
**Lần sau tránh:** hành động cụ thể, có thể kiểm chứng
**Đã làm:** tham chiếu mục trong todo.md
```