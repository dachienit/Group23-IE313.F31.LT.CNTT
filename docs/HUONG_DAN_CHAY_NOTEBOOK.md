# Hướng dẫn chạy notebook

Notebook duy nhất của nhóm: [`bao_cao/do_an_seoul_bike.ipynb`](../bao_cao/do_an_seoul_bike.ipynb) (59 ô, 34 ô code).

## 1. Yêu cầu
- Python 3.10 trở lên (nhóm đã chạy với 3.13).
- Thư viện: `pandas numpy scipy matplotlib seaborn openpyxl` để chạy notebook; thêm `jupyterlab` (hoặc VS Code) để mở; `nbformat nbconvert ipykernel` nếu chạy bằng dòng lệnh; `python-docx` chỉ cần khi chạy các script dựng Word.

```bash
pip install pandas numpy scipy matplotlib seaborn openpyxl jupyterlab nbformat nbconvert ipykernel
```

## 2. Chạy trong Jupyter / VS Code
1. Mở thư mục `bao_cao/` (notebook đọc file bằng đường dẫn tương đối, nên **thư mục làm việc phải là thư mục chứa notebook**).
2. Bảo đảm có `SeoulBikeData_raw.csv` cùng thư mục.
3. Chọn *Run All*. Chạy từ trên xuống, không bỏ ô.

## 3. Chạy bằng dòng lệnh (không cần mở giao diện)
```bash
cd bao_cao
PYTHONIOENCODING=utf-8 python -m nbconvert --to notebook --execute --inplace do_an_seoul_bike.ipynb
```
Lưu ý:
- Dùng `python -m nbconvert`, không dùng `jupyter nbconvert` (lệnh này đã gặp lỗi trên máy nhóm; `python -m nbconvert` dùng đúng Python đang gọi nên ổn định hơn).
- Trên Windows đặt `PYTHONIOENCODING=utf-8` (PowerShell: `$env:PYTHONIOENCODING='utf-8'`) để in tiếng Việt không lỗi.
- Không dùng cờ `python -I`.
- Nên chạy trong một thư mục tạm có `SeoulBikeData_raw.csv` rồi mới copy notebook kết quả về `bao_cao/`, vì lần chạy sẽ tạo thêm thư mục và file (mục 5).

## 4. Cấu trúc notebook
| Phần | Nội dung | Đọc → ghi |
|---|---|---|
| **A. Chuẩn bị dữ liệu** | Đọc dữ liệu gốc, kiểm tra kích thước/kiểu/khuyết/trùng/phạm vi, kiểm tra giá trị 0 và ngoại lệ IQR, chuyển `Date`, tạo `Month`, `DayOfWeek`, `IsWeekend` | `SeoulBikeData_raw.csv` → `SeoulBikeData_clean.csv` |
| **B. EDA và trực quan hóa** | 1 Thiết lập → 2 Nạp và kiểm tra → 3 Thống kê mô tả → 4 Phân phối và ngoại lệ → 5 Theo giờ → 6 Theo mùa và ngày lễ → 7 Nhiệt độ và mưa → 8 Tương quan → 9 ANOVA → 10 Chọn biến → 11 Xuất file → 12 Hình quy trình | `SeoulBikeData_clean.csv` → hình PNG và xlsx |
| **C. Mô hình** (chưa có) | Hồi quy tuyến tính đơn, đa biến, Ridge, đánh giá MAE/RMSE/R²/CV – do Thành viên 3 thêm vào cuối notebook | xem [BAN_GIAO_TV3.md](BAN_GIAO_TV3.md) |

Phần B đọc file sạch do phần A vừa xuất (biến `clean_path`), không tự tìm file ở nơi khác.

## 5. Đầu ra khi chạy
| Đường dẫn (tương đối so với thư mục chạy) | Nội dung |
|---|---|
| `SeoulBikeData_clean.csv` | Dữ liệu sạch 8.760 dòng × 17 cột (14 cột gốc + `Month`, `DayOfWeek`, `IsWeekend`) |
| `figures/eda/*.png` | 13 hình: `00` quy trình; `01`, `01b`, `02` phân phối và boxplot; `03` theo giờ; `04`, `04b`, `05` mùa và ngày lễ; `06`, `06b`, `07` nhiệt độ và mưa; `08` heatmap tương quan; `09` heatmap giờ × mùa |
| `descriptive_statistics.xlsx` | 19 sheet: thống kê mô tả, groupby, pivot, tương quan, bảng chọn biến |
| `anova_result.xlsx` | 5 sheet: giả thuyết, F, p-value, kết luận, so sánh từng cặp mùa |

`figures/` và hai file xlsx là kết quả sinh ra nên **không nằm trong `bao_cao/`**; bản dùng cho báo cáo hiện lưu ở `phan_2/`. Chạy lại cho ra kết quả trùng bản đó (đã kiểm tra: xlsx trùng từng sheet, 13/13 hình trùng).

## 6. Lưu ý về dữ liệu
- `SeoulBikeData_raw.csv` mã hóa `cp1252` (có ký hiệu °), notebook đọc với `encoding='cp1252'`.
- `SeoulBikeData_clean.csv` mã hóa `utf-8-sig`. File trong repo xuống dòng kiểu LF; chạy lại trên Windows sẽ ghi CRLF (nội dung giống hệt, chỉ khác ký tự xuống dòng). Khi cập nhật file trong `bao_cao/`, giữ bản có sẵn.
- Phần B lọc bỏ 295 giờ `Functioning Day = No` (đều có 0 lượt thuê) trong biến `df_run` (8.465 giờ). File dữ liệu **không bị sửa**; mô hình của Thành viên 3 nên dùng cùng phạm vi này (xem [KET_QUA_VA_QUYET_DINH.md](KET_QUA_VA_QUYET_DINH.md)).

## 7. Lỗi thường gặp
| Triệu chứng | Cách xử lý |
|---|---|
| `FileNotFoundError: SeoulBikeData_raw.csv` | Thư mục làm việc không phải thư mục chứa notebook và CSV; mở lại đúng thư mục |
| Tiếng Việt thành ký tự lạ khi in | Đặt `PYTHONIOENCODING=utf-8` |
| `jupyter nbconvert` báo lỗi kernel/môi trường | Dùng `python -m nbconvert` |
| Tên cột có `°` bị lỗi | Đọc raw bằng `cp1252`, đọc clean bằng `utf-8-sig` |
| `.ipynb_checkpoints/` xuất hiện | Đã nằm trong `.gitignore`; có thể xóa |
