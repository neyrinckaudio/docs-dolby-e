# Troubleshooting

## Error Message: "Updated Tpkd Driver Required"

If you see this message when Pro Tools is launching on Windows XP, your PACE iLok driver needs to be updated to a newer version. Go to PACE's website at [www.paceap.com](https://www.paceap.com) to download a driver installer.

## External Dolby E Decoder Won't Decode Data Stream

If a decoder is not recognizing an encoded Dolby E data stream that you are playing with the RTAS Monitor, it suggests the data stream has been **altered**.

!!! danger "A Dolby E or Dolby Digital data stream must never be altered"
    Sample rate conversion, gain change, dithering (including use of the Pro Tools dithering mixer), EQ, compression, and any other type of audio signal processing will alter a data stream and make it unusable.

    See [Important Pro Tools mixer information](../getting-started/system-requirements.md#important-pro-tools-mixer-information).
