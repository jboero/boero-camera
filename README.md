# Boero Camera

An Android camera app for Google Pixel devices that records video using hardware AV1 encoding and saves photos as WebP — the first camera app to use the Tensor G3's dedicated AV1 encoder block. In my experience this produces equivalent images about 1/4 the size of JPEG and equivalent videos about 1/4 the size of their equivalent default H.264.

![danger](https://github.com/user-attachments/assets/9228b5f8-6465-4c8e-8822-cb9cdceb6d88)

WARNING vibe coded with Claude Opus v4.6. I tried occasionally for a few years to build this app but failed without the help of Claude. *Use at your own risk* but I've been using the app for a while now and it works for me.

## Features

- 📸 **WebP photos** — lossy (quality 50–100) or lossless, saved to `DCIM/Camera/` by default.
- 🎬 **AV1 + AAC video** — hardware AV1 via `c2.google.av1.encoder`, AAC audio, MP4 container
- 📱 **H.264/HEVC fallback** — via CameraX Recorder on non-Tensor devices
- ⚙️ **Manual controls** — ISO, shutter, white balance, exposure compensation, focus mode
- 🎞️ **Frame rate** — 24 / 30 / 60 fps
- 📊 **AV1 bitrate slider** — 2–40 Mbps (VBR; Tensor G3 encoder supports CBR/VBR only, no CQ)
- 📐 **Aspect ratio** — 4:3 / 16:9

<img width="20%" alt="Screenshot_20260309-163705" src="https://github.com/user-attachments/assets/df334466-a9d6-4247-9c17-b6f4f779ceb0" />
<img width="20%" alt="Screenshot_20260309-163714" src="https://github.com/user-attachments/assets/eb6523c9-d3db-48b3-a03d-f036b3d72dbe" />
<img width="20%" alt="Screenshot_20260309-163629" src="https://github.com/user-attachments/assets/dba59dff-be3e-455f-b330-b147652c43e3" />
<img width="20%" alt="Screenshot_20260309-163701" src="https://github.com/user-attachments/assets/0d7f6495-f657-418e-8bcb-ae51f4ee3b6a" />
<img width="100%" alt="Screenshot_20260309-163651" src="https://github.com/user-attachments/assets/5bf2dee7-ae9a-4989-9b2e-93522f9af0e3" />


## Requirements

- Android API 26+ (Android 8.0)
- AV1 encoding: Pixel 8 / Tensor G3 or later
- Build: Java 21, AGP 8.3.0, Gradle 8.4

## Build

```bash
./gradlew assembleDebug
adb install -r app/build/outputs/apk/debug/app-debug.apk
adb shell am start -n com.boerocamera.app/.ui.MainActivity
```

## Package

`com.boerocamera.app`

## Credits

Developed by **John Boero**.
Coding architecture and implementation assistance by **Claude** (Anthropic), including the AV1 MediaCodec pipeline, dual-Preview viewfinder-during-recording solution, orientation hint fix, and threading model.

## License

LGPL
