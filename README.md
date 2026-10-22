<p align="center">
  <img src="timecue-logo.png" width="136" height="136" alt="TimeCue logo">
</p>

<h1 align="center">TimeCue</h1>

<p align="center">
  <strong>Timecode-driven show control for Resolume Arena.</strong><br>
  Fire clips and columns, and set or fade any Resolume parameter from LTC or MTC — with the show clock always in view.
</p>

<p align="center">
  <a href="https://github.com/4H1Mzs/TimeCue-Releases/releases/latest"><img alt="Download" src="https://img.shields.io/badge/download-TimeCue%200.14.1-5c8cff?style=for-the-badge"></a>
  <a href="https://timecue.4h1m.com/"><img alt="Website" src="https://img.shields.io/badge/website-timecue.4h1m.com-30343b?style=for-the-badge"></a>
</p>

<p align="center">
  <img alt="Version 0.14.1" src="https://img.shields.io/badge/version-0.14.1-5c8cff">
  <img alt="Windows macOS Linux" src="https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-30343b">
  <img alt="Resolume Arena 7.23–7.28" src="https://img.shields.io/badge/Resolume%20Arena-7.23%E2%80%937.28-d0473b">
  <img alt="Status Preview" src="https://img.shields.io/badge/status-preview-e7a84b">
</p>

<p align="center">
  <a href="#download">Download</a> ·
  <a href="#whats-new-in-09">What's new</a> ·
  <a href="#features">Features</a> ·
  <a href="#interface">Interface</a> ·
  <a href="#quick-start">Quick start</a> ·
  <a href="#bitfocus-companion">Companion</a>
</p>

---

TimeCue is a desktop companion for timecode-driven Resolume shows on Windows, macOS and Linux. It listens to LTC from an audio interface or MTC from MIDI and RTP-MIDI sessions, keeps the incoming clock visible, triggers clips and columns, and sets or fades any parameter in the composition — effects, opacity, blend modes, colours — locked to the timecode.

![TimeCue main window: a live LTC clock, clip cues and parameter fades for Resolume, and a green Resolume connection badge](docs/screenshots/main-window.jpg)

## Download

Get **[the latest TimeCue release](https://github.com/4H1Mzs/TimeCue-Releases/releases/latest)** from the Releases page.

- **Windows x64** — per-user NSIS installer with in-app updates. Windows packages are currently unsigned and may show a SmartScreen warning.
- **macOS Intel and Apple Silicon** — signed and notarized DMG and ZIP packages.
- **Linux x64** — portable AppImage.
- **Bitfocus Companion** — offline `.tgz` module package.

`latest.yml`, `latest-mac.yml` and `latest-linux.yml` are the public update manifests used by TimeCue. `SHA256SUMS.txt` contains checksums for every published artifact.

> [!IMPORTANT]
> TimeCue is preview software. Test the exact build, audio interface, timecode source and Resolume composition before using it in a live show.

## What's new in 0.14

### Arm and disarm

The big transport button is now **Arm cues**. TimeCue listens to the timecode from the moment it opens, but cues fire and parameters are sent only while it is armed — and it always starts disarmed. The top bar, the web remote and Companion show **Armed** or **Disarmed**, and arming never fires cues that already passed.

## What's new in 0.13

### A web remote you can leave open

Follow the show from another computer, a tablet or a phone. The timecode is large and runs smoothly even over Wi-Fi, the next cue with a live countdown is always in view, and the cue list scrolls by itself to keep the next cue visible, with past cues dimmed. Every browser opens **read-only**; controlling TimeCue or editing cues needs the **PIN** set in **Settings → Web remote**, and the link no longer carries a secret. See [Web remote](#web-remote) below.

![TimeCue web remote on a wide screen](docs/screenshots/remote-dashboard.jpg)

## What's new in 0.12

### Resolume autosave with backups

TimeCue can save the open Resolume composition at a fixed interval while you program the show (**Settings → Resolume & timing → Resolume autosave**, 1–120 minutes). After each save it copies the composition into an `Autosave` folder next to it, with the date and time in the name, and keeps the newest 20 — open one in Arena with **File → Open** to go back. TimeCue finds the saved file by itself, and Arena keeps working on its own file without reloading. Autosave is off by default and never travels in show files; while it is on, a pulsing orange **Autosave** badge in the top bar and on the web remote keeps it from being forgotten on a show. Click the badge to turn autosave on or off — or do it from Companion with the new autosave actions, feedbacks and presets.

## What's new in 0.11

### Layer control cues

A new **Layer control** target type acts on a whole layer: **Clear** ejects whatever is playing on it, and **Bypass on/off** and **Solo on/off** switch the layer's bypass and solo. They are set to an explicit state rather than toggled, so a cue gives the same result however often the timecode passes it. Use a pair of cues, such as Bypass on and later Bypass off, for a timed section.

## What's new in 0.10

### Web remote

Prepare cues from your own computer while someone else works in Resolume on the show computer. TimeCue serves its Cue Editor and a control page to browsers in the same network: live clock, next and last cue, Resolume status, Listen, Generator, and Fire and Edit for each cue. See [Web remote](#web-remote) below.

## What's new in 0.9

### Set and fade any Resolume parameter

A cue can now target **any parameter** in the open composition instead of only a clip or column: effect parameters, opacity, layer master, blend modes, bypass, choices and colours. Fades are locked to the timecode — seek into the middle of a fade and Resolume gets the matching value immediately; play in reverse and the fade runs backwards. Between timecode frames, running fades are advanced on the clock for about 60 smooth updates per second.

![Cue Editor with clip cues, a master fade, a Transform scale push-in, a colour fade with the Resolume palette and an instant blend-mode change](docs/screenshots/cue-editor.jpg)

- **Fade** with a start and target value, a duration in seconds (`4s`), frames (`100f`) or timecode, and a linear, ease-in, ease-out or ease-in-out curve
- **Set** a value instantly by leaving the duration empty
- **Continue** from where the previous cue on the same parameter ended by leaving the start value empty
- **Colours** with a colour picker, the parameter's own Resolume palette, and per-channel fades
- **↓ Start / ↓ Target** take the live value from Arena, so a look can be tuned in Resolume and captured without typing numbers

### Pick parameters from the live composition

![Searchable parameter picker listing the Transform parameters of layer 4 with their ranges](docs/screenshots/parameter-picker.jpg)

Every numeric, on/off, choice and colour parameter of the composition, its layer groups, layers and clips — including every video and audio effect — is listed with its range and unit. Type a few words to narrow thousands of parameters down.

### See problems before the show, not during it

![Resolume badge reporting two warnings and two highlighted cues: an empty clip slot and an effect that is no longer in the composition](docs/screenshots/preshow-check.jpg)

The **Resolume** badge shows whether TimeCue is connected. Whenever Resolume reports its composition — on connect and whenever layers, clips or effects change — every cue is checked against it. Empty clip slots, missing layers and columns, moved or removed effects and invalid values are highlighted with the reason.

### Import SMPTE clips with their offsets

![Scan dialog after reading 32 SMPTE offsets from the saved composition file](docs/screenshots/scan-smpte.jpg)

Resolume's API does not report SMPTE offsets, so **Read SMPTE offsets from composition file…** takes them from the saved `.avc` file of the deck that is open in Resolume. Clips are matched by layer, column and name, and Resolume's *SMPTE 1* / *SMPTE 2* inputs map to Engine A and B in dual-engine mode. Save the composition in Arena before reading it.

### Also new

- Bitfocus Companion: Resolume connection and warning variables and feedbacks, a **Stop running test fades** action, and parameter cues in **Trigger a cue now**
- Parameter cues are delivered after a Resolume outage at their current timecode state
- Rescans after an Arena restart update cues instead of duplicating them
- Plain-language connection errors and longer timeouts for large compositions
- Show files with parameter cues need TimeCue 0.9 or newer

## Features

### Two clocks, one clear show state

- One or two independent timecode engines with always-visible clocks
- LTC audio, system MIDI, or native RTP-MIDI source selection independently for each engine
- 24, 25, 29.97 drop-frame/non-drop-frame, and 30 fps timecode
- Forward and reverse decoding with continuity and discontinuity handling
- Raw or delay-compensated clock display

### Clips, columns and parameters

- Trigger a clip by layer and column, or launch a full column across every layer
- Clear a layer, or switch its bypass and solo on or off, on timecode
- `At start`, `At end`, and `During` cue modes with forward, reverse or bidirectional filtering
- Set or fade any parameter: effects, opacity, layer master, blend modes, bypass, choices and colours
- Timecode-locked, smoothed fades with selectable curves
- Composition scan with SMPTE offsets read from the saved composition file
- Manual cue tests, resettable cue state, and `.timecue` show import and export

### Show safety

- Resolume connection badge: connected, connecting, or offline with the reason
- Pre-show check of every cue against the open composition, repeated whenever it changes
- Spreadsheet-style Cue Editor with an explicit Apply/Cancel draft workflow; cues are sorted by timecode when applied
- No automatic update download, installation or restart during a show

### LTC generation and MIDI timecode

- LTC generator with muted internal loopback or audible output to any soundcard
- MTC quarter-frame and full-frame messages with frame-rate detection
- Built-in AppleMIDI/RTP-MIDI session with Bonjour discovery and per-engine peer routing

### Web remote

- Follow the show from another computer, tablet or phone: large, smooth timecode, the next cue with a countdown, and a cue list that keeps the next cue in view
- Read-only by default; unlock a browser tab with the PIN to control TimeCue and edit cues
- The full Cue Editor in the browser, including the live parameter picker
- Edits from the browser and from TimeCue stay in sync; a stale draft never overwrites newer changes
- Off by default; the PIN never leaves the TimeCue computer in show files

### Bitfocus Companion control

- Live clocks, signal health, next-cue countdowns and last-cue results
- Resolume connection and pre-show warning variables and feedbacks
- Generator, input, cue trigger, test-fade stop, cue reset, engine and clock actions
- A coordinated dark preset library for Stream Deck and control surfaces
- Localhost-only by default, with token-protected LAN access

## Interface

### Resolume & timing

![Resolume and trigger timing settings](docs/screenshots/settings-window.jpg)

Set the Resolume address, test the connection, and tune delay compensation, cue match tolerance and the jump threshold.

### LTC generator

![LTC generator settings](docs/screenshots/generator-output.jpg)

Use a muted internal loopback for rehearsals, or route audible LTC to the system default or a selected physical/virtual audio device.

### Companion

![Companion API settings](docs/screenshots/companion-settings.jpg)

Enable the Companion API on this computer, or allow token-protected connections from the local network.

## Quick start

1. Download and install TimeCue from the [latest release](https://github.com/4H1Mzs/TimeCue-Releases/releases/latest).
2. In Resolume Arena, enable **Webserver & REST API** under `Preferences → Webserver`.
3. In TimeCue Settings, set the Resolume address — usually `http://127.0.0.1:8080` — and select **Test connection**. The **Resolume** badge turns green.
4. Select LTC audio, system MIDI, or RTP-MIDI for Engine A and choose the matching input.
5. Add cues in the Cue Editor, or select **Scan Resolume** and **Read SMPTE offsets from composition file…** to import SMPTE clips. For parameter cues, choose **Parameter / effect** and pick the parameter.
6. Start the real timecode source and confirm a stable lock, the expected cue behavior and no warnings on the Resolume badge before the show.

## Bitfocus Companion

Each release includes an offline Companion module, `timecue-<version>.tgz`. Install it as a custom module in Companion and add a **TimeCue** connection to `127.0.0.1:9140`. For Companion on another computer, enable LAN access in **TimeCue → Settings → Companion**, generate an access token, and enter the TimeCue computer's address and the same token in Companion. Keep port `9140` on a trusted show-control network.

## Web remote

![Web remote on a phone](docs/screenshots/remote-phone.jpg)

1. On the TimeCue computer, open **Settings → Web remote**, select **Enable web remote**, choose a **PIN or password** (**New PIN** suggests six digits) and **Save changes**.
2. Select **Copy address** and open it in a browser on the other device. The address contains no secret.
3. The page opens **read-only**: large timecode, the next cue with a countdown and the cue list, which keeps the next cue in view. Scroll by hand to look around; it follows again after a few seconds or with **Follow**.
4. To change anything, select **Locked · Unlock** and enter the PIN. That tab can then use Listen, Generator, **Fire** and **Edit**, and **Edit cues** for the whole list. **Lock** or closing the tab makes it read-only again.

![Cue Editor in the browser](docs/screenshots/remote-editor.jpg)

The browser only talks to TimeCue, and TimeCue talks to Resolume with its own address, so Arena's webserver does not need to be reachable from the other computer. Windows asks once whether TimeCue may accept network connections; allow it for private networks. Anyone on the network can watch unless **Ask for the PIN to view as well** is on. After five wrong PINs a computer is blocked for a minute; use six or more digits, or a password, on shared networks.

![Web remote settings](docs/screenshots/settings-remote.jpg)

## 4H1M

<p align="center">
  <a href="https://4h1m.com/">
    <img src="4h1m-logo-white.png" width="190" alt="4H1M Production">
  </a>
</p>

4H1M, z.s. is a Czech nonprofit audiovisual production serving churches and Christian events through sound, lighting, visuals, livestreaming and video. TimeCue is developed as part of that work and is shared to support reliable, accessible show control for live productions.

<p>
  <a href="https://www.darujme.cz/4h1m"><img alt="Support 4H1M" src="https://img.shields.io/badge/Support%204H1M%20development-f0c75e?style=for-the-badge&logo=heart&logoColor=20252b"></a>
</p>

[4H1M.com](https://4h1m.com/) · [Instagram @4h1m.production](https://www.instagram.com/4h1m.production/)

---

<p align="center">
  <strong>Built for clocks you can trust and cues you can see.</strong><br>
  <sub>TimeCue is an independent project and is not affiliated with Resolume.</sub>
</p>
