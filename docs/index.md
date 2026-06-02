# SoundCode For Dolby E User Guide

**SoundCode For Dolby E** is a suite of software tools for encoding, decoding, and exchanging audio for broadcast applications. Designed for both tape-based and file-based workflows, it lets you encode, export, import, and monitor Dolby&nbsp;E, BWF, and MXF&nbsp;OP1a audio.

SoundCode For Dolby E runs on macOS and Windows as a standalone application, a Pro Tools plug-in, an Audio Unit plug-in, a VST plug-in, and a Final Cut plug-in.

## What SoundCode For Dolby E Does

SoundCode For Dolby E operates as two separate tools:

- **[SoundCode Dolby E Encode / Export](encode-export/overview.md)** — faster-than-realtime Dolby E encoding and multi-program PCM export to BWF and MXF OP1a, with full Dolby E and Dolby Digital metadata.
- **[SoundCode Dolby E Monitor / Import](monitor-import/overview.md)** — realtime and faster-than-realtime Dolby E decoding, multi-channel/multi-program playback, metadata display, and import into Pro Tools.

## Key Features

- Faster-than-realtime Dolby E encoding and decoding
- Real time Dolby E decoding, monitoring, and metadata display
- File-based import/export of multi-program BWF and MXF OP1a files
- Real time audio monitoring of multi-program BWF and MXF OP1a files
- Dolby E metadata import/export
- Compatible with the Dolby DP600
- Integration with Pro Tools, Final Cut, Nuendo, and other workstations
- Batch processing and hot folder processing
- Tape-based and file-based workflows

## Requirements

- macOS (qualified on OS X 10.4 and higher) or Windows XP SP2 and later
- Pro Tools 7.0 or higher (for the Pro Tools plug-in)
- Final Cut Pro / Final Cut Express 6.0.5 or later (for the Final Cut plug-in)
- VST 2.4 compatible host (for the VST plug-in)
- An authorized iLok USB Key or a license file

See [System Requirements](getting-started/system-requirements.md) for important details about sample rates, latency, and the Pro Tools mixer.

## Quick Start

1. [Install SoundCode For Dolby E](getting-started/installation.md).
2. [Authorize the software](getting-started/authorization.md) with your iLok or license file.
3. Launch the standalone application or your workstation, then open the **Encode / Export** or **Monitor / Import** tool.
4. Follow a [workflow](reference/workflows.md) that matches your delivery — for example, Dolby E encoding a 5.1 + Stereo mix and laying it back to a VTR.

!!! warning "Never alter a Dolby E data stream"
    If you listen to a raw Dolby E stream you will hear loud bursts of noise that can damage your hearing or speakers at high volume. A Dolby E (or Dolby Digital) data stream must never be altered — sample-rate conversion, gain changes, dithering, EQ, or compression will make the stream unusable. See [Troubleshooting](reference/troubleshooting.md).
