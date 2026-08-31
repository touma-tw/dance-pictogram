# Dance Pictogram — User Guide

A strip of move cues scrolls beside the video while you dance, showing what comes next a
moment before it happens. Built for [PyPyDance](https://pypydance.com/) in VRChat.

**Languages:** English · [繁體中文](tc.md) · [简体中文](sc.md) · [日本語](jp.md) · [한국어](ko.md)

---

## 1. Install

1. Download the latest `DancePictogram-x.y.z.zip` from
   [Releases](https://github.com/touma-tw/dance-pictogram/releases).
2. Unzip it anywhere — Desktop is fine. Avoid `C:\Program Files`, the app writes its song
   data next to itself.
3. Run `DancePictogram.exe`.

No installer, no account, no key. To uninstall, delete the folder.

## 2. Get some songs

The app ships empty. Open the **Songs** tab.

**The quick way** — press one of the pack buttons at the top:

| Button | What you get |
|---|---|
| **Pictogram** | A drawn figure with arrows. 851 MB for all 598 routines. |
| **Real dancer** | The dancer cut out of the video, same arrows over it. 1632 MB. |
| **Everything** | Both styles. 2244 MB. |

Then press **Download selected**. It takes a few minutes and you can keep using the app
meanwhile.

**The picky way** — type in the search box and press Enter, tick the routines you want, then
**Download selected**. Only those routines are downloaded, not the whole pack.

Search accepts plain words (title, artist, genre, id) and filters you can combine:

```
twice                 anything matching "twice"
artist:twice          only that artist
mode:multi            routines with several coaches to choose from
genre:kpop            by genre
installed:no          things you do not have yet
```

Once everything is installed the pack buttons fold away. Click the header to bring them back.

## 3. Set it up in VR

Go to the **Overlay** tab and press the big **Start** button. Then, in VRChat:

- **VR distance** — how far away the strip floats. Push it out to roughly the depth of the
  video screen so your eyes do not have to refocus between the two.
- **VR scale** — how big it looks, independent of distance.
- **Pin in room** — freeze the strip in place instead of letting it follow your head.
- **Pictogram / Real** — which picture style to show.

There is also a small panel floating over the back of your **right hand**. Look at a button
for a moment to press it. It has **PIN** (re-place the strip without switching back to the
desktop) and **STYLE**.

## 4. While you dance

The app knows which routine is playing by reading the VRChat log, and knows *where* in the
routine you are by listening to your speakers. You do not have to tell it anything.

**If VRChat is not installed in the default location**, the app cannot find the log and will
fall back to identifying routines by sound alone — which cannot tell apart routines that share
a soundtrack. Fix it by editing `config.toml` next to the app, in the `[log]` section:

```toml
[log]
dir = '%USERPROFILE%\AppData\LocalLow\VRChat\VRChat'   # <- change this line
```

Point it at the folder holding your `output_log_*.txt` files. Keep the single quotes — they
stop the backslashes being read as escape characters. Save the file and restart the app.

**Multi-dancer routines** show one lane per coach. When one starts, a picker appears in front
of you — look at the coach you want to follow for two seconds.

**Timing feels slightly off?** Overlay tab → `video_lag_sec` in `config.toml`, or just tell
us. Positive holds the cues back, negative shows them earlier. A cue you have to move to can
be worth showing a little early.

## 5. Recording with OBS

A SteamVR overlay sits on top of VRChat's frames, so VRChat's own camera cannot see the strip.
Turn on **Spout → OBS** in the Overlay tab, then in OBS add a **Spout2 Capture** source and
pick `DancePictogram`. Stack it over your VRChat camera source and set the composite mode to
straight (non-premultiplied) alpha.

## 6. If something is wrong

**The strip is blank.** Nothing is playing, or the app cannot hear it. Check the audio device
in the Overlay tab — it should be the *loopback* of whatever plays VRChat's sound.

**The strip shows the wrong routine.** It reads the VRChat log; if VRChat is not running, it
falls back to identifying by audio, which cannot tell apart routines that share a soundtrack.

**Cues are wrong or badly timed for one routine.** That happens — the cues are generated
automatically, and routines with fast cuts, motion blur, or several dancers crossing come out
worse. [Open an issue](https://github.com/touma-tw/dance-pictogram/issues) with the routine
id. Regenerated routines ship in later batches and the app updates only what changed.

**Updating.** The app checks for new and revised routines at startup. The Songs tab shows
what changed; press **Install everything missing**.
