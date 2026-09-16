# Finch's equipment-check QR redirect

Every laminated QR sign in the factory points here: `https://finchgranite.github.io/checks/?id=<ASSET>`.
The page looks the asset up in `assets.json`, shows the pre-use list, and opens the right Microsoft Form
pre-filled with the asset (from `forms.json`). If a form family has no link yet it says
"Form not live yet - use the paper sheet". Changing a form later means editing `forms.json` — nothing to reprint.

- `assets.json` — generated from `../assets.csv` by `../signs/make_signs.py` (do not hand-edit)
- `forms.json` — one pre-filled-link template per form family, filled in at the Phase 2 build session
- `index.html` — the page (no external scripts, no tracking, `noindex`)
- `publish.py` — pushes this folder to the public repo `Finchgranite/checks` (GitHub Pages)

No records are stored here. Records live in the Finch Health & Safety SharePoint site.
