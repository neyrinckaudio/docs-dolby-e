# Technologies

SoundCode For Dolby E features many technologies used in professional audio environments. This section describes them.

## Dolby E

Dolby E technology was developed by Dolby Laboratories to transport audio and metadata on digital videotapes or AES cables using two channels of PCM audio. Up to **eight channels of audio and metadata** are encoded by a Dolby E encoder, which outputs a Dolby E stream that is two channels of PCM audio.

!!! danger "Do not listen to a raw Dolby E stream at high volume"
    If you listen to a Dolby E stream you will hear loud bursts of noise that can damage your hearing or speakers at high volume. A Dolby E decoder processes the stream to output the original encoded audio and metadata.

Dolby E is often used to deliver audio and metadata on a digital videotape for television broadcasting. The audio being delivered (a 5.1 surround mix, for example) is first Dolby E encoded to a Dolby E stream and recorded to two audio channels of the videotape. The tape is played back by a broadcaster and fed to a Dolby E decoder, which outputs the 5.1 surround mix and metadata. Often, the decoded audio and metadata is connected to a Dolby Digital encoder used in ATSC and digital cable television broadcasting.

SoundCode For Dolby E features a **Dolby E Encode** option and a **Dolby E Decode** option for use on nonlinear audio and video workstations:

- The **Encode** option Dolby E encodes audio and metadata to a stereo WAV file that carries the Dolby E stream. The stream can then be recorded to a video tape or stored as a file for delivery to a broadcaster.
- The **Decode** option decodes a Dolby E stream for editing or quality-assurance testing.

## BWF Files

BWF files are WAV files that can hold up to eight channels of audio, Dolby metadata, and BEXT metadata in a single file. Dolby metadata contains important information for broadcasting — such as how loud the audio is, how it should be downmixed to stereo, and the audio stem format.

Because a single BWF file holds both the audio and the metadata, it is a very convenient format for delivering and receiving audio between workstations and facilities. For example, a mixing engineer can make a 5.1 mix and a stereo mix of a television program, package the two mixes and the Dolby metadata into a single file, and send it to a facility for Dolby E encoding.

BWF files contain a Dolby metadata "chunk" that specifies the metadata. The metadata chunk applies to the entire file — **BWF files are not capable of having metadata that changes over time**.

## Dolby DP600

The Dolby DP600 is a hardware product manufactured by Dolby that implements file-based processing of many Dolby technologies, including Dolby E, Dolby Digital, Pro Logic, and loudness measurement/correction.

SoundCode For Dolby E implements actual Dolby E encoding and decoding, so it is not necessary to use a DP600. But if you are using a DP600, it uses BWF files for input and output. A single BWF file can hold up to eight channels of PCM audio and Dolby E metadata, and SoundCode For Dolby E can read and write BWF files — allowing you to interface your audio/video workstation to a DP600.

## RF64 Files

RF64 files are WAV files that can be larger than 4&nbsp;GB. (Pro Tools does not support files larger than 2&nbsp;GB as of version 8.0.) An RF64 WAV file can also include additional WAV "chunks" that define additional features such as BWF.
