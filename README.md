# Krutons Launcher

Launch Amazon Music, Steam, Discord, and Telegram with one button on [OpenDeck](https://github.com/nekename/OpenDeck).

---

## Actions

| Action | What it does |
|--------|-------------|
| **Amazon Music** | Launches the Amazon Music desktop app |
| **Steam** | Launches Steam |
| **Discord** | Launches Discord |
| **Telegram** | Launches Telegram Desktop |

Each action ships with a sensible default install path and can be overridden per-button if your app is installed somewhere else.

---

## Features

- **One-click launch** — four apps, four buttons, baked-in pixel-art icons for each
- **Custom path override** — point any button at a non-default install location
- **Argument-aware launching** — correctly handles executables that need launch arguments (e.g. Discord's updater bootstrap), not just plain `.exe` paths
- **Pure JS rendering** — no native binaries, no canvas module

---

## Installation

1. Download `krutons-launcher.sdPlugin.zip` from the [Releases](../../releases) page
2. Extract — you should have a folder called `com.kruton.launcher.sdPlugin`
3. Copy it to your OpenDeck plugins directory:
   ```
   %APPDATA%\OpenDeck\plugins\
   ```
4. Restart OpenDeck
5. All four actions will appear in the actions list under **Krutons Launcher**

> **Note:** The folder must be named `com.kruton.launcher.sdPlugin` exactly. OpenDeck uses the folder name to route button updates.

---

## Customisation

Click any placed button to open its settings panel:

| Setting | Description |
|---------|-------------|
| **Custom App Path** | Overrides the default executable path. Leave blank to use the default install location for that app. |

---

## Default paths

| App | Default path |
|-----|--------------|
| Amazon Music | `%USERNAME%\AppData\Local\Amazon Music\Amazon Music.exe` |
| Steam | `C:\Program Files (x86)\Steam\steam.exe` |
| Discord | `%USERNAME%\AppData\Local\Discord\Update.exe --processStart Discord.exe` |
| Telegram | `%USERNAME%\AppData\Roaming\Telegram Desktop\Telegram.exe` |

Discord's default path needs a launch argument (`--processStart Discord.exe`) passed to its updater bootstrap — the plugin splits the executable from its arguments correctly rather than treating the whole string as one literal filename.

---

## Requirements

- **OpenDeck** (Windows 10+)
- Node.js 20+ (bundled with OpenDeck)

---

## Project structure

```
com.kruton.launcher.sdPlugin/
├── index.js                  # Plugin backend — launching, rendering, WebSocket
├── amazonmusic.js             # Baked pixel-art icon data
├── steam.js                   # Baked pixel-art icon data
├── discord.js                 # Baked pixel-art icon data
├── telegram.js                # Baked pixel-art icon data
├── manifest.json               # OpenDeck plugin manifest
├── images/
│   ├── plugin-icon.png
│   ├── amazonmusic-icon.png
│   ├── steam-icon.png
│   ├── discord-icon.png
│   └── telegram-icon.png
├── propertyinspector/
│   └── index.html             # Settings panel (custom path override)
└── node_modules/
    └── ws/                    # WebSocket client
```

---

## Building from source

```bash
git clone https://github.com/Kruton1122/Krutons-OpenDeck-Launcher
cd Krutons-OpenDeck-Launcher/com.kruton.launcher.sdPlugin
npm install
```

Then zip the `com.kruton.launcher.sdPlugin` folder and install as above.

---

## Credits

- WebSocket via [ws](https://github.com/websockets/ws)
- Built for [OpenDeck](https://github.com/nekename/OpenDeck) by nekename

---

## License

MIT
