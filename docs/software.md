# Software & Firmware

The firmware is developed in Arduino IDE using the ESP32 core, tuned for high-FPS MJPEG streaming and robust WiFi behavior.

## Arduino IDE Configuration

- Board: AI Thinker ESP32-CAM
- CPU Frequency: 160 MHz
- Partition Scheme: Huge APP (3MB+)
- PSRAM: Enabled
- Upload Speed: 115200 baud

## Camera Configuration

Key settings for stable high-FPS streaming:

```cpp
config.xclk_freq_hz = 20000000;           // 20 MHz camera clock
config.frame_size   = FRAMESIZE_QVGA;     // 320x240 resolution
config.pixel_format = PIXFORMAT_JPEG;     // Compressed frames
config.jpeg_quality = 10;                 // High compression
config.fb_count     = 2;                  // Double buffering
config.grab_mode    = CAMERA_GRAB_LATEST; // Skip slow frames
```

This configuration balances FPS and responsiveness for real-time monitoring.

## WiFi Implementation

Station mode with timeout logic:

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

## Web Server & MJPEG Streaming

- HTTP server exposes main page with control UI
- Dedicated streaming endpoint captures and transmits frames
- Serial debug output for diagnostics

## Extensibility Hooks (Future)

- mDNS for `esp32cam.local` access
- OTA firmware updates
- HTTPS/TLS authentication
- Motion detection and event recording
- JSON telemetry for cloud integration

---
