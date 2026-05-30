# TODOs

1. **Write `parse_playback_history.py`** — `BoomboxPlaybackSession.json` is the richest file (8,964 records) and the natural starting point. Load it, parse `timestamp_utc`, and produce a summary: total sessions, date range, stutter rate (`message_n_stutter > 0`), average latency (`message_ms_latency`), most common transition type (`message_transition`), breakdown by `context_conn_country`. Print to stdout or write to a CSV. This is the unblocking first script.

2. **Add `.gitignore`** — the entire export is unprotected. `my_spotify_data/` contains 112MB of personal data including search queries, device identifiers, share URLs (with real `spotify.link` links), and geographic location data. Add a `.gitignore` at the project root that excludes `my_spotify_data/` before this ever touches a remote.

3. **Filter and document the epoch-zero records** — at least one event has `timestamp_utc: '1970-01-01T00:00:00.270Z'` (Unix epoch zero — a corrupt or unset timestamp). Before building any timeline or time-series analysis, add a cleaning step that filters `ts < '2020'` and logs the count of affected records per file. `ReadMeFirst_TechnicalLogInformation.pdf` may explain when this occurs.

---

## Future Ideas

4. **Listening pattern analysis** — `BoomboxPlaybackSession.json` has `message_n_seekfwd`, `message_n_seekback`, `message_n_stutter`, and `message_transition` per session. Aggregate by day/week to answer: what % of tracks do you skip? Does stutter rate vary by country (IN vs NL)? Are there listening sessions vs background-play patterns visible in the transition types?

5. **Search history visualisation** — `SearchViewResponse.json` has 53 real queries with the actual text typed (e.g. `'hardc'`, `'par chanaa de'`, `'park chan-wook decision leave'`). Parse and categorise searches by genre, language, or content type (music/podcast/film). A simple word cloud or tag frequency chart would reveal discovery patterns.

6. **Cross-file listening timeline** — join `AddedToPlaylist.json` (32 events), `AddedToCollection.json` (36 events), and `BoomboxPlaybackSession.json` (8,964 events) on `timestamp_utc` to reconstruct a day-by-day timeline: when you discovered something, when you played it, when you saved it. Could reveal how long between first play and saving a track.

7. **Geography and device breakdown** — `context_conn_country` (IN/NL) and `context_device_type`/`context_os_version` appear across many files. Plot listening volume by country and device over the 23-month period. Useful if you've moved or travelled — the data reflects where you actually were.

8. **Podcast and show tracking** — `AddedToCollection.json` contains `message_set: 'show'` entries (podcast follows). Cross-reference show URIs with the Spotify API to resolve actual names and track which podcasts you followed and when.
