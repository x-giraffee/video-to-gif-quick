# video-to-gif-quick

Lightweight video-to-GIF skill for users who already have ffmpeg installed. No install guide, just commands.

## Three Commands

```bash
# Compress video (H.264)
ffmpeg -i input.mov -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 96k -y output.mp4

# Simple GIF
ffmpeg -i input.mp4 -vf "fps=10,scale=1200:-1:flags=lanczos" -y output.gif

# Dither-free GIF (no dots, best for UI)
ffmpeg -i input.mp4 -vf "fps=10,scale=1200:-1:flags=lanczos,palettegen=max_colors=256:stats_mode=diff" -y palette.png
ffmpeg -i input.mp4 -i palette.png -lavfi "fps=10,scale=1200:-1:flags=lanczos[x];[x][1:v]paletteuse=dither=none" -y output.gif
```

## One Rule

**UI screen recording → dither=none.**  
**Need smaller size → reduce width, then reduce fps.**

## Full Version

For install guides and FAQ, see [video-to-gif](https://github.com/x-giraffee/video-to-gif).
