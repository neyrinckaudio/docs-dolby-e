# System Requirements

SoundCode For Dolby E runs in the following environments:

- **Standalone application** — qualified on Windows XP (SP2) and Mac OS X (qualified on OS X 10.4 and higher).
- **Pro Tools plug-in** — on a Digidesign-qualified Pro Tools system running Pro Tools 7.0 or higher.

## Important Pro Tools mixer information

SoundCode For Dolby E allows you to place a Dolby E data stream in the Pro Tools timeline and route it to an AES/SPDIF output. However, this **requires the non-dithered mixer plug-in**.

The Dolby E data stream cannot be altered. The dithered mixer sums a dither signal with the data stream, altering it and making the stream unusable.

!!! warning "Rule of thumb"
    If you are using the **dithered mixer**, you cannot mix a Dolby E data stream to any bus. Any gain, pan, or other modification to the signal will render the data stream unusable.

## Important sample rate information

SoundCode For Dolby E operates on files at all Pro Tools sample rates. However, **files being prepared for Dolby E encoding need to be at 48&nbsp;kHz** — most Dolby Digital encoding is also done at 48&nbsp;kHz.

SoundCode For Dolby E does **not** perform sample-rate conversion. For example, if a multichannel BWF file is being prepared to send to the Dolby DP600 for Dolby E encoding, conversion to 48&nbsp;kHz must happen on the individual inputs before exporting the BWF file.

## Important Dolby E latency information

The Dolby E encoder and decoder each have **one video frame of latency**. This is analogous to Dolby E hardware encoders and decoders.

The Dolby E Encoder tool has an [**Input Offset**](../encode-export/controls.md#input-offset) control to advance the input audio and compensate for these latencies — equivalent to sliding the audio earlier in time. SoundCode emulates Dolby real time hardware because many broadcast delivery specifications assume a hardware-based encoding system. When encoding Dolby E streams, be certain you understand the delivery requirements so you can set the Input Offset correctly.

### RTAS Dolby E decoder latency (Input Source = Track Stream)

The RTAS Dolby E decoder allows live Dolby E stream confidence monitoring with one frame of latency. If you use a Pro Tools system to emulate a standalone hardware decoder, you must:

- Set the **hw mode** control to **ON**, and
- Set the **RTAS buffer size to 256** in the Playback Engine dialog.

This way you can monitor the audio from a live Dolby E stream input and compare it to other audio sources — for example, playing back a video tape with a Dolby E stream on it, decoding it on the Pro Tools system, and testing that it is phase aligned with other tracks. See [Dolby E Hardware Mode](../monitor-import/controls.md#dolby-e-hardware-mode-rtas-only).
