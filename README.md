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

**Refresh:** [`refresh.yml`](.github/workflows/refresh.yml) runs daily (04:00 UTC), pulls the latest dataset from the Cloud Run data API, splits it into the files above, and commits — using the built-in `GITHUB_TOKEN` (no secrets). The data originates from the scrapers → Firestore pipeline in the main repo; this repo is the CDN read path.
