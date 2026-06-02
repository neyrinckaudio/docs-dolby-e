# Metadata Reference

Dolby E and Dolby Digital encoding have many features and options, which are described via **metadata**.

!!! info "See also"
    For a thorough explanation of how the metadata is used, see the separate document **Dolby Encoding Guidelines.pdf**. The following is a simple explanation of the metadata controls for each audio program (selected by the **Metadata Edit Select** menu when using the Dolby E configuration).

## Program metadata controls

### Program

Selects which Dolby E program corresponds to the following metadata controls.

### Coding Mode

Selects the channel configuration of the primary audio channels. Does not include the LFE channel.

### Data Rate

Selects the data rate of the Dolby Digital data stream. A lower setting uses less space (for example, on a DVD) but lower audio quality; a higher setting uses more space but higher audio quality.

### Bitstream Mode

Selects the type of audio being encoded. **Complete Main** is the most common setting.

### Dialog Norm

Selects the level of the dialog in the source material relative to 0&nbsp;dBFS. Its purpose is to let the decoder adjust playback level so dialog loudness is consistent. When set to **−31**, a decoder will not change the playback level; when set to **0**, the decoder reduces the level by 31&nbsp;dB.

### LFE Enable

Sets whether or not you are encoding an LFE channel.

### Center Mix

Selects the gain applied to the center channel when downmixing to stereo. Available only when a center channel is being encoded.

### Surround Mix

Selects the gain applied to the rear channels when downmixing to stereo. Available only when rear channels are being encoded.

### Dolby Surround Mode

Selects whether a stereo mix has been Dolby Surround encoded, has not, or is unknown. Available only when encoding stereo program material.

### Copyright

Turns a flag on or off indicating whether the audio is copyright protected.

### Original

Turns a flag on or off indicating whether the audio being encoded is the original audio or a copy.

### Room Type

Selects the type of room used when mixing the audio being encoded.

### Mix Level

Selects the audio playback levels used when mixing the audio being encoded.

### Info Exists

Turns a flag on or off indicating whether the datastream specifies the **Room Type** and **Mix Level** controls.

### LoRo Cntr Mix

Selects how the center channel will be downmixed for a normal stereo downmix.

### LoRo Surr Mix

Selects how the rear channels will be downmixed for a normal stereo downmix.

### LtRt Cntr Mix

Selects how the center channel will be downmixed for a Dolby Surround compatible stereo downmix.

### Dolby Surround EX Mode

Selects whether the data stream is indicated to be Dolby Surround EX encoded.

### Stereo Downmix Preference

Selects which downmix type is preferred when decoded.

### BSI Extension Enable

Enables or disables whether the bitstream info extensions are used in the datastream.

### Dynamic Range Compression

Selects the "profile" used to encode a dynamic range compression side-chain signal into the data stream.

## Preprocessing controls

### Surr 3 dB Attenuation

When **ON**, the encoder attenuates the rear channels by 3&nbsp;dB. Necessary for mixes made for cinema that are being encoded for DVD.

### Surr Phase Shift

When **ON**, the encoder applies a 90-degree phase shift to the rear channels. This control should always be enabled unless the material will never be downmixed — otherwise an LtRt downmix might sound unbalanced to the right side.

### Lowpass Filter

When **ON**, the encoder applies a lowpass filter to all audio channels.

### LFE Filter

When **ON**, the encoder applies a lowpass filter to the LFE channel.

### DC Filter

When **ON**, the encoder applies a highpass filter to all audio channels.

## Default settings

The metadata controls default to settings recommended by Dolby. You can change the defaults by using Pro Tools' ability to save a user preset and set it as the default. Consult the *Pro Tools Plug-Ins User Guide* for more information.
