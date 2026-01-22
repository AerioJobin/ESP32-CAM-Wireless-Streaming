# Hardware Architecture

The hardware is centered on the ESP32-CAM AI Thinker module, supported by a dedicated USB-Serial programmer and a robust external power supply.

## Components

| Component | Qty | Specification | Role |
|-----------|-----|---------------|------|
| ESP32-CAM AI Thinker | 1 | ESP32, OV2640, 4 MB PSRAM | Main MCU |
| FTDI FT232RL programmer | 1 | 3.3V / 5V USB-Serial | Programming |
| External 5V supply | 1 | 5V, >=1A | Power source |
| Electrolytic capacitor | 1 | 470 uF, low ESR | Power filter |

## Pin Connections (Programming Mode)

- FTDI TX -> GPIO3 (U0R)
- FTDI RX -> GPIO1 (U0T)
- FTDI GND -> GND
- GPIO0 -> GND (upload mode only)

## Programming Sequence

1. Connect GPIO0 -> GND to force upload mode
2. Press RESET on ESP32-CAM
3. Start upload in Arduino IDE at 115200 baud
4. Wait for "Hard resetting via RTS pin"
5. Disconnect GPIO0 from GND
6. Press RESET again to boot into application

## Power Architecture

**Problem:** FTDI 5V rail provides only ~100-300 mA, insufficient for camera init and streaming. OV2640 + ESP32 can draw 500+ mA peaks.

**Solution:** External 5V / >=1A supply + 470 uF capacitor across 5V and GND near the module.

## Physical Integration

- Use short, thick power wiring to minimize voltage drop
- Provide airflow or attach small heatsink to prevent thermal throttling

---
