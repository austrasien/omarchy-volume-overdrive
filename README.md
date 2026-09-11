# Omarchy Volume Overdrive (200%)

One **Omarchy plugin** (`austraz.audio`) with two kinds — **bar-widget** + **panel** — so media keys, the audio panel slider, and the OSD all honor **200%** volume end-to-end from a single `omarchy plugin add`.

> **⚡ Replaces stock `omarchy.audio` and `omarchy.osd`.** Disable both after enable so you only get one volume chip and one OSD (this plugin’s overdrive UI).

```
Volume keys / wheel  →  PATH wrapper (max 200)  →  IPC osd show
Audio panel slider   →  austraz.audio widget     →  summon austraz.audio (OSD)
Media / brightness   →  omarchy.osd id           →  clonedFrom routes here
```

Forked from Omarchy’s built-in audio + OSD panels; 200% overdrive by [austrasien](https://github.com/austrasien).

---

### ☕ Support

If this tweak improves your daily Omarchy workflow, tips are welcome.

[![Donate via PayPal](https://img.shields.io/badge/Donate-PayPal-blue.svg?style=for-the-badge&logo=paypal)](https://paypal.me/austraz)

---

### 💬 Feedback

Questions or bugs → [issues](https://github.com/austrasien/omarchy-volume-overdrive/issues).

---

## What’s inside

| Piece | Role |
| :--- | :--- |
| `Panel.qml` + `Model.js` | Bar audio widget: output slider `0..2`, notch + red fill above 100% |
| `Osd.qml` + `OsdModel.js` | keepLoaded OSD panel: notch at real 100%, urgent fill past NORM |
| `bin/omarchy-audio-output-volume` | User PATH override: clamp 200%, snap VOL± to 5% steps, OSD payload `max: 200` |
| `manifest.json` | `kinds: ["bar-widget", "panel"]`, `clonedFrom: omarchy.osd` |

`clonedFrom: omarchy.osd` is intentional: first-party media / monitor / `omarchy-osd` still address `omarchy.osd`, and the shell resolves them to this plugin once stock OSD is disabled. The audio bar widget is third-party style — put it on the bar and disable stock `omarchy.audio`.

---

## Install

```sh
omarchy plugin add https://github.com/austrasien/omarchy-volume-overdrive.git --enable --yes
```

Then disable the stock pair and install the volume wrapper:

```sh
omarchy plugin disable omarchy.audio
omarchy plugin disable omarchy.osd

mkdir -p ~/.config/omarchy/bin
cp ~/.config/omarchy/plugins/austraz.audio/bin/omarchy-audio-output-volume ~/.config/omarchy/bin/
chmod +x ~/.config/omarchy/bin/omarchy-audio-output-volume
```

Ensure `~/.config/omarchy/bin` is early on your `PATH` (Omarchy does this by default). Reload if needed:

```sh
omarchy-shell shell rescanPlugins
# or: omarchy restart shell
```

### Upgrading from the old two-folder layout

If you previously copied `plugins/austraz.audio` **and** `plugins/austraz.osd` separately:

1. Install / update this single-plugin repo as above.
2. Remove the obsolete panel entry: `omarchy plugin disable austraz.osd` (if listed), then delete `~/.config/omarchy/plugins/austraz.osd` when the merged plugin works.
3. Keep a single bar entry: `austraz.audio`.

---

## Verify

1. Raise volume past 100% with media keys → OSD shows a notch at mid-bar and red fill above it; readout goes to 200%.
2. Slider at 76% then **VOL+** → OSD shows **80%** (next 5% step, not 81%). **Alt+VOL** stays 1%.
3. Open the audio panel → same notch / red overdrive on the output slider; drag above 100% works.
4. Brightness / media OSDs still appear (routed through this panel via `omarchy.osd` clone resolution).

---

## License

MIT — see [LICENSE](LICENSE). Upstream Omarchy shell plugins are the Omarchy project’s; this packaging adds the overdrive behavior and install layout.
