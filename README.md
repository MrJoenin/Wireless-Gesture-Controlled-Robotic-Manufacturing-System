# 🦾 Wireless Gesture-Controlled Robotic Manufacturing System

> A 6-DOF robotic arm controlled wirelessly in real-time using hand gestures captured by an MPU6050 IMU and transmitted via RF communication.

---

## 📸 Demo
<img width="1281" height="921" alt="image" src="https://github.com/user-attachments/assets/fb0f5fe0-8d2d-4c9d-8576-1f576b1a7521" />
![Wireless Gesture-Controlled Robotic Arm](images/Robot.jpg)
---

## 🔍 Overview

This system allows an operator to control a robotic arm simply by moving their hand. An **MPU6050 gyroscope/accelerometer** captures wrist orientation and transmits motion data wirelessly via **RF modules** to a receiver Arduino that drives **6 servo motors** — one per joint. An **ultrasonic sensor** detects nearby objects and triggers a **buzzer** as a proximity alert.

This project was built as a group capstone for **ECET-230-001**, covering embedded systems, wireless communication, PCB design, and mechanical design end-to-end.

---

## ✨ Features

- Real-time wireless gesture control via MPU6050 IMU (pitch, roll, yaw)
- 6 degrees of freedom — base, shoulder, elbow, wrist pitch, wrist roll, gripper
- RF 433MHz communication between handheld controller and arm
- Ultrasonic proximity detection with piezo buzzer audio alert
- LCD display for live system status feedback
- Custom PCB designed in KiCad
- 3D printed mechanical structure (PLA+ / PETG)
- Full project documentation: schematics, logs, test plans, CAD files

---

## ⚙️ Hardware Components

| Component | Quantity | Purpose |
|---|---|---|
| Arduino Uno | 2 | Transmitter & Receiver microcontrollers |
| MPU6050 IMU | 1 | Captures hand orientation (I2C) |
| RF Transmitter + Receiver (433MHz) | 1 pair | Wireless data link |
| Servo Motors | 6 | Drives each joint of the arm |
| Ultrasonic Sensor (HC-SR04) | 2 | Object/proximity detection |
| Piezo Buzzer | 1 | Audio proximity alert |
| LCD Display (I2C) | 1 | Live system status |
| Push Buttons | 5 | Manual input controls |
| LEDs (Red & Green) | 2 | Status indicators |
| 9V Battery + Battery Pack | 1 | Portable power supply |
| Custom PCB (KiCad) | 1 | Clean circuit integration |

**Estimated Total Cost: Under $150**

---

## 🧠 How It Works

```
[ Hand Movement ]
       ↓
[ MPU6050 reads pitch / roll / yaw ]
       ↓
[ Transmitter Arduino encodes data + sends via RF ]
       ↓
[ Receiver Arduino decodes signal ]
       ↓
[ 6 Servo motors move to matching joint angles ]
       ↓
[ Ultrasonic sensor monitors proximity → Buzzer alert ]
```

---

## 🛠️ Tools & Technologies

| Category | Tools |
|---|---|
| Programming | Arduino IDE (C/C++) |
| Mechanical Design | SolidWorks / Fusion 360 |
| PCB Design | KiCad |
| Manufacturing | 3D Printing (PLA+ / PETG), Laser Cutting |
| Version Control | GitHub |
| Libraries | `Wire.h`, `MPU6050.h`, `VirtualWire`, `Servo.h`, `LiquidCrystal_I2C.h` |

---

## 📁 Repository Structure

```
Wireless-Gesture-Controlled-Robotic-Manufacturing-System/
├── Software/           # Arduino .ino source files (transmitter & receiver)
├── Design/             # System architecture, block diagrams, circuit schematics
├── PCB Files/          # KiCad PCB design files
├── Robot 3D Model/     # SolidWorks / Fusion 360 CAD files
├── Logs/               # Weekly progress logs
├── Tasks/              # Task tracking and completion status
├── Definitions/        # Official project scope and requirements
├── Proof of Concept.md # Early validation and feasibility notes
├── Testing Document.md # Test cases, results, and validation
├── LICENSE
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- Arduino IDE installed
- Required libraries (install via Library Manager):
  - `MPU6050` by Electronic Cats
  - `VirtualWire` or `RadioHead` for RF
  - `LiquidCrystal_I2C` for LCD
  - `Servo` (built-in)

### Upload Steps

1. Clone this repo:
   ```bash
   git clone https://github.com/MrJoenin/Wireless-Gesture-Controlled-Robotic-Manufacturing-System.git
   ```
2. Open `Software/transmitter.ino` → upload to the **controller Arduino** (with MPU6050)
3. Open `Software/receiver.ino` → upload to the **arm Arduino**
4. Power both units — the arm will mirror hand movements in real time

---

## 📆 Project Timeline

| Phase | Duration | Description |
|---|---|---|
| Research & Planning | Weeks 1–2 | Brainstorm, block diagram, parts research |
| Design & Prototyping | Weeks 3–6 | CAD models, circuit design, PCB layout |
| Implementation | Weeks 7–10 | Build prototype, write firmware |
| Testing & Debugging | Weeks 11–12 | Verify requirements, fix issues |
| Final Delivery | Week 13 | Report, presentation, live demo |

---

## 🧩 Challenges & What We Learned

- **Servo power management** — Powering all 6 servos from Arduino caused brownouts. Fixed by using a dedicated external supply with a shared ground.
- **RF signal reliability** — Raw RF is noisy; added basic packet validation to prevent erratic servo movement from corrupted signals.
- **IMU drift** — Raw gyroscope data drifts over time. Applied a complementary filter combining accelerometer + gyroscope data for stable, accurate readings.
- **PCB design iteration** — First PCB revision had routing issues; KiCad's DRC tool helped catch and fix them before fabrication.

---

## 🔮 Future Improvements

- [ ] Upgrade to nRF24L01 for bidirectional, more reliable communication
- [ ] Add inverse kinematics for coordinate-based positioning
- [ ] Implement a mobile app as an alternative controller
- [ ] Add force feedback on the gripper

---

## 👥 Team

| Member | Role |
|---|---|
| John (MrJoenin) | CAD, Mechanical Design |
| Alicia | Coding, Testing & Validation |
| Larbi | Research, Schematics, PCB Design |

---

## 📄 License

This project is open source under the [MIT License](LICENSE).  
Feel free to use and modify with attribution.
