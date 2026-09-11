# v2.1.0 — Keyboard volume snaps to 5% steps

Media keys now land on the next/previous 5% palier instead of adding 5 to whatever the slider left behind.

---

### ☕ Support
If this saved you a lot of audio fiddling, a tip is appreciated.

[![Donate via PayPal](https://img.shields.io/badge/Donate-PayPal-blue.svg?style=for-the-badge&logo=paypal)](https://paypal.me/austraz)

---

## What’s new

### 🎯 VOL± snaps to 5%
- **VOL+** from 76% goes to **80%**, not 81%.
- **VOL−** from 76% goes to **75%**.
- Already on a palier (80%) → next/previous cran (85% / 75%).
- Slider stays free; **Alt+VOL** stays 1% precision.

## Upgrade

```sh
omarchy plugin update austraz.audio
# wrapper is a symlink into the plugin for a normal install; otherwise:
# cp ~/.config/omarchy/plugins/austraz.audio/bin/omarchy-audio-output-volume ~/.config/omarchy/bin/
# chmod +x ~/.config/omarchy/bin/omarchy-audio-output-volume
```
