# ESP32-CAM Wireless Camera System - Detailed Project Documentation

This document provides the complete design, debugging, and optimization work of the ESP32-CAM wireless MJPEG streaming system.

---

## Executive Summary

The project successfully deployed and optimized an ESP32-CAM AI Thinker module as a wireless IP camera delivering stable 25-30 FPS MJPEG streaming at QVGA with sub-500 ms latency. The work covered hardware assembly, firmware development, and extensive troubleshooting for power delivery, boot modes, and WiFi compatibility issues.

---

## Hardware Architecture

### Core Components

| Component | Qty | Specification | Notes |
|-----------|-----|---------------|-------|
| ESP32-CAM AI Thinker | 1 | ESP32, OV2640, 4 MB PSRAM | Main MCU |
| FTDI FT232RL programmer | 1 | 3.3V / 5V USB-Serial | Upload only |
| External 5V supply | 1 | 5V, >=1A | Streaming stable |
| Electrolytic capacitor | 1 | 470 uF, low ESR | Power smoothing |

### Wiring (Programming Mode)

- TX (FTDI) -> GPIO3 (U0R)
- RX (FTDI) -> GPIO1 (U0T)
- GND (FTDI) -> GND
- GPIO0 -> GND (upload mode only)

### Power Architecture

Key finding: FTDI 5V output alone (300 mA max) is insufficient for camera initialization and streaming. OV2640 + ESP32 can draw 500+ mA peaks.

**Solution:** External regulated 5V / >=1A supply + 470 uF capacitor across 5V and GND

---

## Software & Firmware

### Arduino IDE Configuration

- Board: AI Thinker ESP32-CAM
- CPU Frequency: 160 MHz
- Partition Scheme: Huge APP (3MB+)
- PSRAM: Enabled
- Upload Speed: 115200 baud

### Camera Configuration

Key settings for stable high-FPS streaming:

```cpp
config.xclk_freq_hz = 20000000;           // 20 MHz camera clock
config.frame_size   = FRAMESIZE_QVGA;     // 320x240 resolution
config.pixel_format = PIXFORMAT_JPEG;     // Compressed frames
config.jpeg_quality = 10;                 // High compression
config.fb_count     = 2;                  // Double buffering
config.grab_mode    = CAMERA_GRAB_LATEST; // Skip slow frames
```

### WiFi Implementation

Station mode with timeout logic to prevent hangs:

```cpp
const char *ssid     = "AERIO4048";
const char *password = "aerio12345678";

WiFi.begin(ssid, password);
int attempts = 0;
while (WiFi.status() != WL_CONNECTED && attempts < 60) {
  delay(500);
  Serial.print(".");
  attempts++;
}
```

---

## Development Timeline & Critical Issues

### Issue 1: Upload Fails (No serial data received)

**Root Cause:** GPIO0 timing, baud mismatch, or driver conflicts

**Resolution:** Enforce GPIO0->GND->RESET sequence, verify 115200 baud, update USB drivers

### Issue 2: Boot Mode 0x13 (Wrong boot mode)

**Root Cause:** GPIO0 left grounded after upload

**Resolution:** Disconnect GPIO0 from GND, press RESET to enter normal boot

### Issue 3: Camera Init Failed (0x105 ESP_ERR_NOT_FOUND)

**Root Cause:** FTDI power rail insufficient current; unstable 5V prevents I2C communication

**Resolution:** Use external 5V / 1A supply + 470 uF capacitor

**Impact:** Immediate success after power fix

### Issue 4: WiFi Connectivity Crisis

**Subissue A:** Wrong credentials
- Error: WL_NO_SSID_AVAIL
- Fix: Verify SSID/password case sensitivity

**Subissue B:** iPhone hotspot failures
- Root cause: iPhone operates in 5GHz-only mode by default
- ESP32-CAM: 2.4 GHz only
- Fix: Use 2.4 GHz laptop/Android hotspot
- Result: Immediate connection success

---

## Performance Metrics

### Streaming

| Metric | Value | Status |
|--------|-------|--------|
| Frame Rate (QVGA) | 25-30 FPS | Excellent |
| Frame Rate (VGA) | 12-15 FPS | Good |
| Latency | 300-500 ms | Acceptable |
| Bandwidth | ~2-3 Mbps | OK on 2.4 GHz |
| WiFi Range (indoor) | ~30 m | Stable |
| Uptime | Continuous | No crashes |

### Power Consumption

| Mode | Current (approx.) |
|------|-------------------|
| Idle | 80 mA |
| Streaming | 400-500 mA |
| Average | 350 mA |
| Peak | 520 mA |

Estimated battery life (5V, 2500 mAh): >5 hours

---

## Lessons Learned

1. **Power is critical:** Undersized power budgets cause cascading failures (camera init, brownouts, WiFi drops)

2. **Programming ritual matters:** Consistent GPIO0/RESET sequence eliminates 90% of upload/boot issues

3. **WiFi limitations:** Always verify 2.4 GHz support; some hotspots default to 5 GHz only

4. **Resolution vs FPS tradeoff:** QVGA + high compression + double buffering = smooth real-time stream

5. **Stability through defaults:** Prefer grab_mode LATEST over older frame queue modes

---

## Future Enhancements

### Hardware
- External 2.4 GHz antenna for 100+ m range
- Larger bulk capacitors for power headroom
- Small heatsink on ESP32 for thermal throttling prevention

### Firmware
- mDNS for `esp32cam.local` access
- OTA firmware updates
- HTTPS/TLS + HTTP authentication
- Motion detection via PIR and frame differencing
- JSON telemetry for cloud analytics

---

## Integration with Biochemical Sensors

The camera system complements sensor monitoring by:
- Visual inspection of electrodes/displays during experiments
- Setup documentation and reproducibility
- Detecting visual anomalies (electrode fouling, bubbles, precipitates)
- Archiving visual records alongside electrochemical data

---
