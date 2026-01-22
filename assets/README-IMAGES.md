# Assets - Image Placeholders

This directory is reserved for project images and diagrams.

## Expected Image Files

### 1. **wiring-diagram.png**
- Description: ESP32-CAM pin connections and FTDI programmer wiring
- Suggested Content:
  - ESP32-CAM module pinout
  - FTDI FT232RL connections
  - GPIO0 → GND connection for programming
  - Power supply connections
  - Dimensions: 800x600 px recommended

### 2. **power-setup.png**
- Description: Power supply circuit and capacitor placement
- Suggested Content:
  - 5V external power supply connection
  - 470 µF electrolytic capacitor placement
  - Voltage regulation circuit
  - Current flow diagram
  - Dimensions: 800x600 px recommended

### 3. **web-ui.png**
- Description: Screenshot of the web interface
- Suggested Content:
  - Live MJPEG stream view
  - Control sliders (resolution, brightness, contrast)
  - Frame rate display
  - WiFi status indicator
  - Dimensions: 1024x768 px recommended

### 4. **stream-preview.gif**
- Description: Animated GIF showing the streaming demo
- Suggested Content:
  - Live video stream in action
  - Resolution change demonstration
  - Frame rate smoothness
  - Duration: 3-5 seconds loop
  - Max file size: 5 MB

## How to Add Images

1. Prepare images in PNG or GIF format
2. Place in this `assets/` directory
3. Update references in `README.md` and documentation files
4. Use relative paths: `assets/image-name.png`

## Example Usage in Markdown

```markdown
![Wiring Diagram](assets/wiring-diagram.png)
![Power Setup](assets/power-setup.png)
![Web UI](assets/web-ui.png)
![Stream Preview](assets/stream-preview.gif)
```

---

*Placeholder information - replace with actual images from your project*
