# Engines and models

## Actual local UI modes

| UI mode | Engine/model | Execution | Status and limits |
|---|---|---|---|
| Original English · GPU (default) | Chatterbox Original English; natural_narration profile | Existing Linux ROCm GPU adapter | Locally exercised; clean-machine distribution not verified; may need pre-generation to avoid pauses |
| Nano · CPU only | Chatterbox Nano; clear_narration profile | CPU-only worker, GPU hidden and parameter placement checked | Local CPU route exercised; may be slower than playback; still requires compatible external bootstrap/runtime |
| Nano · GPU (ROCm) | Chatterbox Nano; clear_narration profile | Existing Linux ROCm GPU adapter, no silent CPU fallback | Locally exercised; pronunciation/pacing varies with content; not universally reliable |

Nano’s internal PyTorch device is named `cuda` on ROCm; this is not evidence of NVIDIA support. Turbo, multilingual and Qwen entries may exist in Voice Studio’s model catalogue but are **not Reader UI modes** and are not supported by this preview.

## Observed environment, not a clean-system lockfile

Inspection date: 2026-11-19. GUI: Python 3.12 family; PyQt6 6.11.0, PyQt6-Qt6 6.11.2, PyQt6-sip 13.13.0, markdown-it-py 4.2.0, mdurl 0.1.2. Speech runtime metadata: torch 2.10.0+rocm7.1, torchaudio 2.10.0+rocm7.1, transformers 4.57.3, safetensors 0.8.0, numpy 2.5.4, soundfile 0.14.0. These are observed installed versions, not a promise that they are available as one public installable set. Chatterbox was imported through an overlay; no chatterbox-tts distribution version was recorded in that runtime.

Observed adapter engine.py SHA-256:
`c8f8b760d731d0272c534894de82bddc817e81d87c8d280bc3626f7f195b2ac6`

This checksum identifies the inspected local engine file; it is not a substitute for a distributable engine/bootstrap/overlay release. The complete compatible source revision and lockfile remain a release gate. Upstream code: https://github.com/resemble-ai/chatterbox . Follow upstream licensing and hardware guidance; do not assume arbitrary latest code matches this adapter.

## Model identities and files

Model revisions below come from local download metadata, not from a new model download. No weights are distributed here.

**Original English:** `ResembleAI/chatterbox`, recorded revision `5bb1f6ee58e50c3b8d408bc82a6d3740c2db6e18`. Required local artifacts: `ve.safetensors`, `t3_cfg.safetensors`, `s3gen.safetensors`, `tokenizer.json`, `conds.pt`. Public revision listing was accessible during verification:
https://huggingface.co/ResembleAI/chatterbox/tree/5bb1f6ee58e50c3b8d408bc82a6d3740c2db6e18

**Nano:** `ResembleAI/chatterbox-nano`, recorded revision `71ccd1d0081b430592cea481f4307e764e07bc64`. Required local artifacts: `ve.safetensors`, `t3_nano_v1.safetensors`, `s3gen_meanflow.safetensors`, `tokenizer_config.json`, plus either `tokenizer.json` or both `vocab.json` and `merges.txt`. Other tokenizer/config files may be required by the selected upstream snapshot. Local metadata identified this revision, but its public revision page was not accessible through the verification tool; public availability and acquisition instructions remain unverified:
https://huggingface.co/ResembleAI/chatterbox-nano/tree/71ccd1d0081b430592cea481f4307e764e07bc64

The compatible engine checks its canonical shared model root at `models/chatterbox/english` or `models/chatterbox/nano`, then its supported legacy/bundled locations. Use that engine’s own model discovery; do not arbitrarily move weights into Reader’s text/audio directory. Verify required files are nonempty and tokenizer assets complete before generation, then verify actual backend metadata in the output. The available metadata does not establish a full content-hash manifest for every weight; that remains necessary for a reproducible release.

## Storage and buffering are separate from models

Original WAV stores generated PCM without Opus encoding. Compact Opus uses approximately 48 kb/s lossy speech encoding after WAV synthesis. Existing cache entries are reused: changing the storage selector alone does not regenerate existing audio. Nano pronunciation problems were reported with WAV too, so Opus is not an established sole cause.

Play as parts are ready allows streaming of completed parts. Nano CPU starts with up to two prepared parts; Original and Nano GPU use a one-part target in the inspected implementation. Preparation can still fall behind, especially at higher playback speed. For reliable uninterrupted listening, disable streaming, prepare the desired scope fully, then play. These are prepared-part buffers, not guarantees of real-time synthesis.
