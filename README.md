# Fight Lab

Personal workout generator + logger for calisthenics/MMA training. Single
self-contained `index.html` — no build, no dependencies, no accounts.

## Use it

- **Phone / anywhere:** https://claude.ai/code/artifact/60feed68-6280-4a3e-8167-9c9d13e62403
  (private artifact; add to home screen for an app feel)
- **Local:** open `index.html` in a browser, or `python3 -m http.server` in this folder.

## What it does

- Generates sessions from location (home/gym), time (20–60m), and focus
  (push / pull / legs / core-rotation / full / conditioning / fight day / mobility).
  Auto mode picks whatever you've trained least in the last 7 days.
- Home plans only use what's actually there: bodyweight, 15 lb kettlebell,
  5–15 lb dumbbells, balance board (pull-up bar / bands / rope toggleable in Setup).
- Logs sets with last-time numbers shown, rest timer, PR detection (est 1RM /
  max reps), quick-log for MMA classes/sparring/runs.
- Progress: 12-week heatmap, weekly minutes, push/pull/legs/core balance with
  neglect warnings, PR board, full history.
- Every generated session ends with kick-flexibility cool-down work.

## Data

`localStorage` only, per device/browser. Setup → Export/Import JSON to move or
back up. No sync between phone and laptop (yet).
