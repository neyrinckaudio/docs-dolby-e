# Monitor / Import Overview

The **SoundCode Dolby E Monitor / Import** tool operates as a standalone application, a realtime AAX Native plug-in, or a non-realtime AudioSuite plug-in. It implements Dolby E decoding and multi-channel, multi-program audio playback and import.

The standalone application can decode and import faster-than-realtime, or decode-and-monitor in realtime, and features hot folder decode-and-import processing. In Pro Tools, the plug-in types are located in the **Sound Field** category.

The **AUDIO PLAYBACK** section can monitor/import polyphonic / multi-program WAV files. Polyphonic or multi-program means the file contains multiple mixes, similar to a professional video tape — SoundCode can choose which program to monitor. For example, you can monitor a WAV file that has a 5.1 PCM mix and a stereo Dolby E pair.

## Plug-in and application windows

### AAX Native Window

The Dolby E Monitor operates as these realtime types: **stereo-to-stereo**, **stereo-to-5.1**, and **stereo to 8-outputs** (auxiliary output stems in Pro Tools). In Pro Tools, open them by clicking a channel insert on a stereo track and navigating the AAX Native multichannel popup menu.

The user interface is divided into three sections:

- **INPUT** — selects the input to be decoded and monitored. The AAX Native plug-in can decode-and-monitor a file using Direct File Monitor technology, controlling which file is played and what time code it synchronizes to.
- **AUDIO PLAYBACK** — controls which program(s) should play.
- **STATUS** — displays information about the file and metadata, plus output meters.

### AudioSuite Window

Open the AudioSuite plug-in window from the AudioSuite menu in Pro Tools. It has the same **INPUT**, **AUDIO PLAYBACK**, and **STATUS** sections as the AAX Native interface, plus an additional popup at the top for choosing the output order (**Film** or **SMPTE**) used when importing files into the session.

### Standalone App Window

The standalone application has the same **INPUT**, **AUDIO PLAYBACK**, and **STATUS** sections as the AAX Native interface. It also has an **IMPORT** section that lets you perform a faster-than-realtime operation and set up hot folder processing.

## Hot Folder Processing

The standalone application features hot folder importing. Drop Dolby E stream files (for example) into a folder, and SoundCode automatically detects and decodes them to a consistent location.

SoundCode looks for a special file named `SoundCodeProcessTemplate.xml` in the hot folder to tell it how to perform the import process. The easiest way to create one:

1. Set the import window controls (the **Location** is most important).
2. Select the menu item **Export XML Process…** and save it with the name `SoundCodeProcessTemplate.xml`.
3. Tell SoundCode where your hot folder is by clicking the **Browse** button in the **HOT FOLDER** section.

See the [Controls Reference](controls.md) for a detailed description of every control.
