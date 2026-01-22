# Overview

The ESP32-CAM Wireless Camera System is a complete embedded solution that transforms the ESP32-CAM AI Thinker module into a production-ready wireless IP camera with stable MJPEG streaming, robust power delivery, and resilient WiFi connectivity.

## Executive Summary

The system delivers real-time video streaming over WiFi using an ESP32 dual-core microcontroller and OV2640 image sensor, achieving stable 25-30 FPS at QVGA with sub-500 ms latency under optimized power and network conditions. Hardware assembly, firmware tuning, and extensive troubleshooting resolved camera initialization failures, boot-mode issues, and WiFi incompatibilities, resulting in a reliable streaming platform ready for IoT and lab integration.

## Objectives

- Establish a functional wireless camera streaming system using the ESP32-CAM module
- Create a browser-based interface for remote camera access and control
- Resolve hardware initialization and connectivity challenges for reliable boot
- Overcome WiFi credential and 2.4 GHz compatibility issues
- Optimize camera parameters for stable, real-time video transmission
- Document the development process for future sensor and IoT integrations

## Application Context

This camera system provides foundational experience for biochemical sensor monitoring, where visual inspection of electrodes, reaction vessels, or displays must be captured and accessed remotely throughout experiments. It can also serve as a general-purpose IP camera for security, environmental monitoring, and remote lab instrumentation where low-cost, low-power video is sufficient.

## Technical Summary

| Parameter | Specification |
|-----------|---------------|
| Microcontroller | ESP32 dual-core, 240 MHz |
| Camera Sensor | OV2640, 2 MP |
| RAM | 520 KB SRAM + 4 MB PSRAM |
| Storage | 4 MB Flash |
| WiFi | 802.11 b/g/n, 2.4 GHz only |
| Max Frame Size | UXGA (1600x1200) |
| Operating Frame Sizes | QVGA, VGA, SVGA, UXGA |
| Video Format | MJPEG over HTTP |
| Supply Voltage | 5 V DC, ~1 A (for stable streaming) |

---
