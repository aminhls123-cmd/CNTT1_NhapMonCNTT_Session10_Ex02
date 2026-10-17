# Tài liệu Hướng dẫn Cài đặt Cảm biến Độ ẩm & Điều khiển Máy bơm
## 1. Code điều khiển máy bơm
```python
import RPi.GPIO as GPIO
import time

PUMP_PIN = 18
GPIO.setmode(GPIO.BCM)
GPIO.setup(PUMP_PIN, GPIO.OUT)

def control_pump(humidity):
    # Nếu độ ẩm dưới 60%, bật máy bơm
    if humidity < 60:
        GPIO.output(PUMP_PIN, GPIO.HIGH)
        print("Đang bật máy bơm...")
    else:
        GPIO.output(PUMP_PIN, GPIO.LOW)
        print("Tắt máy bơm.")

try:
    control_pump(55)
finally:
    GPIO.cleanup()
```

## 2 Bảng so sánh 2 loại cảm biến

| Tiêu chí so sánh | Cảm biến cũ (DHT11) | Cảm biến mới (DHT22) |
| --- | --- | --- |
| **Dải đo độ ẩm** | 20% - 90% | 0% - 100% |
| **Độ chính xác** | 5% | 2% |
| **Tần số lấy mẫu** | 1 Hz (1 giây/lần) | 0.5 Hz (2 giây/lần) |
| **Điện áp hoạt động** | 3V - 5.5V | 3.3V - 6V |

---

## 3 Danh sách kiểm tra thiết bị (Task List)

- [x] Kiểm tra bo mạch Raspberry Pi và nguồn điện
- [x] Kết nối các chân VCC, GND, DATA của cảm biến
- [ ] Chạy thử file Python đọc dữ liệu cảm biến
- [ ] Thiết lập crontab để tự động hóa chạy chương trình
