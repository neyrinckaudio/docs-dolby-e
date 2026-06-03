# Encode / Export Overview

The **SoundCode Dolby E Encode / Export** tool operates as a standalone application window or an AudioSuite plug-in in Pro Tools.

It performs faster-than-realtime Dolby E encoding and multi-program PCM export to BWF, with full Dolby E and Dolby Digital metadata, automatic time code integration, and Dolby E latency compensation.

## How to encode / export a file with the standalone application

1. Launch the standalone application:
    === "macOS"
        ```
        /Applications/Neyrinck/SoundCode/SoundCode Dolby E
        ```
    === "Windows"
        ```
        C:\Program Files\Neyrinck\SoundCode\SoundCode Dolby E.exe
        ```
2. Click an input file box and choose `.wav` files located on your system.
3. Select the [**Configuration Type**](controls.md#type) (Dolby E 16-bit, Dolby E 20-bit, PCM Dolby E, PCM Dolby Digital, or PCM) along with the Dolby E configuration if necessary.
4. Edit the [metadata](metadata.md) for each program if necessary.
5. Set the output file type to Interleaved WAV or Multi-mono WAV.
6. Set the output file name.
7. Browse to select a location for the output file.
8. Click the **Encode / Export** button at the bottom right.

## How to encode / export a file in Pro Tools

1. Open the SoundCode Dolby E Encoder from the **AudioSuite** menu.
2. In Pro Tools, select audio across multiple tracks in the timeline.
3. Select the [**Configuration Type**](controls.md#type) along with the Dolby E configuration if necessary.
4. Edit the [metadata](metadata.md) for each program if necessary.
5. Set the output file type to Interleaved WAV or Multi-mono WAV.
6. Set the output file name.
7. Browse to select a location for the output file.
8. Click the **Encode / Export** button at the bottom of the Pro Tools plug-in.

!!! tip
    For step-by-step delivery scenarios, see [Workflows](../reference/workflows.md). For a detailed description of every control, see the [Controls Reference](controls.md).
