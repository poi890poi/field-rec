# field-rec
Notes, configurations, scripts for field recording, long ambient sounds, and sound editing.

Processing and rendering long hours sound recordings requires special tools and methods. This document provides information about these methods and tools.

## Standard Processings
### LR to MS
- Mid = (L + R) / 2 (-3.0 dB)
- L = L - R
- R = R - L

### EQ
- Filter Curve EQ
- 100Hz Rumble

### Compression
- Avoid as possible.
- Analyze spectrum and RMS to manually supress unwanted parts.

### Amplify
- Usually target for -32 dB RMS.

### Mix and Render
- FLAC, 24 bit, 96 kHz
- Configure channels

### Delete and Corssfade
- Sync lock.
- Select segment to delete.
- Split Clip
- Delete the clip.
- Split left clip at starting point of crossfade.
- Duplicate crossfade clip to new track.
- Delete crossfade clip in original track.
- Split Clip of right clip at ending of crossfade.
- Apply crossfade.
  
## Audacity Quick References
### Invert polarity
`Effect → Special → Invert`
### Sync Lock
`Tracks → Keep tracks sync`
### EQ
`Effect → EQ and Filters → Filter Curve EQ → Preset`
### Crossfade
`Effect → Fading → Crossfade Tracks → Constant Power 1 → Alternating In / Out`
### Amplify
`Effect → Volume and Compression → Amplify`
### Mix and Render
`Tracks → Mix and Render`
### Rescan Audo Devices
`Transport → Rescan Audio Devices`
### Spectrum Analysis
`Analyze → Plot Spectrum`
### Measure RMS (average volume)
`Analyze → Measure RMS`

## FFmpeg Commands

Make video out of a still image:
```shell
ffmpeg -loop 1 -i image.jpg -c:v libx264 -t 3600.00 -pix_fmt yuv420p output.mp4
```

Make video out of a still image and audio track:
```shell
ffmpeg -loop 1 -i image.jpg -i audio.flac -c:v libx264 -c:a copy -shortest -pix_fmt yuv420p output.mp4
```

## Tools and Services Tested
### Audacity
- Your best friend. Does everything you need about sound editing, nice and fast.
### Nyquist Plugins
#### Dynamic Mirror
- Generate volume envelope from a track to be applied on another track.
- Has length limit of 30 minutes.
### FFmpeg
- Super fast for combinging or looping images, videos, audios.
- Is able to completely eliminate quality degradation of transcoding. Copy source material as it is.
### Shotcut
- Unconditionally free.
- GUI is extremely slow when video is long.
### Davinci Resolve
- While editing is smooth, exporting takes forever. (never succeeds)
- Unable to find bit depth setting for FLAC audio codec.
### archive.org
- Not much limitation regarding length and file size. (4 hours and 4.0 GB tested)
- Takes forever to upload. Resuming doesn't actually resume. It just try uploading whole file again. (never succeeds)
### SoundCloud
- Trial plan has length limit of 3 hours.
### YouTube
- Not much limitation regarding length and file size. (4 hours and 20.0 GB tested)
- Doesn't support pure audio uploading.
### Spotify
- Commercial use only. Uploading is not supported for individual creator.
### SoundOn
- Not tested yet.
