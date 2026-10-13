# Hướng dẫn chạy notebook

Notebook duy nhất của nhóm: [`bao_cao/Nhom23_Code.ipynb`](../bao_cao/Nhom23_Code.ipynb) (78 ô, 44 ô code).

## 1. Yêu cầu
- Python 3.10 trở lên (nhóm đã chạy với 3.13).
- Thư viện: `pandas numpy scipy scikit-learn matplotlib seaborn openpyxl` để chạy notebook (`scikit-learn` cho Phần C); thêm `jupyterlab` (hoặc VS Code) để mở; `nbformat nbconvert ipykernel` nếu chạy bằng dòng lệnh; `python-docx` chỉ cần khi chạy các script dựng Word.

```bash
pip install -r requirements.txt
```
hoặc cài trực tiếp:
```bash
pip install pandas numpy scipy scikit-learn matplotlib seaborn openpyxl jupyterlab nbformat nbconvert ipykernel
```

## 2. Chạy trong Jupyter / VS Code
1. Mở thư mục `bao_cao/` (notebook đọc file bằng đường dẫn tương đối, nên **thư mục làm việc phải là thư mục chứa notebook**).
2. Bảo đảm có `Nhom23_Data_raw.csv` cùng thư mục.
3. Chọn *Run All*. Chạy từ trên xuống, không bỏ ô.

## 3. Chạy bằng dòng lệnh (không cần mở giao diện)
```bash
cd bao_cao
PYTHONIOENCODING=utf-8 python -m nbconvert --to notebook --execute --inplace Nhom23_Code.ipynb
```
Lưu ý:
- Dùng `python -m nbconvert`, không dùng `jupyter nbconvert` (lệnh này đã gặp lỗi trên máy nhóm; `python -m nbconvert` dùng đúng Python đang gọi nên ổn định hơn).
- Trên Windows đặt `PYTHONIOENCODING=utf-8` (PowerShell: `$env:PYTHONIOENCODING='utf-8'`) để in tiếng Việt không lỗi.
- Không dùng cờ `python -I`.
- Nên chạy trong một thư mục tạm có `Nhom23_Data_raw.csv` rồi mới copy notebook kết quả về `bao_cao/`, vì lần chạy sẽ tạo thêm thư mục và file (mục 5).

## 4. Cấu trúc notebook
| Phần | Nội dung | Đọc → ghi |
|---|---|---|
| **A. Chuẩn bị dữ liệu** | Đọc dữ liệu gốc, kiểm tra kích thước/kiểu/khuyết/trùng/phạm vi, kiểm tra giá trị 0 và ngoại lệ IQR, chuyển `Date`, tạo `Month`, `DayOfWeek`, `IsWeekend` | `Nhom23_Data_raw.csv` → `Nhom23_Data_clean.csv` |
| **B. EDA và trực quan hóa** | 1 Thiết lập → 2 Nạp và kiểm tra → 3 Thống kê mô tả → 4 Phân phối và ngoại lệ → 5 Theo giờ → 6 Theo mùa và ngày lễ → 7 Nhiệt độ và mưa → 8 Tương quan → 9 ANOVA → 10 Chọn biến → 11 Xuất file → 12 Hình quy trình → 13 Dashboard tổng hợp | `Nhom23_Data_clean.csv` → hình PNG và xlsx |
| **C. Xây dựng và đánh giá mô hình** | C.1 Chọn biến và mã hóa one-hot → C.2 Chia train/test 80/20 → C.3 Ba mô hình (tuyến tính đơn, đa biến, Ridge) → C.4 Đánh giá MAE/RMSE/R² và 5-fold CV → C.5 Biểu đồ → C.6 Mô hình tốt nhất và hệ số Ridge | `df_run` của Phần B → `figures/model/*.png`, `model_comparison.xlsx` |

Phần B đọc file sạch do Phần A vừa xuất (biến `clean_path`), không tự tìm file ở nơi khác. Phần C dùng lại `df_run` của Phần B nên phải chạy tuần tự A → B → C.

## 5. Đầu ra khi chạy
| Đường dẫn (tương đối so với thư mục chạy) | Nội dung |
|---|---|
| `Nhom23_Data_clean.csv` | Dữ liệu sạch 8.760 dòng × 17 cột (14 cột gốc + `Month`, `DayOfWeek`, `IsWeekend`) |
| `figures/eda/*.png` | 14 hình: `00` quy trình; `01`, `01b`, `02` phân phối và boxplot; `03` theo giờ; `04`, `04b`, `05` mùa và ngày lễ; `06`, `06b`, `07` nhiệt độ và mưa; `08` heatmap tương quan; `09` heatmap giờ × mùa; `10_dashboard_tong_hop` dashboard gộp bốn phát hiện chính |
| `descriptive_statistics.xlsx` | 19 sheet: thống kê mô tả, groupby, pivot, tương quan, bảng chọn biến |
| `anova_result.xlsx` | 5 sheet: giả thuyết, F, p-value, kết luận, so sánh từng cặp mùa |
| `figures/model/*.png` | 3 hình: `10` thực tế–dự đoán, `11` phần dư, `12` so sánh MAE/RMSE/R² |
| `model_comparison.xlsx` | MAE, RMSE, R² và cross-validation của ba mô hình |

`figures/` và các file xlsx là kết quả sinh ra nên **không nằm trong `bao_cao/`**; bản dùng cho báo cáo lưu ở `phan_2/` (EDA) và `phan_3/` (mô hình). Chạy lại cho ra kết quả trùng bản đó: ba file xlsx trùng từng sheet, 13/13 hình EDA trùng; ba hình mô hình có thể lệch 1 pixel chiều rộng do `bbox_inches='tight'` làm tròn khác nhau giữa các máy, nội dung không đổi. Riêng `10_dashboard_tong_hop.png` là hình thêm sau khi TV2 bàn giao nên **không có bản đối chiếu trong `phan_2/`**; hình này chỉ sinh ra khi chạy notebook.

## 6. Lưu ý về dữ liệu
- `Nhom23_Data_raw.csv` (bản gốc UCI, trong `phan_1/` vẫn tên `SeoulBikeData_raw.csv`) mã hóa `cp1252` (có ký hiệu °), notebook đọc với `encoding='cp1252'`.
- `Nhom23_Data_clean.csv` mã hóa `utf-8-sig`. File trong repo xuống dòng kiểu LF; chạy lại trên Windows sẽ ghi CRLF (nội dung giống hệt, chỉ khác ký tự xuống dòng). Khi cập nhật file trong `bao_cao/`, giữ bản có sẵn.
- Phần B lọc bỏ 295 giờ `Functioning Day = No` (đều có 0 lượt thuê) trong biến `df_run` (8.465 giờ). File dữ liệu **không bị sửa**. Phần C dùng đúng `df_run` này nên EDA và mô hình cùng một phạm vi dữ liệu (xem [KET_QUA_VA_QUYET_DINH.md](KET_QUA_VA_QUYET_DINH.md)).

## 7. Lỗi thường gặp
| Triệu chứng | Cách xử lý |
|---|---|
| `FileNotFoundError: Nhom23_Data_raw.csv` | Thư mục làm việc không phải thư mục chứa notebook và CSV; mở lại đúng thư mục |
| Tiếng Việt thành ký tự lạ khi in | Đặt `PYTHONIOENCODING=utf-8` |
| `jupyter nbconvert` báo lỗi kernel/môi trường | Dùng `python -m nbconvert` |
| Tên cột có `°` bị lỗi | Đọc raw bằng `cp1252`, đọc clean bằng `utf-8-sig` |
| `.ipynb_checkpoints/` xuất hiện | Đã nằm trong `.gitignore`; có thể xóa |
