# BÀI LÀM – ÔN TẬP NGÀY 2
- **Họ tên: Phạm Tuấn Anh**
- **Lớp:CNTT2**
- **Link repository:**
- **Hệ điều hành (Windows/macOS):Windows**
## Bài 1. Lọc log thủ công
### Lệnh đã chạy
```shell
Get-Content .\logs\access.log | Select-String "ERROR" > .\logs\error_report.txt
Get-Content .\logs\error_report.txt
```
### 2 dòng lỗi đầu tiên trong error_report.txt

```text
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
```
## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
PS C:\Users\Admin\Desktop\trung-tam-tieng-anh 2> (type  logs/access.log | select-string "WARNING").Count
PS C:\Users\Admin\Desktop\trung-tam-tieng-anh 2> (type  logs/payment.log | select-string "ERROR").Count
```

### Kết quả đếm 

```text
WARNING trong access.log: 4
ERROR trong payment.log: 3 
```
## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
.\auto_warning.ps1
```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi

```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
"===TONG HOP ACCESS LOG===" > .\logs\tong_hop_ngay2.txt
gc .\logs\access.log | select-string "ERROR" >> .\logs\tong_hop_ngay2.txt
(gc .\logs\payment.log | select-string "WARNING" | Measure-Object).Count >> .\logs\tong_hop_ngay2.txt

```
```text

=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)

5
```
## Bài 5. Câu hỏi ngắn

- **a)> là ghi đè (xóa dữ liệu cũ, tạo mới); >> là ghi nối tiếp vào cuối file (giữ nguyên dữ liệu cũ).**
- **b)Mất dòng tiêu đề đầu tiên (=== TONG HOP ACCESS LOG ===) vì lệnh thứ hai sẽ ghi đè lên toàn bộ file.**
- **c)Giúp script linh hoạt, chạy được trên mọi máy tính hoặc hệ điều hành khác nhau mà không bị lỗi đường dẫn khi nộp bài.**

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
