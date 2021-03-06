---
title: (cli-tasks) animated GIFs [devhints]
tags: [cli-tasks,images,gif]
---

## Animated GIFs

### Convert MP4 to GIF

```sh
mkdir -p gif
mplayer -ao null -vo gif89a:outdir=gif $INPUT
mogrify -format gif *.png
gifsicle --colors=256 --delay=4 --loopcount=0 --dither -O3 gif/*.gif > ${INPUT%.*}.gif
rm -rf gif
```

You'll need `mplayer`, `imagemagick` and `gifsicle`. This converts frames to .png, then turns them into an animated gif.

### A given range

```sh
mplayer -ao null -ss 0:02:06 -endpos 0:05:00 -vo gif89a:outdir=gif videofile.mp4
```

See `-ss` and `-endpos`.
