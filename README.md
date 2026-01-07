# ESP32-S3-Box-3 Custom Voice Assistant Display

This repository contains **custom ESPHome configuration files** for the **ESP32-S3-Box-3**, designed for use as a **Home Assistant Voice Assistant satellite**.

The goal of this project is to provide a **clean, minimal, and informative display** by removing unnecessary UI elements and adding useful, always-visible information when the device is idle.

---

## ✨ Features

### 🧼 Clean Display Layout
- Removes the default **top and bottom text boxes (bubbles)**
- Uses **full-screen custom illustrations** for all voice assistant states
- Clean, distraction-free interface designed for wall or desk placement

---

### 🕒 Idle Screen (Clock & Temperature)
When the voice assistant is idle, the display shows:
- A **large, centered digital clock**
- **Indoor temperature** pulled directly from Home Assistant
- Optional **blinking colon**
- Optional **AM/PM indicator** (12-hour mode only)

The display automatically returns to this screen after voice interactions complete.

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

## 📁 Available Configuration Files

> ⚠️ **Important:**  
> These YAML files are **ESPHome package files**, not complete standalone device configurations.  
> They must be **included in or merged with your main ESP32-S3-Box-3 ESPHome YAML** and may require editing before compiling.

### 1️⃣ `esp32-s3-box-3.yaml` — Minimal / Clean Display
- Removes top and bottom text bubbles
- Uses full-screen illustrations only
- No clock or temperature display

**Best for:** users who want a clean, image-only voice assistant display.

---

### 2️⃣ `esp32-s3-box-3_clock.yaml` — Clock & Temperature Display
Includes everything from the minimal version, plus:
- Large idle clock
- Indoor temperature display
- 12h / 24h toggle
- AM/PM toggle (12h mode only)
- Blinking colon with no layout shifting

**Best for:** users who want a useful always-on clock and status display.

---

## 📊 Feature Comparison

| Feature | Minimal | Clock |
|------|--------|-------|
| Removes text bubbles | ✅ | ✅ |
| Full-screen illustrations | ✅ | ✅ |
| Idle clock | ❌ | ✅ |
| Indoor temperature | ❌ | ✅ |
| 12h / 24h toggle | ❌ | ✅ |
| AM/PM toggle | ❌ | ✅ |
| Blinking colon | ❌ | ✅ |

---

## 🤔 Which Should I Choose?

- Choose **Minimal** if you want the cleanest possible display with no extra configuration.
- Choose **Clock** if you want the device to double as a smart clock and information display.

If you are unsure, **start with the clock version** — it can always be changed later.

---

## 📸 Screenshots

<p align="center">
  <img src="images/idle.jpg" width="45%">
  <img src="images/listening.jpg" width="45%">
</p>
<p align="center"><em>Idle Screen (Clock & Indoor Temperature) • Listening</em></p>

<p align="center">
  <img src="images/thinking.jpg" width="45%">
  <img src="images/speaking.jpg" width="45%">
</p>
<p align="center"><em>Thinking • Speaking / Replying</em></p>

---

## 🚀 Quick Start Guide

### Requirements
- ESP32-S3-Box-3
- Home Assistant
- ESPHome installed in Home Assistant
- Existing Home Assistant temperature sensor  
  *(example: `sensor.average_indoor_temperature`)*

---

### Step 1: Choose a Configuration File
- `esp32-s3-box-3.yaml` → clean display only
- `esp32-s3-box-3_clock.yaml` → clock + temperature

---

### Step 2: Add the Package to ESPHome
Reference the file from your main ESPHome device YAML:

```yaml
packages:
  s3_box:
    url: github://YOUR_USERNAME/YOUR_REPO/esp32-s3-box-3_clock.yaml@<commit_sha>
```

---

### Step 3: Edit Before Compiling (Clock Version Only)

```yaml
sensor:
  - platform: homeassistant
    id: avg_indoor_temp
    entity_id: sensor.average_indoor_temperature
    internal: true
```

Replace the entity ID with your own sensor.

---

### Step 4: Compile and Upload
- Click **Install**
- Upload firmware
- Wait for reboot

---

### Step 5: Optional Clock Settings
After flashing, Home Assistant will expose:
- 12h / 24h toggle
- AM/PM toggle

These apply instantly and require no reflashing.

---

## 🛠 Notes & Tips
- Screen dimming is best handled using Home Assistant automations
- Layout prevents jitter when the colon blinks
- Optimized for readability from a distance

---

## 📄 License
Provided as-is for personal and educational use.
