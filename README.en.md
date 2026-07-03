# JAVOTT

[한국어](README.md) · **English**

A desktop media library app for managing locally stored video files. Register a folder and JAVOTT automatically fills in posters, plots, and cast metadata, and handles subtitle extraction, mosaic removal, and remote playback — all in one app.

It's a Windows desktop app. Turn the running PC into a server and you can reach your library from a browser on another device (TV, phone, laptop) over your local network or the internet.

> This repository distributes **release builds only**. The source code is closed and is not included here.

> ⚠️ **Notice**: JAVOTT is a personal media library tool that may include adult content. You must meet the minimum age required by your local laws to possess or view adult content, and you are solely responsible for complying with copyright and other applicable laws. If you enable remote access, make sure to set an admin password and web PIN to keep out minors and unauthorized users.

## Table of Contents

- [Key Features](#key-features)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Screens](#screens)
  - [All Movies](#-all-movies)
  - [Player](#-player)
  - [Library Manager](#-library-manager)
  - [Library Folders](#-library-folders)
  - [Subtitle Extraction](#🅲🅲-subtitle-extraction)
  - [Mosaic Removal](#-mosaic-removal)
  - [Server Setup](#-server-setup)
  - [Settings](#-settings)
- [FAQ and Troubleshooting](#faq-and-troubleshooting)
- [License and Third-Party Notices](#license-and-third-party-notices)

## Key Features

- 📁 **Folder-based libraries** — register a folder with videos and JAVOTT scans it into your library. Optionally include subfolders, and cancel a scan or metadata refresh at any time.
- 🖼 **Poster-first browsing** — sort, filter, favorites, a poster-size slider, and adjustable title line count, all tuned to your taste.
- ▶ **Built-in player + external player support** — a full-featured built-in player with shortcuts, or hand playback off to IINA, VLC, PotPlayer, or another external player.
- 🌐 **Automatic online metadata** — recognizes the product code in a filename and fetches posters, fanart, plot, and cast info online. New files can be refreshed automatically as they're detected.
- 📝 **NFO-based metadata** — stores and syncs metadata as NFO files compatible with Kodi/Jellyfin-style tools.
- ⌗⌗ **Spreadsheet-style library grid** — select multiple cells and copy/paste or bulk-edit like Excel.
- 🅲🅲 **Subtitle extraction** — queue videos without subtitles for automatic extraction powered by Faster-Whisper-XXL.
- ▦ **Mosaic removal** — manage LADA-based mosaic removal jobs as a queue with live progress.
- 🔒 **Built-in remote-access server** — an embedded HTTPS server lets you reach your library from a browser on your LAN or over the internet, with admin password, web PIN, and automatic Windows certificate issuance.

## Installation

1. Download the latest Windows installer (`JAVOTT_x.x.x_x64-setup.exe`) from [Releases](../../releases).
2. Run the installer. During setup you'll be asked whether to **install FFmpeg** as well.
   - FFmpeg is used for codec analysis and AV1 transcoded playback. If you accept, the installer downloads the win64 lgpl-shared build from [BtbN FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds) into the install folder.
   - You can skip this — if FFmpeg is already installed on your system later, JAVOTT will find and use it automatically.
3. Launch JAVOTT once installation finishes.

### System Requirements

- Windows 10/11 (x64)
- An internet connection is required for remote access (server); port forwarding is needed for access from outside your network.
- Mosaic removal is much faster with a GPU (NVIDIA CUDA recommended). It also works on CPU alone, just slower.

## Quick Start

1. Add a folder with your videos in **Library Folders**.
2. Run **Scan Library** to detect the video files.
3. Browse your library in the **All Movies** poster grid.
4. Fix any missing or incorrect metadata in **Library Manager**, or run a metadata refresh.
5. Queue videos without subtitles in **Subtitle Extraction**, and videos needing mosaic removal in **Mosaic Removal**.
6. Set up your external player, shortcuts, and language in **Settings**.
7. To watch from other devices, turn on the server in **Server Setup** and note the connection address.

## Screens

You move between these screens from the left sidebar. Subtitle extraction and mosaic removal queues show a number badge next to the menu when jobs are pending, and a progress popup appears at the bottom of the screen whenever a scan or metadata refresh is running — no matter which screen you're on (it keeps going if you navigate away, and you can cancel it right from the popup).

### 🎬 All Movies

![All Movies screen](./screenshots/cinema.png)

The home screen: a poster-first gallery of your registered movies.

- Browse all libraries or one at a time, search, filter by genre/actor/studio, show favorites only
- Sort by recently added, release date, title, rating, or play count, ascending or descending
- Adjust poster size (slider), title line count, and title text size
- Posters show favorite, subtitle-availability, and mosaic-status (Censored/Uncensored/Reduced) badges
- Selecting a movie opens a detail view with the full metadata (plot, cast, tags, etc.), where you can play or toggle favorite directly

### ▶ Player

![Player screen](./screenshots/player.png)

The built-in playback screen, opened by clicking a movie.

- Play/pause, mute, seek, volume, fullscreen, resume, subtitle toggle, black screen, automatic playback position saving
- Shortcuts can be freely rebound in Settings
- Turning on **Server Setup > Use transcoding** makes the server transcode videos in real time when the playback device doesn't support a codec (e.g. AV1). This adds server load and can reduce playback performance, so only enable it when needed.
- Register an external player (IINA, VLC, PotPlayer, etc.) in Settings to have the play button launch it instead of the built-in player.

### 📁 Library Manager

![Library Manager screen](./screenshots/manage.png)

A spreadsheet-style grid for viewing and editing movie metadata at a glance.

- Freely resize, show/hide, and reorder columns; click a header to sort
- Edit cells directly, or select multiple cells to copy/paste or bulk-fill (Ctrl+D) like Excel
- Editing title, original title, studio, director, year, rating, plot, genres, tags, cast, subtitle language, mosaic status, etc. updates both the DB and the NFO
- Run metadata refresh, external playback, permanent delete, subtitle preview, or queue subtitle extraction/mosaic removal for the selected movie(s)
- New video files get a minimal NFO automatically; **Settings > Library Automation** can also auto-refresh online metadata for new files (off by default — it adds network lookups that can slow things down)

### 🗂 Library Folders

![Library Folders screen](./screenshots/manage-libraries.png)

Reached from the Library Manager screen — manage the folders themselves here.

- Add folders (multi-select supported), rename, reorder, or remove them
- Scan a library (optionally including subfolders, with or without codec analysis)
- Refresh all metadata, rewrite NFOs
- Both scanning and refreshing can be cancelled at any time while running

### 🅲🅲 Subtitle Extraction

![Subtitle extraction screen](./screenshots/subtitle.png)

Extract and manage subtitles powered by Faster-Whisper-XXL.

- Install the tool (download or copy a local bundle), with install progress shown
- Queue library movies or arbitrary files, processed in order
- Configure language (Japanese/Korean/English/auto-detect), model (medium/large-v2/large-v3), output format (SRT/VTT), and device (auto/cpu/cuda)
- Start/pause the queue, cancel/delete/retry jobs, reorder, and check progress and logs

### ▦ Mosaic Removal

![Mosaic removal screen](./screenshots/mosaic.png)

Manage LADA-based mosaic removal jobs as a queue.

- Install the NVIDIA/Intel package, set output/temp folders and output filename pattern
- Save your favorite encoder + option combinations as presets
- Fine-tune device (cuda:0/cpu) and other options
- Live progress during processing: resolution, FPS, processing speed, estimated time remaining
- When a job finishes, that movie's mosaic status automatically updates to Reduced

### 🌐 Server Setup

![Server setup screen](./screenshots/server.png)

Turn your PC into a server so TVs and phones on the same network — or, after port forwarding, devices outside it — can reach your library from a browser.

- Port, public domain, and public port settings; start automatically on Windows login
- Admin password and web PIN (a second lock) settings
- Generate a Windows certificate auto-issuance batch file for a DuckDNS domain (powered by win-acme)
- Open the inbound port on the Windows Firewall

> The server feature exposes the app to your network. If you open it up for outside access, **make sure to set an admin password and web PIN**.

### ⚙ Settings

![Settings screen](./screenshots/settings.png)

Adjust your overall app experience here.

- Playback: resume prompt, autoplay
- Language: Korean and English are the primary supported languages right now; Japanese has only basic scaffolding in place
- Register/manage external players, change shortcuts
- Genre mapping (Japanese ↔ Korean)
- Library automation: whether to auto-refresh metadata for new files

## FAQ and Troubleshooting

**Movies aren't showing up in my library.**
Check that the library folder path is correct and the file extension is supported, then run a library scan again.

**A poster or some metadata looks wrong.**
Select the movie in Library Manager and run a metadata refresh, or edit the value directly in the grid and save.

**The subtitle preview button is disabled.**
This means there's no subtitle file next to the video. Try queuing it for subtitle extraction.

**Subtitle extraction or mosaic removal fails.**
Check that the tool (Faster-Whisper-XXL / LADA) is installed and that the device setting (cpu/cuda) matches your PC, then expand the log to check the error message.

**I can't connect remotely.**
Check that the server is running and that you're using the address it shows, then try opening the port on the Windows Firewall. Over the public internet, also check your router's port forwarding and certificate setup.

**I want to stop a scan or metadata refresh in progress.**
While a job is running, a stop button appears in the popup at the bottom of the screen (visible on any screen). Clicking it finishes the current item and cancels the rest.

## License and Third-Party Notices

- JAVOTT is closed-source software. This repository is for distributing executables only; no rights to the source code are granted.
- **FFmpeg**, optionally downloaded during installation, is the win64 `lgpl-shared` build from [BtbN FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds) and is distributed under the GNU LGPL. The full license text and source information are available after installation from the app's Settings screen (open-source notice) and in the install folder's `ffmpeg/licenses/`, `THIRD_PARTY_NOTICES.txt`, and `SOURCE-OFFER.txt`.
- Subtitle extraction calls out to [Faster-Whisper-XXL](https://github.com/Purfview/whisper-standalone-win), and mosaic removal calls out to [LADA](https://github.com/ladaapp/lada), as separate tools. Each tool's license follows its own project.
