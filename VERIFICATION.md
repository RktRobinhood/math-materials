# Function Lab v2.4.2 — Verification record

Tested 21 October 2026 in headless Chromium via Playwright; PDF parsed with PyMuPDF and rendered at 160 dpi with PDFium, QR decoded via OpenCV and zbar.

### Checks passed

- Five-second active question inspection gate and single-tap answer submission.
- 6-question perfect Standard run = 15/15; Boss Run unlocks.
- Four-run session (15, 0, 18, 0) correctly retains 18/15 personal best, round count and Boss flag.
- Standard mode remains adaptive; Boss mode remains six level-3 questions at three marks each.
- Session state and name survive refresh; 20-minute timer is shared between runs; expired incomplete run does not erase previous completed best.
- Final compact FL4 QR correctly encodes score, 4-run trend, best-run question evidence and focus/clipboard telemetry. Independently decoded from a rendered PNG using OpenCV and zbar, including the Danish character ø (QR uses UTF-8 ECI 26).
- Teacher manual check-in parses FL4; reconstructs exact score and category marks; displays wax estimated grade, 4-run trend, 4-skill radar and integrity indicators. Duplicate scan ignored; roster CSV exported.
- Teacher imports older v3 and v2 check-in records.
- Student and teacher grade conversion agree for every mark from 0/15 through 18/15. Grade max remains 7 even for 18/15.
- Touch-enabled graph pan, pinch zoom and Reset view simulated at phone width. No horizontal overflow at 320, 390, 768 and 1280 pixels. Student QR verified at all four widths.
- PDF Blob starts with valid PDF signature, parses as one page and includes the best-run score, estimated grade, response text, and embedded QR. PDF rendered and visually inspected; score, QR and wax emblem do not overlap.

### Review gates

- Academic / teaching reviewer: **8.8 / 10** — appropriate content and application focus; the *illustrative* nature of a full IB boundary applied to a six-question quiz is disclosed at point of use and documented.
- Student / logistics reviewer: **8.8 / 10** — score, radar, wax seal, large retries and check-in are explicit; 20-minute replay loop and persistence are clear; QR and PDF have rescue paths.

### Not verified on physical hardware

- Webcam permission and autofocus on the teacher's computer.
- Physical iPhone Safari pinch gestures, webcam QR decoding and iOS PDF share sheet.
- Live deployment on the teacher's GitHub Pages URL.

**Grade source:** May 2025 Time Zone 3 Mathematics AA SL official overall final grade boundary table; the May 2026 TZ3 figures online are reported but not provided with the complete 1–7 range in sources used for this version. The grade stamp is a classroom benchmark only.

### v2.4.1 single-tap regression (21 October 2026)

- Removed the intermediate **armed** state, confirmation tap and obsolete two-tap wording.
- Kept the original five-second active inspection gate, answer validation, six-question format, shared timer and scoring.
- Chromium Playwright checked that the first allowed click advances exactly one question (multiple-choice and numerical-response paths).
- Tested Standard 15/15, lower-score retry, Boss 18/15, later lower-score retry; 18/15 retained.
- Tested FL4 QR independent decoding, teacher manual import, duplicate protection, roster CSV, PDF receipt, refresh recovery and time expiry. All passed.
- The teacher HTML and bundled licence notices were left byte-for-byte unchanged from the v2.4 downloadable ZIP.

### v2.4.2 mobile scrolling regression (21 October 2026)

- Root cause corrected: the earlier graph canvas used `touch-action: none`, causing all touch swipes to move the graph rather than scroll the page.
- Graph defaults to `touch-action: pan-y` with no finger pointer capture and no touch-event `preventDefault()`; **Explore graph** opts into touch gestures temporarily with `touch-action: none`.
- Checked native vertical page scroll beginning directly on the graph at 320, 390 and 768 px mobile widths using real Chromium DevTools touch events. The graph's centre remains unchanged until exploration is enabled.
- Tested both horizontal and vertical graph dragging, two-finger pinch zoom, Reset view, always-visible in-graph exit, return to native scroll, and no horizontal page overflow at these widths.
- Tested older touch-event fallback (PointerEvent unavailable); swipe-to-scroll and opt-in controls continued to function.
- Desktop mouse dragging and +/-/Reset controls pass without enabling touch mode.
- Full v2.4.1 regression re-run on updated student HTML: perfect standard = 15, lower-scoring replay, Boss = 18, further lower replay, highest score retained, QR+PDF, teacher import and CSV, zero-score path, refresh and session expiry. All passed.
- Teacher HTML is byte-identical to v2.4.1. There is no QR schema or grading change.
- Academic-review pass: 9/10 (curriculum and answers unchanged; no new scoring inconsistencies). Student/logistics-review pass: 9/10 (normal mobile scrolling and escape control remove the prior navigation trap; control labels visible). No blocking issues observed in automated Chromium tests.
- As before, real iPhone Safari and hardware webcam checks need verification on an actual device.
