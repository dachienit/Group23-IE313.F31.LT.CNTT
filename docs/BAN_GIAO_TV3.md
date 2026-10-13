# Phần mô hình (Thành viên 3) – ghi chú nghiệm thu

Hoàn thành 12/10/2026. Bản nguồn ở `phan_3/`; đã gộp vào `bao_cao/` (mục 3.5, 5 và 6 của báo cáo, Phần C của notebook).

## Lựa chọn đã chốt
| Nội dung | Quyết định |
|---|---|
| Phạm vi dữ liệu | `df_run` – 8.465 giờ hoạt động, **cùng phạm vi với phần EDA** |
| Biến mục tiêu | `Rented Bike Count` |
| Biến đầu vào | `Hour`, `IsWeekend`, 8 biến thời tiết, `Seasons`, `Holiday`. Bỏ `Date`, `Month` (trùng thông tin với `Seasons`), `DayOfWeek` |
| Mã hóa | One-hot cho `Hour`, `Seasons`, `Holiday` (`drop_first=True`) → 36 cột đầu vào |
| Chia dữ liệu | 80% train (6.772 giờ) / 20% test (1.693 giờ), `random_state = 42`, dùng chung cho cả ba mô hình |
| Cross-validation | 5-fold `KFold(shuffle=True, random_state=42)` trên tập train |
| Ridge | Pipeline chuẩn hóa + Ridge; alpha chọn bằng Grid Search trên 20 giá trị từ 0,01 đến 1.000 → **alpha ≈ 14,4** |

Khác với quy tắc chọn biến |r| ≥ 0,3 ở phần EDA, mô hình giữ toàn bộ biến thời tiết: Ridge xử lý được đa cộng tuyến nhiệt độ–điểm sương (r = 0,91), còn lượng mưa tuy |r| thấp nhưng làm nhu cầu giảm rất mạnh. Lý do này đã ghi trong báo cáo.

## Kết quả (tập kiểm tra)
| Mô hình | MAE | RMSE | R² | CV R² |
|---|---|---|---|---|
| Hồi quy tuyến tính đơn (nhiệt độ) | 381,2 | 514,8 | 0,325 | 0,313 ± 0,009 |
| Hồi quy tuyến tính đa biến | 275,2 | 363,1 | 0,664 | 0,660 ± 0,011 |
| **Ridge Regression** | **275,1** | **363,0** | **0,664** | 0,660 ± 0,011 |

Ridge được chọn vì sai số thấp nhất và hệ số được kiểm soát, nhưng chênh lệch với hồi quy đa biến rất nhỏ (RMSE lệch 0,14 lượt/giờ) nên báo cáo nêu rõ hai mô hình là tương đương. Hạn chế đã ghi trong Kết luận: mô hình dự đoán thấp ở vùng nhu cầu cao, cho giá trị âm ở vùng nhu cầu thấp, phần dư có dạng hình phễu.

Hệ số lớn nhất của Ridge: độ ẩm (−209,2), điểm sương (+171,5), giờ 18 (+159,2), mùa Đông (−154,0), nhiệt độ (+141,2).

## Đã kiểm chứng (12/10/2026)
- Notebook gộp chạy từ đầu đến cuối không lỗi, `execution_count` liên tục (75 ô / 1–43 khi kiểm chứng Phần C; sau khi thêm mục 13 dashboard của TV2 là 78 ô / 1–44).
- Bảng 4 trong báo cáo khớp từng số với `phan_3/model_comparison.xlsx`.
- Chạy lại trên máy khác cho cùng kết quả: ba file xlsx trùng từng sheet, 13/13 hình EDA trùng byte.
- Code không rò rỉ biến mục tiêu; chuẩn hóa nằm trong pipeline nên không rò rỉ qua cross-validation.

Bản độc lập `phan_3/03_model_evaluation.ipynb` (có công tắc `DROP_OFF`) cho cùng bảng số liệu; chỉ cần cho người muốn chạy riêng phần mô hình.
