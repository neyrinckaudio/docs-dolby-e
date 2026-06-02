# Settings & Menu Commands

## Settings Files

SoundCode For Dolby E can save and recall settings. Settings are saved in one of three categories: **Metadata Settings**, **Process Settings**, and **Process Sets**.

## Menu Commands

The standalone application and the Pro Tools plug-in feature the following menu commands.

### Export XML Process…

Exports an XML process file that specifies all information needed to perform an encode/export or import process. The file can be used later to run a process, as part of a batch process, or as a template for a hot folder import operation.

### Import XML Process…

Reads an XML process file that specifies all information needed to perform an encode/export or import process. All information in the file is imported to the corresponding user interface controls.

### Run XML Process… (batch processing)

Choose one or more XML process files and perform the encode/export or import process described in the file(s).

### Import Pro Tools Settings…

Choose a SoundCode Dolby E settings file. The file format is the same as a Pro Tools plug-in preset and uses the `.tfx` extension. Several presets are installed with SoundCode Dolby E, located at:

=== "macOS"
    ```
    /Library/Application Support/Digidesign/DAE/Plug-In Settings/SC Broadcast
    ```
=== "Windows"
    ```
    C:\Program Files\Common Files\Digidesign\DAE\Plug-In Settings\SC Broadcast
    ```

The preset stores the controls in the **CONFIGURATION** and **METADATA** sections.

### Export Pro Tools Settings…

Saves a SoundCode Dolby E settings file compatible with the Pro Tools plug-in preset system, using the `.tfx` extension. Stores the controls in the **CONFIGURATION** and **METADATA** sections.

### Import XML Settings…

Choose a SoundCode Dolby E settings file encoded in XML format. XML files are text files that can be edited with a text editor and use the `.xml` extension. Several settings files are installed with SoundCode Dolby E, located at:

=== "macOS"
    ```
    /Library/Application Support/Neyrinck/Settings/SoundCode Broadcast
    ```
=== "Windows"
    ```
    C:\Program Files\Common Files\Neyrinck\Settings\SoundCode Broadcast
    ```

The file stores the controls in the **CONFIGURATION** and **METADATA** sections.

### Export XML Settings…

Saves a SoundCode Dolby E settings file encoded in XML format. Stores the controls in the **CONFIGURATION** and **METADATA** sections.

### Import Dolby Metadata From BWF File…

Imports the Dolby metadata in a BWF file that contains Dolby metadata. This affects the controls in the **CONFIGURATION** and **METADATA** sections and the **TIMECODE** portion of the **OUTPUT** section.

### Overwrite Dolby Metadata In BWF File…

Overwrites the Dolby metadata in a BWF file that contains Dolby metadata. The controls in the **CONFIGURATION** and **METADATA** sections and the **TIMECODE** portion of the **OUTPUT** section are used to overwrite the file.

!!! warning
    The Configuration Type and the Dolby E Configuration must match the file being overwritten.
