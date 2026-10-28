# TurboCap - Video & Screen Recorder Pro

<p align="center">
  <img src="assets/icons/app_icon.png" width="84" height="84" alt="TurboCap Logo"><br>
  <strong>High-Performance 120 FPS Screen Recording & Live Streaming Studio for Windows</strong><br>
  <em>Version 2.6.0 Pro Edition | 100% Free Forever | Zero Watermark | Zero Lag</em>
</p>

<p align="center">
  <a href="#downloads"><img src="https://img.shields.io/badge/Download-Google%20Drive-blue?style=for-the-badge&logo=google-drive" alt="Google Drive Download"></a>
  <a href="#developer--credits"><img src="https://img.shields.io/badge/Author-Abir-10b981?style=for-the-badge&logo=github" alt="Author Abir"></a>
  <img src="https://img.shields.io/badge/FPS-120%20Locked%20CFR-ff2a55?style=for-the-badge" alt="120 FPS">
  <img src="https://img.shields.io/badge/Platform-Windows%2011%20%7C%2010%20%7C%207-00e5ff?style=for-the-badge&logo=windows" alt="Windows Support">
  <img src="https://img.shields.io/badge/License-MIT-purple?style=for-the-badge" alt="MIT License">
</p>

---

## Overview

**TurboCap** is an ultra-lightweight, high-performance screen recording and live streaming studio engineered for Windows. Many ordinary screen recorders suffer from severe frame drops, stuttering, washed-out colors, and intrusive watermarks. 

TurboCap solves these issues completely with:
* **Rock-Solid 120 FPS & 60 FPS (Constant Framerate - CFR):** Enforces a 1ms high-precision Windows multimedia timer (`timeBeginPeriod(1)`) with a 500MB zero-drop thread buffer.
* **Lossless Visual Clarity (CRF 6):** Enforces Full PC sRGB (0-255) BT.709 color matrix, delivering deep rich blacks and razor-sharp text with zero washed-out haze.
* **Live Screen Annotation Toolbar:** Draw directly on the screen with Pen, Arrow, Rectangle Box, Marker, Text tool, and 10-Color Palette during recordings.
* **100% Free & Standalone:** No watermarks, no recording time limits, and bundled with standalone FFmpeg engine (no extra codecs required).

---

## Preview Showcase

<p align="center">
  <img src="assets/screenshots/screen_recorder.png" width="95%" alt="TurboCap Studio Recording Interface">
</p>

---

## Key Features

### 1. Ultra-Smooth 120 FPS & 60 FPS (Esports Grade CFR)
* Hardware-level 1ms multimedia timer eliminates Windows thread sleep jitter.
* 500MB input buffer and thread_queue_size 1024 prevent frame drops during fast motion and high-refresh gaming.

### 2. Lossless Visual Fidelity (CRF 6 & Full PC sRGB)
* Visually lossless master recording quality profile.
* Full BT.709 sRGB color range (0-255) prevents the washed-out grey haze found in traditional recording tools.

### 3. Floating Screen Annotation Toolbar
* Floating transparent drawing bar with quick keyboard shortcuts:
  * **Pointer Tool:** Standard desktop mouse interaction.
  * **Pen Tool:** Freehand sketching and notes.
  * **Arrow Tool:** Point out buttons, menus, and UI components.
  * **Rectangle Box:** Highlight windows and text areas.
  * **Marker / Highlighter:** Translucent highlighting over documents and code.
  * **Text Tool:** Inline click-to-type text anywhere on the screen.
  * **10-Color Palette:** Vibrant neon colors with instant undo and clear.

### 4. Studio-Grade 320 kbps AAC Audio
* High-fidelity 320 kbps 48kHz stereo sound recording.
* Independent microphone and desktop system audio capture with real-time VU visualizer meters.

### 5. Multi-Platform RTMP Live Streaming
* Direct live broadcasting to YouTube Live, Facebook Live, Twitch, and Kick with customizable bitrates and low-latency tuning.

### 6. Standalone & Privacy-First
* Bundled with FFmpeg 64-bit engine - zero extra installs or codecs needed.
* Zero telemetry, zero bloatware, and zero background services.

---

## Screenshots Gallery

| Studio Recorder View | 120 FPS Esports Settings |
|:---:|:---:|
| <img src="assets/screenshots/screen_recorder.png" width="460" alt="Studio Recorder"> | <img src="assets/screenshots/screen_settings.png" width="460" alt="120 FPS Settings"> |
| **Verified & Authored by Abir** | **Floating Annotation Toolbar** |
| <img src="assets/screenshots/screen_about.png" width="460" alt="About Tab"> | <img src="assets/screenshots/screen_toolbar.png" width="460" alt="Toolbar"> |

---

## Downloads

* **Standalone Setup Installer (Google Drive Mirror):**
  [Download TurboCap_Setup.zip on Google Drive](https://drive.google.com/file/d/1kuxVeJvwLijQ-79vS04lNrCdkZOWHamQ/view?usp=sharing)
* **GitHub Releases:**
  Available under the Releases tab of this repository.

---

## Default Keyboard Hotkeys

| Hotkey | Action |
|:---:|:---|
| **F9** | Start Recording / Pause / Resume |
| **F10** | Stop Recording & Auto-Save Video |
| **Camera Icon** | Instant High-Resolution Screen Snapshot |

---

## Building from Source

TurboCap is built in pure C# using Windows Forms and .NET Framework 4.0 - 4.8. It requires no heavy Visual Studio IDE installation to compile.

### 1. One-Click Compile
Double-click `build.bat` in the project root folder, or run in PowerShell / CMD:
```cmd
build.bat
```

### 2. Manual Command-Line Compilation (csc.exe)
```cmd
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe /nologo /target:winexe /optimize+ /win32manifest:app.manifest /win32icon:app.ico /out:TurboCap.exe /r:System.dll,System.Core.dll,System.Drawing.dll,System.Windows.Forms.dll *.cs
```

### 3. Packaging Standalone Installer (Inno Setup)
To build `TurboCap_Setup.exe`:
1. Install [Inno Setup 6](https://jrsoftware.org/isdl.php).
2. Right-click `installer.iss` and click **Compile**, or run:
```cmd
iscc installer.iss
```

---

## Repository Structure

```text
TurboCap/
|-- assets/
|   |-- icons/
|   |   `-- app_icon.png      # Application logo
|   `-- screenshots/          # High-resolution screenshots
|       |-- screen_recorder.png
|       |-- screen_settings.png
|       |-- screen_about.png
|       `-- screen_toolbar.png
|-- AreaSelectorForm.cs       # Custom region selection with crosshair
|-- AssemblyInfo.cs           # Assembly metadata & Abir credits
|-- FloatingToolbarForm.cs    # Floating annotation toolbar UI
|-- GlobalHotkeys.cs          # Low-level Windows keyboard hook (F9, F10)
|-- IconFactory.cs            # Dynamic vector icon generation
|-- MainForm.cs               # Main studio viewport, modes & settings
|-- Program.cs                # Application entry point
|-- RecorderEngine.cs         # FFmpeg CFR 120 FPS high-precision engine
|-- RecordingBorderForm.cs    # Glowing red capture boundary overlay
|-- RecordingFinishedDialog.cs# Instant preview dialog after capture
|-- ScreenDrawOverlay.cs      # Transparent canvas for pen, shapes & text
|-- ThemeManager.cs           # Cyber-Dark UI colors & styles
|-- app.ico                   # High-res application icon
|-- app.manifest              # Windows DPI awareness & admin privileges
|-- build.bat                 # 1-Click C# compiler script
|-- installer.iss             # Inno Setup 6 installer script
|-- preview_wallpaper.jpg     # 4K mountain lake viewport wallpaper
|-- LICENSE                   # MIT License
`-- README.md                 # Project documentation
```

---

## Developer & Credits

* **Developer:** Abir
* **Product:** TurboCap Pro Edition (v2.6.0)
* **License:** [MIT License](LICENSE) - 100% Free and Open Source.

---

<p align="center">
  Developed by <strong>Abir</strong>
</p>
