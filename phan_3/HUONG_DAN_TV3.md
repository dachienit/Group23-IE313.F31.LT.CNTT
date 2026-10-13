# Bàn giao Thành viên 3 – Mô hình và kết quả

| File | Nội dung |
|---|---|
| `03_model_evaluation.ipynb` | Bản chạy độc lập: mã hóa, train/test, 3 mô hình, đánh giá, biểu đồ |
| `model_comparison.xlsx` | MAE, RMSE, R², cross-validation của 3 mô hình |
| `figures/model/*.png` | 10 thực tế–dự đoán, 11 residual plot, 12 so sánh mô hình |
| `Noi_dung_TV3.docx` | Bản nháp riêng: Phương pháp mô hình, Kết quả phân tích, Kết luận |
| `SeoulBikeData_clean.csv` | Dữ liệu sạch của TV1 (không chỉnh sửa) |
| `do_an_day_du/` | **Toàn bộ đồ án nhóm** đã hoàn chỉnh phần TV3 |

## Trong `do_an_day_du/`
- `bao_cao/Nhóm 23 báo cáo.docx`: báo cáo chung, đã chèn mục 3.5 (Xây dựng và đánh giá mô hình), 5 (Kết quả phân tích), 6 (Kết luận), tài liệu tham khảo [2], Phụ lục phân công, và tóm tắt kết quả ở đoạn 1 của Giới thiệu.
- `bao_cao/do_an_seoul_bike.ipynb`: notebook chung, có **Phần C** ở cuối (Run All từ Phần A đến C).
- `phan_3/`: bản nguồn phần TV3. `docs/TRANG_THAI.md` đã cập nhật.

## Chạy
```
pip install -r requirements.txt

# Bản độc lập (thư mục này)
python -m nbconvert --to notebook --execute --inplace 03_model_evaluation.ipynb

# Toàn bộ đồ án (Phần A, B, C)
cd do_an_day_du/bao_cao
PYTHONIOENCODING=utf-8 python -m nbconvert --to notebook --execute --inplace do_an_seoul_bike.ipynb
```
Thư mục làm việc phải là thư mục chứa notebook. Hai bản cho cùng bảng số liệu.

## Lựa chọn trong mô hình
- Loại 295 giờ `Functioning Day = No` (cùng `df_run` 8.465 giờ của Phần B); bản độc lập có công tắc `DROP_OFF`.
- `Hour`, `Seasons`, `Holiday` mã hóa one-hot; không dùng `Month`, `DayOfWeek`, `Date`.
- Chia 80/20, `random_state = 42`; 5-fold CV; Ridge chọn alpha bằng Grid Search (alpha ≈ 14,4).
