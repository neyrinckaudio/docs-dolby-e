# Workflows

This section provides step-by-step procedures for common delivery scenarios.

## Dolby E encode a 5.1 + Stereo mix and lay back to a VTR (Pro Tools)

In this scenario, you are mixing an audio soundtrack in both 5.1 surround and stereo, and need to deliver a Dolby E encoded stream onto a video tape.

1. Finish the mixes by bouncing them to disk in Pro Tools.
2. Import the bounced files into Pro Tools tracks — a 5.1 track for the 5.1 mix and a stereo track for the stereo mix (or eight mono tracks if you prefer).
3. Make sure the imported mix files are positioned at the correct location in the timeline (typically at the far left).
4. Select the imported mix in the timeline.
5. Select the **SoundCode Dolby E Encoder** plug-in in the AudioSuite menu.
6. Set the configuration controls to **Dolby E 20 bit** and **5.1 + Stereo**.
7. Set up the metadata for both the 5.1 program and the stereo program.
8. Name the output file and location, and click **Encode**.
9. Create a new stereo track to output the Dolby E encoded stream.
10. Import the stereo WAV Dolby E stream created in step 8 and spot it to the stereo track created in step 9.
11. Place a hardware insert on the stereo track to send the Dolby E stream to the VTR inputs and return it from the VTR.
12. Insert a **stereo-to-5.1 AAX Native SoundCode Dolby E Monitor** plug-in after the hardware insert.
13. Enable the **dolby e** control so the Dolby E stream returning from the VTR can be monitored.

## Prepare a 5.1 + Stereo mix for Dolby E encoding with the Dolby DP600 and lay back to a VTR (Pro Tools)

In this scenario, you are mixing in both 5.1 surround and stereo, and need to deliver a Dolby E encoded stream onto a video tape using a Dolby DP600.

1. Finish the mixes by bouncing them to disk in Pro Tools.
2. Import the bounced files into Pro Tools tracks — a 5.1 track for the 5.1 mix and a stereo track for the stereo mix (or eight mono tracks if you prefer).
3. Make sure the imported mix files are positioned at the correct location in the timeline (typically at the far left).
4. Select the imported mix in the timeline.
5. Select the **SoundCode Dolby E Encoder** plug-in in the AudioSuite menu.
6. Set the configuration controls to **Dolby E** and **5.1 + Stereo**.
7. Set up the metadata for both the 5.1 program and the stereo program.
8. Name the output file and location, and click **Export**.
9. Send the exported file to the DP600 (by dragging to the hot folder, for instance). Bring the newly encoded file back to your desktop.
10. Create a new stereo track to output the Dolby E encoded stream.
11. Select the **SoundCode Dolby E Monitor** plug-in in the AudioSuite menu on the stereo aux track, and browse to the encoded Dolby E WAV file.
12. Now playing the session outputs the encoded stream synchronized to the Pro Tools timeline (and the video being delivered). Adjust the **frame offset** as needed to account for Dolby E decoding.

## Audition a SMPTE-ordered multichannel BWF file (Pro Tools)

In this scenario, you would like to listen to a 5.1 interleaved BWF file synchronized to Pro Tools video playback.

1. Create a stereo aux track and instantiate the **AAX Native stereo-to-5.1 SoundCode Dolby E Monitor** plug-in.
2. Click the **Browse** control and select the multichannel WAV file to be played.
3. Place the timeline cursor as appropriate for playing the file according to the timecode in the file or session start (which may be the same).
4. Select the program to play (in this case the 5.1 program is the only choice).
5. Start the transport and listen.

## Edit the Dolby metadata in a BWF file

In this scenario, you would like to modify the Dolby metadata in an existing Dolby BWF file. This is done in the standalone SoundCode Broadcast application using menu commands to import the metadata, alter the controls, and overwrite the file.

1. Open the standalone **SoundCode Broadcast** application.
2. Select the menu command **Import Dolby Metadata From BWF File…**
3. Select a BWF file to edit.
4. Use the controls in SoundCode to change the metadata.
5. Select the menu command **Overwrite Metadata In BWF File…**

## Export a multichannel RF64 file larger than 2 GB (Pro Tools)

In this scenario, you would like to export a single multichannel mix to a file larger than 2&nbsp;GB.

1. Finish the mixes by bouncing them to disk in Pro Tools.
2. Import the bounced files into Pro Tools tracks — a 5.1 track for the 5.1 mix (or six mono tracks if you prefer).
3. Make sure the imported mix files are positioned at the correct location in the timeline (typically at the far left).
4. Select the imported mix in the timeline.
5. Select the **SoundCode BWF Export** plug-in in the AudioSuite menu.
6. Set the configuration controls to **BEXT**.
7. Set up the mode control to **LCRLsRs** and enable the **LFE** control.
8. Name the output file and location, and click **Export**.
