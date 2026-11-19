# Status and setup

## What is available

This public repository is a documentation/voice preview. It has no Reader application source, wheel, binary, supported package-install command or model downloader. Do not install unrelated packages named similarly. A local portable candidate passed synthetic tests, but a clean-machine software installation has not been demonstrated.

The existing local implementation uses Linux/Python 3.12, PyQt6 for the GUI and Qt multimedia for playback. It calls a separately installed compatible Voice Studio engine and bootstrap from a separate speech Python runtime. Stock upstream `chatterbox-tts` alone is not a verified drop-in replacement for those interfaces. Windows, macOS, NVIDIA and alternate GPU configurations are unverified.

## Portable candidate interface (for future source review)

The candidate reads a local JSON file selected by `PLAGUES_READER_CONFIG`. It isolates user data in `plagues-book-reader-candidate` under XDG data storage by default and does not discover or migrate an existing personal Reader installation. Configuration supplies:

| Key | Meaning |
|---|---|
| data_dir | Writable new Reader data directory |
| voice_library_root | Library root containing voices.json and voices/ |
| engine_install_root | Directory containing separately installed chatterbox_rocm_runner.py |
| engine_source_root | Import root containing chatterbox_studio and its dependencies |
| engine_python | Existing compatible speech interpreter |
| model_overlay_root | Compatible import root containing chatterbox/ |
| gpu_lock_file | Writable lock path agreed with other apps sharing the GPU engine |
| executables | Local ffmpeg, ffprobe and pdftotext paths or PATH names |

These are user-selected paths, never developer-specific absolute locations. Only configure trusted local code: the runtime and source/overlay paths are executable dependencies. Unset configuration placeholders fail rather than guessing. Model lookup remains owned by the external engine; changing Reader’s data_dir does not relocate model weights.

## Reproducibility checklist before a supported release

1. Resolve Reader source ownership/license and external adapter/overlay provenance.
2. Freeze an available engine/bootstrap/overlay artifact with checksums and its complete dependency lock. The currently observed package versions and engine checksum are in [Engines-and-models](Engines-and-models.md).
3. On a clean Linux system, create an isolated environment and acquire reviewed upstream wheels/models through an explicitly approved installation process. Pin versions and verify hashes; do not download on app startup.
4. Build/install Reader into that environment, verify configuration and voice/model discovery, then run synthetic import/resume/storage tests.
5. With other generation paused, render a small synthetic passage in each claimed mode, inspect backend/parameter-placement proof, listen to the audio and test cancellation/restart.
6. Document the verified OS, hardware, drivers and reproducible commands. Until these checks pass, no universal supported setup is claimed.

There is deliberately no fabricated one-command engine installer here. This preview does not install packages, weights or drivers.
