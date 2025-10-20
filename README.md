# BLE-Smart-Hub-Remote
ESP32-based Hub–Remote BLE authentication and relay control system.
# BLE Smart Hub – Remote (ESP32 Framework)

Dự án này xây dựng hệ thống **Hub–Remote BLE** trên nền **ESP-IDF**,  
mục tiêu là mô phỏng **cơ chế khóa thông minh**: Hub nhận tín hiệu BLE từ Remote, xác thực Key, và điều khiển Relay để mở khóa.

---

## ⚙️ Tính năng chính

- **Kết nối BLE:** Hub (Central) quét, phát hiện và kết nối Remote (Peripheral).  
- **Xác thực Key:** Remote gửi Key mã hóa; Hub giải mã, kiểm tra hợp lệ.  
- **Điều khiển Relay:** Khi Key đúng → Hub kích relay mở khóa; sai → bỏ qua hoặc báo lỗi.  
- **Quản lý thiết bị:** Lưu địa chỉ MAC Remote đã pair; thêm/xóa Remote linh hoạt.  
- **BLE Low Energy:** Tối ưu điện năng, chỉ hoạt động khi có sự kiện.  
- **Cấu trúc phân tầng:** Tách rõ `Driver` / `HAL` / `Service` / `Application`.  

---

## 🧱 Cấu trúc thư mục

BLE-Smart-Hub-Remote/
├── main/ # Ứng dụng chính (FSM, app_main, BLE init)
│ ├── main.c
│ └── CMakeLists.txt
│
├── components/
│ ├── drivers/ # Giao tiếp phần cứng cấp thấp (GPIO, PWM, UART,...)
│ ├── hal/ # Lớp trừu tượng phần cứng (Hardware Abstraction Layer)
│ ├── services/ # Logic nghiệp vụ (BLE, Key Exchange, Relay Control)
│ └── utils/ (tùy chọn) # Hàm tiện ích chung (logger, crypto,...)
│
├── CMakeLists.txt # File build chính của ESP-IDF
├── .gitignore # Bỏ qua file build, IDE, sdkconfig,...
└── README.md # Tài liệu dự án

less
Copy code

---

## 🧠 Nguyên lý hoạt động

1. **Hub (ESP32 Central)** khởi tạo BLE, quét thiết bị gần đó.  
2. Khi phát hiện **Remote (ESP32 Peripheral)** → tiến hành kết nối.  
3. **Remote** gửi Key mã hóa BLE → **Hub** nhận, giải mã và kiểm tra.  
4. Nếu hợp lệ → **Hub** kích relay mở khóa, đồng thời lưu thông tin Remote đã pair.  
5. Nếu sai → **Hub** bỏ qua hoặc báo lỗi qua LED cảnh báo.  

---

## 🛠️ Cách build & nạp chương trình

1. Cài đặt ESP-IDF theo hướng dẫn của Espressif  
   👉 [ESP-IDF Get Started](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/)  
2. Trong terminal, chuyển tới thư mục dự án:
   ```bash
   cd BLE-Smart-Hub-Remote
   idf.py set-target esp32
   idf.py build
   idf.py -p COMx flash   # (thay COMx bằng cổng nối tiếp của bạn)
   idf.py monitor
🧩 Kiến trúc phần mềm
sql
Copy code
+-----------------------------+
|        Application          | → main.c (FSM, system logic)
+-----------------------------+
|          Services           | → BLE logic, Key exchange, Relay control
+-----------------------------+
|             HAL             | → API trừu tượng cho BLE, GPIO, Relay
+-----------------------------+
|           Drivers           | → Code phần cứng cụ thể ESP32
+-----------------------------+
👤 Tác giả
Hồ Đức – Embedded Developer
📍 ESP32 / BLE / Firmware / IoT Systems
GitHub: https://github.com/Ductin168

📜 Giấy phép
MIT License – sử dụng tự do cho học tập, nghiên cứu và phát triển sản phẩm.

yaml
Copy code

---

### ✅ Cách dùng:
Lưu lại nội dung này vào **file `README.md`** ngay trong thư mục gốc repo →  
rồi chạy:
```bash
