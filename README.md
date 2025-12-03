# 🏠 Maker Faire Smart Home Demo Project

<p align="center">
  <img src="https://img.shields.io/badge/Platform-ESPHome-blue?style=for-the-badge&logo=esphome" />
  <img src="https://img.shields.io/badge/Integration-Home%20Assistant-41BDF5?style=for-the-badge&logo=home-assistant" />
  <img src="https://img.shields.io/badge/Hardware-Seeed%20Studio-green?style=for-the-badge" />
</p>

> 🎪 **A complete smart home demo system built for Maker Faire!**
> 
> A full-featured smart home solution built with Seeed Studio XIAO ESP32 series development boards + ESPHome + Home Assistant.

---

## ✨ Project Highlights

- 🎯 **Plug and Play** - All configurations ready to use, easy to flash
- 🌈 **Feature Rich** - Covers smart lighting, environmental monitoring, health monitoring, and more
- 📊 **Visual Dashboard** - Beautiful e-paper data center + Home Assistant control panel
- 🌐 **Bilingual Support** - Chinese and English Dashboard configurations included
- 🔧 **Highly Customizable** - Modular design for easy secondary development

---

## 🎁 Device List

| Device | Chip | Function | File |
|--------|------|----------|------|
| 📷 **[XIAO ESP32-S3 Sense Camera](https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html)** | ESP32-S3 | Bedroom real-time monitoring | `xiao-esp32s3-camera.yaml` |
| 🛏️ **[XIAO MR60BHA2 mmWave Radar Kit](https://www.seeedstudio.com/MR60BHA2-60GHz-mmWave-Sensor-Breathing-and-Heartbeat-Module-p-5945.html)** | ESP32-C6 | Human presence detection, heart rate & breathing monitoring | `mr60bha2.yaml` |
| 🔘 **[Seeed IoT Button](https://www.seeedstudio.com/Seeed-IoT-Button-p-6419.html)** | ESP32-C6 | Three-function wireless button (single/double/long press) | `seeed-iot-button.yaml` |
| 💨 **XIAO Gas Sensor** | [XIAO ESP32-C3](https://www.seeedstudio.com/Seeed-XIAO-ESP32C3-p-5431.html) | VOC, CO, NO₂, Ethanol detection | `xiao-esp32-c3-gas-sensor.yaml` |
| 🌈 **XIAO LED Strip Controller** | XIAO ESP32-C3 + [LED Driver Board](https://www.seeedstudio.com/LED-Driver-Board-for-Seeed-Studio-XIAO-p-6451.html) | WS2812 addressable LED strip (48 LEDs) | `xiao-esp32-c3-led-strip.yaml` |
| 🎵 **XIAO MP3 Player** | XIAO ESP32-C3 | WT2605C module, supports SD card playback | `xiao-esp32-c3-mp3.yaml` |
| 🌀 **XIAO Smart Fan** | [XIAO ESP32-C6](https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32C6-p-5884.html) | PWM speed-controlled motor | `xiao-esp32-c6-fan.yaml` |
| 💡 **XIAO LED Lighted Button** | XIAO ESP32-C6 | 3-channel illuminated button control | `xiao-esp32-c6-led-button.yaml` |
| 🌱 **[XIAO Soil Moisture Sensor](https://www.seeedstudio.com/XIAO-Soil-Sensor-p-6452.html)** | XIAO ESP32-C6 | Plant watering reminder with calibration | `xiao-soil-moisture.yaml` |
| 📺 **[reTerminal E1002](https://www.seeedstudio.com/reTerminal-E1002-p-6533.html)** | ESP32-S3 | 7.3-inch color e-paper dashboard | `reterminal-e1002.yaml` |

---

## 🚀 Quick Start

### 📋 Prerequisites

- ✅ [ESPHome](https://esphome.io/) installed (Home Assistant add-on version recommended)
- ✅ [Home Assistant](https://www.home-assistant.io/) running
- ✅ WiFi network environment
- ✅ Hardware devices listed above

### 🔧 Installation Steps

#### 1️⃣ Clone the Project

```bash
git clone https://github.com/your-repo/maker_faire_demo.git
cd maker_faire_demo
```

#### 2️⃣ Create WiFi Configuration File

Create a `secrets.yaml` file in the project directory:

```yaml
# secrets.yaml
wifi_ssid: "Your_WiFi_Name"
wifi_password: "Your_WiFi_Password"
```

#### 3️⃣ Compile and Flash

Using ESPHome command line tool:

```bash
# Compile firmware
esphome compile xiao-esp32-c3-led-strip.yaml

# Flash to device (USB connection required for first time)
esphome upload xiao-esp32-c3-led-strip.yaml

# Or all-in-one: run = compile + upload + logs
esphome run xiao-esp32-c3-led-strip.yaml
```

#### 4️⃣ Add to Home Assistant

After the device comes online, Home Assistant will automatically discover new devices. Navigate to:
> **Settings** → **Devices & Services** → **Integrations** → Click **Configure** for ESPHome device

---

## 📱 Detailed Device Descriptions

### 📷 XIAO ESP32-S3 Sense Camera

Ultra-compact WiFi camera solution!

```yaml
# Key Features
- PSRAM support (OCTAL mode, 80MHz)
- Automatic image flip
- Real-time video streaming to Home Assistant
```

**🔌 Wiring**: No additional wiring needed, uses onboard OV2640 camera

---

### 🛏️ MR60BHA2 mmWave Radar

60GHz mmWave radar, contactless health monitoring technology!

```yaml
# Detection Capabilities
- 👤 Human presence detection
- 📏 Target distance measurement
- ❤️ Real-time heart rate monitoring
- 🌬️ Real-time respiratory rate monitoring
- 💡 Ambient illuminance (BH1750)
- 🌈 RGB indicator light
```

**🔌 Wiring**:
| MR60BHA2 | ESP32-C6 |
|----------|----------|
| RX | GPIO17 |
| TX | GPIO16 |
| SDA | GPIO22 |
| SCL | GPIO23 |

---

### 🔘 Seeed IoT Button

One button, three ways to play! Super cool RGB light feedback!

```yaml
# Operation Methods
- Single click: Trigger switch 1 + Blink effect
- Double click: Trigger switch 2 + Flicker effect
- Long press (1-2 sec): Trigger switch 3 + Rainbow effect
```

**💡 RGB Light Effects**:
- Blink
- Rainbow
- Subtle Flicker
- Random Color

---

### 💨 XIAO Gas Sensor

Guard your air quality! Supports multiple gas detection.

```yaml
# Detection Metrics
- 🧪 VOC (Volatile Organic Compounds)
- 💀 CO (Carbon Monoxide)
- ⚠️ NO₂ (Nitrogen Dioxide)
- 🍺 Ethanol
```

**🔌 Wiring**:
| Grove Gas Sensor | ESP32-C3 |
|------------------|----------|
| SDA | GPIO6 |
| SCL | GPIO7 |

---

### 🌈 XIAO LED Strip Controller

48 WS2812 LEDs to create dreamy ambient lighting!

```yaml
# Built-in Light Effects (One-click Switch)
🔴 Pulse
🔵 Strobe
🟣 Strobe Red and Blue (Police lights)
🟢 Random
🟡 Slow Random Transition
🟠 Flicker (Candle effect)
🌈 Rainbow / Fast Rainbow
🎨 Color Wipe
✨ Twinkle / Random Twinkle
🎆 Fireworks
🔄 Automation RGB Cycle
```

**🔌 Wiring**: LED data line connects to GPIO2

---

### 🎵 XIAO MP3 Player

Smart music player based on WT2605C module!

```yaml
# Features
▶️ Play/Pause/Stop
⏮️⏭️ Previous/Next track
🔊 Volume control (0-31 levels)
🔁 Play modes: Sequential/Single loop/Folder loop/Random/Single shot

# Home Assistant Services
- play_track: Play specific track
- play_file: Play by filename
- set_volume: Set volume
- send_command: Send custom AT command
```

**🔌 Wiring**:
| WT2605C | ESP32-C3 |
|---------|----------|
| RX | GPIO21 |
| TX | GPIO20 |

**📁 SD Card Format**: Name songs as `0001.mp3`, `0002.mp3`...

---

### 🌀 XIAO Smart Fan

PWM speed-controlled motor, forward and reverse rotation with ease!

```yaml
# Control Functions
🔄 Forward (Open)
🔃 Reverse (Close)
⏹️ Stop
📊 Speed slider control (0-100%)
```

**🔌 Wiring**:
| Motor Driver | ESP32-C6 |
|--------------|----------|
| IA (Forward) | GPIO1 |
| IB (Reverse) | GPIO0 |

---

### 💡 XIAO LED Lighted Button

3-channel illuminated buttons, press to light up with clear feedback!

```yaml
# Features
- Auto-on LEDs at boot
- 2x blink feedback when pressed
- Independent control for each button
- Bindable to Home Assistant automations
```

**🔌 Wiring**:
| Button | LED(SIG1) | BTN(SIG2) |
|--------|-----------|-----------|
| Button 1 | GPIO0 | GPIO1 |
| Button 2 | GPIO19 | GPIO20 |
| Button 3 | GPIO2 | GPIO21 |

---

### 🌱 XIAO Soil Moisture Sensor

Smart plant nanny, never forget to water again!

```yaml
# Features
- 🔴 Red light: Soil dry, needs watering
- 🟡 Yellow light: Soil slightly dry, can water
- 🟢 Green light: Moisture normal

# Operation
- Single button press: Check once and flash LED indicator
- 3 consecutive button presses: Enter calibration mode
```

**📊 Calibration Process**:
1. Red LED flashes for 10 sec → Place sensor in dry soil
2. Green LED flashes for 10 sec → Place sensor in moist soil
3. Fast green flash = Calibration success ✅ / Fast red flash = Calibration failed ❌

---

### 📺 reTerminal E1002 E-Paper Display

7.3-inch color e-paper display, create your smart home data center!

```yaml
# Display Pages
📄 Page 1: Sensor Data Overview
  - Bedroom status (illuminance, distance, heart rate, respiratory)
  - Balcony plants (soil moisture, battery level)
  - Whole house power (voltage, power, current, total energy)

📄 Page 2: Switch Control
  - MP3 playback control (play/pause, previous, next)
  - LED strip control
  - Fan control
  - Living room air quality (CO, NO₂, Ethanol, VOC)

📄 Page 3: Sensor Data (Yellow Theme)
  - Bedroom status card
  - Balcony plants card
  - Whole house power large card
  - Device power consumption card
```

**🎛️ Button Operations**:
| Button | Function |
|--------|----------|
| Green key | Refresh screen (double beep feedback) |
| Right white key | Next page |
| Left white key | Previous page |

---

## 🎨 Home Assistant Dashboard

The project includes two carefully designed Dashboard configurations:

| File | Language | Description |
|------|----------|-------------|
| `chinese-dashboard.yaml` | 🇨🇳 Chinese | Complete Chinese interface |
| `english-dashboard.yaml` | 🇺🇸 English | Complete English interface |

### 📥 Import Method

1. Open Home Assistant
2. Go to **Settings** → **Dashboards**
3. Click **Add Dashboard**
4. Select **Create from YAML**
5. Copy and paste the corresponding file content

---

## 🔗 Purchase Links

| Product | Link |
|---------|------|
| XIAO ESP32-C3 | [Seeed Studio](https://www.seeedstudio.com/Seeed-XIAO-ESP32C3-p-5431.html) |
| XIAO ESP32-C6 | [Seeed Studio](https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32C6-p-5884.html) |
| XIAO ESP32-S3 Sense | [Seeed Studio](https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html) |
| MR60BHA2 Kit | [Seeed Studio](https://www.seeedstudio.com/MR60BHA2-60GHz-mmWave-Sensor-Breathing-and-Heartbeat-Module-p-5945.html) |
| reTerminal E1002 | [Seeed Studio](https://www.seeedstudio.com/reTerminal-E1002-p-6533.html) |
| Grove Gas Sensor V2 | [Seeed Studio](https://www.seeedstudio.com/Grove-Multichannel-Gas-Sensor-v2-p-4569.html) |
| Home Assistant Green | [Seeed Studio](https://www.seeedstudio.com/Home-Assistant-Green-p-5792.html) |
| 2-Channel Wi-Fi AC Energy Meter | [Seeed Studio](https://www.seeedstudio.com/XIAO-2-Channel-Wi-Fi-AC-Energy-Meter-Bundle-Kit.html) |
| IoT Button | *Coming Soon* |
| XIAO Soil Moisture Sensor | [Seeed Studio](https://www.seeedstudio.com/XIAO-Soil-Sensor-p-6452.html) |
| XIAO 2-Channel WiFi AC Relay | [Seeed Studio](https://www.seeedstudio.com/Dual-Smart-Relay-Module-for-XIAO-p-6309.html) |
| Grove RED LED Button | [Seeed Studio](https://www.seeedstudio.com/Grove-Red-LED-Button.html) |
| Grove Yellow LED Button | [Seeed Studio](https://www.seeedstudio.com/Grove-Yellow-LED-Button.html) |
| LED Driver Board | [Seeed Studio](https://www.seeedstudio.com/LED-Driver-Board-for-Seeed-Studio-XIAO-p-6451.html) |
| Grove - MP3 Module V4.0 | [Seeed Studio](https://www.seeedstudio.com/Grove-MP3-V4-p-5862.html) |
| Grove Base for XIAO | [Seeed Studio](https://www.seeedstudio.com/Grove-Shield-for-Seeeduino-XIAO-p-4621.html) |

---

## 📚 Reference Resources

- 📖 [ESPHome Official Documentation](https://esphome.io/)
- 🏠 [Home Assistant Official Documentation](https://www.home-assistant.io/docs/)
- 🌱 [Seeed Studio Wiki](https://wiki.seeedstudio.com/)
- 🎯 [MR60BHA2 ESPHome Component](https://github.com/limengdu/MR60BHA2_ESPHome_external_components)

---

## 🤝 Contributing

Issues and Pull Requests are welcome!

If this project helps you, please give it a ⭐ Star!

---

## 📄 License

MIT License - Use freely, just give credit 😊

---

<p align="center">
  <b>🎪 Made with ❤️ for Maker Faire</b>
  <br>
  <i>Making smart home accessible to everyone!</i>
</p>

