# 🌊 Smart Water Flow Meter - STM32 IoT Device

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/horizonhnk/smart-water-flow-meter)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![STM32](https://img.shields.io/badge/STM32-F4xx-blue.svg)](https://www.st.com/en/microcontrollers-microprocessors/stm32f4-series.html)
[![IoT](https://img.shields.io/badge/IoT-Enabled-green.svg)](https://github.com/horizonhnk/smart-water-flow-meter)

> **An intelligent water consumption and flow-rate monitoring system designed for accurate billing, remote monitoring, and water management optimization.**

## 📺 YouTube Tutorial Series

🎥 **Complete Build Tutorial:** [Smart Water Meter Project Playlist](https://www.youtube.com/playlist?list=PLrZbkNpNVSww9A7tyf1CkCTiHRaKb9gtL)

*Follow along with our comprehensive video series covering everything from component selection to final deployment!*

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Hardware Requirements](#-hardware-requirements)
- [Software Requirements](#-software-requirements)
- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Circuit Diagram](#-circuit-diagram)
- [Configuration](#-configuration)
- [API Documentation](#-api-documentation)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## 🎯 Overview

The **Smart Water Flow Meter** is an innovative IoT-based solution designed to accurately measure water consumption and flow rates in real-time. Built around the powerful STM32 microcontroller, this device provides:

### 🎭 Problem Statement
> Traditional water meters lack real-time monitoring capabilities and precise flow control, leading to inefficient water management and billing disputes.

### 🎯 Solution
Our device addresses these challenges by providing:
- **Real-time monitoring** of water consumption and flow rates
- **Remote access** via web interface and mobile connectivity
- **Precise billing** with accurate measurement capabilities
- **Flow control** from zero to maximum capacity
- **Data logging** for historical analysis and optimization

---

## ✨ Features

### 📊 Core Functionality
- [x] **Accurate Measurement**: Precise water consumption tracking in liters
- [x] **Flow Rate Monitoring**: Real-time flow rate measurement in L/min
- [x] **Flow Control**: Adjustable flow control from 0% to 100%
- [x] **Touch Interface**: Intuitive touchscreen display for local control
- [x] **Web Dashboard**: Remote monitoring via web server interface
- [x] **Data Logging**: Historical consumption data storage
- [x] **Mobile Connectivity**: Smartphone app integration
- [x] **Alert System**: Configurable alerts for unusual consumption patterns

### 🌐 IoT Capabilities
- [x] **WiFi Connectivity**: Wireless data transmission
- [x] **Cloud Integration**: Data sync with cloud platforms
- [x] **RESTful API**: Easy integration with existing systems
- [x] **MQTT Protocol**: Lightweight IoT communication
- [x] **Real-time Updates**: Live data streaming

### 🔧 Technical Features
- [x] **STM32 Powered**: High-performance ARM Cortex-M4 processor
- [x] **Low Power Mode**: Energy-efficient operation
- [x] **Calibration System**: Self-calibrating sensors for accuracy
- [x] **Expandable Design**: Modular architecture for future upgrades

---

## 🛠 Hardware Requirements

### 📦 Core Components

| Component | Model/Specification | Quantity | Purpose |
|-----------|-------------------|----------|---------|
| **Microcontroller** | STM32F4xx Series | 1 | Main processing unit |
| **Flow Sensor** | YF-S201 Water Flow Sensor | 1 | Flow rate measurement |
| **Display** | 3.5" TFT Touchscreen | 1 | User interface |
| **WiFi Module** | ESP8266/ESP32 | 1 | Internet connectivity |
| **Solenoid Valve** | 12V DC Water Valve | 1 | Flow control |
| **Power Supply** | 12V/2A Adapter | 1 | System power |
| **Enclosure** | IP65 Waterproof Box | 1 | Protection |

### 🔌 Additional Components

```
📋 Shopping List:
├── Resistors: 10kΩ, 4.7kΩ, 1kΩ (5 each)
├── Capacitors: 100nF, 10µF, 22pF (3 each)
├── LEDs: Status indicators (3x)
├── Push Buttons: Reset, Config (2x)
├── PCB: Custom PCB or breadboard
├── Connectors: Terminal blocks, headers
└── Cables: Jumper wires, power cables
```

---

## 💻 Software Requirements

### 🖥 Development Environment

```bash
# Required Software
STM32CubeIDE     # Version 1.8.0 or later
STM32CubeMX      # Code generation tool
Git              # Version control
Node.js          # For web interface (v16+)
Python           # For data analysis scripts (3.8+)
```

### 📚 Libraries & Dependencies

#### STM32 Libraries
```c
// Core STM32 Libraries
#include "stm32f4xx_hal.h"
#include "main.h"
#include "gpio.h"
#include "usart.h"
#include "tim.h"
#include "adc.h"

// Custom Libraries
#include "flow_sensor.h"
#include "display_driver.h"
#include "wifi_handler.h"
#include "data_logger.h"
```

#### Web Interface Dependencies
```json
{
  "dependencies": {
    "express": "^4.18.0",
    "socket.io": "^4.5.0",
    "chart.js": "^3.8.0",
    "bootstrap": "^5.2.0",
    "axios": "^0.27.0"
  }
}
```

---

## 🚀 Quick Start

### ⚡ 5-Minute Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/smart-water-flow-meter.git
   cd smart-water-flow-meter
   ```

2. **Open in STM32CubeIDE**
   ```bash
   # Import existing project
   File → Import → General → Existing Projects
   ```

3. **Configure hardware connections**
   ```
   Flow Sensor → Pin PA0 (Timer Input)
   Display SPI → Pins PB13-15
   WiFi UART  → Pins PA9-10
   Valve PWM  → Pin PC6
   ```

4. **Build and flash**
   ```bash
   # Build project
   Ctrl + B
   
   # Flash to STM32
   Run → Debug (F11)
   ```

5. **Access web interface**
   ```
   http://192.168.1.100:8080
   ```

---

## 📥 Installation

### 🔧 Step-by-Step Setup

#### 1. Hardware Assembly

> **⚠️ Safety First**: Always disconnect power when making connections

```
Connection Guide:
┌─────────────────┐    ┌─────────────────┐
│   STM32F4xx     │    │   Flow Sensor   │
│                 │    │                 │
│ PA0 ────────────┼────┤ Signal (Yellow) │
│ 5V  ────────────┼────┤ VCC (Red)       │
│ GND ────────────┼────┤ GND (Black)     │
└─────────────────┘    └─────────────────┘
```

#### 2. Software Installation

```bash
# 1. Clone repository
git clone https://github.com/yourusername/smart-water-flow-meter.git

# 2. Initialize submodules
git submodule update --init --recursive

# 3. Install web dependencies
cd web_interface
npm install

# 4. Setup Python environment
cd ../scripts
pip install -r requirements.txt
```

#### 3. Configuration

```bash
# Copy configuration template
cp config/config_template.h config/config.h

# Edit WiFi credentials
nano config/config.h
```

```c
// config/config.h
#define WIFI_SSID "YourWiFiNetwork"
#define WIFI_PASSWORD "YourPassword"
#define SERVER_PORT 8080
#define FLOW_CALIBRATION_FACTOR 7.5  // Pulses per liter
```

---

## 🎮 Usage

### 📱 Local Interface (Touchscreen)

The device features an intuitive touchscreen interface:

```
┌─────────────────────────────────┐
│     SMART WATER METER v2.1      │ 
├─────────────────────────────────┤
│ Current Flow: 5.2 L/min         │
│ Total Consumed: 1,247 L         │
│ Daily Usage: 89 L               │
│ Cost Today: $2.34               │
├─────────────────────────────────┤
│ [Settings] [History] [Control]  │
└─────────────────────────────────┘
```

### 🌐 Web Dashboard

Access the web interface at `http://[device-ip]:8080`

#### Main Dashboard Features:
- **Real-time Monitoring**: Live flow rate and consumption data
- **Historical Charts**: Consumption trends and patterns
- **Control Panel**: Remote valve control and settings
- **Alerts**: Configurable notifications and alerts
- **Reports**: Downloadable consumption reports

### 📊 API Endpoints

```javascript
// Get current readings
GET /api/current
{
  "flowRate": 5.2,
  "totalConsumption": 1247.5,
  "timestamp": "2025-05-30T10:30:00Z"
}

// Control valve
POST /api/valve/control
{
  "action": "open",      // "open", "close", "set"
  "position": 75         // 0-100% (for "set" action)
}

// Get historical data
GET /api/history?period=week
{
  "data": [
    {"date": "2025-05-24", "consumption": 125.3},
    {"date": "2025-05-25", "consumption": 98.7}
  ]
}
```

---

## 📁 Project Structure

```
smart-water-flow-meter/
├── 📁 Core/                    # STM32 Core files
│   ├── 📁 Inc/                 # Header files
│   │   ├── main.h
│   │   ├── flow_sensor.h
│   │   └── display_driver.h
│   └── 📁 Src/                 # Source files
│       ├── main.c
│       ├── flow_sensor.c
│       └── display_driver.c
├── 📁 Drivers/                 # HAL drivers
│   ├── 📁 STM32F4xx_HAL_Driver/
│   └── 📁 CMSIS/
├── 📁 Middlewares/             # Third-party libraries
│   ├── 📁 ST/
│   └── 📁 Third_Party/
├── 📁 web_interface/           # Web dashboard
│   ├── 📁 public/
│   │   ├── index.html
│   │   ├── style.css
│   │   └── script.js
│   ├── 📁 server/
│   │   ├── server.js
│   │   └── api.js
│   └── package.json
├── 📁 mobile_app/              # Mobile application
│   ├── 📁 android/
│   └── 📁 ios/
├── 📁 hardware/                # Circuit designs
│   ├── schematic.pdf
│   ├── pcb_layout.pdf
│   └── bill_of_materials.xlsx
├── 📁 docs/                    # Documentation
│   ├── user_manual.pdf
│   ├── installation_guide.pdf
│   └── api_reference.md
├── 📁 scripts/                 # Utility scripts
│   ├── calibration.py
│   ├── data_export.py
│   └── requirements.txt
├── 📁 tests/                   # Test files
│   ├── unit_tests/
│   └── integration_tests/
├── .gitignore
├── README.md
├── LICENSE
└── CHANGELOG.md
```

---

## 🔌 Circuit Diagram

### 📋 Main Circuit Schematic

```
                    STM32F4xx Development Board
                    ┌─────────────────────────┐
                    │                         │
    Flow Sensor ────┤ PA0 (TIM2_CH1)         │
    (YF-S201)       │                         │
                    │                         │
    Display CS  ────┤ PB12                   │
    Display CLK ────┤ PB13 (SPI2_SCK)       │
    Display MOSI────┤ PB15 (SPI2_MOSI)      │
    Display DC  ────┤ PB14                   │
    Display RST ────┤ PB11                   │
                    │                         │
    WiFi RX     ────┤ PA9  (USART1_TX)      │
    WiFi TX     ────┤ PA10 (USART1_RX)      │
                    │                         │
    Valve Control───┤ PC6  (TIM3_CH1)       │
                    │                         │
    Status LED  ────┤ PC13                   │
                    └─────────────────────────┘
```

### ⚡ Power Distribution

```
Power Supply (12V/2A)
├── STM32 Board (5V regulated)
├── Display Module (3.3V)
├── WiFi Module (3.3V)
├── Flow Sensor (5V)
└── Solenoid Valve (12V)
```

---

## ⚙ Configuration

### 📝 Configuration File Template

```c
// config/config.h
#ifndef CONFIG_H
#define CONFIG_H

// Network Configuration
#define WIFI_SSID "YourNetworkName"
#define WIFI_PASSWORD "YourNetworkPassword"
#define SERVER_PORT 8080
#define MQTT_BROKER "mqtt.example.com"
#define MQTT_PORT 1883

// Sensor Calibration
#define FLOW_SENSOR_CALIBRATION 7.5f    // Pulses per liter
#define FLOW_SENSOR_TIMEOUT 5000        // ms
#define MIN_FLOW_RATE 0.1f              // L/min
#define MAX_FLOW_RATE 30.0f             // L/min

// Display Settings
#define DISPLAY_BRIGHTNESS 80           // 0-100%
#define SCREEN_TIMEOUT 30               // seconds
#define UI_REFRESH_RATE 500             // ms

// Data Logging
#define LOG_INTERVAL 60                 // seconds
#define MAX_LOG_ENTRIES 1000
#define ENABLE_CLOUD_SYNC 1

// Alert Thresholds
#define HIGH_FLOW_ALERT 20.0f           // L/min
#define DAILY_LIMIT_ALERT 500.0f        // L/day
#define LEAK_DETECTION_THRESHOLD 0.5f   // L/min for 30min

#endif // CONFIG_H
```

### 🎛 Calibration Procedure

> **Important**: Proper calibration ensures accurate measurements

```bash
# Run calibration script
python scripts/calibration.py

# Follow the prompts:
# 1. Measure exactly 10 liters through the system
# 2. Record the pulse count
# 3. Calculate calibration factor
# 4. Update config.h with new value
```

---

## 📖 API Documentation

### 🔄 Real-time Data Endpoints

#### Get Current Status
```http
GET /api/status
```

**Response:**
```json
{
  "status": "ok",
  "timestamp": "2025-05-30T10:30:00Z",
  "data": {
    "flowRate": 5.2,
    "totalConsumption": 1247.5,
    "dailyConsumption": 89.3,
    "valvePosition": 100,
    "temperature": 23.5,
    "pressure": 2.1
  }
}
```

#### Control Valve
```http
POST /api/valve/control
Content-Type: application/json

{
  "action": "set",
  "position": 75
}
```

#### Get Historical Data
```http
GET /api/history?period=week&interval=hour
```

### 🔔 WebSocket Events

```javascript
// Connect to WebSocket
const socket = io('http://192.168.1.100:8080');

// Listen for real-time updates
socket.on('flowUpdate', (data) => {
  console.log('Flow Rate:', data.flowRate);
  console.log('Total:', data.totalConsumption);
});

// Listen for alerts
socket.on('alert', (alert) => {
  console.log('Alert:', alert.message);
  console.log('Type:', alert.type);
});
```

---

## 🐛 Troubleshooting

### ❌ Common Issues

#### Flow Sensor Not Reading
```bash
# Check connections
# Verify power supply (5V)
# Test with multimeter
# Check configuration in config.h

# Debug output:
Serial.println("Flow sensor pulse count: " + String(pulseCount));
```

#### WiFi Connection Issues
```bash
# Verify credentials in config.h
# Check signal strength
# Reset WiFi module
# Monitor debug output:

Serial.println("WiFi Status: " + String(WiFi.status()));
Serial.println("IP Address: " + WiFi.localIP().toString());
```

#### Display Not Working
```bash
# Check SPI connections
# Verify power (3.3V)
# Test with simple graphics
# Check CS, DC, RST pins
```

### 🔍 Debug Mode

Enable debug mode by adding to `config.h`:
```c
#define DEBUG_MODE 1
#define DEBUG_SERIAL_BAUD 115200
```

### 📞 Support Channels

> 💡 **Need Help?** Check these resources:

- 📺 [Video Tutorials](https://www.youtube.com/playlist?list=PLrZbkNpNVSww9A7tyf1CkCTiHRaKb9gtL)
- 📖 [Documentation Wiki](https://github.com/horizonhnk/smart-water-flow-meter/wiki)
- 💬 [Discussion Forum](https://github.com/horizonhnk/smart-water-flow-meter/discussions)
- 🐛 [Issue Tracker](https://github.com/horizonhnk/smart-water-flow-meter/issues)

---

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### 🎯 How to Contribute

1. **Fork the repository**
   ```bash
   git fork https://github.com/yourusername/smart-water-flow-meter.git
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/awesome-new-feature
   ```

3. **Make your changes**
   ```bash
   # Make your improvements
   git add .
   git commit -m "Add awesome new feature"
   ```

4. **Push and create PR**
   ```bash
   git push origin feature/awesome-new-feature
   # Create Pull Request on GitHub
   ```

### 📋 Contribution Guidelines

- ✅ Follow existing code style
- ✅ Add tests for new features
- ✅ Update documentation
- ✅ Add comments for complex logic
- ✅ Test on real hardware when possible

### 🏆 Contributors

Thanks to these amazing people:

<table>
  <tr>
    <td align="center">
      <a href="#">
        <img src="https://github.com/github.png" width="100px;" alt=""/>
        <br /><sub><b>Your Name</b></sub>
      </a>
    </td>
    <!-- Add more contributors -->
  </tr>
</table>

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 Smart Water Flow Meter Project

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software...
```

---

## 📞 Contact

### 🌐 Project Links

- **GitHub Repository**: [Smart Water Flow Meter](https://github.com/horizonhnk/smart-water-flow-meter)
- **YouTube Channel**: [SmartFlow Tech](https://www.youtube.com/playlist?list=PLrZbkNpNVSww9A7tyf1CkCTiHRaKb9gtL)
- **Documentation**: [Wiki](https://github.com/horizonhnk/smart-water-flow-meter/wiki)

### 👥 Team

**Project Lead**: Your Name  
📧 Email: hhnk3693@gmail.com  

**Institution**: Cape Peninsula University of Technology  
🏫 Department: Engineering & Technology

---

## 🙏 Acknowledgments

- Cape Peninsula University of Technology for project support
- STMicroelectronics for excellent development tools
- Open-source community for libraries and inspiration
- YouTube community for feedback and suggestions

---

## 🔄 Changelog

### v2.1.0 (2025-05-30)
- ✅ Added mobile app integration
- ✅ Improved calibration system  
- ✅ Enhanced web dashboard
- 🐛 Fixed WiFi reconnection issues

### v2.0.0 (2025-05-15)
- ✅ Complete rewrite with STM32F4
- ✅ Added touchscreen interface
- ✅ Implemented flow control
- ✅ Added cloud connectivity

### v1.0.0 (2025-04-01)
- 🎉 Initial release
- ✅ Basic flow measurement
- ✅ Simple web interface

---

<div align="center">

### ⭐ If you found this project helpful, please give it a star!

[![GitHub stars](https://img.shields.io/github/stars/horizonhnk/smart-water-flow-meter.svg?style=social&label=Star)](https://github.com/horizonhnk/smart-water-flow-meter)
[![GitHub forks](https://img.shields.io/github/forks/horizonhnk/smart-water-flow-meter.svg?style=social&label=Fork)](https://github.com/horizonhnk/smart-water-flow-meter/fork)

**Made with ❤️ by the SmartFlow Tech Team**

</div>
