# ESP32-CAM Wireless MJPEG Streaming System

A production-ready ESP32-CAM (AI Thinker) wireless IP camera system that delivers real-time MJPEG video streaming over WiFi with 25-30 FPS at QVGA, sub-500 ms latency, and a power/WiFi architecture tuned for stability in IoT, robotics, and embedded vision applications.

## Project Overview

This project implements a fully operational ESP32-CAM web-based video streaming server using the OV2640 camera sensor, with the system designed, debugged, and optimized to solve common ESP32-CAM issues such as brownouts, boot-mode errors, and WiFi reliability problems.

Key focus areas include:

- Stable high-FPS streaming (25-30 FPS at QVGA)
- Robust power delivery with external 5 V / >=1 A supply
- Reliable WiFi connection and credential handling
- PSRAM-enabled buffering for smoother MJPEG streaming

---

## Features

- Live MJPEG streaming over HTTP in any modern browser
- Web-based control interface for resolution and image tuning
- Stable 25-30 FPS at QVGA and 12-15 FPS at VGA
- PSRAM-enabled double buffering with CAMERA_GRAB_LATEST
- Robust WiFi station-mode logic with timeout handling
- Serial debug output for WiFi, camera, and streaming diagnostics
- Ready for sensor/IoT integration and lab monitoring

---

## System Preview

![Stream Preview](ESP32-CAM-Wireless-Streaming/images/stream-preview.gif)

Additional views:
- Wiring: `ESP32-CAM-Wireless-Streaming/images/wiring-diagram.png`
- Power setup: `ESP32-CAM-Wireless-Streaming/images/power-setup.png`
- Web UI: `ESP32-CAM-Wireless-Streaming/images/web-ui.png`

---

## Hardware Requirements

### Core Components

| Component | Qty | Key Specification | Notes |
|-----------|-----|-------------------|-------|
| ESP32-CAM AI Thinker | 1 | ESP32, OV2640, 4 MB PSRAM | Main MCU |
| FTDI FT232RL programmer | 1 | 3.3 V / 5 V USB-Serial | Upload only |
| External 5 V supply | 1 | 5 V, >=1 A | Streaming stable |
| Electrolytic capacitor | 1 | 470 uF, low ESR | Power smoothing |

**Important:** Insufficient power is the number one cause of ESP32-CAM instability (camera init errors, brownouts, random reboots).

---

## Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/AerioJobin/ESP32-CAM-Wireless-Streaming.git
cd ESP32-CAM-Wireless-Streaming
```

### 2. Wire for Programming (FTDI => ESP32-CAM)

| FTDI pin | ESP32-CAM pin |
|----------|---------------|
| TX | GPIO3 (U0R) |
| RX | GPIO1 (U0T) |
| GND | GND |
| GPIO0 | GND (upload only) |

### 3. Arduino IDE Settings

- Board: **AI Thinker ESP32-CAM**
- Upload Speed: **115200** baud
- CPU Frequency: **160 MHz**
- Partition Scheme: **Huge APP (3MB+)**
- PSRAM: **Enabled**

### 4. Programming Sequence

1. Connect **GPIO0 => GND**
2. Press **RESET**
3. Click **Upload** in Arduino IDE
4. Wait for "Hard resetting via RTS pin"
5. Disconnect **GPIO0** from GND
6. Press **RESET** again to run the firmware

---

## Usage

1. Power the ESP32-CAM from a **stable 5 V >=1 A** supply (not just FTDI)
2. Open the **Serial Monitor at 115200 baud** and wait for WiFi connection
3. Note the printed IP address and open in a browser:

```
http://<esp32-ip-address>/
```

4. Use the web interface to:
   - View the live MJPEG video stream
   - Change resolution (QVGA, VGA, SVGA, UXGA)
   - Adjust brightness, contrast, saturation
   - Flip image horizontally/vertically
   - Tune JPEG quality for bandwidth vs clarity

---

## Performance Summary

### Streaming Metrics

| Metric | Value | Status |
|--------|-------|--------|
| Frame Rate (QVGA) | 25-30 FPS | Excellent |
| Frame Rate (VGA) | 12-15 FPS | Good |
| Latency | 300-500 ms | Acceptable |
| Bandwidth | ~2-3 Mbps | OK on 2.4 G |
| WiFi Range (indoor) | ~30 m | Stable |
| Uptime | Multi-hour | No crashes |

### Power Consumption (5 V)

| Mode | Current (approx.) |
|------|-------------------|
| Idle | 80 mA |
| Streaming | 400-500 mA |
| Average | 350 mA |
| Peak | 520 mA |

A 5 V, 2500 mAh battery can typically run the system for more than 5 hours.

---

## Troubleshooting Highlights

- **Upload fails (No serial data received)**
  - Recheck GPIO0=>GND and reset sequence
  - Ensure 115200 baud and correct COM port/driver

- **Wrong boot mode (0x13)**
  - Remove GPIO0-GND after upload and press RESET

- **Camera init failed (0x105 ESP_ERR_NOT_FOUND)**
  - Use external 5 V / 1 A plus 470 uF capacitor; avoid powering from FTDI only

- **WiFi not connecting**
  - ESP32-CAM is **2.4 GHz only**; avoid 5 GHz / some iPhone hotspots
  - Verify SSID and password (case-sensitive)

---

## Documentation

More details (timeline, root-cause analysis, deployment recommendations) are collected in:

- `docs/project-documentation.md` - Complete project development log
- `docs/overview.md` - Executive summary & objectives
- `docs/hardware.md` - Hardware architecture & wiring
- `docs/software.md` - Firmware configuration & logic
- `docs/troubleshooting.md` - Detailed issue resolution
- `docs/performance.md` - Metrics & specifications
- `docs/lessons-learned.md` - Best practices & enhancements

---

## License

MIT License. See LICENSE file for details.

---

**Created by:** AerioJobin
**Status:** Production-ready for IoT & lab integration
