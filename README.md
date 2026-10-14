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

## due.json — "what is due" banner (13 Oct 2026)
Built hourly by `scripts/hs_due_build.py` (refresh-jobs-dashboard Step 0g) from the diary map + calendar + completions + the
checks register + the equipment register. `index.html` shows a NEEDS DOING NOW box (overdue = red pill, due today = amber,
first one = grey, done = green) plus external exams (Zurich), and when exactly ONE check is due it pre-selects the form's
"Check type" (forms.json `check_type_q` + `cadence_options`, family 01 only so far - add the others' question ids to extend).
With a banner the page no longer auto-forwards; the lad taps the big button. Asset ids + dates only - no names (public repo).
publish.py pushes due.json only when hs_due_build.py reports it written (a date or state moved), so pushes are a few a day.

## Check lists on the phone page (14 Oct 2026)
`assets.json` now carries `weekly`, `weekly_when`, `monthly`, `monthly_when` and `other` (`[label, when, items]`) per asset — the same
DAILY / WEEKLY / MONTHLY lists as the printed sign (issue 02, layout C), built by `signs/make_signs.py` from `assets.csv`.
`index.html` shows them as collapsible blocks under the daily list. No names in these lists.

