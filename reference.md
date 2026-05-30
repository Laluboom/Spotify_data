# Reference — Spotify_data

_Last refreshed: 2026-05-30_

## Purpose
Spotify data export workspace for future listening-history and behavior analysis. Raw exports and private dataset metadata stay local and are not tracked in Git.

## Stack
- Data only — JSON files exported via Spotify's "Download your data" feature
- No scripts, no dependencies

## Entry Points
```bash
# No runnable code exists yet. To start analysis:
python3 -c "import json; data = json.load(open('my_spotify_data/Spotify Technical Log Information/BoomboxPlaybackSession.json')); print(len(data), 'playback sessions')"
```

## Key Files
| File or path | Role |
|--------------|------|
| `my_spotify_data/` | Local raw Spotify export — ignored by Git |
| `spotify_data.local.json` | Local private export summary — ignored by Git |
| `reference.md` | Safe tracked project reference |
| `todo.md` | Safe tracked next steps |
| `last_run.json` | Safe tracked run summary |

## Run Status (2026-05-30)
No runnable analysis code exists yet. Raw export files were inspected locally and are ignored. Keep exact dataset counts, device details, location data, search terms, links, and listening history in ignored local files only.
