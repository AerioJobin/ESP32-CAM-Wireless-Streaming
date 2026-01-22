# **ESP32-CAM Wireless Video Streaming System**

A **production-ready ESP32-CAM (AI Thinker) wireless IP camera system** providing real-time MJPEG video streaming over WiFi.

This project prioritizes **stability, power reliability, and high frame-rate performance**, making it suitable for **IoT, monitoring, robotics, and embedded vision applications**.

---

## **📌 Project Overview**

This project implements a **fully operational ESP32-CAM web-based video streaming server** using the **OV2640 camera sensor**. The system was designed, debugged, and optimized over ~24 hours, addressing common ESP32-CAM issues such as:

* Power instability and brownouts
* Boot mode and GPIO0 upload issues
* WiFi connection reliability
* PSRAM and buffer configuration

**Current Status:** ✅ Complete & Operational
**Streaming Performance:** 25–30 FPS @ QVGA
**Latency:** ~300–500 ms

---

## **🚀 Features**

* 📡 Live MJPEG video streaming over HTTP
* 🌐 Web-based camera control interface
* 🎥 Stable **25–30 FPS** streaming (QVGA)
* 🧠 PSRAM-enabled **double buffering**
* 📶 Robust WiFi connection with timeout handling
* 🐞 Serial debug output for diagnostics
* ⚡ Production-stable power configuration

---

## **🧠 Hardware Used**

| Component               | Specification                  |
| ----------------------- | ------------------------------ |
| ESP32-CAM               | AI Thinker, OV2640, 4MB PSRAM  |
| USB Programmer          | FTDI FT232RL                   |
| Power Supply            | External 5V / **≥1A required** |
| Capacitor (Recommended) | 470µF across 5V & GND          |

> ⚠️ **Important:** Insufficient power is the #1 cause of ESP32-CAM instability.

---

## **🔌 Programming Wiring (FTDI → ESP32-CAM)**

| FTDI  | ESP32-CAM                |
| ----- | ------------------------ |
| TX    | GPIO3 (U0R)              |
| RX    | GPIO1 (U0T)              |
| GND   | GND                      |
| GPIO0 | GND *(upload mode only)* |

### **Programming Sequence**

1. Connect **GPIO0 → GND**
2. Press **RESET**
3. Upload the sketch
4. Disconnect **GPIO0 from GND**
5. Press **RESET** again to run

---

## **⚙️ Arduino IDE Configuration**

* **Board:** AI Thinker ESP32-CAM
* **Upload Speed:** 115200
* **CPU Frequency:** 160 MHz
* **Partition Scheme:** Huge APP (3MB+)
* **PSRAM:** Enabled

---

## **📂 Project Structure**

```
ESP32-CAM-Streaming/
├── src/
│   └── main.ino        # Core camera + web server logic
├── README.md           # Project documentation
└── assets/             # (Optional) Images / diagrams
```

---

## **▶️ Usage**

1. Power the ESP32-CAM using a **stable 5V supply**
2. Open the **Serial Monitor (115200 baud)**
3. Note the assigned **IP address** after WiFi connects
4. Open a browser and navigate to:

```
http://<ESP32-IP>
```

* The web interface allows live viewing and camera parameter adjustments

---

## **🛠️ Troubleshooting**

### **Camera Not Detected**

* Ensure **AI Thinker ESP32-CAM** board is selected
* Confirm PSRAM is enabled
* Check ribbon cable seating

### **Brownout / Reboot Loop**

* Use an external **5V ≥1A** power supply
* Add a **470µF capacitor** across 5V & GND

### **No WiFi Connection**

* Verify SSID and password
* Use 2.4GHz WiFi (ESP32 does not support 5GHz)

---

## **📈 Performance Notes**

* QVGA provides the best balance of **FPS vs stability**
* Higher resolutions significantly reduce frame rate
* MJPEG chosen for simplicity and browser compatibility

---

## **🔒 Security Notes**

* HTTP streaming is **unencrypted** by default
* Not recommended for public internet exposure without:

  * Network isolation
  * Reverse proxy
  * VPN or authentication layer

---

## **📜 License**

This project is released under the **MIT License**.
You are free to use, modify, and distribute this project with attribution.

---

## **🤝 Contributing**

Pull requests, improvements, and performance optimizations are welcome.

---

**Built for reliability. Tuned for performance.** 🚀
