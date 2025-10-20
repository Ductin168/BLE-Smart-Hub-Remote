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
Hồ Đức – Embedded Developer
📍 ESP32 / BLE / Firmware / IoT Systems
GitHub: https://github.com/Ductin168

📜 Giấy phép
MIT License – sử dụng tự do cho học tập, nghiên cứu và phát triển sản phẩm.

yaml
Copy code

---

✅ **Kết quả sau khi sửa:**  
- Cấu trúc thư mục hiển thị dưới dạng *khối code đẹp, căn thẳng hàng*  
- Sơ đồ kiến trúc hiển thị đúng khung ASCII  
- Không còn dòng “SQL Copy code”  
- Hiển thị chuẩn trên GitHub, VSCode, hoặc GitLab  

---

Bạn chỉ cần:
1. Mở `README.md`
2. Xóa đoạn lỗi cũ
3. Dán đoạn trên vào
4. Rồi commit lại:

```bash
git add README.md
git commit -m "docs: fix markdown display for folder structure and architecture diagram"
git push origin main