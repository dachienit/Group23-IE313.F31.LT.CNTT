# Group23 – IE313.F31.LT.CNTT: Phân tích nhu cầu thuê xe đạp công cộng tại Seoul

Đồ án môn **Phân tích và trực quan dữ liệu (IE313)** – Trường Đại học Công nghệ Thông tin, ĐHQG TP.HCM. Nhóm 23, 3 thành viên.

Đề tài phân tích số lượt thuê xe đạp công cộng theo giờ tại Seoul dựa trên thời gian, thời tiết và ngày lễ, bằng Python/Pandas: kiểm tra và làm sạch dữ liệu, phân tích thăm dò, trực quan hóa, kiểm định ANOVA, sau đó xây dựng và đánh giá các mô hình hồi quy.

**Dữ liệu:** *Seoul Bike Sharing Demand*, UCI Machine Learning Repository, DOI [10.24432/C5F62R](https://doi.org/10.24432/C5F62R), giấy phép CC BY 4.0. 8.760 dòng (24 giờ × 365 ngày, 01/12/2017–30/11/2018), 14 cột gốc.

## Cấu trúc repo
| Đường dẫn | Nội dung |
|---|---|
| `bao_cao/` | **Sản phẩm nộp thầy**: báo cáo Word, notebook duy nhất, 2 file CSV |
| `phan_1/` | Bản nguồn phần Thành viên 1 (chuẩn bị dữ liệu, mở đầu) |
| `phan_2/` | Bản nguồn phần Thành viên 2 (EDA, trực quan hóa, ANOVA) |
| `template/` | Mẫu báo cáo `Template_IE313.docx` và `Slides.pptx` của thầy |
| `Phan_cong_do_an_phantich.docx` | Phân công nhiệm vụ 3 thành viên |
| `docs/` | Tài liệu bàn giao cho nhóm (xem bên dưới) |

## Bắt đầu nhanh
```bash
pip install pandas numpy scipy matplotlib seaborn openpyxl nbformat nbconvert ipykernel python-docx
cd bao_cao
jupyter lab do_an_seoul_bike.ipynb      # rồi chọn Run All
```
Chi tiết (chạy dòng lệnh, đầu ra, lỗi thường gặp): [docs/HUONG_DAN_CHAY_NOTEBOOK.md](docs/HUONG_DAN_CHAY_NOTEBOOK.md).

## Tài liệu trong `docs/`
| File | Dùng để |
|---|---|
| [TRANG_THAI.md](docs/TRANG_THAI.md) | Tiến độ hiện tại, việc còn lại của từng người, hạn nộp |
| [HUONG_DAN_CHAY_NOTEBOOK.md](docs/HUONG_DAN_CHAY_NOTEBOOK.md) | Cách chạy, cấu trúc notebook, đầu ra, lỗi thường gặp |
| [YEU_CAU_CUA_THAY.md](docs/YEU_CAU_CUA_THAY.md) | Checklist sản phẩm và báo cáo theo hướng dẫn Buổi 10 |
| [KET_QUA_VA_QUYET_DINH.md](docs/KET_QUA_VA_QUYET_DINH.md) | Quyết định phân tích đã chốt và số liệu chính để các phần dùng thống nhất |
| [BAN_GIAO_TV3.md](docs/BAN_GIAO_TV3.md) | Việc cần làm của Thành viên 3: đầu vào, cách nối vào báo cáo và notebook |

## Quy ước làm việc
- Chỉ đưa vào `bao_cao/` những gì sẽ nộp; `phan_1/` và `phan_2/` là bản nguồn, không sửa.
- Báo cáo Word dùng đúng style của template (Heading 1/2, BT, G1, TLTK); không để code hay chữ hướng dẫn trong báo cáo.
- Số liệu trong báo cáo, bảng, hình và slide phải trùng nhau; số liệu lấy từ notebook.
