# Hướng Dẫn Cài Đặt Cảm Biến Độ Ẩm Trang Trại Lan
Tài liệu này hướng dẫn thiết lập hệ thống giám sát độ ẩm tự động cho vườn lan.

Khi thao tác trên máy tính nhúng, bạn dùng biến `SENSOR_PIN` để chỉ định chân kết nối và chạy lệnh `python main.py` trong Terminal để bắt đầu thu thập dữ liệu.

Lưu ý hiển thị ký hiệu: Trong tài liệu này, các ký tự đặc biệt được giữ nguyên bằng dấu escape: *ngưỡng cảnh báo* và # không phải tiêu đề mục.
## 1. Đoạn Mã Python Điều Khiển Máy Bơm Tự Động
Đoạn mã sau đọc dữ liệu từ cảm biến và kích hoạt máy tưới phun sương khi độ ẩm xuống dưới mức cho phép:
```python
import time

HUMIDITY_THRESHOLD = 65.0

def read_sensor_data(pin):
    return 62.5

def control_irrigation_system():
    sensor_value = read_sensor_data(pin=4)
    print(f"Do am hien tai: {sensor_value}%")
    
    if sensor_value < HUMIDITY_THRESHOLD:
        print("Trang thai: Kich hoat may bom tuoi phun suong.")
    else:
        print("Trang thai: Do am on dinh, tat may bom.")

if __name__ == "__main__":
    control_irrigation_system()
```
## 2. Bảng So Sánh Cảm Biến Độ Ẩm
|Tiêu chí|Cảm biến điện trở (Loại cũ)|Cảm biến điện dung v1.2 (Loại mới)|
|:---:|:---:|:--:|
|**Độ bền ăn mòn**|Dễ bị oxy hóa sau 1-2 tháng|Chống oxy hóa, hoạt động bền bỉ|
|**Độ chính xác**|Sai số cao khi độ ẩm đất thay đổi|Sai số thấp (±2%)|
|**Mục đích dùng**|Thử nghiệm mô hình nhỏ|Triển khai thực tế tại trang trại lan|
## 3. Danh Sách Kiểm Tra Thiết Bị (Task List)
-   [x] Cố định bo mạch điều khiển trong hộp chống nước
-   [x] Cấp nguồn 5V ổn định cho module cảm biến
-   [ ] Cắm chân cảm biến vào giá thể xơ dừa của giò lan
-   [ ] Kiểm tra tín hiệu kích hoạt rơ-le (Relay) đóng ngắt máy bơm