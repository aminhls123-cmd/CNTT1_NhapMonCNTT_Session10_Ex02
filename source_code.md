# Tài liệu Hướng dẫn Cài đặt Cảm biến Độ ẩm & Điều khiển Máy bơm

## 1. Cài đặt hệ thống
Chạy lệnh `sudo apt update && sudo apt upgrade -y` để cập nhật hệ thống. Để chỉnh sửa lịch trình chạy tự động, sử dụng lệnh `crontab -e`.

## 2. Code điều khiển máy bơm
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
