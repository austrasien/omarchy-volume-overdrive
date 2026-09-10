# v2.0.0 — Single multi-kind plugin

Breaking packaging change: one git URL → one folder → one `manifest.json`.

## What’s new

- **Merged** former `austraz.audio` + `austraz.osd` into **`austraz.audio`** with `kinds: ["bar-widget", "panel"]`.
- **Install** via `omarchy plugin add https://github.com/austrasien/omarchy-volume-overdrive.git`.
- **IPC**: panel keeps `IpcHandler` target `osd`; `clonedFrom: omarchy.osd` so media/monitor/`omarchy-osd` keep working; audio panel summons `austraz.audio`.
- Same 200% clamp, 100% notch, and red overdrive UI as v1.

## Upgrade

```sh
omarchy plugin add https://github.com/austrasien/omarchy-volume-overdrive.git --enable --yes
# or, if already installed as austraz.audio: omarchy plugin update austraz.audio
omarchy plugin disable omarchy.audio
omarchy plugin disable omarchy.osd
# remove obsolete separate clone if present:
# rm -rf ~/.config/omarchy/plugins/austraz.osd
```

Re-copy the volume wrapper if needed:

```sh
cp ~/.config/omarchy/plugins/austraz.audio/bin/omarchy-audio-output-volume ~/.config/omarchy/bin/
chmod +x ~/.config/omarchy/bin/omarchy-audio-output-volume
```
