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

Technique-first MMA prep — stance work, kicks and fists, light loads through
full range of motion. Not a bodybuilding app.

- Generates sessions from location (home/gym), time (20–60m), and focus
  (technique / push / pull / legs / core-rotation / full / conditioning /
  fight day / mobility). Auto mode picks whatever you've trained least in the
  last 7 days, and suggests a technique day if a week has none.
- **Technique focus**: stance drills (horse stance, switches, footwork box,
  pivots, level changes), kick technique (teeps, round kicks, slow side kicks,
  chamber holds), punch form reps, and light KB flows (halos, carries,
  windmills) — full-ROM strength that isn't about getting huge. Every other
  session ≥30 min also opens with a short Stance & Technique block.
- Plans only use equipment that's actually there — home gear (bodyweight,
  15 lb KB, light DBs, balance board + toggles) and now a **gym equipment**
  card in Setup (barbell / DB rack / KBs / pull-up & dip / machines / power
  tools / rope+bands). Defaults assume a freeweight gym. The session header
  lists the gear the plan needs.
- Every exercise shows **How** (form cues) and **Why** (fight carryover) —
  inline on warm-up/cool-down rows, one tap ("ⓘ how & why") on work cards.
- Anything can be **skipped with a reason** (didn't know how / no equipment /
  pain / time); skips land in history, so the log shows what was actually done
  vs. skipped — block headers count done/skipped live during the session.
- Logs sets with last-time numbers shown, rest timer, PR detection (est 1RM /
  max reps), quick-log for MMA classes/sparring/runs.
- Progress: 12-week heatmap, weekly minutes, push/pull/legs/core balance with
  neglect warnings, PR board, full history.
- Every generated session ends with kick-flexibility cool-down work, and each
  day carries one martial principle (Musashi, Bruce Lee, gym wisdom).

This repo is public only to get free GitHub Pages hosting; it contains app code
only. All personal data lives in the private data repo.
