# Using Reader

These instructions describe the existing local implementation. This public documentation preview does not yet provide an application installer. See [Setup](Setup.md) first.

## First run

Verify the local speech engine/configuration and choose an authorized voice (Sabrina Reader is the preferred default when present). Pick a narration mode supported by your runtime. Choose Original WAV or Compact Opus for **newly generated** audio. Opening the app itself does not load a model. With no compatible engine/voice, imports may work but narration cannot be prepared.

## Books and documents

Use **Import file…** for EPUB, PDF, TXT, DOCX, ODT, HTML or Markdown. EPUB chapters follow spine order; PDFs use extracted pages. Scanned PDFs require separate OCR; encrypted/protected files may fail. Complex layouts/tables need review. Markdown imports remove formatting syntax while retaining meaningful visible text/code/links and the original Markdown separately. Older raw Markdown readings are not silently rewritten; reimport creates a separate cleaned reading when text changes, preserving old audio/bookmarks.

## Webpages

**Web page… → enter HTTP(S) URL → OK → review extracted text → Import text.** Review/cancel does not replace the open reading; importing saves its position and switches to the new one. The static extractor honors supported ARIA names/hidden content and prefers article/main text. No browser cookies, JavaScript, external CSS evaluation or live accessibility tree are used. Copy rendered text from private/dynamic pages instead; Reader does not bypass authentication.

## Paste

**Paste / selection…** opens an editable review. Paste clipboard text, or use X11 primary selection when supported. Check **Interpret pasted text as Markdown** only when that is intended. Plain text has no ARIA structure; decorative symbols, menus or form labels may need manual cleanup. Meaningful symbols should not be stripped indiscriminately.

## Prepare and listen

Choose Preview first part for a short test or Prepare narration for the selected scope, then confirm. Current chapter prepares the selected section; Whole book prepares all missing sections. A webpage normally imports as one section. Completed parts are reused and retained on cancellation. For uninterrupted listening, prepare fully before Play / Pause. Changing voice/mode selects a different audio cache; it does not convert previous audio.

Resume reading continues saved chapter/part/time. Stop preserves progress. Save bookmark creates a permanent named place; Bookmarks restores it with its associated voice and mode. Play book from start deliberately starts over. Closing during generation requests cancellation; close again after it stops. Missing audio/voices should produce a message without erasing the bookmark.

Example synthetic test text: “Privacy. Updated. Our team works in Tennessee. Please review the details.” Check actual pronunciation and pacing before preparing a long reading. Do not infer quality from speed or a successful file export alone.
