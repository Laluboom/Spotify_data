# Reference — Spotify_data

_Last refreshed: 2026-05-30_

## Purpose
Personal Spotify data export — 169 JSON files of technical telemetry logs covering 23 months of listening activity (Jan 2024 – Nov 2025). No analysis code exists yet. The data is the raw material for a listening-history and behaviour analysis project.

## Stack
- Data only — JSON files exported via Spotify's "Download your data" feature
- No scripts, no dependencies

## Entry Points
```bash
# No runnable code exists yet. To start analysis:
python3 -c "import json; data = json.load(open('my_spotify_data/Spotify Technical Log Information/BoomboxPlaybackSession.json')); print(len(data), 'playback sessions')"
```

## Key Files
| File | Records | What it contains |
|------|---------|-----------------|
| `BoomboxPlaybackSession.json` | 8,964 | Per-track playback sessions — device, OS, country, latency, stutter count, seek events, transition type |
| `AddedToPlaylist.json` | 32 | Tracks added to playlists — track URI, playlist URI, timestamp |
| `AddedToCollection.json` | 36 | Liked tracks and shows — item URI, content type (track/show), timestamp |
| `SearchViewResponse.json` | 53 | Search queries — query text, candidate result URIs, country, platform |
| `SessionCreation_Hourly.json` | 8 | Session IDs and creation timestamps |
| `RemovedFromPlaylist.json` | 4 | Tracks removed from playlists |
| `Share.json` | 1 | Share event — destination app (WhatsApp), entity shared, share URL |
| `ReadMeFirst_TechnicalLogInformation.pdf` | — | Spotify's schema documentation for all log types |

## Data Snapshot
- **Total events (real):** 127,701 across all 169 files
- **Date range:** 2024-01-06 → 2025-11-16
- **Device:** iPhone 15 Plus (`iPhone15,4`), iOS 18.x
- **Countries observed:** IN (India), NL (Netherlands)
- **Total export size:** ~112 MB
- **Epoch-zero artifact:** at least one record has `timestamp_utc: 1970-01-01` — filter `ts > '2020'` before any analysis

## Run Status (2026-05-30)
No code to run. Data inspected directly: loaded `BoomboxPlaybackSession.json` (8,964 records), `AddedToPlaylist.json` (32), `SearchViewResponse.json` (53), `AddedToCollection.json` (36), `SessionCreation_Hourly.json` (8), `Share.json` (1). All files are valid JSON. Full event count and date range confirmed via script.
