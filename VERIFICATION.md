# Function Lab v2.5 — Verification

## Automated functional checks completed

- [x] JavaScript parses successfully on Chromium-compatible browsers.
- [x] **900,000ms** shared session limit; countdown and visible depletion bar; zero-time behavior is automatic final submission.
- [x] Time-out with zero answers produces a teacher-checkable **0/15** record, without leaving students stranded.
- [x] Time-out during a partially answered Boss run keeps the earlier personal best and preserves the partial run evidence.
- [x] Automatic submission hides the reference-sheet modal rather than leaving final results blocked.
- [x] Correct Standard run 15/15 unlocks Boss, incorrect retry 0/15 does not replace the best, correct Boss run produces **18/15**, subsequent worse Boss run does not replace the best.
- [x] Cumulative skill map includes all answers from all runs: six questions after one run, 12 after two, 18 after three, and 24 after four in the test sequence.
- [x] Grade cutoffs for all integer results **0–18** match the raised-by-8-percentage-point policy; 16–18 receive the **7+** badge.
- [x] Final **FL5** QR encodes aggregate skill marks and remains independently decodable, including Danish characters.
- [x] Dense 12-attempt FL5 QR (longer name, several review flags) independently decoded at **320px mobile**.
- [x] Teacher scans/imports FL5 record and shows correct 7+ grade, radar, trend, telemetry, and roster; repeated scan does not duplicate entry.
- [x] Teacher accepts an existing **FL4** and legacy **v3** submission.
- [x] CSV export includes the adjusted grade and cumulative category marks for FL5.
- [x] Student PDF is a valid, single-page selectable-text PDF, containing 7+, accumulated category marks, best-run answers and QR.
- [x] Mobile result layouts at **320, 390, 768 and 1280px** do not overflow horizontally.
- [x] Previously verified mobile graph `Explore graph`, panning, pinch zoom, scrolling, and `Reset view` implementation left intact.

## Manual checks before a class session

- [ ] Launch the live student URL on at least one actual iPhone and Android device; check the 15-minute timer and graph scroll/gesture mode.
- [ ] Give teacher browser camera permission on GitHub Pages HTTPS; scan one complete FL5 QR from a real student phone.
- [ ] Validate manual QR text and QR screenshot import as backups.
- [ ] Export the teacher CSV and check it can be opened in the intended spreadsheet program.

## Educational and student-logistics review

**Teaching / academic critic (self-audit): 9/10.** Existing bank remains confined to covered AA SL function families and log rules; no reflections or quadratics are added. Diagnostic radar is transparent about difficulty-weighted proportions and accumulates actual attempted-question evidence. The grade is explicitly labelled teacher-adjusted and unofficial. **Limitation:** six-question samples and a short total session provide only provisional evidence.

**Student / logistics critic (self-audit): 9/10.** Boss unlock and replay are high-contrast, near the top of results; one-tap answers, mobile scrolling, visible timer, autosave, and multiple submission fallbacks remain. **Limitations:** practical webcam permissions and all device-specific touch behavior cannot be certified without a physical classroom smoke test.

Neither critic score represents an external independent review. Automated tests cannot guarantee all devices or network conditions.

## Run-local penalties: additional verification

Chromium test: a 15/15 raw attempt with two deductions recorded 13/15 net, unlocked Boss Run, and a following clean 15/15 attempt retained 15/15 as the personal best. The FL8 payload parsed successfully in the teacher dashboard and retained the trend [13, 15]. This does not certify physical mobile camera or Safari operation.
