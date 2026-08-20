# Downtown + Area Supply Map

Interactive multifamily supply pipeline map, expanded beyond the original
downtown Churchill Apartments catchment to include the area west of 109th
Street. Same map design/behavior as the original Supply-Map-St.-Albert-
repo's Downtown Edmonton map, just a wider set of tracked projects.

## Files

- `supply_map_colab.py` — Colab-editable source. Edit `PROJECTS` (and the
  `_st`/`_ac`/`_uc`/`_pr` header stats near the bottom) here, run it in
  Colab, and it downloads a standalone HTML file for manual use.
- `build_site.py` — same generator, kept in sync with `supply_map_colab.py`,
  but writes to `public/index.html` for the Firebase Hosting deploy step
  instead of a Colab download. **This is the file the live site is actually
  built from** — if you edit project data, update both files (or copy
  `supply_map_colab.py`'s `PROJECTS`/stats over into `build_site.py`).
- `public/` — generated at build time by `build_site.py`. Not committed
  (gitignored); GitHub Actions regenerates it on every push.

## One-time Firebase setup (still needed)

1. Create a new Firebase project in the [Firebase console](https://console.firebase.google.com)
   with Hosting enabled.
2. Project Settings → Service Accounts → generate a new private key (downloads
   a JSON file).
3. In this repo: Settings → Secrets and variables → Actions → New repository
   secret, named `FIREBASE_SERVICE_ACCOUNT`, value = the full JSON file
   contents.
4. Replace `REPLACE_WITH_YOUR_FIREBASE_PROJECT_ID` in both `.firebaserc` and
   `.github/workflows/firebase-deploy.yml` with your actual Firebase project
   ID.
5. Push to `main` — the workflow builds and deploys automatically.

## Updating project data

Edit the `PROJECTS` list and the `_st`/`_ac`/`_uc`/`_pr` stat variables in
**both** `supply_map_colab.py` and `build_site.py`, then push to `main`.
