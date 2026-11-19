# Voices

## Sabrina Reader default

The owner expressly authorized publication of the exact Sabrina Reader reference used by the local Reader and attested full rights to its use. The only published recording is `assets/sabrina-reader/voices/sabrina-reader.wav`. See the separate NOTICE.md; no MIT or general third-party redistribution license is assigned to the recording.

The cleaned WAV retains identical PCM audio: 48,000 Hz, stereo, 16-bit PCM, 118.5465 seconds. Metadata/comment/ID3 chunks were removed without resampling, trimming or normalizing audio. Verify SHA-256:

`9dbcef8815ad5e50b070bd64708c6228b4f7d350f6f44e60f339c753da4a7fef`

The accompanying manifest records audio parameters and PCM checksum. No transcript, personal identifiers from the original voice catalogue or unrelated audio is published.

## Configure an existing compatible Reader / future portable candidate

Use `assets/sabrina-reader` as voice_library_root. Its voices.json contains one entry named **Sabrina Reader**, file `sabrina-reader.wav`, resolved inside its `voices/` subdirectory. The portable candidate prefers that name when no saved voice is selected. A saved user preference takes priority; loading the app does not overwrite it.

Use only your own voice or voices you own, have licensed for this use, or have permission to use. We don’t condone piracy or support unauthorized voice use. The Reader does not verify permissions or block custom voices, so legitimate uses, including accessibility, aren’t restricted.

To supply another authorized voice, create a separate local library outside the repository:

```json
[{"id":"my-local-voice","name":"My local voice","file":"reference.wav"}]
```

Put your authorized recording at `voices/reference.wav` under that library root and select its name in the app. Use a clear recording appropriate to the chosen engine and review that engine’s reference requirements. Do not place personal recordings or voice-library state in Git. Do not rename an unrelated reference as Sabrina Reader. Other voices are entirely user-supplied; this repository does not grant rights to them.
