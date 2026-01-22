# Performance

Measured performance of the ESP32-CAM streaming system under typical indoor WiFi conditions.

## Streaming Metrics

| Metric | Value | Assessment |
|--------|-------|-------------|
| Frame Rate (QVGA) | 25-30 FPS | Excellent |
| Frame Rate (VGA) | 12-15 FPS | Good |
| Latency | 300-500 ms | Acceptable |
| Bandwidth | ~2-3 Mbps | OK on 2.4 GHz |
| WiFi Range (indoor) | ~30 m | Stable |
| Uptime | Continuous | No crashes |

QVGA configuration with high JPEG compression and double buffering delivers smooth motion suitable for monitoring and telepresence applications.

## Power Consumption

| Operating Mode | Current (approx.) |
|----------------|-------------------|
| Idle | 80 mA |
| Streaming | 400-500 mA |
| Average | 350 mA |
| Peak | 520 mA |

Estimated battery life (5V, 2500 mAh): >5 hours at typical average load.

## Reliability & Uptime

- No crashes observed during continuous multi-hour streaming sessions following power and configuration optimizations
- Brownout and reset events were eliminated by using a 5V/1A supply and adding a 470 uF capacitor
- Multi-hour stress testing shows stable performance

## Technical Specification Summary

| Parameter | Specification |
|-----------|---------------|
| Microcontroller | ESP32 (240 MHz dual-core) |
| Camera Sensor | OV2640, 2 MP |
| RAM | 520 KB SRAM + 4 MB PSRAM |
| Flash Storage | 4 MB |
| WiFi | 802.11 b/g/n, 2.4 GHz |
| Max Frame Size | UXGA (1600x1200) |
| Supported Sizes | QVGA, VGA, SVGA, UXGA |
| JPEG Quality Range | 0-63 (10 used) |
| Video Format | MJPEG over HTTP |
| Power Supply | 5 V DC, 1 A nominal |
| Operating Temperature | 0-40 C |

---
