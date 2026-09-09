# Omarchy Volume Overdrive (200%)

A focused Omarchy customization that lets output volume go up to **200%** with clear overdrive visuals:

- **Notch at real 100%** on the OSD and Audio panel slider
- **Red fill over 100%** (`Color.urgent`)
- **Media keys + panel slider** both honor the 200% cap

```
Volume keys / wheel  →  wrapper (max 200)  →  OSD max 200
Audio panel slider   →  cloned plugin       →  same overdrive UI
```

---

### ☕ Support

If this tweak improves your daily Omarchy workflow, tips are welcome.

[![Donate via PayPal](https://img.shields.io/badge/Donate-PayPal-blue.svg?style=for-the-badge&logo=paypal)](https://paypal.me/austraz)

---

## What’s inside

- `bin/omarchy-audio-output-volume`
  - user-level override of Omarchy volume script
  - raises clamp from 100 to 200
  - sends OSD payload with `max: 200` + explicit `progressText`

- `plugins/austraz.osd/`
  - clone of `omarchy.osd`
  - adds notch at the normalized 100% position
  - turns progress fill red above 100%

- `plugins/austraz.audio/`
  - clone of `omarchy.audio`
  - output slider range changed to `0..2`
  - same notch + red-overdrive behavior
  - OSD payload aligned to 200% scale

---

## Install (Omarchy)

1. Clone:

```sh
git clone https://github.com/austrasien/omarchy-volume-overdrive.git
cd omarchy-volume-overdrive
```

2. Install wrapper script:

```sh
mkdir -p ~/.config/omarchy/bin
cp bin/omarchy-audio-output-volume ~/.config/omarchy/bin/
chmod +x ~/.config/omarchy/bin/omarchy-audio-output-volume
```

3. Install plugin clones:

```sh
mkdir -p ~/.config/omarchy/plugins
cp -r plugins/austraz.audio ~/.config/omarchy/plugins/
cp -r plugins/austraz.osd ~/.config/omarchy/plugins/
```

4. Enable clones and reload shell:

```sh
omarchy plugin enable austraz.audio
omarchy plugin enable austraz.osd
omarchy plugin disable omarchy.audio
omarchy plugin disable omarchy.osd
omarchy restart shell
```

## Verify

- Press volume-up keys: should go beyond 100% up to 200%
- OSD shows:
  - notch at 100%
  - red fill only above 100%
- Audio panel output slider reaches 200% and matches same visuals

---

## Notes

- This project intentionally avoids editing `/usr/share/omarchy/`.
- It follows Omarchy’s clone-and-override pattern so updates are safer.

