# Daily review — Spotify_data — 2026-09-19

**Verdict: PARK.**

## What I looked at

The whole repo, which took about four minutes, because the whole repo is four files:
`reference.md`, `todo.md`, `last_run.json`, `.gitignore`. Two commits, both on
2026-05-30. No source files of any kind. I did not run a browser check — there is no
web code, and no code at all.

## What I found

The finding that decides this review is that **the Spotify export is not on this
machine.** `my_spotify_data/` doesn't exist, `spotify_data.local.json` doesn't exist,
and `git status --ignored --short` comes back completely empty — not one ignored file.
This is a data-analysis project with no data. Every item in the old `todo.md` assumed
that export was sitting there; none of them are executable today.

Two smaller things fall out of that. `reference.md:15` advertised the project's only
"entry point" as a `python3 -c` one-liner reading
`my_spotify_data/.../BoomboxPlaybackSession.json` — that's a documented command that
fails with `FileNotFoundError`, so I removed it rather than leave the trap. And
`.gitignore:30` is a blanket `*.json` with only `!last_run.json` exempted, which will
quietly swallow a `package.json` or any schema fixture the moment someone starts
writing code here. Worth ten minutes now, miserable to debug later.

There's also a self-inflicted wound worth naming. Commit `ea364b7` ("Sanitize Spotify
data scaffold") replaced `total_files`, `total_size_mb`, `total_events_real` and
`date_range` in `last_run.json` with `"redacted"`. Right call on privacy — but the
repo now has no record of what its own dataset even looked like, so a restart starts
from zero twice over.

## Why PARK and not RETIRE or REVIVE

I considered RETIRE and it's overreach. Personal Spotify-export analysis is a real,
well-trodden, genuinely fun project; it isn't redundant with anything and it wasn't a
bad thought. But REVIVE would be dishonest. The tier rule is that a REVIVE has to name
the smallest end-to-end thing that *works*, and nothing can be made to work this
session — I can't write a parser against a schema I can't inspect, and I can't test it
against data that isn't here. That's precisely the write-architecture-instead-of-
software failure this tier is meant to catch.

So: park, with a crisp precondition. Two things have to be true — the export is back
on disk, and there's one concrete question with a number for an answer. Not "listening
pattern analysis" (the old `todo.md:13`), which is a category, not a question.

## What I'm proposing

The quick win is deliberately not code: **re-request the export today.** Spotify takes
up to 30 days. It's the only task on the list that can be finished this afternoon, and
doing it now means the day you actually feel like building this, you aren't starting a
month-long wait. That asymmetry is the whole argument for touching this repo at all
today.

After that: pick the one question (four months and five unscoped "future ideas"
produced zero lines of code — that's the diagnosis, not bad luck), move the folder out
of the active tiers so the review rotation stops drawing a repo that can't progress,
fix the gitignore landmine, and — when the export lands — write the schema into a
gitignored `schema.local.md` before sanitizing anything.

One honest note on cadence: I set `next_review` to 2026-09-29 per the standard 10-day
rule, but if you action the park that slot should go to a repo with something in it.
