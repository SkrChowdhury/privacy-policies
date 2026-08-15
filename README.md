# Privacy Policies

Public privacy policies for apps published by [SkrChowdhury](https://github.com/skrchowdhury),
served by GitHub Pages so each app has a stable, public URL for its Play Store
listing.

**This repository must stay public.** Google Play stores the privacy policy URL
on the listing and re-checks it over time — an app whose policy URL starts
returning 404 can be *removed*, not merely rejected. Keeping the policies here,
separate from each app's source, means the app repositories can be private
without taking the policies offline.

## Live URLs

| App | Package | Policy URL |
|---|---|---|
| BDT Rate Today | `com.skrchowdhury.bdtratestoday` | `/bdt-rate-today/` |
| GPA Calculator BD | `com.skrchowdhury.cgcalculatorbd` | `/gpa-calculator-bd/` |
| শব্দ খেলা (Shobdo Khela) | `com.skrchowdhury.shobdokhela` | `/shobdo-khela/` |

Base: `https://skrchowdhury.github.io/privacy/`

## Setup

Settings → Pages → Deploy from a branch → `main`, folder `/ (root)`.

`.nojekyll` is present so Pages serves the files as-is rather than running them
through Jekyll.

## Adding an app

1. `mkdir <app-slug>` and copy the closest existing `index.html` into it
2. Drop a 512×512 icon at `assets/<app-slug>.png`
3. Update the header, title, package name and the body
4. Add a row to `index.html`
5. Commit and push — Pages redeploys within a minute

## Writing an accurate policy

The three policies here differ because the apps differ, and the differences are
the parts a reviewer actually checks. Verify each of these against the source
rather than copying a template:

- **Permissions** — read `android/app/src/main/AndroidManifest.xml`. An app with
  no `INTERNET` permission genuinely cannot transmit anything, and saying so is
  much stronger than a vague "we respect your privacy".
- **Local storage** — MMKV, AsyncStorage, SQLite and files all count as data
  kept on the device. List what is stored, and say it never leaves.
- **`android:allowBackup`** — if it is `true` (the Android default), the OS may
  copy app data to the user's Google Drive. That is disclosable, and it is the
  single most commonly missed item. `BDT Rate Today` sets it to `false`; the
  other two leave it on.
- **Export and share** — a document picker or share sheet sends a file wherever
  the *user* chooses. Say that it is user-initiated and that nothing uploads on
  its own.
- **Network calls** — list every host the app contacts and what each is for.
- **Ad and analytics SDKs** — check `package.json` dependencies, not source
  greps. Searching for "tracking" hits typographic letter-spacing tokens.

## Contact

emailofs2o@gmail.com
