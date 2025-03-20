# ⚡ Mạch Điều Khiển Relay Qua I2C (Nguồn 24V) ⚡

## 📜 Schematic

📷 **Circuit Diagram:**  
![Schematic](./Schematic.pdf)

## 🖼️ Hình Ảnh PCB

### 🔻 **Mặt Dưới (Bottom Layer)**
![Bottom Layer](./bot_layer_rounting.JPG)

### 🔺 **Mặt Trên (Top Layer)**
![Top Layer](./top_layer_rounting.JPG)

### 🎥 **Hình 3D**
![3D View](./3d.JPG)

## 🛠️ Giới Thiệu
Mạch này sử dụng nguồn **24V** và có khả năng điều khiển relay qua giao tiếp **I2C**. Các thành phần chính bao gồm:

- 🔹 **`MCP23017`**: Bộ mở rộng GPIO qua giao tiếp I2C.
- 🔹 **`ULN2803A`**: Mạch Darlington transistor driver để kích relay.
- 🔹 **`VOM617A-2T`**: Optocoupler để cách ly tín hiệu.
- 🔹 **`Relay`**: Được điều khiển để bật/tắt tải điện.
- 🔹 **`LM2596`**: Module hạ áp từ **24V xuống 5V** để cấp nguồn cho vi điều khiển và MCP23017.
- 🔹 **`RJ45`**: Dùng để kết nối tín hiệu điều khiển từ xa.

## 📋 Sơ Đồ Mạch

- 🟢 **Nguồn chính 24V** cấp cho toàn bộ hệ thống.
- 🟢 **LM2596** hạ áp từ **24V xuống 5V** để cấp cho MCP23017, ULN2803A và vi điều khiển.
- 🟢 **MCP23017** mở rộng cổng GPIO để điều khiển nhiều relay hơn.
- 🟢 **ULN2803A** khuếch đại dòng điện từ MCP23017 để kích hoạt relay.
- 🟢 **Optocoupler VOM617A-2T** giúp cách ly tín hiệu điều khiển khỏi mạch công suất.
- 🟢 **RJ45** giúp truyền tín hiệu I2C hoặc tín hiệu điều khiển khác từ xa.
- 🟢 **Relay 24V** được kích hoạt để đóng/ngắt tải điện cao hơn.

## ⚡ Chức Năng
✅ Điều khiển bật/tắt relay thông qua vi điều khiển với giao tiếp I2C.  
✅ Cách ly tín hiệu điều khiển và tải điện cao áp.  
✅ Hỗ trợ mở rộng nhiều relay bằng MCP23017.  
✅ **Sử dụng LM2596 để hạ áp 24V xuống 5V** mà không cần mạch nguồn phụ.  
✅ Truyền tín hiệu điều khiển từ xa qua cổng RJ45.  

## 🔌 Hướng Dẫn Sử Dụng
### 1️⃣ Kết Nối Phần Cứng

```yaml
🔋 Nguồn vào: 24V cấp cho relay và LM2596
⚡ LM2596: Giảm 24V xuống 5V để cấp cho IC điều khiển
🔗 SDA, SCL của MCP23017 → Vi điều khiển (ESP32, Raspberry Pi, Arduino...)
🖲️ OUTPUT của MCP23017 → INPUT của ULN2803A
🔌 OUTPUT của ULN2803A → Relay 24V
🛡️ Optocoupler (VOM617A-2T) → Cách ly tín hiệu điều khiển
🌐 RJ45 → Kết nối mạch với hệ thống điều khiển từ xa
