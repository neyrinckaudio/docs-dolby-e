# Encode / Export Controls Reference

The user interface is divided into sections:

- The **CONFIGURATION** section determines whether the file includes Dolby E metadata, Dolby Digital metadata, or no Dolby metadata. (A WAV file output always has a BEXT chunk.)
- The **METADATA** section displays and controls the metadata and preprocessing settings for each program in the configuration. These settings can be saved as presets using the Pro Tools plug-in preset features. See the [Metadata Reference](metadata.md).
- The **OUTPUT** section controls the name and location of the exported WAV file. These settings **cannot** be saved as presets — instead, the output file name and location are persistent and stored in a preferences file that is read when the plug-in window opens and saved when it closes. The preferences file is associated with the currently logged-in user; each user account has a separate preferences file.

## CONFIGURATION Controls

The configuration controls set up the processing to match the type of broadcast delivery you are making.

### Type

This popup menu selects the type of file to be encoded or exported.

- **Dolby E** file types: 16-bit, 20-bit, or 24-bit. The bit depth selected should match the digital video tape the Dolby E stream will be laid back to, or — for file-based delivery — your delivery requirements.
- **MBWF** (Multichannel Broadcast Wave Format) types: MBWF Dolby E, MBWF Dolby Digital, or MBWF BEXT. MBWF files are PCM audio and can be used to exchange audio with embedded metadata.

### Dolby E Configuration

Dolby E supports many different audio stem formats as well as grouping multiple audio programs together. There are **22 separate configurations** to choose from. This control selects the configuration to use, and is disabled when the Type control is set to a type that does not use Dolby E.

### Input Offset

Dolby E encoding and decoding processing each have a latency of one video frame. This control "advances" the audio to compensate for that latency — equivalent to sliding the audio earlier in the timeline.

The value you choose depends on the broadcast delivery specification you need to meet. Typically you set it to **+2 frames** to compensate one frame each for encoding and decoding:

| Input Offset | Result at a Dolby DP572 output |
|---|---|
| 0 | Two frames late |
| +1 | One frame late |
| +2 | Zero frames late |

### Dolby E Timecode

A Dolby E stream may optionally carry an active time code value in each frame. This control enables or disables that time code. It defaults to **ON**.

## OUTPUT Controls

The output controls let you select a file name and location to save the exported BWF file.

### File Name

Sets the name of the file written by the encoder. It is not used to set the file name extension — click it, type the name, and press ++enter++. A `.WAV` extension is appended automatically.

### Browse

Launches a Choose Folder dialog. Use it to select a location to add to the list managed by the **Location** control.

### Location

A popup menu that manages a list of locations to choose from — where the WAV file(s) will be written. If the list is empty, you must select a location with **Browse**. Once you have one or more locations, use this popup to select one. The last two entries in the popup let you remove the current entry or all entries.

### File Type

A popup menu that selects the type of file to encode/export to:

- **Interleaved WAV** — a single WAV file containing all channels of audio interleaved together. Simpler to exchange and archive.
- **Split / Multi-mono WAV** — multiple WAV files, one per channel of audio. Because Pro Tools cannot directly use interleaved files, split WAV can save time if you need to import the audio back into Pro Tools.

### Pro Tools controls at bottom of window

The **Export** control at the bottom of the window starts the export process and writes a WAV file containing the PCM audio and Dolby metadata.

## Additional Controls in the Standalone Application

### INPUT Controls

The input section lets you select WAV files to export. Up to **eight** separate mono or multichannel files can be selected, for up to eight total channels of input. The channel for each file is indicated to the left of each file path; the length of the file is displayed to the right as a SMPTE timecode value.

#### File Path

Click a file path and a Choose File dialog opens. Select one or more `.wav` files.

### OUTPUT Controls (standalone)

The standalone application features additional output controls.

#### Auto

Sets the timecode start and frame rate automatically by examining the BEXT timestamp or Dolby E metadata in the first input file.

#### Start Time

The SMPTE timecode used for the exported BWF file. When **Auto** is enabled, the time values cannot be edited. When Auto is disabled, click a value to change it.

#### End Time

Displays the end time of the exported file. Not editable — based on the length of the first input file.

#### Length

Displays the length of the exported file. Not editable — based on the length of the first input file.

#### Encode / Export

Starts the process of encoding a Dolby E file or exporting an MBWF file.
