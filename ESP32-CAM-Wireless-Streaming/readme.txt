# ESP32-CAM Wireless Video Streaming System

A production-ready ESP32-CAM (AI Thinker) wireless IP camera system providing real-time MJPEG video streaming over WiFi.  
This project focuses on **stability, power reliability, and high frame-rate performance**, and is suitable for IoT, monitoring, and embedded vision applications.

---

## 📌 Project Overview

This project implements a fully operational ESP32-CAM web-based video streaming server using the OV2640 camera sensor. The system was designed, debugged, and optimized over ~24 hours, addressing common ESP32-CAM challenges such as power instability, boot mode issues, and WiFi compatibility problems.

**Current Status:** ✅ Complete & Operational  
**Streaming Performance:** 25–30 FPS @ QVGA  
**Latency:** ~300–500 ms  

---

## 🚀 Features

- Live MJPEG video streaming over HTTP
- Web-based camera control interface
- Stable 25–30 FPS streaming (QVGA)
- PSRAM double buffering enabled
- WiFi connection with timeout handling
- Serial debug output for diagnostics
- Production-stable power configuration

---

## 🧠 Hardware Used

| Component | Specification |
|---------|---------------|
| ESP32-CAM | AI Thinker, OV2640, 4MB PSRAM |
| USB Programmer | FTDI FT232RL |
| Power Supply | External 5V / 1A (minimum) |
| Capacitor (Recommended) | 470µF across 5V & GND |

---

## 🔌 Programming Wiring (FTDI → ESP32-CAM)

| FTDI | ESP32-CAM |
|----|-----------|
| TX | GPIO3 (U0R) |
| RX | GPIO1 (U0T) |
| GND | GND |
| GPIO0 | GND *(upload mode only)* |

### Programming Sequence
1. Connect GPIO0 → GND  
2. Press RESET  
3. Upload sketch  
4. Disconnect GPIO0 from GND  
5. Press RESET again to run  

---

## ⚙️ Arduino IDE Configuration

- **Board:** AI Thinker ESP32-CAM  
- **Upload Speed:** 115200  
- **CPU Frequency:** 160 MHz  
- **Partition Scheme:** Huge APP (3MB+)  
- **PSRAM:** Enabled  

---

## 📂 Project Structure

