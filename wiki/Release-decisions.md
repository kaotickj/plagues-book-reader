# Release decisions and verification gaps

Only newly authored documentation and the owner-authorized, metadata-cleaned Sabrina voice are published in this preview. No application source is published yet: the older owner-local Reader modules lacked Git history and a Reader-specific license, so complete provenance/contributor-rights verification is still pending. The local portable candidate was built from an explicit module allowlist; no private repository was copied or made public.

No source license is selected on the owner’s behalf. Sabrina has its own publication notice; do not infer that any future source license automatically covers its recording. Review upstream code, weights, runtime and dependency terms separately.

Local package metadata identifies PyQt6 6.11.0 as GPL-3.0-only, Qt6 6.11.2 as LGPL v3 and PyQt6-sip 13.13.0 as BSD-2-Clause. markdown-it-py/mdurl license fields were not populated in the inspected metadata; verify upstream files. Review exact FFmpeg build options, Opus and Poppler obligations if shipping binaries. The separate Voice Studio project’s MIT declaration is not a blanket license for its dependencies or voice assets.

Before source/binary release: resolve ownership/license; publish a reviewed engine/bootstrap/overlay artifact and compatible dependency lock; verify model availability/revisions/checksums; validate clean-system installation and wheel packaging; exercise each claimed mode/hardware; test keyboard and assistive-technology interaction; review untrusted document/web extraction and privacy/deletion behavior; document performance/quality limits. Do not claim full screen-reader support or accessibility certification.

Evidence boundary: local installed Reader regression suite passed 150 tests plus 24 focused installed-code tests for resume/Markdown. The separate portable source candidate passed 12 newly authored synthetic tests without model downloads or live generation. These tests are not clean-machine speech-installation certification. Short matched speech samples showed variable quality and included startup overhead; they are not published here and are not general performance promises.

Existing private repositories remain private. No Voice Studio code or settings were altered for this project.
