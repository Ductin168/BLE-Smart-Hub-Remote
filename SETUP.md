# ⚙️ Hướng Dẫn Chuẩn Hóa Môi Trường Phát Triển  
**Dự án:** BLE Smart Hub & Remote  
**Framework:** ESP-IDF v5.3.1  
**Ngày cập nhật:** 20/10/2025  

---

## 🧭 1. Mục tiêu  
Tài liệu này giúp các thành viên thiết lập môi trường phát triển **đồng nhất**, đảm bảo tất cả đều có thể:
- Build & flash project ESP32 không lỗi.
- Sử dụng đúng phiên bản toolchain & thư viện.
- Làm việc thống nhất trên cùng nền tảng.

---

## 🧰 2. Công cụ & Phiên bản yêu cầu  

| Thành phần | Phiên bản khuyến nghị | Ghi chú |
|-------------|----------------------|---------|
| **ESP-IDF** | 5.3.1 | Framework chính cho ESP32 |
| **Python** | 3.11 | ESP-IDF sử dụng để chạy công cụ |
| **Git** | ≥ 2.42 | Quản lý mã nguồn nhóm |
| **VS Code** | Mới nhất | IDE được khuyến nghị |
| **ESP-IDF Tools** | Mặc định theo IDF 5.3.1 | Cài cùng installer |
| **ESP-IDF Extension for VS Code** | ≥ 1.7.0 | Dễ build & flash trực tiếp trong VS Code |
| **OS** | Windows 10/11 64-bit | Được kiểm thử chính thức |

---

## 🪜 3. CÀI ĐẶT VÀ CẤU HÌNH ESP-IDF  

ESP-IDF là framework chính để lập trình ESP32.  
Các thành viên có thể thiết lập theo **một trong hai cách sau** để đảm bảo đồng bộ môi trường.

---

### 🔹 Cách 1: Sử dụng ESP-IDF Tools Installer + ESP-IDF Command Prompt 

> Cách này cài toàn bộ môi trường (toolchain, Python, Git, ESP-IDF) tự động và ổn định nhất cho Windows.

#### Bước 1. Tải và cài đặt
1. Truy cập: [https://dl.espressif.com/dl/esp-idf/](https://dl.espressif.com/dl/esp-idf/)  
2. Tải bản `ESP-IDF Tools Installer for Windows (Online)`  
3. Khi cài đặt:
   - Chọn ESP-IDF Version: **v5.3.1**  
   - Tick chọn **Add ESP-IDF to PATH**  
   - Tick chọn **Install Python, Git**

#### Bước 2. Mở đúng terminal ESP-IDF
Sau khi cài, mở: Start Menu → ESP-IDF 5.3.1 → ESP-IDF 5.3.1 Command Prompt

#### Bước 3. Kiểm tra môi trường
Trong cửa sổ vừa mở, gõ:
```bash
''' idf.py --version '''

---

### 🔹 Cách 2: Sử dụng Terminal trong VS Code (tích hợp ESP-IDF Extension)

> Cách này cho phép bạn **build, flash và monitor trực tiếp trong VS Code**, không cần mở Command Prompt riêng.  
> Phù hợp nếu bạn muốn lập trình trong một IDE duy nhất và thao tác nhanh hơn.

Làm theo hướng dẫn của link:  https://www.youtube.com/watch?si=6yAYuSna5tZOGRqE&v=YK9g9GWQigg&feature=youtu.be

---

