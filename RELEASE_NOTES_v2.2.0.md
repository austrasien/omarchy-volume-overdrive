# v2.2.0 — OSD in the minimap, held volume keys, keyboard backlight

---

### ☕ Support
If this saved you a lot of audio fiddling, a tip is appreciated.

[![Donate via PayPal](https://img.shields.io/badge/Donate-PayPal-blue.svg?style=for-the-badge&logo=paypal)](https://paypal.me/austraz)

---

## What’s new

### 🗺️ OSD in the minimap
- With [austraz.minimap](https://github.com/austrasien/omarchy-minimap) on screen, volume, brightness and mic OSDs show in its middle circle (0–200 % ring, 100 % at six o'clock, red past it).
- Minimap disabled, hidden or not loaded → the usual card, automatically.

### ⏩ Held VOL± keeps stepping
- Overlapping repeats used to read the same level and land on the same step, so the volume stalled. Runs are now serialised; extra repeats are dropped so the level stops when you let go.

### ⌨️ Keyboard backlight OSD
- Fn+Space (Framework) changes the backlight in the embedded controller with no key event; the OSD now watches the level and shows it.

## Upgrade

```sh
omarchy plugin update austraz.audio
omarchy-restart-shell
```
