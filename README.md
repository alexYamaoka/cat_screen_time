
# cat screen time
A macOS menu bar app that reminds you to take regular breaks from your screen — with cat companion to keep you company.

## Features

- **Scheduled break reminders** — prompts appear at a configurable interval (default: every 45 minutes)
- **Countdown timer** — large, readable countdown during each break so you know exactly how long is left
- **Animated overlays** — plays a GIF or video during breaks; supports green-screen removal for clean compositing
- **Menu bar presence** — lives quietly in your system tray; no Dock icon, no clutter
- **Take a break now** — trigger a break manually from the menu at any time
- **Customizable settings** — adjust break interval, break duration, and choose your own animation
- **Native macOS feel** — frosted glass vibrancy effect on the overlay window via NSVisualEffectView

<!-- SCREENSHOT: settings window -->

---

## Demo
<img width="1706" height="1107" alt="Screenshot 2026-05-12 at 22 02 30" src="https://github.com/user-attachments/assets/dcf81062-716a-47ce-8efd-b9b045a55af8" />
<!-- GIF: break overlay appearing with countdown -->
<!-- GIF: settings window -->

---

## How It Works

Screen Time runs a background scheduler that fires at your chosen interval. When a break is due, a full-screen overlay fades in with an animation and a countdown timer. Once the timer reaches zero the overlay dismisses itself automatically, and the scheduler resets for the next cycle.

```
Scheduler fires → overlay displays → animation plays + countdown runs → overlay dismisses → repeat
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.11+ |
| GUI | PySide6 (Qt 6) |
| Scheduling | APScheduler 3 |
| Animation | Qt frame-by-frame (GIF) · QMediaPlayer (MP4/WebM) |
| Image processing | NumPy (green-screen removal) |
| macOS integration | PyObjC / Cocoa (vibrancy, tray) |

---

## Configuration

Settings are stored in `~/.screen_time/config.json` and editable through the in-app Settings window.

| Key | Default | Description |
|---|---|---|
| `interval_minutes` | `45` | Minutes between break reminders |
| `break_duration_seconds` | `60` | How long each break lasts |
| `animation_path` | `assets/cat.gif` | Path to GIF, MP4, WebM, or MOV |

---

## Requirements

- macOS 12 Monterey or later
- Python 3.11+
