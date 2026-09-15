[Русский](README.md) | English

<p align="center">
  <img src="assets/brand/gameque-mark-128.png" width="96" height="96" alt="Gameque">
</p>

<h1 align="center">Gameque</h1>

<p align="center">
  <b>Spotify that pauses itself for your VALORANT matches.</b><br>
  Gameque pauses your music when a match starts and brings it back when the match is over.
</p>

<p align="center">
  <a href="https://github.com/IskhakovMA/Gameque-Releases/releases/latest"><img src="https://img.shields.io/badge/Download-Windows-E8912B?style=for-the-badge&labelColor=0E1013" alt="Download for Windows"></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Windows-10%201809%2B%20%7C%2011-0E1013?logo=windows&logoColor=white" alt="Windows 10 1809+ and Windows 11">
  <a href="https://github.com/IskhakovMA/Gameque-Releases/releases/latest"><img src="https://img.shields.io/github/v/release/IskhakovMA/Gameque-Releases?label=version&color=E8912B&labelColor=0E1013" alt="Latest version"></a>
</p>

<p align="center">
  <img src="assets/hero.png" alt="Gameque pausing Spotify during a VALORANT match">
</p>

---

## What is Gameque

Gameque is a small Windows app that watches your VALORANT match state and handles Spotify for you. When a match begins, your music pauses; when the match ends, it plays again. It works with Spotify Desktop and Spotify Web, and you decide, mode by mode, whether music should pause at all.

## How it works

```
VALORANT  →  Gameque sees a match starting  →  Spotify pauses
          →  match over                     →  music plays again
```

- **When to pause** is your choice: agent select, match loading, or the start of the match itself.
- **Each game mode** has its own setting — keep the music playing in Deathmatch, for example.
- **If you resume the music yourself** mid-match, Gameque leaves it alone until the next match by default. You can change that too.

## Features

- Automatic Spotify pause and resume as the match goes
- VALORANT state detection: menus, queue, agent select, loading, in match
- Spotify Desktop
- Spotify Web through the Gameque browser extension — public installation and store listings are still being prepared ([details](#spotify-desktop-and-spotify-web))
- Configurable pause point
- Per-game-mode behaviour
- Runs in the tray: closing the window does not stop Gameque
- Global shortcuts: show or hide the window (`Ctrl+Shift+H`), turn automation on or off (`Ctrl+Alt+A`)
- Launch with Windows (off by default)
- Automatic update discovery

Russian and English interfaces are already built and ship in the next public release. The current public release is English only.

## Spotify Desktop and Spotify Web

**Spotify Desktop** works out of the box: Gameque controls it through Windows' standard media controls. You never sign in to Spotify through Gameque.

**Spotify Web** in your browser works through the Gameque extension for Chrome and Edge. The Gameque installer already sets up the connection between the app and the browser, but the extension itself is not yet on the Chrome Web Store or Edge Add-ons — store publishing and a simple setup for users are still being prepared. Until then, Spotify Desktop is the most reliable choice.

## Screenshots

<p align="center">
  <img src="assets/screenshots/dashboard.png" alt="Gameque dashboard: match state and Spotify">
  <br><sub>Dashboard</sub>
</p>

<table>
  <tr>
    <td width="50%" align="center">
      <img src="assets/screenshots/settings.png" width="100%" alt="Gameque settings">
      <br><sub>Settings</sub>
    </td>
    <td width="50%" align="center">
      <img src="assets/screenshots/update.png" width="100%" alt="An update available in Gameque">
      <br><sub>Updates</sub>
    </td>
  </tr>
</table>

## Installation

1. Open the [latest release](https://github.com/IskhakovMA/Gameque-Releases/releases/latest).
2. Download `Gameque-<version>-setup.exe`.
3. Run the installer. No administrator rights needed: Gameque installs for your user account.
4. Start Gameque from the Start menu.

If Windows SmartScreen shows a warning, see [the answer below](#why-might-windows-smartscreen-show-a-warning).

## Updates

Installed Gameque checks this repository for a new version by itself — shortly after it starts, then about every six hours.

- A new version is shown in the app, with one Windows notification.
- Nothing is downloaded or installed until you choose to.
- Before running a downloaded installer, Gameque checks its size and SHA-256 against the release's `release.json`. A file that does not match is deleted, never run.
- The update installs over your current version with the normal installer, keeping your settings.

## Security and privacy

- Gameque itself needs no account.
- Gameque learns the VALORANT state only by reading the game's local log file. It does not interfere with the game's processes.
- Spotify Desktop is controlled through Windows' standard media controls; Gameque does not ask for your Spotify account details.
- Checking for updates is an anonymous request to this repository's public releases.
- Installers in each release come with a SHA-256 checksum, and the built-in updater verifies it before running anything.
- This repository contains no Gameque source code.

## System requirements

- Windows 10 version 1809 or later, or Windows 11
- 64-bit (x64) Windows
- VALORANT
- Spotify Desktop or Spotify Web

## FAQ

### Does Gameque need to stay open?

It needs to be running, but you can close the window — it keeps working from the tray. To avoid starting it by hand, turn on launch with Windows in the settings. To quit completely, use the tray icon's menu.

### Does it work with Spotify Desktop?

Yes. It is the main and simplest option.

### Does it work with Spotify Web?

Yes, through the Gameque browser extension. The extension is not yet published on the Chrome or Edge stores — [see above](#spotify-desktop-and-spotify-web).

### Can I turn automation off for Deathmatch?

Yes. Each game mode has its own setting for whether music pauses, in the game modes section of the settings. You can also switch automation off entirely with the switch in the app window, or with `Ctrl+Alt+A`.

### Are updates installed automatically?

No. Gameque finds a new version on its own and tells you about it, but downloading and installing only happen when you choose to.

### Why might Windows SmartScreen show a warning?

The Gameque installer is not yet signed with a code-signing certificate, so SmartScreen may warn about an unknown publisher. Code signing is planned but not set up yet. Only download Gameque from this repository's [releases page](https://github.com/IskhakovMA/Gameque-Releases/releases), and verify the file as described below if you like.

## Verifying a download

Optional — not needed for a normal installation.

Every [release](https://github.com/IskhakovMA/Gameque-Releases/releases) contains three files:

| File | What it is |
|---|---|
| `Gameque-<version>-setup.exe` | The Windows installer |
| `Gameque-<version>-setup.exe.sha256` | Its SHA-256, in `sha256sum` format |
| `release.json` | Version, tag, source commit, installer name, size and checksum |

The files are built and verified by Gameque's release pipeline and uploaded here unchanged; nothing is built in this repository.

To check a downloaded installer, run in PowerShell:

```powershell
(Get-FileHash .\Gameque-<version>-setup.exe -Algorithm SHA256).Hash.ToLower()
```

The result must match the first field of the matching `.sha256` file.

---

Gameque's source code is kept in a private repository. This repository is used only for official releases and update metadata.
