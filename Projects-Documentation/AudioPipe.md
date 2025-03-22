# AudioPipe

## Goal:
Redirect audio from speakers to a webserver so it can be streamed to multiple devices by connecting via a web interface.

## Implementation:
1. **Capture system audio.**
   - Encode it for streaming.
   - Redirect & serve the decoded audio through a webserver for device access.

## Overview:
### **Capture System Audio**
Possible approaches:
- Provide support for ALSA & others via ALSA, PulseAudio, or PipeWire.
- Negate the hook at a lower level:
  - Hook system calls using `LD_PRELOAD` to override system calls sending audio to `/dev/snd/pcmC0D0p` or similar devices.
  - Use **eBPF hooks** to intercept system calls.

### **Encoding for Streaming**
- Capture and encode audio (Opus, MP3, or AAC).
- Ensure low-latency encoding.
- Track application state for:
  - `write()`: Captures data written to the sound device.
  - `open()`: Detects application opening an audio device.
  - `close()`: Detects application closing an audio device.
  - `read()`: Captures raw data.
- Intercept `write()` calls & append captured data to a buffer for streaming.

### **Stream Audio to a Server**
- HTTP live streaming (`HLS`, `WebRTC`, or `HTTP`).
- Serve the audio stream in a browser-compatible format.
- Client-side playback via:
  - HTML5 audio player.
  - WebRTC-based client.

## General Tech:
- **Languages:** C, Python, HTML, CSS.
- **Potential Improvements:** Add mechanism for clients to send audio back.

