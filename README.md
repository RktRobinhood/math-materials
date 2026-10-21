# Function Lab 2.4 — IB Mathematics AA SL

Mobile-first six-question adaptive mathematics game with one **20-minute active-time session**. Includes a teacher check-in dashboard for GitHub Pages.

## Quick deployment

1. Upload **all the files in this folder** (especially `index.html` and `teacher.html`) to the root of your GitHub Pages repository. If replacing v2.3, replace **both** HTML files, because the QR payload is now the shorter `FL4` format.
2. GitHub repo → Settings → Pages → Deploy from a branch → main / (root). Wait until the GitHub Pages URL is live.
3. Share your site root (`https://rktrobinhood.github.io/math-materials/`) with students.
4. Open `https://USERNAME.github.io/REPOSITORY/teacher.html` on your computer. Select **Check scanner setup**, allow webcam access, and scan one test submission. If scanning fails, use a screenshot or paste the plain-text QR record.
5. **Export the teacher CSV or backup JSON before closing/clearing the browser data.** Scores are stored locally in the teacher browser, not on a server.

## What students see

- Six shuffled questions per run, from log laws, function reconstruction, horizontal/vertical translations and dilations, with random numerical values and varying templates.
- Interactive graph: one-finger drag, pinch zoom with two fingers, plus/minus zoom, **Reset view** to recenter, labelled coordinates and a light mathematical grid.
- Minimum five active seconds to inspect each question and a two-tap answer lock to discourage accidental guessing.
- Six-question Standard adaptive runs, worth up to **15** (1 then 2 then four 3-mark questions for a perfect route).
- **Boss Run unlocked after 13/15 or better on a Standard run.** Under this exact progression a Standard score above 12 is 15/15. Boss Run uses six challenge-level questions worth three each, maximum **18/15**.
- One shared 20-minute active-time budget across all runs; interruption pauses active time and is counted. The name, best score, short attempt history, and session state persist on the same device. The final submit button freezes results and displays a compact QR, printable PDF, and fallback text.
- Personal-best score /15, correct answer count, four-category skills radar, attempt trend, and **wax-seal estimated IB-style grade out of seven** on the result page. The seal appears before and after final submission. Boss raw marks above 15 are retained for the score, but capped at 100% for the grade estimate.

## Estimated IB-equivalent grade: transparent benchmark

**Benchmark used: Mathematics: Analysis and Approaches SL, May 2025, Time Zone 3 — overall final grade boundaries (scaled from 0–100).** The complete documented bands are:

| IB grade | Scaled overall percentage |
|---|---|
| 1 | 0–9 |
| 2 | 10–20 |
| 3 | 21–32 |
| 4 | 33–47 |
| 5 | 48–61 |
| 6 | 62–76 |
| 7 | 77–100 |

The app computes `percentage = round(min(best_mark, 15) * 100 / 15)`, then looks up the band. Consequently on this 15-mark quiz:

| Best score /15 | Estimated grade |
|---|---|
| 0–1 | 1 |
| 2–3 | 2 |
| 4 | 3 |
| 5–7 | 4 |
| 8–9 | 5 |
| 10–11 | 6 |
| 12–15, or 16–18 in Boss Run | 7 |

**This is an illustrative classroom comparison, not an official IB grade or a defensible forecast.** The short adaptive quiz samples only a small part of the full syllabus and has a different difficulty/weighting profile from an IB examination. Boundaries are session-specific and are used only as a recognizable student-facing benchmark. The wax emblem is original artwork, not the official IB seal.

Why May 2025? It is a fully documented and cross-checkable complete 1–7 TZ3 table. May 2026 TZ3 *reported* boundary listings currently available to us include grades 3–7, but not a verified complete 1–7 grade range; the game therefore does not mix undocumented or estimated low-grade cutoffs with the 2026 reports.

References:
- May 2025 Math AA SL TZ3 subject report: https://sufferingrepo.me/IB%20SUBJECT%20REPORTS/Group%205%20-%20Mathematics/AASL/Maths%20AASL%20Subject%20Report%20M25%20TZ3.pdf
- Session-by-session sourced boundary comparison: https://www.pietromeloni.com/ib-grade-boundaries/maths-aa-sl

## Teacher check-in and QR

The new `FL4` QR is shorter and includes plain-text name, best score /15, Boss/Standard mode, correct/attempted, earned/available marks in four skills, run count, best attempt index, recent score trend (last 12 attempts), first-attempt question summary, best-run question evidence, and counts for focus interruptions, pause duration, active time, copy/paste/cut/context menu and reload events. Teacher scans reconstruct the **same May 2025 TZ3 estimated grade** from the score, and show it as a small wax seal. Grade does not need a redundant QR field.

Teacher mode accepts **FL4 and older Function Lab v3/v2** check-in records. In a serverless/static site, a QR checksum confirms internal data consistency only; it does not cryptographically authenticate a submission or prove that a student's answers were their own.

## Technical cautions

- Student and teacher app state is local to a single browser/device. Do not clear browsing data until results have been exported. No account or server synchronizes results.
- Webcam APIs normally require HTTPS (`github.io` is HTTPS) or localhost. On `file://`, manual entry works but camera scanning and PDF viewing may be inconsistent.
- A built-in QR decoder is used where available, with two external JavaScript decoder fallbacks. When external resources are blocked and there is no built-in decoder, copy the student's verification text instead.
- Clipboard protections and focus telemetry are best-effort browser-side review indicators, not proof of misconduct. Students may use other devices or modify client-side code. Do not treat focus changes, pasted content or rapid completion as sufficient evidence of wrongdoing.
- This package is suitable for classroom trial after one real student-device/browser and teacher-webcam smoke test. Automated Chromium touch simulations cannot guarantee iOS Safari behavior or camera hardware support.

## Package

`index.html` — full bundled student quiz (self-contained HTML/CSS/JS including a UTF-8-aware QR encoder)

`teacher.html` — teacher webcam/screenshot/manual check-in, radar and trend, CSV and JSON exports

`VERIFICATION.md` — QA record and caveats

`LICENSES.md`, `APACHE-2.0.txt` — notices for bundled QR code library
