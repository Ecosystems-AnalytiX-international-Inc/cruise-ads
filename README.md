# cruise-ads

Adverts shown at the top of **My Vehicle** in the CruisE app. The app reads `ads.json`
from this repository (public) and loads the images next to it.

## Add or change an advert

1. Put the image in `images/` — PNG, JPG, animated GIF or WebP.
   Size **1200 × 375 px** (ratio 3.2 : 1), under **500 KB** (GIF under 1 MB).
2. Add an entry to `ads.json` (copy the sample). Commit to `main`.
3. The app picks it up within about 5 minutes (pull down on My Vehicle to refresh).

| Field | Required | Meaning |
|---|---|---|
| `id` | yes | Unique name, e.g. `winter-tires-2026` |
| `image` | yes | Path in this repo (`images/x.gif`) or a full `https://` URL |
| `image_fr` | no | French version of the image |
| `link` | no | `https://` page opened inside the app when tapped |
| `alt`, `alt_fr` | no | Text read by screen readers |
| `aspect` | no | Width ÷ height, default `3.2` |
| `start`, `end` | no | `YYYY-MM-DD`, inclusive |
| `markets` | no | `["CA"]`, `["MU"]` |
| `provinces` | no | e.g. `["ON","QC"]` (province of the user's first vehicle) |
| `plans` | no | `["free"]`, `["free","premium"]`… (empty = everyone) |
| `weight` | no | Higher = shown more often when several adverts rotate |

`rotate_seconds` (top level, 3–120, default 8) sets the rotation speed.
To stop all adverts, set `"ads": []`.

Rules: only `https` links and images are accepted; keep the file valid JSON
(check it at jsonlint.com before committing). Adverts are labelled "Sponsored".
