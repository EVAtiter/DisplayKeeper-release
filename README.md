[English](README.md) | [日本語](README.ja.md)

# DisplayKeeper

A macOS app that shows the detailed settings of your displays, lets you change them, saves them to a file, and restores
them later — just by double-clicking the file.

Resolution, refresh rate, rotation, arrangement and mirroring often change after you swap a dock or a cable, wake from
sleep, or update macOS. Save your setup once, and DisplayKeeper puts it back.

---

## Download

Download the latest version from [Releases](https://github.com/EVAtiter/DisplayKeeper-release/releases/latest).

1. Unzip `DisplayKeeper-x.x.x.zip` and move `DisplayKeeper.app` to the Applications folder
2. Open DisplayKeeper. No special permission is needed

You can also install it with Homebrew.

```bash
brew install --cask EVAtiter/tap/displaykeeper
```

If Homebrew 7 or later reports an "untrusted tap", trust displaykeeper first with the command below, then install again.

```bash
brew trust --cask evatiter/tap/displaykeeper
```

---

## How to use

### Save

- **File → Save All Displays…** (⌘S) saves the settings of every connected display to one file (`.dkset`)
- **File → Save This Display…** (⇧⌘S) saves one display (`.dkdisplay`). Use it on that display's tab
- **File → Save Each Display to Folder…** (⌥⌘S) saves every display to its own file in a folder you choose
- In the save panel, choose which items to include. Items left out are not changed when the file is applied

### Restore

- **Double-click a saved file** while DisplayKeeper is not running. DisplayKeeper applies the settings without opening a
  window and quits. It shows a message only when something could not be applied
- Hold **⌥ (Option)** while double-clicking to open the file in the window instead, without applying it
- Add a saved file to **System Settings → General → Login Items** to restore your setup every time you log in

### Check before applying

Open a file from **File → Open…**, drag it onto the window, or double-click it while DisplayKeeper is running.
DisplayKeeper shows which connected display each entry matches and what will change. Click **Load as Changes**, then
**Apply** in the window. A file for one display can also be loaded into another display (for example, a monitor of the
same model).

### Change settings

Each display has its own tab. Change a value, then click **Apply** at the bottom of the window — nothing changes until
you do. After you apply a new resolution, refresh rate, rotation or mirroring, DisplayKeeper asks whether to keep it.
If you do not answer within 15 seconds, the previous settings come back, so you are safe even if the screen goes blank.

To change the arrangement, drag a display in the diagram on the **Overview** tab. It snaps to nearby edges, and goes
back if you drop it over another display.

### Use from the Shortcuts app

Two actions are available: **Apply DisplayKeeper File** and **Save Current Display Settings**. Both run without
opening a window. The save action returns a `.dkset` file, so use the **Save File** action to choose where it goes.

### Use from the command line

When installed with Homebrew, the `displaykeeper` command is available.

```bash
displaykeeper apply ~/Displays.dkset   # apply a file
displaykeeper save ~/Displays.dkset    # save all displays
displaykeeper dump                     # print the current state
```

The exit status is 0 for success, 1 when some settings were not applied, and 2 for an error.
Without Homebrew, run `/Applications/DisplayKeeper.app/Contents/Resources/displaykeeper`.

---

## Features

- **Display information** — maker and model, year and week of manufacture, connection, physical size and pixel
  density, current mode and every available mode, color profile, brightness, and DDC/CI values
- **Settings you can change, save and restore** — resolution and refresh rate, rotation, arrangement, main display,
  mirroring, color profile, reference mode (built-in XDR displays and others), HDR, built-in display brightness, and
  brightness and contrast of external monitors over DDC/CI
- **Matching** — a saved display is found again by its UUID, serial number, model and port, even after it is
  reconnected
- **Japanese / English**

---

## Notes

- DDC/CI (brightness and contrast of external monitors) works only with monitors that support it. It may not work
  through a USB-C to HDMI adapter, a hub or a switch. When it does not, the display's tab shows the reason
- Reference modes such as HDR Video or Internet & Web (sRGB) fix the brightness of the built-in display, so the
  brightness is not changed while one of them is selected
- The resolution and rotation of a display that mirrors another follow the mirror source and are not changed separately
- When a file is applied by double-clicking, only values that are available on this Mac right now are applied.
  If a display in the file is not connected yet, DisplayKeeper waits up to 10 seconds for it
- HDR switching has not been tested yet with an HDR monitor

---

## Privacy

DisplayKeeper does not use the network. It does not record what you do or store personal information.
To read and change display settings that macOS does not offer to apps, it uses some private macOS frameworks
(SkyLight, MonitorPanel, DisplayServices, CoreDisplay and IOAVService). Because of this, it is not on the Mac App Store.

---

## Requirements

macOS 14 Sonoma or later (tested on macOS 27.2) / Apple Silicon (arm64) only / Notarized by Apple

---

## Acknowledgments

DisplayKeeper is based on knowledge from [Crisp](https://github.com/didriksg/Crisp) (MIT License). The license text is
shown in **About DisplayKeeper**.

---

Copyright © 2026 EVA Titer. All rights reserved.
