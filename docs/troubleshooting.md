# Troubleshooting

This section captures major issues encountered and their resolutions.

## Upload Issues

### No serial data received

**Root Causes:**
- Incorrect GPIO0 timing during RESET
- Baud rate mismatch (use 115200)
- Outdated USB drivers (CH340/FTDI)

**Resolutions:**
- Enforce strict sequence: GPIO0->GND, RESET, Upload
- Verify 115200 baud in Serial Monitor and IDE
- Update USB-Serial drivers

---

### Wrong boot mode (0x13)

**Root Cause:** GPIO0 not released from GND after upload

**Resolution:** Disconnect GPIO0, press RESET, confirm boot to application entry point

---

## Camera Init Failures

### Camera init failed (0x105 ESP_ERR_NOT_FOUND)

**Root Causes:**
- FTDI power rail insufficient (300 mA max vs 500+ mA needed)
- Unstable 5V prevents OV2640 I2C communication

**Solution:** External 5V/1A supply + 470 uF capacitor across 5V/GND

**Result:** Immediate camera detection and init success

---

## WiFi Connectivity

### WiFi status 6 (WL_NO_SSID_AVAIL)

**Root Cause:** Incorrect SSID or password

**Fix:** Verify SSID/password case sensitivity

---

### iPhone hotspot connection failures

**Root Cause:** iPhone defaults to 5 GHz; ESP32-CAM is 2.4 GHz only

**Fix:** Use 2.4 GHz laptop or Android hotspot

**Result:** Immediate connection success

---

## Stability & Brownouts

### Intermittent brownouts and frame drops

**Causes:**
- Marginal power supply
- High-resolution settings with excessive current

**Mitigations:**
1. Add 470 uF capacitor
2. Use QVGA resolution instead of UXGA
3. Enable PSRAM double buffering
4. Set grab_mode = CAMERA_GRAB_LATEST

**Result:** Stable 25-30 FPS streaming, no brownouts

---
