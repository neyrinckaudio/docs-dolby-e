# XML Processing & Automation

SoundCode Dolby E can save a complete encode or decode job — inputs, output destination, Dolby E configuration, and all per-program metadata — into a single **XML process file**. Think of it as a portable "process preset."

Once you have a process file you can:

- **Re-run a known-good job** at any time without re-entering settings.
- **Manage a library of deliverables** — keep one process file per delivery spec (network A, network B, archive, etc.).
- **Drive SoundCode from an automated system** by passing the file on the command line — no dialogs, no clicking.

!!! info "Full field reference"
    This page is a practical guide to creating and running process files. For the complete element-by-element specification (every metadata field and its allowed values), see the **SoundCode Dolby E — XML Process File Reference** and the formal schema, [SoundCodeProcess.xsd](../assets/examples/SoundCodeProcess.xsd). The Dolby Digital metadata elements map one-to-one to the controls described in the [Metadata Reference](../encode-export/metadata.md).

## Creating a process file from the app

The easiest way to author a process file is to let the application write it for you:

1. Open the **Encode / Export** (or **Monitor / Import**) tool.
2. Set up the job exactly as you want it — inputs, configuration, metadata, output name and location.
3. Choose **File → Export XML Process…** and save the `.xml` file.

The saved file captures everything in the **CONFIGURATION**, **METADATA**, and **OUTPUT** sections. You can re-open it later with **File → Import XML Process…**, or run it as described below.

!!! tip "Edit by hand"
    Process files are plain UTF-8 text. Once the app has written one, you can duplicate it and edit values in any text editor to spin up variations — the values are the exact strings shown in the app's popups (for example `448 kbps`, `3/2 LCRLsRs`, `5.1 + Stereo`).

## Running a process file

### From the application

**File → Run XML Process…** opens a file picker, then runs the selected file. This is the same engine used by automation, so a file that runs here will run identically from the command line.

### From the command line (automated systems)

Both the macOS and Windows builds accept a process file path as a launch argument and feed it straight into the processor, skipping all dialogs. This is how you wire SoundCode into a render farm, watch-folder service, or build script.

=== "macOS"
    ```bash
    # Run the binary inside the .app bundle; blocks until the job finishes
    "/Applications/SoundCode Dolby E Encoder.app/Contents/MacOS/SoundCode Dolby E Encoder" \
        "/path/to/session.xml" -q
    ```

=== "Windows"
    ```bat
    "SoundCode Dolby E.exe" "C:\path\to\session.xml" -q
    ```

| Argument | Meaning |
|----------|---------|
| `*.xml`  | Path to the process file to run. |
| `-q`     | Quit the application automatically when the job finishes (recommended for automation). |

!!! warning "One file per launch"
    The command-line parser forwards a **single** `.xml` file per launch. To process several jobs non-interactively, either launch the app once per file, or place several jobs inside one **Process Set** file (see below).

## Process file types

A process file's root element is one of three things:

| Root element | Purpose |
|--------------|---------|
| `Neyrinck_SoundCode_Process`     | A single job — one encode (**Export**) or one decode (**Import**). |
| `Neyrinck_SoundCode_Process_Set` | A **batch** — an ordered list of jobs run in sequence. |
| `Neyrinck_SoundCode_ProcessList` | A **hot-folder template** that points at a process template file. |

The application routes the file to the encoder or decoder by reading the `type` attribute of the process node:

| `type` | Routed to | `version` to use |
|--------|-----------|------------------|
| `Export` | Encoder | `1.0` |
| `Import` | Decoder / Player | `2.0` |

## Example: encode (Export)

This encodes six mono inputs into a 20-bit Dolby E **5.1 + Stereo** stream as an interleaved WAV, with two programs of Dolby Digital metadata and BEXT metadata. (Abbreviated — see the full file linked below.)

```xml
<Neyrinck_SoundCode_Process type="Export" version="1.0">

    <Neyrinck_SoundCode_Settings version="2.0">
        <Type>Dolby E 20 bit</Type>
        <Dolby_E_Configuration>5.1 + Stereo</Dolby_E_Configuration>
        <TimecodeEnable>On</TimecodeEnable>

        <Program value="1">           <!-- the 5.1 program -->
            <Neyrinck_DolbyDigital_Metadata version="2.0">
                <bitrate>448 kbps</bitrate>
                <mode>3/2 LCRLsRs</mode>
                <lfe>On</lfe>
                <dialnorm>-27 dB</dialnorm>
                <description>Main 5.1 program</description>
            </Neyrinck_DolbyDigital_Metadata>
        </Program>

        <Program value="2">           <!-- the stereo program -->
            <Neyrinck_DolbyDigital_Metadata version="2.0">
                <bitrate>192 kbps</bitrate>
                <mode>2/0 Stereo</mode>
                <dialnorm>-27 dB</dialnorm>
                <description>Stereo program</description>
            </Neyrinck_DolbyDigital_Metadata>
        </Program>
    </Neyrinck_SoundCode_Settings>

    <Input>
        <InputFile path="$(INPUTROOT)/prog_L.wav"   channel="1"/>
        <InputFile path="$(INPUTROOT)/prog_R.wav"   channel="2"/>
        <InputFile path="$(INPUTROOT)/prog_C.wav"   channel="3"/>
        <InputFile path="$(INPUTROOT)/prog_LFE.wav" channel="4"/>
        <InputFile path="$(INPUTROOT)/prog_Ls.wav"  channel="5"/>
        <InputFile path="$(INPUTROOT)/prog_Rs.wav"  channel="6"/>
    </Input>

    <OutputName value="demo_dolbye"/>
    <OutputPath value="$(OUTPUTROOT)"/>
    <OutputFileType value="Interleaved WAV"/>

</Neyrinck_SoundCode_Process>
```

A few rules worth knowing:

- **Only what you specify is changed.** Any element you omit keeps its current/default value.
- **Program numbers are 1-based** (`1`–`8`) and must match the chosen `Dolby_E_Configuration`.
- Input audio is typically one mono file per channel, assigned with the `channel` attribute.

📎 Download the full working file: [encoder-process.xml](../assets/examples/encoder-process.xml)

## Example: decode (Import)

An Import job uses the same root element name, but `type="Import"` and `version="2.0"` route it to the decoder.

```xml
<Neyrinck_SoundCode_Process type="Import" version="2.0">
    <Input>
        <Source>File</Source>
        <File>$(IMPORTFILEROOT)/demo_dolbye.wav</File>
    </Input>
    <Playback>
        <Audio>
            <Configuration>5.1 + Stereo</Configuration>
            <DolbyE>
                <Enable>On</Enable>
                <EnablePCM>Off</EnablePCM>
                <Program>1</Program>
            </DolbyE>
        </Audio>
    </Playback>
    <Import>
        <Audio>
            <Name>demo_decoded</Name>
            <Type>WAV</Type>
            <Path>$(IMPORTAUDIOROOT)/out</Path>
        </Audio>
        <Type>Audio</Type>
    </Import>
</Neyrinck_SoundCode_Process>
```

📎 Download: [decoder-process.xml](../assets/examples/decoder-process.xml)

## Batching deliverables with a Process Set

To produce several deliverables from one launch — for example, encoding multiple reels in sequence — wrap the jobs in a **Process Set**. All jobs in a Set are treated as the same kind (Export or Import) as the first.

```xml
<Neyrinck_SoundCode_Process_Set version="1.0">
    <Neyrinck_SoundCode_Process type="Export" version="1.0"> … reel 1 … </Neyrinck_SoundCode_Process>
    <Neyrinck_SoundCode_Process type="Export" version="1.0"> … reel 2 … </Neyrinck_SoundCode_Process>
</Neyrinck_SoundCode_Process_Set>
```

📎 Download: [process-set.xml](../assets/examples/process-set.xml)

## Reusable templates with path variables

Hard-coding absolute paths makes a process file specific to one machine. Instead, any path can contain a single **root variable** of the form `$(NAME)`, resolved at run time from a globals file. This lets you reuse the same process file across machines or jobs by changing only the variable definitions.

| Variable | Used in | Job type |
|----------|---------|----------|
| `$(INPUTROOT)`     | `Input/InputFile/@path`           | Export |
| `$(OUTPUTROOT)`    | `OutputPath/@value`               | Export |
| `$(SETTINGSROOT)`  | external settings `@filepath`     | Export |
| `$(PROCESSROOT)`   | external process `@filepath`      | Export / Import |
| `$(IMPORTFILEROOT)`| `Input/File`                      | Import |
| `$(IMPORTAUDIOROOT)`| `Import/Audio/Path`, `Import/Video/Path` | Import |

Define the values in a file named exactly **`SoundCodeGlobals.xml`**, placed in the **same directory** as the process file. The app loads it automatically and substitutes each token.

```xml
<Neyrinck_SoundCode_Globals>
    <INPUTROOT       value="/Volumes/Media/incoming"/>
    <OUTPUTROOT      value="/Volumes/Media/encoded"/>
    <IMPORTFILEROOT  value="/Volumes/Media/decode/in"/>
    <IMPORTAUDIOROOT value="/Volumes/Media/decode/out"/>
</Neyrinck_SoundCode_Globals>
```

If a `$(NAME)` token has no matching variable (or no globals file is present), the token is left unchanged in the path. Paths may use forward slashes on both platforms.

📎 Download: [SoundCodeGlobals.xml](../assets/examples/SoundCodeGlobals.xml)

## Hot folders

The hot-folder feature uses the same engine: drop media into a watched folder and SoundCode applies a process **template** automatically. See [Hot Folder Processing](../monitor-import/overview.md#hot-folder-processing) for setup. A `Neyrinck_SoundCode_ProcessList` file (or a `SoundCodeProcessTemplate.xml` placed next to the dropped media) names the template to apply.

## Good to know

- **Files are UTF-8.** A leading `<?xml version="1.0" encoding="UTF-8"?>` declaration is accepted but optional.
- **Element and attribute names are case-insensitive;** text *values* (such as `448 kbps`) are matched case-sensitively against the app's UI strings.
- **Unknown elements are ignored,** so extra notes or attributes won't break a file — but they have no effect.
- **Settings version 2.0** carries each value as element text (`<bitrate>448 kbps</bitrate>`). Legacy version 1.0 used a `value` attribute; the loader accepts both, but new files should use 2.0.
- The application does **not** validate against the [XSD](../assets/examples/SoundCodeProcess.xsd) at run time — it is provided for authoring tools and editors.
