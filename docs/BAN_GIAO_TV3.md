# Bàn giao cho Thành viên 3: xây dựng và đánh giá mô hình

Phần mô tả công việc đầy đủ nằm trong `Phan_cong_do_an_phantich.docx` (mục 4). Tài liệu này tóm tắt những gì đã có để bạn nối tiếp.

## 1. Đầu vào đã sẵn sàng
| Thứ | Ở đâu |
|---|---|
| Dữ liệu sạch dùng chung (8.760 × 17, không khuyết) | `bao_cao/SeoulBikeData_clean.csv`, đọc bằng `encoding='utf-8-sig'` |
| Notebook chung (Phần A, B đã chạy sạch) | `bao_cao/do_an_seoul_bike.ipynb` |
| Báo cáo Word gộp phần 1 và 2 | `bao_cao/Nhóm 23 báo cáo.docx` |
| Số liệu, quyết định, gợi ý chọn biến | [KET_QUA_VA_QUYET_DINH.md](KET_QUA_VA_QUYET_DINH.md) |
| Bảng thống kê và bảng chọn biến | `phan_2/descriptive_statistics.xlsx` (sheet `ChonBien_BienSo`, `ChonBien_PhanLoai`, `TuongQuan_*`) |

## 2. Việc cần làm
1. Xác định biến mục tiêu `Rented Bike Count`, chọn biến đầu vào và mã hóa biến phân loại (không đưa biến mục tiêu vào đầu vào).
2. Chia 80% train / 20% test, `random_state` cố định, dùng chung cho cả ba mô hình.
3. Xây dựng **hồi quy tuyến tính đơn**, **hồi quy tuyến tính đa biến** và **Ridge** (có thể dùng pipeline và Grid Search chọn alpha).
4. Đánh giá bằng MAE, RMSE, R² và k-fold cross-validation; vẽ giá trị thực tế so với dự đoán, residual plot và biểu đồ so sánh mô hình.
5. Chọn mô hình tốt nhất và giải thích dựa trên nhiều chỉ số, không chỉ một.
6. Chỉ dùng các mô hình và kỹ thuật đã học trong môn.

**Phạm vi dữ liệu:** các phần EDA dùng 8.465 giờ hoạt động. Nên dùng **cùng phạm vi** cho mô hình (lọc `Functioning Day == 'Yes'`), vì 295 giờ còn lại luôn bằng 0 và sẽ làm sai lệch chỉ số; nếu chọn khác phải ghi rõ lý do trong báo cáo.

## 3. Cách nối vào notebook
- Thêm các ô vào **cuối** `do_an_seoul_bike.ipynb` dưới tiêu đề `# Phần C. Xây dựng và đánh giá mô hình`; không tạo notebook riêng (thầy thích một file).
- Đọc dữ liệu từ `df_run` (đã có từ Phần B) hoặc đọc lại `SeoulBikeData_clean.csv`; không sửa file CSV.
- Hình lưu vào `figures/model/` với tên có số thứ tự (ví dụ `10_thuc_te_vs_du_doan.png`); bảng chỉ số lưu `model_comparison.xlsx`.
- Chạy lại toàn bộ notebook từ đầu trước khi bàn giao (xem [HUONG_DAN_CHAY_NOTEBOOK.md](HUONG_DAN_CHAY_NOTEBOOK.md)) và bảo đảm không dùng đường dẫn cá nhân.
- Cập nhật mục lục ở ô tiêu đề đầu notebook thêm dòng Phần C.

## 4. Cách nối vào báo cáo Word
Mở `bao_cao/Nhóm 23 báo cáo.docx` bằng Word và **chèn trước** mục "TÀI LIỆU THAM KHẢO":
1. Thêm một mục Heading 2 trong "Phương pháp phân tích" mô tả phương pháp mô hình (biến, mã hóa, chia train/test, ba mô hình, cross-validation, ý nghĩa các chỉ số). Hiện mục 3 có 3.1 Quy trình, 3.2 Tiền xử lý, 3.3 Phạm vi dữ liệu, 3.4 Kỹ thuật thăm dò; Hình 1 (quy trình) đã nói bước 8 là mô hình.
2. Thêm Heading 1 "KẾT QUẢ PHÂN TÍCH" (tên tự đặt): bảng so sánh ba mô hình (MAE, RMSE, R², CV), biểu đồ thực tế–dự đoán, residual plot, xác định mô hình tốt nhất.
3. Thêm Heading 1 "KẾT LUẬN" (khoảng nửa trang, không ghi hướng phát triển).
4. Thêm "PHỤ LỤC PHÂN CÔNG NHIỆM VỤ" sau TLTK.

Quy ước định dạng để không sai template:
- Dùng đúng style: Heading 1/2, **BT** cho đoạn văn, **G1/G2** cho gạch đầu dòng, **TLTK** cho tài liệu tham khảo. Không copy từ Google Docs.
- Số hiệu tiếp tục từ **Hình 7** và **Bảng 4** (đã dùng Hình 1–6, Bảng 1–3). Mỗi hình/bảng có câu dẫn trước, caption bên dưới (dạng "Hình 7. ..."), đoạn giải thích sau.
- Hình nên cao khoảng 6–8 cm, đặt giữa trang, giữ cho hình và caption không bị tách trang (Keep with next).
- Tên cột/biến giữ như trong dữ liệu; số theo kiểu Việt Nam (1.234,5).
- Không để code trong thân báo cáo.
- Sau khi chèn, xem lại số trang (từ Giới thiệu đến Kết luận nên không quá 10–12 trang).

## 5. Các việc cùng nhóm sau khi xong
- Cập nhật **đoạn 1 của Giới thiệu** để tóm tắt kết quả (số liệu mô hình tốt nhất), không bình luận.
- Báo lại cho TV1 và TV2 số liệu cuối để slide và báo cáo trùng nhau.
- Điền Phụ lục phân công đúng thực tế (xem `Phan_cong_do_an_phantich.docx` mục 5).
- Cập nhật [TRANG_THAI.md](TRANG_THAI.md).
