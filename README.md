# ECHO LINK Desktop — Starter v0.1

A Windows desktop starter for the ECHO LINK phone-to-PC projection project. It provides a dark PySide6 dashboard, Android Debug Bridge (ADB) device discovery, wireless ADB pairing/connection helpers, and launches scrcpy for real-time Android screen projection.

## Features
- Dark dashboard with Home, Devices, Projection and Settings sections.
- Discover devices connected through ADB and refresh the device list.
- Connect to an Android device over Wi-Fi using its IP address and port.
- Start Android Wireless Debugging pairing with a pairing code.
- Launch scrcpy for the selected device.
- Configure orientation, maximum video size, frame rate and fullscreen mode.
- No credentials are saved and no device data is sent to a server.

## Current limitations
- This is a starter, not the finished ECHO LINK platform.
- scrcpy projection opens in a separate window; it is not embedded in the dashboard.
- scrcpy's maximum-size option is not an exact custom output resolution.
- Orientation behavior depends on the device, Android version and scrcpy version.
- Virtual landscape display, exact custom resolutions, PC-to-phone streaming, and the Android companion app are future milestones.

## Requirements
- Windows 10 or 11
- Python 3.10+
- Android phone with Developer Options enabled
- [scrcpy for Windows](https://github.com/Genymobile/scrcpy/releases)
- [Android Platform Tools / ADB](https://developer.android.com/tools/releases/platform-tools)

## Install and run
Open PowerShell in this repository folder:

```powershell
py -3 -m venv .venv
.\.venv\Scripts\python.exe -m pip install --upgrade pip
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe main.py
```

If you prefer activation, run `.\.venv\Scripts\Activate.ps1` first and then use `python main.py`.

## Add ADB and scrcpy
Recommended layout:

```text
echo-link-desktop/
  main.py
  requirements.txt
  tools/
    platform-tools/   # place adb.exe and its supporting files here
    scrcpy/           # place scrcpy.exe and its supporting files here
```

You can also install ADB and scrcpy separately and put them on your Windows PATH.

## First USB test
1. Enable Developer Options > USB debugging on Android.
2. Connect the phone to the PC and accept the debugging prompt.
3. Click Refresh in ECHO LINK and select the device.
4. Click Start Projection.

## Wireless setup (Android 11+)
1. Connect the phone and PC to the same Wi-Fi network.
2. Enable Developer Options > Wireless debugging on the phone.
3. Use Pair over Wi-Fi with the IP address, pairing port and pairing code shown on Android.
4. Use Connect over Wi-Fi with the separate IP address and port shown on the main Wireless debugging screen.
5. Refresh the device list and select the network device.

Wireless debugging ports can change. Do not expose ADB ports to public networks.

## Troubleshooting
- **No devices found:** install Platform Tools, check ADB availability, authorize the PC and refresh.
- **Unauthorized:** unlock the phone and accept the USB debugging prompt.
- **scrcpy not found:** put scrcpy and its supporting files under `tools/scrcpy/` or add it to PATH.
- **Wireless connection fails:** pairing and connection use different ports.
- **PowerShell activation blocked:** use the venv Python executable directly.

## Roadmap
1. Embed projection into the ECHO LINK workspace.
2. Improve orientation and virtual-display handling where supported.
3. Add secure device pairing independent of ADB.
4. Build ECHO LINK Mobile in Kotlin.
5. Add PC-to-phone streaming, clipboard and file sharing.
