# vidclip

Trim and merge videos using TOML.

## Installation

```
$ pip install vidclip
```

Requires [FFmpeg](https://ffmpeg.org/).

## Examples

### Rendering a TOML Project File

`project.toml`:

```toml
# Video project file for vidclip (https://github.com/makes/vidclip)
# usage: vidclip render <filename>

[output]
path = "./out.mp4"
x = 1920
y = 1080
fps = 29.97
video_codec = "libx264"
crf = 23  # Constant Rate Factor. Lower CRF -> higher quality (x264: 0-51, default 23)
audio_codec = "aac"
audio_bitrate = "256k"

[[clip]]
file = "vid1.mp4" # 30 fps
interval = [ "00:20.222", "00:28.458" ] # 606 - 853
[[clip]]
file = "vid2.mp4"
interval = [ "0", "00:15.560" ]
[[clip]]
file = "vid1.mp4" # 30 fps
interval = [ "36.492", "41.829" ] # 1094 - 1254
[[clip]]
file = "vid3.mov"
interval=[ 0, 10 ]
```

Render command:

```
$ vidclip render project.toml output.mp4
```

### Extracting a Clip

```
$ vidclip extract input.mp4 00:20.222 00:28.458 output.mp4
```
