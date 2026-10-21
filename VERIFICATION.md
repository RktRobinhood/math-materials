# Function Lab v2.4 — Verification record

Tested 21 October 2026 in headless Chromium via Playwright; PDF parsed with PyMuPDF and rendered at 160 dpi with PDFium, QR decoded via OpenCV and zbar.

### Checks passed

- Five-second active question inspection gate and two-tap lock.
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
