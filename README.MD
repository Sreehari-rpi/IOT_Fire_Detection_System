# IoT Fire Detection System
**Project Status:** Functional / Prototype

## 📖 Overview
A smart safety system that utilizes a NodeMCU (ESP8266) and an Infrared Flame Sensor to monitor environments for fire outbreaks. When fire is detected, the system triggers a physical alarm and sends a push notification to a mobile device via the Blynk IoT platform.

## 🛠️ Bill of Materials
| Component | Quantity | Description |
| :--- | :--- | :--- |
| NodeMCU (ESP8266) | 1 | Wi-Fi enabled microcontroller |
| Flame Sensor | 1 | IR-based flame detection module |
| Active Buzzer | 1 | 5V alarm for local alerts |
| Breadboard & Wires | 1 | For prototyping connections |

## 🔌 Circuit Design
- **Flame Sensor VCC** -> NodeMCU 3.3V
- **Flame Sensor GND** -> NodeMCU GND
- **Flame Sensor DO (Digital Out)** -> NodeMCU D2 (GPIO 4)
- **Buzzer (+)** -> NodeMCU D5 (GPIO 14)
- **Buzzer (-)** -> NodeMCU GND

## 🧠 System Logic
1. **Setup:** Connect to local Wi-Fi and authenticate with the Blynk Cloud.
2. **Monitoring:** Continuously poll the Digital Pin of the Flame Sensor.
3. **Trigger:** If the sensor pin goes LOW (standard for flame detection):
   - Set Buzzer Pin to HIGH.
   - Send `Blynk.logEvent("fire_detected")`.
4. **Reset:** Once the flame is removed, the buzzer stops and the system returns to monitoring.