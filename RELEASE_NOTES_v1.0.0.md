# v1.0.0 — Volume overdrive to 200% (OSD + panel)

Feature release: Omarchy volume can now exceed 100% with consistent UI feedback across media keys OSD and Audio panel.

---

### ☕ Support
If this saved you a lot of audio fiddling, a tip is appreciated.

[![Donate via PayPal](https://img.shields.io/badge/Donate-PayPal-blue.svg?style=for-the-badge&logo=paypal)](https://paypal.me/austraz)

---

## What’s new

### 🔊 Volume up to 200%
- Output volume clamp increased from 100% to **200%** in the user override script.
- Media-key volume changes now keep using Omarchy OSD with a 200% scale.

### 🎚 Normalized visual reference at 100%
- Added a fixed **notch at real 100%** in OSD progress bar.
- Added the same notch in the Audio panel output slider row.

### 🚨 Overdrive color above 100%
- Progress fill switches to **red** (`Color.urgent`) when output is above 100%.
- Under 100%, default styling remains unchanged.

### 🧩 Omarchy-native implementation
- No modifications under `/usr/share/omarchy/`.
- Implemented via plugin clones (`austraz.audio`, `austraz.osd`) + PATH wrapper.

---

## Upgrade / Apply

```sh
git pull
cp bin/omarchy-audio-output-volume ~/.config/omarchy/bin/
chmod +x ~/.config/omarchy/bin/omarchy-audio-output-volume
cp -r plugins/austraz.audio ~/.config/omarchy/plugins/
cp -r plugins/austraz.osd ~/.config/omarchy/plugins/
omarchy restart shell
```

