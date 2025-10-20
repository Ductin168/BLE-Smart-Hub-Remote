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
🛠️ Hướng dẫn tạo và nạp code
1️⃣ Cài đặt ESP-IDF

Tải và cài đặt ESP-IDF theo hướng dẫn chính thức:
👉 https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/

Sau khi cài, mở ESP-IDF PowerShell / Terminal và kiểm tra:

idf.py --version


Nếu hiện version (ví dụ v5.3) là đã cài đúng.

2️⃣ Tạo project từ GitHub

Clone repo về máy:

git clone https://github.com/Ductin168/BLE-Smart-Hub-Remote.git
cd BLE-Smart-Hub-Remote

3️⃣ Thiết lập môi trường build

Chạy lệnh:

idf.py set-target esp32


👉 Dòng này giúp ESP-IDF hiểu bạn đang build cho chip ESP32 (hoặc esp32s3, esp32c3 nếu dùng loại khác).

4️⃣ Build firmware
idf.py build


ESP-IDF sẽ tự động biên dịch toàn bộ components/ và main/.

5️⃣ Nạp chương trình vào ESP32

Cắm board vào máy tính, xác định cổng COM (Windows) hoặc /dev/ttyUSB0 (Linux).
Sau đó chạy:

idf.py -p COMx flash


(thay COMx bằng cổng thật, ví dụ COM3)

6️⃣ Mở Serial Monitor để xem log
idf.py monitor


Bạn sẽ thấy log BLE scan, pairing, key exchange, và trạng thái relay ngay trên terminal.

⏹ Dừng monitor bằng tổ hợp Ctrl + ]

---
## 🧱 Cấu trúc thư mục

```text
BLE-Smart-Hub-Remote/
├── main/                    # Ứng dụng chính (FSM, app_main, BLE init)
│   ├── main.c
│   └── CMakeLists.txt
│
├── components/
│   ├── drivers/             # Giao tiếp phần cứng cấp thấp (GPIO, PWM, UART,...)
│   ├── hal/                 # Lớp trừu tượng phần cứng (Hardware Abstraction Layer)
│   ├── services/            # Logic nghiệp vụ (BLE, Key Exchange, Relay Control)
│   └── utils/ (tùy chọn)    # Hàm tiện ích chung (logger, crypto,...)
│
├── CMakeLists.txt           # File build chính của ESP-IDF
├── .gitignore               # Bỏ qua file build, IDE, sdkconfig,...
└── README.md                # Tài liệu dự án
🧩 Kiến trúc phần mềm
text
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
Hồ Đức Tín – Embedded Developer
📍 ESP32 / BLE / Firmware / IoT Systems
GitHub: https://github.com/Ductin168

📜 Giấy phép
MIT License – sử dụng tự do cho học tập, nghiên cứu và phát triển sản phẩm.

---
