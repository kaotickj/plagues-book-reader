# Plague’s Book Reader

Read-aloud assistance for books, documents, static webpages and pasted text.

**Public project status: documentation-first preview, not an installable Reader release.** A portable local source candidate exists, but the older modules’ ownership/provenance chain, source license and clean-machine external-runtime setup still need review. This repository deliberately publishes no application source or installer yet. It does include the owner-authorized **Sabrina Reader** default reference; other voices must be user-supplied.

Reader is not a full system screen reader. It does not announce desktop focus, inspect arbitrary application controls, read images using OCR, or follow a live browser accessibility tree.

## What the local implementation does

- Imports EPUB, text PDFs, TXT, DOCX, ODT, HTML and Markdown; takes pasted text and HTTP(S) page text.
- Provides a text review step for pasted/web content, an explicit pasted-Markdown option, ARIA-aware static HTML extraction, and Markdown formatting cleanup.
- Prepares narration locally, caches completed parts, supports playback/speed/seeking and whole-reading preparation.
- Restores reading positions and offers Resume reading, Save bookmark and Bookmarks.
- Offers Original English GPU, Nano CPU and Nano GPU modes through a separately installed compatible engine; these are local implementation modes, not a promise of turnkey support from this repository.

## Start here

1. Read [Status and setup](docs/Setup.md). There is no supported `pip install` or binary download for Reader here yet.
2. Review [Engines and models](docs/Engines-and-models.md) for exact observed artifacts, prerequisites and gaps.
3. Read [Voices](docs/Voices.md) before using Sabrina or supplying a different authorized reference.
4. For an existing compatible local installation, follow [Using Reader](docs/Using-Reader.md) and [Troubleshooting](docs/Troubleshooting.md).
5. Check [Release decisions](docs/Release-decisions.md) before treating this preview as a software release.

The [GitHub Wiki](https://github.com/kaotickj/plagues-book-reader/wiki) uses the same maintained guide pages. The `wiki/` directory holds their staged source; it is not a substitute for initializing/publishing the actual Wiki.

## Custom voices

Supply an authorized reference using the [local voice-library instructions](docs/Voices.md).

Use only your own voice or voices you own, have licensed for this use, or have permission to use. We don’t condone piracy or support unauthorized voice use. The Reader does not verify permissions or block custom voices, so legitimate uses, including accessibility, aren’t restricted.

## Quality and performance

Nano worked well with one prepared book but had reported pronunciation/pacing problems on web, pasted and Markdown content. Markdown-marker leakage and lost resume timestamps were independently reproduced and fixed in the local implementation. Those fixes do not prove general Nano speech quality. Original with original WAV may require preparing ahead to avoid pauses. Short timing samples include startup and do not predict sustained throughput.

Text/model inference remains local. Fetching a webpage contacts that URL and redirects; it does not use browser login cookies or execute JavaScript. Imported text, bookmarks and generated audio are private user data, not repository assets. Neither DRM removal nor access-control bypass is offered.

## Licensing and publication scope

No source-code license is assigned in this documentation preview. No Voice Studio code, engine code, model weights, books, private state, generated narration, credentials or other voices are included. Sabrina’s owner attested rights and expressly authorized publication as the default; see its separate [publication notice](assets/sabrina-reader/NOTICE.md). That notice does not assign an MIT or blanket redistribution license to the recording.

Voice Studio remains a separate project: https://github.com/kaotickj/plagues-voice-studio . No existing repository is being converted to public as part of this project.
