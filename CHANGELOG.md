# Changelog

All notable changes to Pathfinder will be documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Planned
- Dual ultrasonic sensor support (left/right detection)
- Battery level indicator via LED or buzzer pattern
- BLE companion app for configuration
- PCB design for production-ready form factor

---

## [1.0.0] — 2024-12-31

### Added
- Initial firmware for XIAO ESP32S3
- HC-SR04 ultrasonic sensor integration via `NewPing` library
- Three-zone obstacle detection:
  - **Clear zone** (> 50 cm): no feedback
  - **Obstacle zone** (20–50 cm): vibration motor active
  - **Danger zone** (< 20 cm): buzzer alert + vibration
- Haptic feedback via vibration motor
- Audio alert via piezoelectric buzzer
- Serial debug output at 115200 baud
- Startup self-test sequence (motor + buzzer confirmation pulses)
- Placeholder integration hooks for Edge Impulse TinyML model
- Hardware documentation: BOM (`hardware/components.md`) and schematic (`hardware/schematic.md`)
- Edge Impulse model deployment guide (`src/model_deployment/README.md`)
- MIT License

### Notes
- Built in 24 hours at TinkerHub TinyML Hackathon 2024 by Team VYSE
- Edge Impulse model integration is present but gated behind compile-time comments (requires separate model download)
