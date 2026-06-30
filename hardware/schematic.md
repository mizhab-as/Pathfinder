# Pathfinder — Hardware Schematic & Wiring

This document describes how to wire all components to the XIAO ESP32S3.

---

## Pin Mapping

| XIAO ESP32S3 Pin | GPIO | Connected To | Notes |
|---|---|---|---|
| `5V` | — | HC-SR04 VCC | Use 5V rail if available; sensor can run on 3.3V too |
| `GND` | — | HC-SR04 GND, Motor –, Buzzer – | Common ground |
| `D2` | GPIO2 | HC-SR04 TRIG | Digital out, 10 µs pulse to trigger |
| `D3` | GPIO3 | HC-SR04 ECHO | Digital in, pulse duration = distance |
| `D5` | GPIO5 | Vibration Motor + (via transistor) | Do **not** connect motor directly to GPIO |
| `D6` | GPIO6 | Buzzer + | Passive buzzer, uses `tone()` |

---

## Connection Diagram

```
                    ┌──────────────────────────────┐
                    │        XIAO ESP32S3          │
                    │                              │
                    │  5V  ──────────────────────► │── HC-SR04 VCC
                    │  GND ──────┬───────────────► │── HC-SR04 GND
                    │            │                 │── Motor (–)
                    │            │                 │── Buzzer (–)
                    │            │                 │
                    │  D2  ──────────────────────► │── HC-SR04 TRIG
                    │  D3  ◄──────────────────────┤── HC-SR04 ECHO
                    │                              │
                    │  D5  ─── [220Ω] ─── Base    │
                    │                  │ 2N2222   │
                    │            GND ──┘ Emitter  │
                    │         Motor+ ── Collector  │
                    │                              │
                    │  D6  ──────────────────────► │── Buzzer (+)
                    └──────────────────────────────┘
```

---

## HC-SR04 Ultrasonic Sensor

```
HC-SR04
┌─────────────────┐
│  VCC  ──── 5V   │ ← Power
│  TRIG ──── D2   │ ← Trigger pulse (10 µs HIGH)
│  ECHO ──── D3   │ → Echo pulse (duration ∝ distance)
│  GND  ──── GND  │ ← Ground
└─────────────────┘

Distance formula (calculated by NewPing library):
  distance_cm = echo_duration_µs / 58
```

---

## Vibration Motor (via NPN Transistor)

> ⚠️ **Never connect the motor directly to a GPIO pin.** The XIAO ESP32S3 GPIOs are rated for ~12 mA max. The vibration motor draws 80–150 mA. A transistor (or MOSFET) is required.

```
D5 ──[220Ω]──► Base (2N2222)
               Collector ──► Motor (+)
               Emitter   ──► GND

Motor (–) ──► GND
Motor (+) ──► 3.3V or 5V (through transistor collector)
```

---

## Buzzer

```
D6 ──► Buzzer (+)
GND ──► Buzzer (–)
```

Using `tone(BUZZER_PIN, frequency, duration)` in firmware.  
- Obstacle warning: 1500 Hz  
- Danger alert: 2000 Hz

---

## Power

The XIAO ESP32S3 can be powered via:
- **USB-C** during development/flashing
- **LiPo battery** connected to the XIAO battery pads (BAT+/BAT–) for field use

A 500 mAh LiPo provides approximately **3–5 hours** of continuous operation with all sensors active.

---

## Multi-Sensor Configuration (Optional)

For left/right detection, add two more HC-SR04 sensors:

| Sensor | TRIG | ECHO | Direction |
|---|---|---|---|
| Sensor 1 | D2 | D3 | Front |
| Sensor 2 | D4 | D7 | Left |
| Sensor 3 | D8 | D9 | Right |

Update `#define TRIGGER_PIN`, `ECHO_PIN` and introduce separate `NewPing` instances per sensor.
