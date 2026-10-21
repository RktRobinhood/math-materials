# Function Lab v2.5 — Mathematics AA SL

Mobile-first, serverless, 15-minute adaptive quiz with unlimited retries during one session, cumulative skills radar, Boss Run unlock, wax-seal classroom grade, and teacher QR check-in. Designed for deployment on GitHub Pages.

## Deploy in two minutes

1. Upload all files in this directory to your GitHub Pages repository root. **If upgrading, replace BOTH `index.html` and `teacher.html`: v2.5 uses the new `FL5` QR format.** Keep `README.md`, `LICENSES.md`, and `APACHE-2.0.txt` if you publish the whole package.
2. In GitHub, enable **Settings > Pages > Deploy from branch > main > /(root)**, or keep your existing Pages configuration.
3. Give students `https://USERNAME.github.io/REPOSITORY/` and open `https://USERNAME.github.io/REPOSITORY/teacher.html` on your own computer.
4. On the teacher page, click **Check scanner setup**. Allow webcam permissions (HTTPS required), then scan a test phone. If scanning fails, upload a screenshot or paste the fallback QR text.
5. Export CSV or backup JSON before clearing your browser, using a different teacher computer, or closing the grading session. **The class roster is stored locally in the teacher browser**, not in a shared database.

## How the game works

- **One 15-minute active-time clock across every run**, not 15 minutes per run. The thin top bar visualizes remaining time. The clock still *pauses when the quiz loses focus*, as previously requested, and records interruptions for teacher review. It continues between runs and while viewing results. At zero, the app **automatically submits** and displays the final score and QR—even during an unfinished attempt. If no questions have been answered, it submits 0/15.
- Standard runs have **6 shuffled randomized questions**: log laws, function reconstruction, horizontal/vertical translation, and horizontal/vertical dilation. Each question requires five active seconds of inspection, then **one tap** to submit. A fully correct Standard run earns 15/15.
- **Personal best is never lowered** by a worse retry. The stored name, completed runs, partial timed-out run, best-run answer evidence, and 15-minute timer persist locally on the same browser/device. A partial final attempt contributes whatever questions were answered, and may improve the personal best.
- A Standard score of at least 13/15 unlocks **Boss Run**. Given this version's exact adaptive scoring, that threshold is effectively **15/15**. Boss Run offers six hard questions worth three marks each: up to **18/15**. The result page prominently displays the locked/unlocked Boss gate and an oversized **PLAY AGAIN** button.
- The four-skill spider chart is now **cumulative across ALL completed or partially timed-out runs**. Each answered question contributes its earned marks and offered marks to the relevant subject area; challenge questions carry more marks. The chart updates after each run. Exact category totals and question counts appear below it, along with a compact strongest/next-focus suggestion. This is diagnostic evidence, not a precise standardized ability estimate.
- Graphs retain the translucent grid and axes, **Reset view**, zoom controls, and touch-safe navigation. Phone swipes **scroll the page by default**; **Explore graph** enables touch panning/pinch zoom until students tap **Done · scroll page**.
- Students see their score, the four-skill radar, progress trend, and an original wax-seal grade. The final screen supplies the teacher QR, a PDF of the best-run answers, an independently saved QR image, print fallback, and readable verification text.

## Classroom-adjusted IB-style grade

Basis: **May 2025 IB Mathematics AA SL, Time Zone 3 overall grade boundaries**, with **8 percentage points added to each grade-2 through grade-7 lower cutoff**. This also raises each preceding grade's upper cutoff by 8 points. Grade 1 continues to begin at zero. Values are illustrative classroom benchmarks, **not official IB boundaries or predicted exam grades**.

| Grade | Minimum (%) | Marks from 15 |
|---|---:|---:|
| 1 | 0 | 0–2 |
| 2 | 18 | 3–4 |
| 3 | 29 | 5–6 |
| 4 | 41 | 7–8 |
| 5 | 56 | 9–10 |
| 6 | 70 | 11–12 |
| 7 | 85 | 13–15 |
| **7+** | **Above 100** | **16–18**, possible only in Boss Run |

The percentage is `round(score / 15 * 100)` for scores up to 15. **7+ is a game achievement, not an additional official IB grade.** The teacher console and PDF use the same grading adjustment.

Sources for the original May 2025 grade cutoffs (the +8-point adjustment is teacher-defined):

- May 2025 Math AA SL TZ3 subject report: https://sufferingrepo.me/IB%20SUBJECT%20REPORTS/Group%205%20-%20Mathematics/AASL/Maths%20AASL%20Subject%20Report%20M25%20TZ3.pdf
- Grading comparison: https://www.pietromeloni.com/ib-grade-boundaries/maths-aa-sl

## QR and teacher records

**FL5** records contain the student's name, best score (possibly above 15 in Boss Run), correct/attempted best-run count, recent score trend and total run count, best-run level/correctness pattern, first-run pattern, **cumulative four-skill marks** (earned/offered across all runs), focus losses and pause time, active time, clipboard/context-menu/reload attempts, session ID, and checksum. The teacher can reconstruct the best-run evidence separately and render the accumulated radar. FL5 codes remain compact enough for phone cameras; manual text and screenshot import are fallback options.

`teacher.html` continues accepting **FL4, Function Lab v3/v2, and FL1** records. Earlier codes show a *best-run* radar rather than the new all-run map. Older v3 QR records containing a historical grade are validated against their original historical thresholds; the current classroom grade shown on the teacher screen follows the **+8-percentage-point policy**.

The checksum catches transcription corruption, **not deliberate tampering**. Client-side telemetry is a review indicator, not proof of cheating; no browser-only activity can securely authenticate exam marks. Webcam and screenshot QR decoding may depend on browser-native APIs or an externally hosted library (`jsQR`) if unavailable natively. The scanner does not upload images or results to any service.

## Browser and privacy notes

- Host on HTTPS (GitHub Pages), not `file://`, for dependable webcam permissions and sharing. A physical device/browser camera test is still necessary.
- The student session and teacher roster live in **separate localStorage areas on separate devices**; they are not synchronized. Private browsing, clearing site data or switching browsers will lose records.
- The activity records only aggregate session evidence (focus/clipboard/reload counts, time) and submitted answers needed to verify the best run. No keylogging, location tracking, or server upload.
- User-facing fields do not prevent a technically skilled student from decoding or altering client-side data. Use the tool for formative checking rather than high-stakes secure examinations.
- The full regression test report is in `VERIFICATION.md`.
