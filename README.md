# ESP32-S3-Box-3 Custom Voice Assistant Display

This repository contains **custom ESPHome configuration files** for the **ESP32-S3-Box-3**, designed for use as a **Home Assistant Voice Assistant satellite**.

The goal of this project is to provide a **clean, minimal, and informative display** by removing unnecessary UI elements and adding useful, always-visible information when the device is idle.

---

## ✨ Features

### 🧼 Clean Display Layout
- Removes the default **top and bottom text boxes**
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
- **Replying**
- **Error / Not Ready**
- **Timer Finished**

Once the response is complete, the display returns to the idle clock screen.

---

### ⏱️ Clock Display Options
This project exposes easy-to-use toggles in Home Assistant:

- **12-hour / 24-hour format toggle**
- **AM/PM display toggle** (only visible in 12-hour mode)

All changes:
- Apply instantly
- Do **not** require reflashing
- Can be changed at any time

---

## 📸 Screenshots

> *(Add screenshots to an `images/` folder in this repository)*

Suggested screenshots:
- Idle screen with clock and temperature
- Listening screen
- Thinking screen
- Replying screen

Example usage:

```markdown
![Idle Clock](images/idle.jpg)
```

---

## 🚀 Quick Start Guide

### Requirements
- **ESP32-S3-Box-3**
- **Home Assistant**
- **ESPHome** installed in Home Assistant
- An existing **indoor temperature sensor** in Home Assistant  
  *(example used: `sensor.average_indoor_temperature`)*

---

### Step 1: Add the YAML to ESPHome
1. Open **ESPHome** in Home Assistant
2. Create a new device or edit your existing ESP32-S3-Box-3
3. Paste the contents of:

```text
esp32-s3-box-3_clock.yaml
```

into your ESPHome configuration  
*(or reference it using `packages:` if preferred)*

---

### Step 2: Configure the Temperature Sensor
Ensure your Home Assistant temperature sensor is defined correctly:

```yaml
sensor:
  - platform: homeassistant
    id: avg_indoor_temp
    entity_id: sensor.average_indoor_temperature
    internal: true
```

Replace `sensor.average_indoor_temperature` with your own sensor if needed.

---

### Step 3: Compile and Upload
1. Click **Install**
2. Upload the firmware to the ESP32-S3-Box-3
3. Wait for the device to reboot

Once online, the idle screen will display the clock and temperature.

---

### Step 4: Clock Display Options
After flashing, new entities appear in Home Assistant:
- Toggle **12-hour / 24-hour** time format
- Toggle **AM/PM display** *(12-hour mode only)*

These settings:
- Take effect immediately
- Do **not** require reflashing
- Can be changed at any time

---

## 🛠 Notes & Tips
- Screen dimming is best handled using **Home Assistant automations**
- The display layout prevents text shifting when the colon blinks
- Designed to remain readable from across a room
- All voice assistant states use full-screen illustrations

---

## 📄 License
This project is provided **as-is** for personal and educational use.
