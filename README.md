# 🚗 Autonomous Arduino Car with Object Detection and Avoidance

An IoT-based autonomous vehicle built with **Arduino Uno** that detects obstacles in real-time using ultrasonic sensors and intelligently navigates around them — no human input required.

> **Module:** CS5068NI – Cloud Computing & IoT  
> **Institution:** Islington College (London Metropolitan University)  
> **Team:** Manita Basnet, Krish Shrestha, Mohammad Masood Siddiqui, Kushal Maharjan, Mishan Katuwal Chhetri

---

## 📌 Project Overview

This project demonstrates IoT principles in action by combining sensor input, microcontroller processing, and motor control to build a self-navigating car. When an obstacle is detected within 20 cm, the car stops, scans left and right using a servo-mounted ultrasonic sensor, and turns toward the clearer path.

---

## 🛠️ Hardware Components

| Component | Purpose |
|---|---|
| Arduino Uno (ATmega328P) | Central processing unit |
| HC-SR04 Ultrasonic Sensor | Obstacle detection & distance measurement |
| L293D Motor Driver Shield | Controls speed and direction of DC motors |
| 4x TT DC Motors | Locomotion (forward, backward, turn) |
| Servo Motor (SG90) | Rotates ultrasonic sensor for left/right scanning |
| Jumper Wires | Electrical connections between components |
| SPDT Switch | Manual power on/off control |
| 2x Lithium Batteries | Power supply (optimal configuration) |
| Wheels + Sunboard Chassis | Physical frame and mobility |

---

## 💻 Software & Tools

- **Arduino IDE** — Code development and upload
- **Fritzing** — Circuit and schematic diagram design

### Libraries Used
```cpp
#include <AFMotor.h>    // Motor control via Adafruit Motor Shield
#include <NewPing.h>    // Ultrasonic sensor distance reading
#include <Servo.h>      // Servo motor control
```

---

## ⚙️ Circuit Connections

### Ultrasonic Sensor → Motor Driver Shield
| Sensor Pin | Connects To |
|---|---|
| VCC | +5V on motor driver shield |
| GND | GND on motor driver shield |
| TRIG | Analog Pin A0 |
| ECHO | Analog Pin A1 |

### Motors → Motor Driver Shield
| Motor | Port |
|---|---|
| Motor 1 | M1 |
| Motor 2 | M2 |
| Motor 3 | M3 |
| Motor 4 | M4 |

### Servo Motor
- Connected to **SERVO1** port on the motor driver shield

---

## 🔄 How It Works

```
Start
  │
  ▼
Measure distance ahead
  │
  ├── Distance > 20cm? ──► Keep moving forward
  │
  └── Distance ≤ 20cm?
        │
        ▼
      Stop → Move backward → Stop
        │
        ▼
      Scan RIGHT (servo to 50°) → measure distance
      Scan LEFT  (servo to 170°) → measure distance
      Reset servo to 115°
        │
        ├── Right > Left? ──► Turn Right
        └── Left ≥ Right? ──► Turn Left
              │
              ▼
           Keep moving
```

---

## 🚀 Getting Started

### Prerequisites
- Arduino IDE installed ([download here](https://www.arduino.cc/en/software))
- Install the following libraries via Arduino Library Manager:
  - `AFMotor` (Adafruit Motor Shield library)
  - `NewPing`
  - `Servo` (built-in)

### Upload Instructions
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/autonomous-arduino-obstacle-avoidance-car.git
   ```
2. Open `obstacle_avoidance.ino` in Arduino IDE
3. Connect Arduino Uno to your PC via USB
4. Select the correct **Board** (`Arduino Uno`) and **Port** in Arduino IDE
5. Click **Upload**
6. Disconnect USB, connect battery pack, flip the switch — the car is live!

---

## 🧪 Testing Summary

| Test | Objective | Result |
|---|---|---|
| Test 1 | Code compiles and uploads successfully | ✅ Passed |
| Test 2 | Ultrasonic sensor detects obstacles | ✅ Passed |
| Test 3 | Motors rotate correctly | ✅ Passed |
| Test 4 | Servo motor moves and holds position | ✅ Passed |
| Test 5 | Motor driver shield supplies power | ✅ Passed |
| Test 6 | Optimal battery configuration found | ⚠️ 2 batteries required (3–4 caused overheating) |

> **Key Finding:** Using 3 or 4 lithium batteries caused wires to overheat and melt due to excess current draw. **2 lithium batteries** is the stable and safe operating configuration.

---

## 🔮 Future Improvements

- Integrate **AI-powered camera** for smarter object/person recognition
- Build a **mobile app** for remote monitoring and control (battery status, start/stop, alerts)
- Add **LIDAR or infrared sensors** for improved detection accuracy
- Implement **self-parking and auto-tracking** features
- Optimize motor efficiency for lower energy consumption

---

## 📁 Repository Structure

```
autonomous-arduino-obstacle-avoidance-car/
├── src/
│   └── obstacle_avoidance.ino   # Main Arduino sketch
├── diagrams/
│   ├── circuit_diagram.png      # Fritzing circuit layout
│   ├── schematic_diagram.png    # Schematic diagram
│   ├── block_diagram.png        # System block diagram
│   └── flowchart.png            # Logic flowchart
├── docs/
│   └── report.pdf               # Full project report
└── README.md
```

---

## 👥 Team Contributions

| Member | Contributions |
|---|---|
| Manita Basnet | Introduction, development, formatting, device integration, testing |
| Krish Shrestha | System architecture, schematic diagram, coding, debugging |
| Mohammad Masood Siddiqui | Requirement analysis, hardware/software evaluation, future works |
| Mishan Katuwal Chhetri | Abstract, acknowledgement, hardware evaluation, resource management |
| Kushal Maharjan | Conclusion, project design, flowchart, review, resource management |

---

## 📄 License

This project was developed for academic purposes at Islington College. Feel free to use it as a reference for learning.
