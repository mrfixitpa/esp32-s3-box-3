# ESP32-S3-Box-3 Custom Voice Assistant Display

This repository contains a **custom ESPHome package** for the **ESP32-S3-Box-3**, designed for use as a **Home Assistant Voice Assistant satellite**.

The goal of this project is to provide a **clean, minimal, and informative display** by removing unnecessary UI elements and adding useful, always-visible information when the device is idle.

> ✅ **Stable Release:**  
> The features described below are part of the **v1.3.0 stable release**.

---

## ✨ Features

### 🧼 Clean Display Layout
- Removes the default **top and bottom text boxes (bubbles)**
- Uses **full-screen custom illustrations** for all voice assistant states
- Clean, distraction-free interface designed for wall or desk placement

---

### 🕒 Idle Screen (Clock, Temperature & HVAC Status)
When the voice assistant is idle, the display shows:
- A **large, centered digital clock**
- **Indoor temperature** pulled directly from Home Assistant
- **HVAC system status icon**
  - 🔥 Heating (red, fixed)
  - ❄️ Cooling (blue, fixed)
  - Hidden when idle
- Optional **blinking colon**
- Optional **AM/PM indicator** (12-hour mode only)

The display automatically returns to this screen after voice interactions complete.

---

### 🎨 UI Theme Color Picker (Introduced in v1.3.0)
The ESP32-S3-Box-3 exposes a **virtual RGB light** in Home Assistant that provides a **full color wheel UI**.

- The selected color is applied to:
  - Clock text
  - AM / PM indicator
  - Indoor temperature text
- Color selection is **stored on the device** and restored after reboot
- HVAC icons are **not affected** by the theme color

> This feature is implemented **entirely in ESPHome** — no Home Assistant helpers or templates are required.

---

### 🎛 Clock Controls (No Reflash Required)
After flashing, Home Assistant exposes configuration controls:
- 12-hour / 24-hour time format toggle
- AM/PM display toggle (12-hour mode only)
- AM/PM **horizontal offset slider**
- AM/PM **vertical offset slider**

All changes apply instantly and do **not** require recompiling firmware.

---

### 🎙️ Voice Assistant Integration
When you say **“Hey Jarvis”**, the display seamlessly switches to full-screen illustrations that reflect the current state:

- **Listening**
- **Thinking**
- **Speaking / Replying**
- **Error / Not Ready**
- **Timer Finished**

Once the response is complete, the display returns to the idle clock screen.

---

## 📁 Configuration File

> ⚠️ **Important:**  
> This repository provides an **ESPHome package file**, not a complete standalone device configuration.  
> It must be **included in your main ESP32-S3-Box-3 ESPHome YAML** and requires light editing before compiling.

### `esp32-s3-box-3.yaml`
Includes:
- Bubble-free display layout
- Idle clock with temperature
- HVAC heating/cooling indicator (thermostat-agnostic)
- UI theme color picker
- Full voice assistant state illustrations
- User-adjustable clock and AM/PM settings

---

## 🖼️ Screenshots

<p align="center">
  <img src="images/idle.jpg" width="45%">
  <img src="images/listening.jpg" width="45%">
</p>
<p align="center"><em>Idle Screen (Clock, Temperature & HVAC Status) • Listening</em></p>

<p align="center">
  <img src="images/thinking.jpg" width="45%">
  <img src="images/speaking.jpg" width="45%">
</p>
<p align="center"><em>Thinking • Speaking / Replying</em></p>

---

## 🖼️ Screen Illustrations (Images)

This project uses **custom full-screen illustrations** to represent the different voice assistant states (idle, listening, thinking, speaking, error, etc.).

### Included Free Illustration Sets
This repository includes **two free, ready-to-use illustration sets** you can try immediately:

- https://github.com/mrfixitpa/esp32-s3-box-3/tree/main/illustrations

Each set contains full-screen images sized correctly for the ESP32-S3-Box-3 display and can be swapped in by updating the image substitutions in your ESPHome config.

### Image Requirements
- Resolution: **320 × 240**
- Orientation: Landscape
- Formats: `.png` or `.jpg`
- Simple, high-contrast designs recommended

---

### Where to Store Images (Home Assistant)

Upload images to:
```
/config/www/voice_assistant_images/
```

Example filenames:
```
idle.jpg
listening.jpg
thinking.jpg
speaking.jpg
error.jpg
```

Reference them in ESPHome like this:

```yaml
substitutions:
  idle_illustration_file: /local/voice_assistant_images/idle.jpg
  listening_illustration_file: /local/voice_assistant_images/listening.jpg
  thinking_illustration_file: /local/voice_assistant_images/thinking.jpg
  replying_illustration_file: /local/voice_assistant_images/speaking.jpg
```

> `/local/` maps to `/config/www/` in Home Assistant.

---

## 🚀 Quick Start Guide

### Requirements
- ESP32-S3-Box-3
- Home Assistant
- ESPHome installed in Home Assistant
- **Any Home Assistant temperature sensor**
- **Any Home Assistant climate (thermostat) entity** that exposes `hvac_action`

---

### Step 1: Add the Package to ESPHome
In your **main ESPHome device YAML**, add:

```yaml
packages:
  s3_box:
    url: github://mrfixitpa/esp32-s3-box-3/esp32-s3-box-3.yaml@v1.3.0
```

---

### Step 2: Edit Before Compiling

#### 1️⃣ Define your indoor temperature sensor
```yaml
sensor:
  - platform: homeassistant
    id: avg_indoor_temp
    entity_id: sensor.average_indoor_temperature
    internal: true
```

Replace the entity ID with any valid Home Assistant temperature sensor.

---

#### 2️⃣ Define your thermostat (HVAC status)
```yaml
text_sensor:
  - platform: homeassistant
    id: hvac_action
    entity_id: climate.your_thermostat
    attribute: hvac_action
    internal: true
```

- Used to determine heating vs cooling icons
- Icon hidden when `idle` or unavailable

---

### Step 3: Compile and Upload
- Click **Install**
- Upload firmware to the ESP32-S3-Box-3
- Wait for the device to reboot

---

## 🛠 Notes & Tips

- Screen dimming is best handled using Home Assistant automations  
  - Example automation: **ESP32-S3-Box-3 Screen Brightness Automation**  
  - https://github.com/mrfixitpa/HA-Code-and-Templates/blob/main/ESP32-S3-Box3-Screen-Brightness-Automation
- Layout prevents jitter when the colon blinks
- Designed for readability from across a room

---

## 📄 License
Provided as-is for personal and educational use.
