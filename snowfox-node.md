# 🦊 SnowFoxOS v3 — The `snowfox node` Concept

The `snowfox node <mode>` command centrally controls the entire workflow of SnowFoxOS-v3. It acts as a **State Switcher** that starts or stops services, adjusts i3 window rules, and loads the appropriate user interface depending on the selected mode.

## 📊 The 3 Core Modes

| Mode | Focus | Primary Architecture Changes |
| :--- | :--- | :--- |
| `desktop` | Productivity & Daily Driving | Loads the default i3 setup with Gaps, Polybar, Picom (compositor), PCManFM, and all standard background services utilizing the signature SnowFox purple design. |
| `server` | Resources & Headless Operation | Switches the system into a minimal headless or terminal-only setup. Completely deactivates the X-Server/i3 or pauses unneeded GUI services to maximize hardware resources for server daemons (e.g., Docker). |
| `console` | Gaming & Immersion | Switches into a dedicated, controller-driven fullscreen interface. Optimizes the hardware for maximum gaming performance and operates entirely offline. |

---

## 🎮 Deep Dive: The `console` Mode

The focus of the gaming mode is to ensure **maximum performance**, **full gamepad support**, and a **100% offline-capable local web app (HTML/CSS/JS)** acting as the launcher interface (bundled via Tauri or managed by a lightweight local Node.js/Python backend).

### 1. UI & Display Adjustments (i3wm Control)
* **Kill Polybar:** Running `killall polybar` removes all system bars to ensure an immersive, distraction-free gaming experience.
* **Zero Gaps:** Via `i3-msg`, all inner/outer gaps and window borders are set to `0` (`border none`). This forces the gaming web app and launched games into true, seamless fullscreen.
* **Mute Dunst:** The notification daemon is blocked or switched to "Do Not Disturb" mode, ensuring only critical system alerts (e.g., critical battery levels) break through.
* **Disable X11 Screensaver:** Executing `xset -dpms s off` and `xset s off` prevents the screen from dimming or sleeping during pure controller gameplay.

### 2. Performance Optimizations (FPS Boost)
* **Kill Compositor:** Running `killall picom` disables window transparencies and shadows, which drastically reduces input lag, frees up GPU resources, and eliminates screen tearing in games.
* **CPU Governor Switching:** The system automatically forces the *Performance* energy profile to lock the CPU at maximum clock speeds.
* **Pause Background Daemons:** Active background synchronization tasks (e.g., MEGA cloud sync) are temporarily suspended to preserve storage I/O and network bandwidth for the active game.

### 3. Controller Integration & Input Mapping
* **Native Gamepad API:** The front-end web app utilizes the browser's native Gamepad API to handle input from Xbox, PlayStation, and Nintendo Switch controllers directly in JavaScript for smooth menu navigation.
* **System-wide Home Button Mapping:** The Xbox/PS Guide button is intercepted at the system level. A long-press triggers a background script that gracefully kills the active game (`killall`) and instantly routes the user back to the launcher's main menu.

### 4. Local Game Discovery & Offline Downloads (Zero Web-API Dependencies)
* **Local Parsing:** A lightweight background script scans local configuration files, such as Steam's `.acf` manifests located in `~/.steam/steam/steamapps/` as well as Heroic/Lutris databases, to index installed titles.
* **Cached Artwork:** The launcher pulls game covers directly from local cache directories (e.g., Steam's `.../librarycache/` or Heroic caches). It relies on **no external web APIs**, protecting user privacy and ensuring full offline functionality.
* **CLI Download Bridge:** Game downloads and updates are triggered within the clean web interface but executed reliably in the background via established CLI utilities:
    * `steamcmd` for Steam titles.
    * `legendary` for Epic Games.
    * `gogdl` for GOG.
  The web app hooks into the terminal output stream to capture and visualize download progress metrics using a custom purple HTML/CSS progress bar.
