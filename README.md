# Blue-Blaster-ESP32-Dual-2.4GHz-Radio-Battery-Charger-Board
A custom open-source ESP32 development board featuring the WROOM-32E module, integrated TP4056 Li-Ion/Li-Po battery charging, dual E01-ML01DP5 (nRF24L01+) 2.4GHz wireless modules, USB-C with CH340C, and an onboard 0.96" OLED display. Designed for advanced wireless projects, robotics, and handheld controllers.
# 🔵 Blue Blaster - ESP32 Dual-Radio Dev Board

![Blue Blaster PCB Render](images/PCB_Front.png)

The **Blue Blaster** is a feature-packed, custom ESP32 development board designed for advanced wireless communication projects. It combines the power of the ESP32-WROOM-32E with dual 2.4GHz radio modules (E01-ML01DP5), seamless USB-C connectivity, and robust Li-Ion/Li-Po battery management. 

This board is perfect for building DIY remote controllers, IoT sensor hubs, RC robotics, or any project requiring robust data transfer between multiple devices.

> ⚠️ **Note:** This project is currently in the prototyping/design phase. Please review the schematic and ensure it suits your needs before ordering the PCB.

---

## ✨ Key Features

*   **Main Controller:** ESP32-WROOM-32E (4MB Flash).
*   **Power Management:**
    *   TP4056 Li-Ion/Li-Po battery charger with status LEDs.
    *   AMS1117 3.3V voltage regulator for main logic.
*   **Connectivity:**
    *   **USB Type-C:** Handles both power and data via the CH340C USB-to-Serial chip.
    *   **Dual 2.4GHz Radio:** Two E01-ML01DP5 modules (compatible with nRF24L01+ and SX1280 ecosystem) enabling master/slave or node-to-node communication.
*   **User Interface:**
    *   0.96" I2C OLED Display.
    *   3x Tactile Buttons (UP, DOWN, SELECT) for menu navigation.
    *   Dedicated RESET and BOOT buttons.
*   **PCB Layout:** 2-layer board with surface-mount components.

---

## 🖥️ Gallery

| Schematic | PCB | 
<img width="1772" height="852" alt="Schematic_Blue_Blaster_2026-05-03" src="https://github.com/user-attachments/assets/9b315182-075c-4c9e-af80-d161b4edf53f" />

| :---: | :---: | 
<img width="680" height="612" alt="Blue_Blaster_3D_Top_View" src="https://github.com/user-attachments/assets/a37437dc-fac4-4cf5-8188-a6dc73e76257" />


| [![Schematic](images/Schematic_Blue_Blaster.jpg)](images/Schematic_Blue_Blaster.jpg) 
<img width="696" height="607" alt="Blue_Blaster_3D_Bottom_View" src="https://github.com/user-attachments/assets/c36aaa09-acf8-4805-aa15-43a970c44d6e" />

| [![PCB Top](images/PCB_Front.png)](images/PCB_Front.png) |
<img width="570" height="472" alt="Blue_Blaster_2D_View" src="https://github.com/user-attachments/assets/6537d9ae-2af9-4c7d-8339-ea60d1b2e1c2" />

---

## 📌 Hardware Specifications

### ⚡ Power
*   **Input Voltage:** 5V (via USB-C) or 3.7V-4.2V Battery (via BAT pads)
*   **Onboard Charger:** TP4056 with a default 1A charging current.

### 🔌 Pinout / GPIO Mapping (ESP32)

| Peripheral | Signal | ESP32 GPIO |
| :--- | :--- | :--- |
| **OLED Display** | SDA (I2C Data) | IO21 |
| | SCL (I2C Clock) | IO22 |
| **Buttons** | UP | IO32 |
| | DOWN | IO33 |
| | SELECT | IO26 |
| | BOOT | IO0 |
| **Radio 1 (E01-ML01DP5)** | MISO | IO25 |
| | MOSI | IO23 |
| | SCK | IO19 |
| | CSN | IO17 |
| | CE | IO18 |
| | IRQ | IO16 |
| **Radio 2 (E01-ML01DP5)** | MISO | IO14 |
| | MOSI | IO12 |
| | SCK | IO13 |
| | CSN | IO15 |
| | CE | IO27 |
| | IRQ | IO04 |
| **USB/Serial** | RXD0 | IO3 |
| | TXD0 | IO1 |
| **Battery** | TP_VBAT | ADC (Internal) |

---

## 🛠️ Getting Started

### 1. **Fabricate the PCB**
You can use the provided `Gerber` files (if available in your repository) or download the `PCB_PCB_Blue_Blaster-copy-copy_2026-05-03.json` file and upload it to [EasyEDA](https://easyeda.com/) or [JLCPCB](https://jlcpcb.com/) to manufacture the board.

### 2. **Solder Components**
Use the Silkscreen and the provided PDF Schematic to assemble the board.

### 3. **Programming**
You can program this board using the **Arduino IDE** or **ESP-IDF** via the USB-C port.

*   **Install Driver:** Ensure you have the [CH340 driver](https://www.wch-ic.com/downloads/CH341SER_EXE.html) installed.
*   **Arduino Setup:**
    1. Install the ESP32 board package.
    2. Select `ESP32 Dev Module`.
    3. Connect via USB-C.

### 4. **Example Code (BLE Scan)**
Here is a quick snippet to verify flashing works:

```cpp
void setup() {
  Serial.begin(115200);
  pinMode(32, INPUT); // UP Button
}

void loop() {
  if(digitalRead(32) == LOW) {
    Serial.println("Button UP Pressed!");
  }
  delay(100);
}
