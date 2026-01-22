# Contributing to ESP32-CAM Wireless Streaming

Thank you for your interest in contributing! This document provides guidelines and instructions for contributing to the project.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/ESP32-CAM-Wireless-Streaming.git
   cd ESP32-CAM-Wireless-Streaming
   ```
3. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Development Setup

### Hardware Requirements
- ESP32-CAM AI Thinker module
- FTDI FT232RL USB-Serial programmer
- External 5V / 1A power supply
- 470 µF electrolytic capacitor

### Software Requirements
- Arduino IDE 1.8.16 or later
- ESP32 board support (install via Board Manager)
- USB-Serial drivers (CH340 or FTDI)

## Code Style Guidelines

- **C++ Code**: Follow Arduino style guidelines
- **Naming Conventions**:
  - Functions: `camelCase()`
  - Variables: `camelCase`
  - Constants: `UPPER_SNAKE_CASE`
  - Classes: `PascalCase`

- **Comments**: Document complex logic clearly
- **Line Length**: Keep lines under 100 characters when possible

## Testing Before Submission

1. **Hardware Testing**:
   - Test on physical ESP32-CAM board
   - Verify camera initialization (0x105 error resolution)
   - Test WiFi connectivity with 2.4 GHz only
   - Confirm 25-30 FPS at QVGA resolution

2. **Documentation**:
   - Update README.md if adding features
   - Add troubleshooting entries for known issues
   - Update relevant docs/ files

## Submitting Changes

1. **Commit Messages**:
   ```
   Type: Brief description (max 50 chars)

   Detailed explanation if needed. Keep to 72 characters per line.
   Reference issues: Fixes #123
   ```
   Types: `fix:`, `feat:`, `docs:`, `test:`, `refactor:`, `perf:`

2. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

3. **Create a Pull Request**:
   - Title: Clear, concise description
   - Description: Explain what changed and why
   - Link related issues
   - Include testing details

## Pull Request Checklist

- [ ] Code follows project style guidelines
- [ ] Comments and documentation added
- [ ] README.md updated (if needed)
- [ ] Tested on physical hardware
- [ ] No new warnings or errors introduced
- [ ] Commits are clean and well-described

## Reporting Issues

When reporting bugs, include:
- **Hardware**: ESP32-CAM model and power setup
- **Software**: Arduino IDE version, ESP32 core version
- **Error**: Full error message or unexpected behavior
- **Reproduction**: Steps to reproduce the issue
- **Logs**: Serial monitor output (if applicable)

## Feature Requests

For feature requests, describe:
- **Use Case**: Why is this feature needed?
- **Implementation**: Suggested approach (if any)
- **Impact**: Potential changes or breaking changes

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

## Questions?

Feel free to open an issue or discussion for clarification.

---

Thank you for contributing!
