# ll-music-data

Daily-refreshed Love Live dataset for [ll-music-reactions](https://github.com/mting314/ll-music-reactions), served as static JSON over GitHub Pages' global CDN.

Each entity is its own file (fetched at runtime by the app), à la [sekai-viewer](https://github.com/Sekai-World/sekai-viewer):

| File | Contents |
|------|----------|
| `songs.json` | song catalog |
| `artists.json` | artists |
| `discographies.json` | albums/singles (incl. album art URLs) |
| `seriesInfo.json` | series metadata |
| `seriesNames.json` | series id → English name |
| `performances.json` | concerts/lives |
| `setlists.json` | performance setlists |
| `build.json` | `{ generatedAt, counts }` — provenance / "last updated" |

Served at `https://mting314.github.io/ll-music-data/<file>.json`.

**Refresh:** these files are committed by the daily **Cloud Run job** in the main
repo (`pipeline/`), which scrapes the catalog, builds the dataset, and pushes the
per-entity JSON here (via a GitHub token). There is no database and no data API —
this repo is the single source the frontend reads. See `pipeline/README.md` in the
main repo.
