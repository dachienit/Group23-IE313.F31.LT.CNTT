# Trạng thái đồ án

Cập nhật: **13/10/2026**. Hạn nộp trên eLearning: 24/9, 1/10, **8/10**, **15/10** (hạn cuối). Thầy cho nộp lại tối đa một lần và bản sau phải tốt hơn rõ rệt, nên nhóm nhắm nộp một lần cho hoàn chỉnh.

## Sản phẩm phải nộp (hệ online)
| # | Sản phẩm | Trạng thái |
|---|---|---|
| 1 | Báo cáo Word (`bao_cao/Nhom23_Bao_cao.docx`) | **Xong**: đủ bìa, Giới thiệu (2 đoạn, có cam kết dùng AI), Mô tả, Phương pháp, Phân tích thăm dò, Kết quả phân tích, Kết luận, TLTK, Phụ lục phân công; header và footer đã điền |
| 2 | Code và data (`bao_cao/Nhom23_Code.ipynb`, `Nhom23_Data_raw.csv`, `Nhom23_Data_clean.csv`) | **Xong**: có Phần A, B, C. Lưu ý: 5 ô code đầu (Phần A và ô thiết lập Phần B) đang không có output và `execution_count` rỗng — nên chạy lại Run All một lượt trước khi nộp |
| 3 | Slide thuyết trình | Chưa làm |
| 4 | Video thuyết trình ≤ 15 phút (thấy mặt cả nhóm) | Chưa làm |

Nhóm đã quyết định **chỉ nộp bản Word**, chưa làm PDF (thầy hướng dẫn nộp thêm bản PDF có nội dung giống hệt; nếu còn thời gian, xuất PDF từ Word ở bước cuối).

## Theo thành viên
| TV | Phụ trách | Trạng thái |
|---|---|---|
| 1 | Chuẩn bị dữ liệu; Giới thiệu, Mô tả bộ dữ liệu, Tiền xử lý, TLTK; quản lý file báo cáo | Xong phần đã giao (bản nguồn ở `phan_1/`) |
| 2 | Phương pháp phân tích (quy trình, kỹ thuật EDA), Phân tích thăm dò, ANOVA | Xong (bản nguồn ở `phan_2/`); đã gộp vào `bao_cao/` |
| 3 | Mô hình hồi quy (đơn, đa biến, Ridge), Kết quả phân tích, Kết luận | **Xong** (bản nguồn ở `phan_3/`); đã gộp Phần C vào notebook và mục 3.5, 5, 6 vào báo cáo |

## Việc còn lại (theo thứ tự ưu tiên)
1. **Chạy lại notebook một lượt** (Run All) để 44 ô code có `execution_count` liên tục 1–44 và Phần A có output; hiện 5 ô đầu trống.
2. **Dọn `bao_cao/`**: chỉ để đúng 4 file nộp, bỏ `Nhom23_Code_old.ipynb` và `Nhóm 23 báo cáo.docx` (bản cũ) ra ngoài.
3. **Slide và video**: slide 1 giới thiệu nhóm, slide 2 ảnh thấy mặt từng người và tự giới thiệu; video ≤ 15 phút thấy mặt cả nhóm.
4. **Trước khi nộp**: đối chiếu [YEU_CAU_CUA_THAY.md](YEU_CAU_CUA_THAY.md); số liệu báo cáo, bảng, slide phải trùng nhau; mở thử file trên máy khác.

Đã xong: ~~TV3 mô hình, Kết quả phân tích, Kết luận, Phần C~~; ~~tóm tắt kết quả ở Giới thiệu~~; ~~Phụ lục phân công~~; ~~đánh số Hình 7–9, Bảng 4~~; ~~dashboard: mục 13 của notebook và Hình 7 trong báo cáo~~ (các hình mô hình đã dời thành Hình 8–10); ~~giải thích sau Bảng 1 và Hình 1~~ — nay cả 14 hình/bảng đều có câu dẫn trước và giải thích sau; ~~bìa, header, footer~~; ~~đổi tên 4 file nộp theo "Nhom23_"~~; ~~cam kết dùng AI ở đoạn 2 Giới thiệu~~.

## Kích thước báo cáo hiện tại
Word đo 16 trang: bìa (trang 1), **nội dung chính Giới thiệu → Kết luận ở trang 2–14, tức 13 trang**, TLTK (trang 15), Phụ lục (trang 16). Thầy tính số trang từ Giới thiệu đến Kết luận, không tính bìa, TLTK và phụ lục: tối thiểu 5, khuyến nghị 10, tối đa 20 → 13 trang là hợp lệ. Nếu muốn gọn hơn, chuyển Bảng 2 hoặc Hình 3 xuống phụ lục. (Số trang có thể lệch 1 tùy máy và máy in mặc định.)

## Điểm cần lưu ý đã biết
- Bản gộp chỉ sửa 3 chỗ nhỏ trong phần của TV1 để hai phần nhất quán: thêm phạm vi 8.465 giờ ở Giới thiệu, ghi rõ "trên toàn bộ 8.760 giờ" cho 158 giờ ngoại lệ, đổi tên notebook (nay là `Nhom23_Code.ipynb`).
- Số ngoại lệ khác nhau theo phạm vi: 158 giờ (ngưỡng 2.376,6; trên 8.760 giờ) ở mục Tiền xử lý và 152 giờ (ngưỡng 2.389; trên 8.465 giờ) ở mục Phân tích thăm dò. Cả hai đều đúng, đã ghi chú phạm vi trong báo cáo.
- Heading 1 màu đỏ là do style của template, giữ nguyên.
- Báo cáo soạn bằng Word trên Windows; không dùng Google Docs vì dễ vỡ style template.
- Phần mô hình đã được kiểm chứng chạy lại trên máy khác: mọi số liệu trùng khớp; ba hình mô hình lệch 1 pixel chiều rộng do `bbox_inches='tight'`, nội dung không đổi.
- Notebook cần `scikit-learn` (Phần C); xem `requirements.txt` ở thư mục gốc.
- `phan_3/do_an_day_du/` là bản copy toàn bộ dự án do TV3 bàn giao, giữ lại để đối chiếu; bản chính thức là thư mục gốc.
