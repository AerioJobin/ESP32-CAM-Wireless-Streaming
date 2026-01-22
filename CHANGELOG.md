# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Planned
- OTA (Over-The-Air) firmware updates
- mDNS hostname support (`esp32cam.local`)
- HTTPS/TLS encryption for streaming
- Motion detection with PIR sensor
- Event-triggered recording to SD card
- JSON telemetry endpoint
- Advanced WiFi credential management
- Multi-resolution streaming profiles

---

## [1.0.0] - 2026-01-22

### Added
- Initial ESP32-CAM wireless streaming system release
- MJPEG video streaming over HTTP (25-30 FPS at QVGA)
- Web-based control interface for camera settings
- Resolution switching (QVGA, VGA, SVGA, UXGA)
- Brightness, contrast, and saturation adjustment
- WiFi station-mode connectivity with timeout handling
- PSRAM-enabled double buffering for smooth streaming
- Serial debug diagnostics for WiFi and camera status
- Power-optimized firmware with brownout mitigation
- Professional documentation suite (8 markdown files)
- Contribution guidelines and code of conduct
- MIT License

### Documentation
- README.md with quick start and troubleshooting
- docs/overview.md - Executive summary
- docs/hardware.md - Hardware architecture and wiring
- docs/software.md - Firmware configuration
- docs/troubleshooting.md - Issue resolution with root causes
- docs/performance.md - Metrics and specifications
- docs/lessons-learned.md - Best practices and recommendations
- docs/project-documentation.md - Development timeline
- CONTRIBUTING.md - Contribution guidelines
- CHANGELOG.md - Version history
- .gitignore - Arduino/ESP32 exclusions

### Hardware Support
- ESP32-CAM AI Thinker module
- OV2640 2MP camera sensor
- External 5V/1A power supply
- 470 µF power smoothing capacitor
- FTDI FT232RL USB-Serial programmer

### Fixed
- Resolved camera initialization failure (0x105 ESP_ERR_NOT_FOUND) via external power
- Fixed boot mode 0x13 errors through GPIO0 release timing
- WiFi connectivity issues with 2.4 GHz-only networks
- Brownout events through capacitor and power optimization
- Upload failures via consistent programming ritual documentation

### Known Limitations
- WiFi: 2.4 GHz only (no 5 GHz support)
- Range: ~30 m indoor with internal antenna
- Frame rate: 12-30 FPS depending on resolution
- Latency: 300-500 ms over WiFi
- Storage: 4 MB flash, 4 MB PSRAM

---

## Future Roadmap

### Version 1.1 (Planned Q2 2026)
- [ ] OTA firmware updates
- [ ] mDNS support
- [ ] Motion detection

### Version 2.0 (Planned Q3 2026)
- [ ] HTTPS/TLS support
- [ ] Multiple camera support
- [ ] Cloud integration
- [ ] Mobile app

---

## How to Contribute

See [CONTRIBUTING.md](CONTRIBUTING.md) for development guidelines and submission process.

## License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.
