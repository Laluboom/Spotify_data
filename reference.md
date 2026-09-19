# Reference — Spotify_data

_Last refreshed: 2026-09-19_

## Status: PARKED — blocked on missing data

This repo contains **no code**. It has four tracked files (`reference.md`, `todo.md`,
`last_run.json`, `.gitignore`) and two commits, both on 2026-05-30. Nothing since.

More importantly: **the Spotify export is gone from this machine.** Neither
`my_spotify_data/` nor `spotify_data.local.json` exists, and `git status --ignored`
reports zero ignored files. The project is premised on a dataset that is not here.

## Purpose

Analyze a personal Spotify "Download your data" export — listening history, skips,
search activity, playlist/collection events — locally. Raw exports are personal data
and stay out of Git.

## Stack

Nothing chosen. No language, no dependencies, no scripts. A future implementation
would most naturally be Python + pandas over the export's JSON files, but that is a
guess, not a decision.

## Entry Points

None. There is no runnable code.

The previous version of this file documented a `python3 -c "import json; ..."` one-liner
against `my_spotify_data/Spotify Technical Log Information/BoomboxPlaybackSession.json`.
That path does not exist, so the command fails with `FileNotFoundError`. It has been
removed rather than left as a trap.

## Key Files

| File | Role |
|------|------|
| `reference.md` | This file |
| `todo.md` | Ranked next steps — currently a wind-down/park list |
| `last_run.json` | Review record |
| `.gitignore` | Ignores exports; note the `*.json` blanket rule at line 30 |

## What would have to be true to start

1. A fresh Spotify export downloaded and unpacked locally. Spotify takes up to
   **30 days** to fulfil the request, so this is the long pole.
2. One specific question worth answering, written down. "Listening pattern analysis"
   is not a scope; "what fraction of tracks do I skip within 30s, by hour of day?"
   is one afternoon of work.

Until both hold, there is nothing to build.

## Note on the sanitize commit

`ea364b7` ("Sanitize Spotify data scaffold") replaced every concrete dataset fact in
`last_run.json` with `"redacted"` — file counts, total size, event counts, date range.
Privacy-wise that was right; practically it means the repo no longer records anything
about the shape of the data it was built around. If the export returns, record the
*schema* (field names, types, row counts) in a gitignored local file so that knowledge
survives the next cleanup.
