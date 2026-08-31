# Dance Pictogram

Move cues for dancing along in VR. A strip of pictograms scrolls beside the video, showing
what the next move is a moment before it happens — the same idea as the cue bar in dance
games, generated automatically for routines that never had one.

Built for [PyPyDance](https://pypydance.com/) in VRChat. Works as a SteamVR overlay, as a
desktop window, and as a Spout source for OBS.

**Full user guide:** [English](readme/en.md) · [繁體中文](readme/tc.md) ·
[简体中文](readme/sc.md) · [日本語](readme/jp.md) · [한국어](readme/ko.md)

![strip](https://raw.githubusercontent.com/touma-tw/dance-pictogram/main/docs/strip.png)

## Getting it

1. Download the latest release below and unzip it anywhere.
2. Run `DancePictogram.exe`.
3. Open the **Songs** tab and press a download pack. The app fetches the routines itself.

Nothing else to install. No account, no key, free.

## How it works

The app listens to what your speakers are playing and reads the VRChat log to know which
routine is on and how far into it you are, then scrolls the cues for that routine in time
with the music. Two picture styles are available and you can switch between them in VR:

- **Pictogram** — a drawn figure with arrows for the direction of each movement
- **Real dancer** — the same cues drawn over a cutout of the dancer from the video

Multi-dancer routines get one lane per coach, and you pick which coach to follow by looking
at them.

## Song data

The app ships empty and downloads what you ask for. Two ways, and it chooses for you:

- Press a **pack** button to install a whole batch in one go
- Or search the list and tick individual routines — the app then pulls only those songs out of
  the pack, by byte range, instead of downloading the whole thing

| | |
|---|---|
| Routines | 598 |
| Pictogram style | 851 MB |
| Real dancer style | 1632 MB |

Both styles can be installed side by side. New batches arrive as new releases; the app
notices and offers to update only what changed.

The data lives in this repository's releases. `index.json` is the catalogue — it lists every
routine and the address of the pack holding it, which is why the app only ever needs to know
one URL.

## Requirements

- Windows 10 / 11
- SteamVR, for the in-headset overlay (the desktop window works without it)
- VRChat, for automatic routine detection

## Reporting a problem

Open an issue. A routine with badly timed or wrong cues is worth reporting with its id — the
cues are generated automatically and are regenerated in later batches, so a bad one can be
fixed for everyone.

## Licence

The application is free to use and is not open source. The song data is covered by
[`LICENSE`](LICENSE): free for personal practice, no redistribution, no commercial use, no
model training.

The routines themselves come from videos published on PyPyDance. The choreography, the
performances, and the music belong to their respective rights holders — this project only
distributes the movement cues and the pictures generated from them, never audio or video. If
you hold rights in a routine here and want it removed, open an issue.
