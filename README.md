# Cherry Clock

A minimal **menu bar Pomodoro timer** for macOS (works on Linux/Windows too, minus AppleScript), written in **C++20 + Qt 6**.

## MVP features
- Tray app with Start / Pause / Skip / Reset
- Multiple profiles (25/5, 52/17, etc)
- Phase transitions (short/long breaks after N focus sessions)
- Persistent local stats as JSONL (sessions started/ended)
- Apple Music pause/play stubs (macOS via AppleScript)

## Build (macOS)
1. Install Qt 6 (e.g., `brew install qt`).
2. Configure & build:
   ```bash
   cd pomodoro-basic
   mkdir build && cd build
   cmake -DCMAKE_PREFIX_PATH=$(brew --prefix qt) ..
   cmake --build . --config Release
   # If built as bundle:
   open PomodoroBasic.app
   # Otherwise:
   ./pomodoro
Notes
* Profiles can be customized by placing a profiles.json in the app data dir (~/Library/Application Support/PomodoroBasic/profiles.json).
* Session events are logged to ~/Library/Application Support/PomodoroBasic/sessions.jsonl.
Next steps (easy adds)
* Notifications & sounds
* macOS Focus mode toggle via Shortcuts
* Slack/Discord “In Focus” status
* Preferences window to edit profiles
MIT licensed. Have fun!

## profiles.json (starter)
```json
[
  { "name": "Pomodoro 25/5", "focusMin": 25, "shortBreakMin": 5,  "longBreakMin": 15, "longEveryN": 4 },
  { "name": "52/17",        "focusMin": 52, "shortBreakMin": 17, "longBreakMin": 25, "longEveryN": 2 }
]
