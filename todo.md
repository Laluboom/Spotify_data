# TODOs

1. **Write `parse_playback_history.py`** — load the local playback-session export, parse `timestamp_utc`, and produce a safe local summary. Keep generated summaries ignored unless they are explicitly anonymized.

2. **Keep raw exports ignored** — `my_spotify_data/` contains personal listening history, search queries, device identifiers, links, and location-related metadata. Do not commit raw export files or generated datasets.

3. **Filter invalid timestamps** — before building any timeline or time-series analysis, add a cleaning step that filters implausibly old timestamps and logs counts only to ignored local output.

---

## Future Ideas

4. **Listening pattern analysis** — aggregate playback fields by day/week to study skips, stutters, and transition types without committing raw or identifiable data.

5. **Search history visualization** — parse and categorize search activity locally. Do not commit raw search terms or charts that expose specific queries.

6. **Cross-file listening timeline** — join playlist, collection, and playback events locally on `timestamp_utc` to reconstruct discovery and save behavior.

7. **Geography and device breakdown** — analyze location and device metadata locally. Treat outputs as private unless aggregated enough to be non-identifying.

8. **Podcast and show tracking** — cross-reference saved show or podcast URIs locally if API resolution is useful, keeping resolved names out of Git unless anonymized.
