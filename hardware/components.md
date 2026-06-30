# Pathfinder — Hardware Components (Bill of Materials)

This document lists all components required to build the Pathfinder navigation assistant.

---

## Core Components

| Component | Qty | Specification | Purpose |
|---|---|---|---|
| [XIAO ESP32S3](https://www.seeedstudio.com/XIAO-ESP32S3-p-5627.html) | 1 | Seeed Studio, 240 MHz dual-core, 8 MB Flash | Main MCU — runs firmware + TinyML inference |
| HC-SR04 Ultrasonic Sensor | 1–3 | Range: 2–400 cm, accuracy ±3 mm | Obstacle distance measurement |
| Vibration Motor (coin/pancake) | 1–2 | 3V DC, 80–150 mA, offset eccentric weight | Haptic feedback |
| Piezoelectric Buzzer (passive) | 1 | 3–5V, < 30 mA | Audio alert tones |
| LiPo Battery | 1 | 3.7V, 500 mAh minimum (1000 mAh recommended) | Portable power supply |
| LiPo Battery Charger / Shield | 1 | Compatible with XIAO ESP32S3 | Safe charging circuit |

---

## Supporting Components

| Component | Qty | Specification | Purpose |
|---|---|---|---|
| NPN Transistor (2N2222 or similar) | 1–2 | Vceo ≥ 30V, Ic ≥ 200 mA | Motor drive (GPIO current protection) |
| Resistor | 2 | 220 Ω, ¼ W | Transistor base resistor for motor |
| Resistor | 2 | 10 kΩ, ¼ W | Pull-down for echo/signal lines |
| Jumper Wires | ~20 | Male–male, male–female | Connections on breadboard |
| Half-size Breadboard | 1 | 400 tie points | Prototyping |
| USB-C Cable | 1 | For programming & charging | Firmware flashing |

---

## Optional / Future

| Component | Purpose |
|---|---|
| OV2640 Camera Module (XIAO-compatible) | Camera input for Edge Impulse image classification |
| DFPlayer Mini + small speaker | Voice output for object identification |
| 3D printed enclosure | Wearable / handheld form factor |
| Custom PCB | Replace breadboard for a compact finished device |

---

## Sourcing Notes

- The **XIAO ESP32S3** is available from [Seeed Studio](https://www.seeedstudio.com/XIAO-ESP32S3-p-5627.html), ~$7–10 USD.
- **HC-SR04** sensors are widely available on Amazon, AliExpress, and Digi-Key, ~$1–3 USD each.
- **LiPo batteries** — use a protected cell (with built-in over-discharge protection).
- Total BOM cost for a prototype: approximately **$15–25 USD**.
