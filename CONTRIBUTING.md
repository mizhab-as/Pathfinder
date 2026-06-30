# Contributing to Pathfinder

Thank you for your interest in contributing! Pathfinder started as a 24-hour hackathon project and we welcome improvements from the community.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)
- [Submitting a Pull Request](#submitting-a-pull-request)
- [Development Setup](#development-setup)
- [Coding Style](#coding-style)

---

## Code of Conduct

Be respectful and inclusive. This is an assistive technology project — contributions should keep the end users (visually impaired individuals) in mind at all times.

---

## How to Contribute

There are many ways to help:

- 🐛 **Bug reports** — Open an issue with steps to reproduce
- 💡 **Feature ideas** — Open an issue with the `enhancement` label
- 📖 **Documentation** — Fix typos, improve clarity, add examples
- 🔧 **Hardware improvements** — Better schematics, BOM optimizations, PCB designs
- 🤖 **ML model improvements** — Better training data, new object classes, model optimization
- 💻 **Firmware** — New features, performance improvements, cleaner code

---

## Reporting Bugs

Before opening a bug report, please:
1. Check existing [issues](../../issues) to avoid duplicates
2. Confirm you're using the latest code from `main`

When opening the issue, include:
- **Hardware:** Which sensors/components you're using, and their connections
- **Arduino IDE version** and **ESP32 board package version**
- **Serial Monitor output** (if applicable)
- **Steps to reproduce**
- **Expected vs actual behavior**

---

## Suggesting Features

Open an issue with the `enhancement` label. Describe:
- The problem you're solving
- Your proposed solution
- Any hardware changes required

---

## Submitting a Pull Request

1. **Fork** the repository
2. **Create a branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```
3. **Make your changes**
4. **Test** on real hardware (or document that you couldn't and why)
5. **Commit** with a clear message:
   ```
   feat: add second ultrasonic sensor for left/right detection
   fix: prevent motor stall when distance < 2cm
   docs: add wiring diagram for dual-sensor setup
   ```
6. **Push** and open a Pull Request against `main`

We'll review promptly. For large changes, please open an issue first to discuss before investing time.

---

## Development Setup

See [README.md → Software Setup](README.md#-software-setup) for Arduino IDE and library installation instructions.

Quick test checklist:
- [ ] Firmware compiles without errors
- [ ] Serial Monitor shows distance readings at 115200 baud
- [ ] Vibration motor activates when obstacle < 50 cm
- [ ] Buzzer fires when obstacle < 20 cm

---

## Coding Style

- Follow existing C++ formatting in `src/main.ino`
- Comment all `#define` constants
- Keep functions focused and short (< 50 lines where possible)
- Use descriptive variable names — clarity over brevity
- Add a `Serial.println()` debug statement for any new major state change
