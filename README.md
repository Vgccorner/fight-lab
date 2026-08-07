# Fight Lab

Personal workout generator + logger for calisthenics/MMA training. Single
self-contained `index.html` — no build, no dependencies, no accounts.

## Use it

- **Everywhere (synced):** https://vgccorner.github.io/fight-lab/ — add to home
  screen on the phone.
- **Local:** open `index.html` in a browser, or `python3 -m http.server` here.
  Local copies sync too once connected.
- Claude artifact (offline-only, no sync — its CSP blocks network):
  https://claude.ai/code/artifact/60feed68-6280-4a3e-8167-9c9d13e62403

## Sync

One shared log across devices, stored as `data.json` in the **private** repo
[`fight-lab-data`](https://github.com/Vgccorner/fight-lab-data) — every change
is a commit, so history is free.

Per device (once): Setup tab → Sync via GitHub → paste a fine-grained PAT
(github.com → Settings → Developer settings → Fine-grained tokens; repository
access = only `fight-lab-data`; permissions = Contents read/write).

How it works: pull → union-merge by workout id (deletions carried as
tombstones, settings by newest `updatedAt`, exercise-rotation stamps by max) →
push with sha-based conflict retry. Pulls on open and on tab focus; pushes
debounced ~4 s after any change. The token lives only in that browser's
localStorage — never in exports or `data.json`.

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

This repo is public only to get free GitHub Pages hosting; it contains app code
only. All personal data lives in the private data repo.
