# MBBank — Phân tích xác thực sinh trắc học và ý định tiếp tục sử dụng

## 1. Mục tiêu

`MBBank_Research_Analysis.py` thực hiện quy trình phân tích định lượng cho nghiên cứu:

**Nghiên cứu các yếu tố ảnh hưởng đến niềm tin vào xác thực sinh trắc học và ý định tiếp tục sử dụng App MBBank của khách hàng cá nhân tại TP. Hồ Chí Minh.**

Bộ dữ liệu mặc định gồm **1.187 quan sát**.

Các cấu trúc nghiên cứu:

- **PSE** — Hiệu quả bảo mật cảm nhận.
- **BAR** — Độ tin cậy xác thực sinh trắc học.
- **PT** — Minh bạch quy trình xác thực.
- **BPC** — Lo ngại quyền riêng tư sinh trắc học.
- **AE** — Nỗ lực xác thực cảm nhận.
- **BSE** — Năng lực tự thực hiện xác thực sinh trắc học.
- **TBA** — Niềm tin vào xác thực sinh trắc học.
- **CI** — Ý định tiếp tục sử dụng App MBBank.

Cấu trúc trọng tâm:

`PSE, BAR, PT, BPC → TBA`

và:

`TBA, AE, BSE, AE×BSE + biến kiểm soát → CI`

## 2. Chạy nhanh trong VSCode

Mở:

```text
MBBank_Research_Analysis.py
```

Sau đó chọn **Run Python File**.

Khi chạy không truyền tham số, chương trình sử dụng bộ dữ liệu nghiên cứu được lưu cùng mã nguồn và tạo:

```text
MB BANK kết quả(2).xlsx
```

ngay trong cùng thư mục với file Python.

## 3. Môi trường Python

Khuyến nghị Python 3.11 trở lên.

Các thư viện phân tích chính:

```text
numpy
scipy
statsmodels
scikit-learn
artifact_tool
```

Nếu môi trường chưa có các gói phân tích phổ biến:

```bash
pip install numpy scipy statsmodels scikit-learn
```

`artifact_tool` phải có sẵn trong môi trường chạy để xuất workbook Excel theo đúng định dạng nghiên cứu.

## 4. Chạy bằng Terminal

Chạy với dữ liệu mặc định:

```bash
python MBBank_Research_Analysis.py
```

Chỉ định file đầu ra:

```bash
python MBBank_Research_Analysis.py --output "ket_qua_mbbank.xlsx"
```

Chạy với workbook dữ liệu khác:

```bash
python MBBank_Research_Analysis.py --input "du_lieu_mbbank.xlsx" --output "ket_qua_mbbank.xlsx"
```

Khi sử dụng `--input`, workbook cần có sheet dữ liệu mang tên:

```text
DuLieu_n1187
```

và giữ đúng mã biến mà mô hình sử dụng.

## 5. Workbook đầu ra

Workbook có 3 sheet:

### Giải thích

Trình bày tên biến, ý nghĩa, vai trò trong mô hình và cách hiểu những chỉ số thống kê quan trọng bằng ngôn ngữ dễ đọc.

### Mẫu

Dữ liệu ở cấp từng khách hàng khảo sát. Các cột gồm đặc điểm mẫu, câu hỏi thang đo và thông tin bổ sung của từng phản hồi.

### Kết quả

Tập trung các bảng kết quả được sử dụng trong phân tích và báo cáo nghiên cứu, theo đúng tên chỉ số thực sự có trong dự án.

## 6. Các phân tích chính

Chương trình thực hiện:

- thống kê đặc điểm mẫu;
- Cronbach's Alpha;
- tương quan biến – tổng;
- EFA;
- kiểm tra mô hình đo lường;
- VIF;
- hồi quy chuẩn hóa;
- R² và Adjusted R²;
- bootstrap;
- tác động trực tiếp và điều tiết;
- One-Sample T-Test;
- Independent Samples T-Test;
- ANOVA;
- kiểm định khác biệt giữa các nhóm;
- kiểm tra độ bền với biến kiểm soát;
- dự báo ngoài mẫu;
- K-Means;
- phân tích mức độ quan trọng;
- IPMA.

Không tạo thêm chỉ số không thuộc kết quả nghiên cứu đang sử dụng.

## 7. Một số kết quả kiểm tra khi chạy

Sau khi hoàn tất, Terminal hiển thị nhanh:

```text
n = 1187
R² TBA
R² CI
Beta PSE→TBA
Beta TBA→CI
Beta AE×BSE→CI
K-Means counts
```

Các bảng đầy đủ nằm trong sheet `Kết quả`.

## 8. Kiểm soát dữ liệu

Chương trình kiểm tra:

- số quan sát;
- mã biến bắt buộc;
- miền giá trị Likert;
- biến dùng cho mô hình;
- cấu trúc dữ liệu trước khi chạy phân tích.

Nếu dữ liệu không đạt yêu cầu cấu trúc, chương trình dừng để tránh tạo ra kết quả không tương thích với thiết kế nghiên cứu.

## 9. File chính

```text
MBBank_Research_Analysis.py
MB BANK kết quả(2).xlsx
README_MBBank_Research_Analysis.md
```
