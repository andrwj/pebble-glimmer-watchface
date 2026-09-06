# Glimmer for Pebble (Emery Edition)

An ultra-battery-efficient, dynamic analog watchface exclusively optimized for Pebble Time 2 (**Emery** platform, 200×228 resolution).

---

## ✨ Features

- **Dynamic Catch-up Rolling Animation**:
  - Automatically freezes in standby and winds clock hands forward with a smooth, fixed-point **Cubic Ease-Out** animation (700ms, max 2 revolutions) when checked.
- **Natural Flip & Un-flip Gestures (3D Vector)**:
  - **Flip Outward ($\ge 80^\circ$)**: Puts the watch to sleep instantly with a brief 30ms haptic pulse and dark gray dial mask.
  - **Turn Inward ($\le 60^\circ$)**: Immediately wakes up the watch and rolls hands to the exact current time.
- **Capacitive Touchscreen Wake-up**:
  - Touch or tap the screen at any time to wake up the watchface instantly.
- **Ultra-Low Power Architecture**:
  - **0 Display Redraws in Standby**: Sharp Memory LCD maintains static display with near-zero power draw ($<2\mu\text{W}$).
  - **100% Deep Sleep in Hibernation**: Eliminates unnecessary polling and maximizes battery life (5.5 ~ 7+ days typical, 10+ days resting).
- **High-Resolution Emery Dial (260×260)**:
  - Precision 12px uniform hour/minute hands and high-contrast uppercase Day (`MON`) and Date (`SEP.07`) typography underneath clock hands.
- **Mobile Configuration Webview**:
  - Modern web settings with live dial preview, Pebble 64-color palette selector, and customizable gesture angle sliders.

---

## 🛠️ Build & Installation

### Prerequisites
- [Pebble SDK](https://rebble.io/howto/) with `emery` platform support
- `arm-none-eabi-gcc` toolchain

### Makefile Targets
```bash
# Clean and build the .pbw package
make rebuild

# Install directly to physical watch over Wi-Fi/Phone
make install

# Install and launch in the Emery emulator
make install-emu

# Stream emulator logs
make logs
```

---

## 📸 Taking Screenshots from the Emulator

You can capture pixel-perfect PNG screenshots directly from the running emulator:

```bash
# Capture screenshot from Emery emulator
pebble screenshot --emulator emery screenshot.png
```

Or via Makefile shortcut:
```bash
make screenshot
```

---

## 🕹️ Emulator Gesture & Motion Testing

Test gestures directly in the emulator using Pebble CLI tools:

```bash
# 1. Flip watch face-down (Sleep / Hibernate)
pebble emu-accel gravity+z --emulator emery

# 2. Turn watch upright (Wake-up / Roll)
pebble emu-accel gravity-z --emulator emery

# 3. Simulate wrist raise / look at watch
pebble emu-accel tilt-forward --emulator emery

# 4. Simulate screen touch / tap
pebble emu-tap --emulator emery

# 5. Interactive 3D sensor control (opens browser Web UI)
pebble emu-control --emulator emery
```

---

## ⚙️ Configuration Page (Settings)

The watchface settings page is hosted via GitHub Pages:
- **URL**: `https://andrwj.github.io/pebble-glimmer-watchface/settings.html`

### Configurable Options
- **Flip to Sleep / Wake Toggle**: Enable/disable automatic flip sleep.
- **Sleep Tilt Angle**: Outward angle threshold ($60^\circ \sim 120^\circ$, default $80^\circ$).
- **Wake Tilt Angle**: Inward angle threshold ($30^\circ \sim 75^\circ$, default $60^\circ$).
- **Face-Up Rest Sleep**: Optional sleep when placed flat face-up on a desk.
- **Date & Day Color**: Choose from 8 Pebble palette colors (Dark Gray, Cerulean, Cobalt, Rose, etc.).
- **Update Interval**: Periodic background sync (0 min for pure on-demand wake, 5 ~ 60 min).

---

## 📄 License
MIT License © A.J (`andrwj`)
