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
**Sai:** 149 ảnh trong repo, **chỉ có 11 ảnh** (Spiral Atlas) có file `license.txt` kèm theo. 138 ảnh còn lại không có bất kỳ thông tin nguồn hay license nào.
**Vì sao sai:** Tên file kiểu `FREE_BG_1.png` **không phải bằng chứng có quyền sử dụng**. "Free" nhiều khi chỉ nghĩa là "miễn phí tải" chứ vẫn yêu cầu credit hoặc cấm thương mại.
**Lần sau tránh:** Mỗi lần tải asset → **ghi luôn file `SOURCE.md` cạnh folder** gồm: tên tác giả, link gốc, license, ngày tải. Khi phát hành game, đây là dữ liệu để làm màn hình Credits.
**Đã làm:** Tạo `CREDITS.md` ở gốc dự án; đổi tên 11 ảnh Spiral Atlas thành tiền tố `bg_sa_` để **nhìn tên file là biết phải credit**. Xem `docs/08_ASSET_MANIFEST.md` mục 08.05.

---

## L007 — Tên file asset chưa chuẩn hoá
**Ngày:** 2026-10-02
**Sai:** `FREE_BG_1.png`, `bedroom 3.jpg`, `01.1.png`, `chibi Dương.png`, `Copilot_20260821_095258.png`, `ChatGPT Image 20_15_55 21 thg 8, 2026.png`...
**Vì sao sai:** Tài liệu thiết kế yêu cầu tên thống nhất (`bg_home_livingroom.png`, `char_duong_base.png`) để code load được bằng key từ config. Tên hiện tại vừa có dấu tiếng Việt, vừa có khoảng trắng, vừa mang tên tool AI — không group được theo loại.
**Lần sau tránh:** Ngay khi bắt đầu dự án asset: chốt convention tên file **trước**, ví dụ `<loại>_<chủ thể>_<biến thể>.<ext>`. Rồi viết script đổi tên hàng loạt.
**Đã làm:** Đổi **105 file** ngày 02/10. Không đổi tay — dựng bảng ánh xạ CSV, kiểm tra trùng/sai quy ước **trước khi** ghi, rồi mới áp dụng. Xem L012.

---

## L008 — File rác từ macOS
**Ngày:** 2026-10-02
**Sai:** Thư mục `__MACOSX` chứa **15** file rác: `.DS_Store`, `._.DS_Store`, `._bathroom.jpg`... (file AppleDouble rỗng ~120–600 byte).
**Vì sao sai:** Kéo thả folder từ macOS xong copy cả nguyên folder ẩn. Tài liệu gốc ghi 14 nhưng đếm thật là **15** — nếu tin tài liệu sẽ sót 1 file.
**Lần sau tránh:** Copy asset trên macOS dùng `rsync` hoặc `ditto` không kèm resource fork, hoặc thêm `.gitignore` cho `__MACOSX` và `.DS_Store`.
**Đã làm:** Xoá **16 file rác** (15 `__MACOSX` + 1 `.DS_Store`). Xem L012.

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

## L012 — Tự đếm bằng trí nhớ thì SAI, phải đo lại bằng script
**Ngày:** 2026-10-02
**Sai:** Trong `08_ASSET_MANIFEST.md` tôi ghi "23 ảnh dùng được" rồi đổi thành "20 ảnh dùng được / 19 tham khảo" — cả hai đều **sai**. Số thật là **23 / 16**. Sai sót này lan xuống tổng số kho (121 thay vì 105) và số ảnh chưa verify license (110 thay vì 138).
**Vì sao sai:** Tôi đếm trong đầu từ danh sách tên file, thay vì chạy script so sánh danh sách với thư mục thật. Khi danh sách dài, con người (và cả LLM) đếm sai là bình thường — đặc biệt khi có phân loại trùng lặp giữa "dùng được" và "tài liệu".
**Lần sau tránh:** **Mọi con số trong tài liệu phải sinh ra từ script, không gõ tay.** Khi đã ghi một số vào doc → trước khi commit, chạy lại script kiểm tra và đối chiếu tổng: `dùng được + tham khảo = tổng`.
**Đã làm:** Viết script so 16 tên file tham khảo với 39 file thật → xác nhận 23 + 16 = 39. Sửa lại 08.00 / 08.02.1 / 08.05.2 / 08.08 và tổng số trong `todo.md`. Sau đó kiểm tra chéo: **108 tên file được tài liệu trích dẫn → 105 tồn tại thật + 3 đúng là mục đã khai thiếu.** Không còn tên nào trỏ vào file không tồn tại.

---

## L013 — Đổi tên hàng loạt phải qua bảng ánh xạ + kiểm tra, không đổi tay
**Ngày:** 2026-10-02
**Sai:** Có nguy cơ đổi tên 105 file bằng tay → rất dễ sai, rất dễ đụng tên, rất khó hoàn tác.
**Vì sao sai:** Thao tác thủ công trên quy mô lớn tạo lỗi ngẫu nhiên (gõ nhầm, trùng tên) mà không có cách nào phát hiện ngoài việc kiểm tra thủ công toàn bộ.
**Lần sau tránh:** Quy trình 4 bước cho mọi thao tác hàng loạt:
1. Dựng bảng ánh xạ `old → new` và **ghi ra file** để audit được.
2. Kiểm tra tự động **trước khi** ghi: đúng số lượng? trùng `old`? trùng `new`? mọi `old` đều tồn tại? mọi `new` có đúng convention?
3. Chỉ chạy khi **không có dòng ERR nào**.
4. Xác nhận sau khi chạy: đếm lại, và để **git làm bằng chứng**.
**Đã làm:** Script dựng CSV 105 dòng, chặn 3 lỗi trước khi ghi. Sau khi áp dụng: `git status` báo **105 `R100`** (rename 100% giống nhau → nội dung không đổi) + **16 `D`**. Bằng chứng khớp với dự kiến.

---

## L014 — PowerShell 5.1 đọc file `.ps1` không BOM theo ANSI → hỏng tiếng Việt
**Ngày:** 2026-10-02
**Sai:** Viết script PowerShell có chuỗi tiếng Việt rồi chạy → `'Dương quàn áo thường ngày.jpg'` bị đọc thành `'DĂ¡ng Ä‘á»©ng...'`, dẫn đến báo "KHÔNG TỒN TẠI".
**Vì sao sai:** Windows PowerShell 5.1 mặc định giả định file script là **ANSI/Windows-1252** khi không có BOM. File UTF-8 không BOM bị đọc sai từng byte.
**Lần sau tránh:** Trước khi chạy script `.ps1` có ký tự không ASCII, thêm BOM:
```powershell
$p = 'script.ps1'
$c = [System.IO.File]::ReadAllText($p, [System.Text.Encoding]::UTF8)
[System.IO.File]::WriteAllText($p, $c, (New-Object System.Text.UTF8Encoding $true))
```
Hoặc dùng `pwsh` (PowerShell 7) vốn mặc định UTF-8.
**Đã làm:** Script chạy đúng sau khi thêm BOM.

---

## L015 — `\uXXXX` KHÔNG phải escape của PowerShell
**Ngày:** 2026-10-02
**Sai:** Trong script tôi viết đường dẫn `'t\u1ec7p \u1ea3nh background\City'` — PowerShell hiểu là chuỗi chữ `\u1ec7p` → `Cannot find path`.
**Vì sao sai:** `\uXXXX` là cú pháp của **Java/JSON**, không có trong PowerShell. PowerShell dùng backtick (`` `n ``, `` `t ``) hoặc escape Unicode kiểu PowerShell 7 (`` `u{1EC7} ``).
**Lần sau tránh:** Với đường dẫn chứa tiếng Việt trong script PowerShell, **ghi thẳng ký tự thật**. Kết hợp với L014 (thêm BOM) thì chạy đúng.
**Đã làm:** Sửa sang ký tự literal, chạy thành công.

---

## L016 — `Get-ChildItem -Path X -Include *.jpg -Recurse` trả kết quả SAI
**Ngày:** 2026-10-02
**Sai:** Dùng `Get-ChildItem -LiteralPath $root -File -Recurse -Include *.jpg,*.png` để đếm ảnh → trả về **42** dòng trong đó có cả `.md`, `.docx`, `.txt` — tức là filter **không hoạt động** đúng như mong đợi.
**Vì sao sai:** Khi `-Include` đi kèm `-Recurse` và đường dẫn không có wildcard, PowerShell áp dụng `-Include` cho **tất cả** kết quả đệ quy, kể cả file nằm trong thư mục con ngoài phạm vi dự kiến. Kết hợp với việc không có `-LiteralPath` khiến hành vi càng khó đoán.
**Lần sau tránh:** Đếm từng thư mục bằng `-LiteralPath` **không kèm `-Recurse`**, rồi lọc bằng `.Extension`:
```powershell
Get-ChildItem -LiteralPath $dir -File | Where-Object { $_.Extension -in '.jpg','.png' }
```
**Đã làm:** Đếm lại theo từng thư mục: 43 + 28 + 11 + 39 = **121 ảnh**, khớp với tổng trước khi đổi tên → chứng minh không mất file nào.

---

## L017 — `-like` coi `*` và `?` là ký tự đại diện, không tìm được chuỗi có `**`
**Ngày:** 2026-10-02
**Sai:** Dùng `$txt -notlike "*$marker*"` với `marker = "**TIẾP** → ..."` để tìm vị trí chèn → không khớp, script báo lỗi.
**Vì sao sai:** `-like` là toán tử **wildcard**. `**` trong marker bị hiểu là "ký tự bất kỳ", nên chuỗi literal chứa `*` không bao giờ khớp với chính nó.
**Lần sau tránh:** Khi tìm chuỗi **literal** trong text (markdown, code, JSON) → dùng `.Contains()` hoặc `.IndexOf()`, không dùng `-like`/`-match`.
**Đã làm:** Chuyển sang `.Contains()` — tìm thấy ngay và chèn phụ lục thành công.

---

## L018 — Đừng đoán dữ liệu chưa ai xác nhận rồi nhét vào tên file
**Ngày:** 2026-10-02
**Sai:** Quy ước tên file ban đầu là `bg_<map>_<room>_<time>.png`. Nhưng **không ai xác nhận** ảnh nào thuộc map nào — tôi chỉ suy đoán từ tên file cũ (`bedroom 3.jpg` → "chắc là M01?").
**Vì sao sai:** Ghi dữ liệu suy đoán vào tên file là **đóng băng một phỏng đoán thành dữ kiện**. Sau này khi người tác giả xác nhận "không, ảnh đó là cho M07", phải đổi tên lại toàn bộ — và mọi tham chiếu đã viết trong tài liệu cũng sai theo.
**Lần sau tránh:** Chuẩn hoá những gì **chắc chắn** (`a-z0-9`, tiền tố loại, số thứ tự), **bỏ trống phần chưa chắc** (`<map>`), và ghi rõ trong tài liệu chỗ nào đang để trống + lý do + điều kiện để điền.
**Đã làm:** Đặt tên theo `<theme>` thay vì `<map>` (`bg_bedroom_03.jpg` chứ không phải `bg_m01_bedroom_03.jpg`), và ghi rõ trong 08.06: khi map được chốt thì đổi `bg_<theme>` → `bg_<map>_<room>` bằng một lệnh hàng loạt.

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