# Troubleshooting

- **No install command/release:** this is a documentation-first preview. Do not assume the separate Voice Studio package is a standalone Reader installer.
- **Missing runtime / engine / overlay:** verify every configured dependency path and the compatible source/bootstrap contract. No automatic download or CPU fallback repairs a missing GPU runtime.
- **Nano model unavailable:** local metadata identifies a Nano artifact, but public availability is not verified. Do not use a guessed replacement or claim it is supported.
- **Voice list empty:** check voice_library_root/voices.json and referenced files under voices/. Use the published Sabrina manifest to verify the intended reference. Supply only authorized recordings.
- **PDF empty:** check that the PDF contains selectable text and pdftotext is available. Scans need separate OCR.
- **Markdown symbols spoken:** use a new Markdown import or explicitly enable pasted Markdown interpretation. Old audio remains unchanged and will not become corrected merely by selecting a new storage format.
- **Web preview does not appear:** inspect the status message for download, encoding or content errors. Use HTTP(S), fetch a text page, or paste visible text. Login/JavaScript pages may not work. The local URL-field lifetime bug was fixed; ensure the installed build includes it.
- **Wrong/missing reading position:** choose Resume reading, not Play book from start. The local fix defers seeking until playback is ready and keeps Stop from zeroing progress. A position already overwritten by an older build cannot reliably be reconstructed. Named bookmarks are separate from automatic progress. Do not delete caches/state to troubleshoot.
- **Prepared audio seems absent:** verify selected voice/mode and recent reading first. Different modes have independent recordings. Do not regenerate or restore a database until identifying the mismatch.
- **Pauses during playback:** pre-generate the selected scope; increase preparation lead time or use normal playback speed. A one/two-part buffer does not promise sustained real-time performance.
- **Nano mispronounces words or rushes copied page text:** inspect the source layout and formatting, test a short passage, and compare Original mode. Nano performed well on one prepared book but not all page/document inputs. Experimental text/phone/pause changes have not been accepted for release; no pronunciation cure is claimed.
- **CPU/GPU contention:** stop competing model jobs through their owning applications before a new preparation. Never kill unrelated processes to make Reader run. Verify output backend metadata rather than relying on the word cuda alone on ROCm.

Report a minimal synthetic reproduction, selected mode/storage, versions, and expected vs observed behavior. Do not publish personal books, recordings, private URLs, credentials, full logs or state files in an issue.
