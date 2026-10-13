# Kết quả và quyết định phân tích đã chốt

Số liệu dưới đây lấy từ `descriptive_statistics.xlsx` và `anova_result.xlsx` (do notebook sinh ra) và đã khớp với báo cáo. Khi viết phần khác, dùng đúng các số này.

## 1. Quyết định về dữ liệu
| Quyết định | Lý do |
|---|---|
| Giữ nguyên 8.760 dòng trong file dữ liệu sạch (`Nhom23_Data_clean.csv`); không xóa, không điền khuyết (không có ô khuyết hay dòng trùng) | Dữ liệu sạch sẵn; chỉ cần chuyển `Date` và thêm 3 cột `Month`, `DayOfWeek`, `IsWeekend` |
| Khi phân tích **bỏ 295 giờ `Functioning Day = No`**, còn **8.465 giờ** (`df_run` trong notebook) | Cả 295 giờ đều có 0 lượt thuê vì hệ thống ngừng phục vụ, không phản ánh nhu cầu người dùng |
| Giữ các giờ có số lượt thuê rất cao | Đó là nhu cầu thật (giờ tan tầm, mùa Hạ), không phải lỗi đo |
| Ngưỡng ngoại lệ IQR: Q3 + 1,5 × IQR | Theo slide Bài 5; trên 8.760 giờ có 158 giờ (ngưỡng 2.376,6), trên 8.465 giờ có 152 giờ (1,8%, ngưỡng 2.389) |
| Mức ý nghĩa α = 0,05; so sánh cặp mùa dùng ngưỡng 0,05/6 ≈ 0,0083 | Hiệu chỉnh Bonferroni cho 6 cặp |
| Thang đánh giá tương quan |r|: ≥ 0,8 mạnh; 0,5–0,8 vừa; 0,3–0,5 yếu; < 0,3 gần như không | Theo thang của môn học |

## 2. Số liệu chính (8.465 giờ hoạt động, trừ khi ghi khác)
**Số lượt thuê mỗi giờ:** trung bình 729,2 (toàn bộ 8.760 giờ: 704,6); trung vị 542; độ lệch chuẩn 642,4; lớn nhất 3.556; Q1 = 214, Q3 = 1.084, IQR = 870; skewness 1,14 (phân phối lệch phải).

**Theo giờ (thứ Hai–thứ Sáu):** hai đỉnh lúc 8h (1.306 lượt/giờ) và 18h (1.724 lượt/giờ). Cuối tuần không có đỉnh sáng, cao nhất lúc 17h (1.161).

**Theo mùa:** Hạ 1.034, Thu 924, Xuân 746, Đông 226 lượt/giờ.

**ANOVA 4 mùa:** H0: trung bình bốn mùa bằng nhau. F(3; 8.461) = 875,6; p < 0,001; η² = 0,237 → bác bỏ H0. Cả 6 cặp mùa đều khác biệt có ý nghĩa (lớn nhất Hạ–Đông F = 2.832,2; nhỏ nhất Hạ–Thu F = 28,9). Độ lệch chuẩn các mùa rất khác nhau (150–690) nên kết quả là bằng chứng mạnh về sự khác biệt, không phải thước đo chính xác độ lớn.

**Ngày lễ:** 529 lượt/giờ so với 739 ngày thường, chủ yếu vì 192 trong 408 giờ lễ rơi vào mùa Đông; trong mùa Hạ hai nhóm gần bằng nhau (1.022 và 1.034).

**Nhiệt độ:** r = 0,56 (mức vừa); nhu cầu đạt đỉnh khoảng 1.254 lượt/giờ ở 25 °C rồi giảm còn 879 ở 37 °C (không tuyến tính hoàn toàn).

**Mưa:** 766 lượt/giờ khi không mưa, xuống 224, 114, 73 ở mức mưa nhỏ, vừa, lớn. Chỉ 516 giờ (6,1%) có mưa nên r chỉ −0,13, nhưng hiệu ứng vẫn rõ khi so trong cùng mùa (mùa Hạ: 258 so với 1.110).

**Tương quan với số lượt thuê:** Nhiệt độ 0,56; Giờ 0,43; Điểm sương 0,40; Bức xạ 0,27; Tầm nhìn 0,21; Độ ẩm −0,20; Tuyết −0,15; Mưa −0,13; Gió 0,13; Cuối tuần −0,05. **Nhiệt độ và điểm sương tương quan r = 0,91** (gần như trùng thông tin).

## 3. Gợi ý chọn biến cho mô hình (đã tính ở sheet `ChonBien_*`)
Theo quy tắc |r| ≥ 0,3 (biến số) và ANOVA (biến phân loại):
- Biến số được chọn: Nhiệt độ, Giờ, Điểm sương. Không đạt ngưỡng: Bức xạ, Tầm nhìn, Độ ẩm, Tuyết, Mưa, Gió, Cuối tuần.
- Biến phân loại (đều có ý nghĩa): Mùa (η² = 0,237), Ngày lễ (0,005), Giờ xét như phân loại (0,314), Thứ trong tuần (0,004), Tháng (0,288).

**Lưu ý cho TV3:**
- Nhiệt độ và điểm sương gần như trùng thông tin (r = 0,91): dùng một trong hai hoặc xử lý đa cộng tuyến, đặc biệt với hồi quy tuyến tính đa biến.
- Giờ có hai đỉnh, quan hệ với số lượt thuê **không tuyến tính** → nên mã hóa dạng phân loại (one-hot) hoặc ghi rõ hạn chế nếu để dạng số.
- Mưa không đạt ngưỡng |r| ≥ 0,3 nhưng làm nhu cầu giảm rất mạnh; cân nhắc giữ lại (ví dụ dạng có mưa/không mưa) và nêu lý do.
- Tháng và Mùa trùng thông tin, không nên đưa cả hai.
- Chia train/test 80/20 với `random_state` cố định; ba mô hình cùng một cách chia để so sánh được.
