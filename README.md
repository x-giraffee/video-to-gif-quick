# 🎬 Video Compress & GIF (Quick)

> Lightweight. No install guide. Three commands.

---

## What it does

```
Input Video ──┬──▶ Compress ──▶ Small MP4 (5x smaller)
              │
              └──▶ GIF ───────▶ Simple / No-Dots
```

---

## The Three Commands

### 1️⃣ Compress

```bash
ffmpeg -i input.mov -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 96k -y output.mp4
```

```
63 MB ──▶ 11 MB
```

### 2️⃣ GIF — Simple

```bash
ffmpeg -i input.mp4 -vf "fps=10,scale=1200:-1:flags=lanczos" -y output.gif
```

### 3️⃣ GIF — No Dots

```bash
ffmpeg -i input.mp4 -vf "fps=10,scale=1200:-1:flags=lanczos,palettegen=max_colors=256:stats_mode=diff" -y palette.png
ffmpeg -i input.mp4 -i palette.png -lavfi "fps=10,scale=1200:-1:flags=lanczos[x];[x][1:v]paletteuse=dither=none" -y output.gif
```

---

## Tweak Guide

| Want | Do |
|------|-----|
| Smaller file | `fps=5` or `scale=640:-1` |
| Chat/IM share | `scale=480:-1` |
| Cut first 30s | `-t 30` |
| Skip intro | `-ss 10` |

---

## Full Version

Need install guide and FAQ? → [video-to-gif](https://github.com/x-giraffee/video-to-gif)

---

## Requires

`ffmpeg` installed. `brew install ffmpeg` on macOS.
