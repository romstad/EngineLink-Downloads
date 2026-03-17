# EngineLink

EngineLink lets you run a powerful chess engine on your computer and use it from **The Marvelous Brass Chessplaying Automaton** on your iPhone. This gives you much stronger analysis, and also helps conserve your phone's battery life. Your phone just presents the chess board and the engine analysis, your computer at home does all the heavy lifting.

**How it works:**

1. Install EngineLink on your computer
2. Launch it - a QR code appears on screen
3. Scan the QR code from the app on your iPhone - done!

Your computer runs the chess engine; your phone sends it positions and receives analysis. No technical setup required.

---

## Download

| Platform | Download | Notes |
|---|---|---|
| macOS | [EngineLink.dmg](#) | Stockfish engine included |
| Windows | [EngineLink-Setup.exe](#) | Stockfish download required (see below) |
| Linux (GUI) | [EngineLink.AppImage](#) · [EngineLink.deb](#) | Stockfish download required (see below) |
| Linux (Terminal) | [enginelink.gz](#) | For terminal/server use; Stockfish download required (see below) |

---

## Setup Instructions

Jump to your platform:
- [macOS](#macos)
- [Windows](#windows)
- [Linux (GUI)](#linux-gui)
- [Linux (Terminal)](#linux-terminal)

---

### macOS

Stockfish is already included - no extra downloads needed.

1. Open the downloaded **EngineLink.dmg** file
2. Drag **EngineLink** into your **Applications** folder
3. Open EngineLink from Applications

**If macOS shows a security warning** ("Apple could not verify..."):
- Open **System Settings** → **Privacy & Security**
- Scroll down to the security section
- Click **Open Anyway** next to the EngineLink message
- Launch EngineLink again

4. A large QR code appears on screen - you're ready to connect from your iPhone

---

### Windows

1. Run the downloaded **EngineLink-Setup.exe** installer and follow the prompts

**If Windows shows a SmartScreen warning** ("Windows protected your PC"):
- Click **More info**
- Click **Run anyway**

2. Download Stockfish (see [Getting Stockfish](#getting-stockfish) below)
3. Launch **EngineLink** from the Start menu
4. On the first launch, a configuration screen appears
5. Click **Browse...** and select the Stockfish file you downloaded
6. Click **Save & Connect**
7. A QR code appears - you're ready to connect from your iPhone

---

### Linux (GUI)

Two download options are available — pick whichever suits your system:

- **AppImage** - works on any Linux distribution, no installation needed
- **.deb** - installs system-wide on Debian, Ubuntu, and related distributions

**AppImage:**

1. Download the `.AppImage` file
2. Make it executable and run it:
   ```
   chmod +x EngineLink.AppImage
   ./EngineLink.AppImage
   ```

**Deb package:**

1. Install the downloaded package:
   ```
   sudo dpkg -i EngineLink.deb
   ```
2. Launch **EngineLink** from your application menu or run `enginelink` in a terminal

**Then, for either option:**

3. Download Stockfish (see [Getting Stockfish](#getting-stockfish) below)
4. On the first launch, a configuration screen appears
5. Click **Browse...** and select the Stockfish file you downloaded
6. Click **Save & Connect**
7. A QR code appears - you're ready to connect from your iPhone

---

### Linux (Terminal)

This version runs entirely in your terminal - no graphical desktop required.

1. Download and extract the file:
   ```
   gunzip enginelink.gz
   chmod +x enginelink
   ```
2. Download Stockfish (see [Getting Stockfish](#getting-stockfish) below)
3. Run EngineLink in a terminal:
   ```
   ./enginelink
   ```
4. On the first launch, a configuration screen appears with text fields
5. Type the full path to your Stockfish file (e.g. `/usr/local/bin/stockfish`)
6. Use **Tab** to move between fields, then press **Enter** to save and connect
7. A QR code appears in your terminal — you're ready to connect from your iPhone

A standard 80x24 terminal window is large enough to display the QR code.

#### Headless mode

If you want to run EngineLink in the background - for example on a server or over SSH - you can skip the interactive interface entirely with `--headless`. Pass the path to Stockfish directly on the command line:

```
./enginelink --headless --engine-path /usr/local/bin/stockfish
```

The QR code prints once to the terminal and status updates appear as plain text. No interactive UI is drawn, so it works over SSH and in scripts. Press **Ctrl+C** to stop.

You can also set engine options:

```
./enginelink --headless --engine-path /usr/local/bin/stockfish --hash 512 --threads 4
```

If you have already configured EngineLink (by running it interactively at least once), you can omit `--engine-path` and it will use your saved settings:

```
./enginelink --headless
```

---

## Connecting from Your iPhone

1. Open **The Marvelous Brass Chessplaying Automaton** on your iPhone
2. Open the app settings (the gear in the top right corner)
3. Find the "Remote Engine" section and press "Connect Remote Engine..."
4. Point your camera at the QR code displayed by EngineLink on your computer
5. Once connected, remote engine analysis is available in the app

In any screen that provides engine analysis (like the analysis board or the course editor), you can switch between using the local or the remote engine.

If you disconnect from the remote engine, you don't have to scan the QR code again: The app will remember how to connect to EngineLink on your home computer, as long as you keep the EngineLink app running.

Your phone and computer do not need to be on the same network - EngineLink works over the internet.

---

## Getting Stockfish

*macOS users can skip this section - Stockfish is already included in the app.*

Stockfish is a free, open-source chess engine and one of the strongest in the world. EngineLink needs it (or any other UCI-compatible chess engine) to provide analysis.

1. Go to [stockfishchess.org/download](https://stockfishchess.org/download/)
2. Download the version for your operating system:
   - **Windows**: Download the Windows ZIP file, extract it, and note where you saved the `stockfish` executable
   - **Linux**: Download the Linux version, extract it, and make it executable:
     ```
     chmod +x stockfish
     ```
3. When EngineLink asks for the engine path, point it to the Stockfish file you just downloaded

Any UCI-compatible engine works with EngineLink, but Stockfish is recommended.

---

## Troubleshooting

**macOS: "Apple could not verify" warning**
Open **System Settings** → **Privacy & Security**, scroll down, and click **Open Anyway**. This only needs to be done once.

**Windows: "Windows protected your PC" warning**
Click **More info**, then click **Run anyway**. This only appears the first time you run the installer.

**QR code not appearing**
EngineLink needs an internet connection to set up the relay. Check that your computer is online and try again.

**Engine not starting**
Make sure the engine path in the configuration screen points to the correct file. On Linux, ensure the file has execute permissions (`chmod +x stockfish`).

**iPhone can't connect after scanning**
Make sure your iPhone has an internet connection. Try closing and reopening The Marvelous Brass Chessplaying Automaton, then scan the QR code again.

**Need to change settings later?**
- **macOS**: Open **Settings** from the menu bar (or press Cmd+,)
- **Windows / Linux (GUI)**: Click **Edit Config** on the main screen
- **Linux (Terminal)**: Press **e** on the main screen
