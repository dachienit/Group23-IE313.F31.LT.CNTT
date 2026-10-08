# Trạng thái đồ án

Cập nhật: **08/10/2026**. Hạn nộp trên eLearning: 24/9, 1/10, **8/10**, **15/10** (hạn cuối). Thầy cho nộp lại tối đa một lần và bản sau phải tốt hơn rõ rệt, nên nhóm nhắm nộp một lần cho hoàn chỉnh.

## Sản phẩm phải nộp (hệ online)
| # | Sản phẩm | Trạng thái |
|---|---|---|
| 1 | Báo cáo Word (`bao_cao/Nhóm 23 báo cáo.docx`) | **Đang dở**: có Giới thiệu, Mô tả, Phương pháp, Phân tích thăm dò; thiếu phần mô hình, Kết luận, Phụ lục phân công |
| 2 | Code và data (`bao_cao/do_an_seoul_bike.ipynb`, 2 CSV) | **Đang dở**: có Phần A và B, chạy sạch; thiếu Phần C (mô hình) |
| 3 | Slide thuyết trình | Chưa làm |
| 4 | Video thuyết trình ≤ 15 phút (thấy mặt cả nhóm) | Chưa làm |

Nhóm đã quyết định **chỉ nộp bản Word**, chưa làm PDF (thầy hướng dẫn nộp thêm bản PDF có nội dung giống hệt; nếu còn thời gian, xuất PDF từ Word ở bước cuối).

## Theo thành viên
| TV | Phụ trách | Trạng thái |
|---|---|---|
| 1 | Chuẩn bị dữ liệu; Giới thiệu, Mô tả bộ dữ liệu, Tiền xử lý, TLTK; quản lý file báo cáo | Xong phần đã giao (bản nguồn ở `phan_1/`) |
| 2 | Phương pháp phân tích (quy trình, kỹ thuật EDA), Phân tích thăm dò, ANOVA | Xong (bản nguồn ở `phan_2/`); đã gộp vào `bao_cao/` |
| 3 | Mô hình hồi quy (đơn, đa biến, Ridge), Kết quả phân tích, Kết luận | **Chưa bắt đầu** – xem [BAN_GIAO_TV3.md](BAN_GIAO_TV3.md) |

## Việc còn lại (theo thứ tự ưu tiên)
1. **TV3**: xây dựng mô hình, viết "Phương pháp mô hình", "Kết quả phân tích", "Kết luận", thêm Phần C vào notebook, tạo `model_comparison.xlsx` và hình mô hình.
2. **Cả nhóm**:
   - Phụ lục phân công nhiệm vụ: ghi đúng thực tế, từng việc cụ thể (thầy dùng để cộng điểm khuyến khích).
   - Đoạn 1 của Giới thiệu đang thiếu **tóm tắt kết quả đạt được** (thầy bắt buộc); cập nhật sau khi TV3 có kết quả, chỉ nêu số, không bình luận.
   - Bìa: họ tên, MSSV, ngành của TV2 và TV3, ngành của TV1; header và footer theo template.
   - Đánh số Hình/Bảng tiếp từ **Hình 7** và **Bảng 4**; kiểm tra tổng số trang.
   - Slide (bắt buộc: slide 1 giới thiệu nhóm, slide 2 ảnh thấy mặt và tự giới thiệu), video, và rà soát chéo mở file trên máy khác.
3. **Trước khi nộp**: đối chiếu [YEU_CAU_CUA_THAY.md](YEU_CAU_CUA_THAY.md); xóa mọi chữ hướng dẫn còn sót; số liệu báo cáo, bảng, slide phải trùng nhau.

## Kích thước báo cáo hiện tại
9 trang trong Word, nội dung chính (Giới thiệu → hết Phân tích thăm dò) ở trang 2–8, tức **7 trang**. Thầy yêu cầu 5–10 trang cho phần từ Giới thiệu đến Kết luận (khuyến nghị 10, tối đa 20); thêm phần mô hình và kết luận có thể vượt 10. Nếu cần cắt, chuyển Bảng 2 hoặc Hình 3 xuống phụ lục.

## Điểm cần lưu ý đã biết
- Bản gộp chỉ sửa 3 chỗ nhỏ trong phần của TV1 để hai phần nhất quán: thêm phạm vi 8.465 giờ ở Giới thiệu, ghi rõ "trên toàn bộ 8.760 giờ" cho 158 giờ ngoại lệ, đổi tên notebook thành `do_an_seoul_bike.ipynb`.
- Số ngoại lệ khác nhau theo phạm vi: 158 giờ (ngưỡng 2.376,6; trên 8.760 giờ) ở mục Tiền xử lý và 152 giờ (ngưỡng 2.389; trên 8.465 giờ) ở mục Phân tích thăm dò. Cả hai đều đúng, đã ghi chú phạm vi trong báo cáo.
- Heading 1 màu đỏ là do style của template, giữ nguyên.
- Báo cáo soạn bằng Word trên Windows; không dùng Google Docs vì dễ vỡ style template.
