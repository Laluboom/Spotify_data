# TODOs

**Verdict: PARK.** The idea is fine. The data is missing and there is no code. Every
task in the previous list was unexecutable — they all assumed an export that is not on
disk. These five are the wind-down, in order.

---

1. **[QUICK WIN ~15min] Re-request the Spotify data export.**
   Go to spotify.com → Privacy Settings → "Download your data", tick *Extended
   streaming history*, submit. Spotify takes **up to 30 days** to deliver. This is the
   only action here that can be completed today, and it is the one thing blocking
   everything else. Do it now even if you have no intention of writing code soon —
   otherwise the day you *do* feel like working on this, you wait another month.
   The old entry point (`reference.md`, previously line 15) pointed at
   `my_spotify_data/Spotify Technical Log Information/BoomboxPlaybackSession.json`;
   that whole tree is gone.

2. **[DESIGN] Write down the single question this project answers.** ~20min.
   The old `todo.md:13-21` listed five "future ideas" — listening patterns, search
   viz, cross-file timeline, geography/device, podcast tracking. Five unscoped ideas
   and zero code for four months is the diagnosis, not a coincidence. Pick **one**
   answerable question with a number for an answer (e.g. "what share of tracks do I
   skip inside 30s, bucketed by hour of day?") and put it in `reference.md` under
   Purpose. If you can't pick one you care about, that is a real signal — retire the
   repo instead.

3. **[CHORE] Action the park: move the folder out of `04_early_stage_and_ideas`.** ~10min.
   Move to a `parked/` (or archive the GitHub repo) and note the revisit trigger:
   *"when the export lands"*. Right now the daily review keeps drawing a repo that
   cannot progress — this run produced no code findings because there is no code to
   find. Parking it frees review slots for the tiers that have something to review.

4. **[CHORE] Fix the `*.json` blanket ignore before any code is written.** ~10min.
   `.gitignore:30` is `*.json` with a single `!last_run.json` exception (line 31). That
   will silently swallow `package.json`, any tool config, and any small anonymized
   schema fixture you try to commit — and silent gitignore misses are miserable to
   debug months later. Narrow it to the actual export paths (`my_spotify_data/`,
   `spotify_data.local.json`, `outputs/`) which lines 26-27 and 37-40 already cover.
   Do this now, while it costs ten minutes and not a confusing afternoon.

5. **[DOCS] When the export arrives, record the schema before sanitizing.** ~30min.
   `last_run.json:8-12` shows `total_files`, `total_size_mb`, `total_events_real` and
   `date_range` all replaced with `"redacted"` by commit `ea364b7`. The privacy call
   was correct; the side effect is the repo now knows nothing about its own dataset.
   On arrival, write field names, types and row counts per file into a **gitignored**
   `schema.local.md`. That is the artifact that makes a cold restart cheap.
