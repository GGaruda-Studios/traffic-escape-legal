# traffic-escape-legal

The Privacy Policy, Terms of Service and data-deletion page for **Traffic Escape**
(`oreo.traffic.escape.cars.puzzle`), an Android traffic puzzle game by Golden Garuda Studios.
Published as a static site with GitHub Pages.

Google Play requires a reachable Privacy Policy URL on the store listing, so this repo
is a **production dependency of the shipped app**, not documentation.

## Live URLs

    https://ggaruda-studios.github.io/traffic-escape-legal/
    https://ggaruda-studios.github.io/traffic-escape-legal/privacy
    https://ggaruda-studios.github.io/traffic-escape-legal/terms
    https://ggaruda-studios.github.io/traffic-escape-legal/delete-data

## Publishing

1. Push these files to the default branch of `GGaruda-Studios/traffic-escape-legal`.
2. **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`.**
3. Wait for the first build, then open all four URLs above in a browser.

A Privacy Policy URL that 404s is worse than a missing one: Play rejects the listing.

## Do not rename these paths

The Play listing points at `/privacy` (and the Data safety form at `/delete-data`), and the
game's **Open on the web** button links to the site root. Every released build carries that
URL, so renaming a folder, the repo or the org breaks the link in installed apps. If a path
has to change, leave a redirect at the old one.

## No webfonts, analytics or trackers

Deliberate. Every page is plain HTML plus one local stylesheet, so reading the policy
cannot be logged by anyone but GitHub. `.nojekyll` makes GitHub Pages serve the files
as written.

## The pages are generated from the game

`privacy/index.html` and `terms/index.html` are written by `tools/build_legal_site.py` in the
game repo from `scripts/ui/legal_catalog.gd`, the same text the game shows under
**Settings → Privacy & Terms**. To change a document:

1. Edit `legal_catalog.gd` in the game repo and bump `UPDATED`.
2. Run `python tools/build_legal_site.py` there, then commit and push this repo.
3. If `delete-data/` is affected, edit it by hand and bump its date.
4. If a change is material, say so in the game's Play release notes.

## What the app does today

The app sends **anonymous usage data (Firebase Analytics)** only: level, hint, setting,
look and rating-prompt events. In the EEA, UK and Switzerland (and where the device region
is unknown) collection is off until the player switches on **Settings → Privacy & Terms →
Share usage data**; elsewhere it is on, and anyone can switch it off. Advertising consent is
always denied. It also uses Google Play's in-app update and in-app review prompts.
No ads, purchases, accounts, crash reporting or Play Games.

**Set the Firebase project's data retention to 14 months** (Analytics → Data settings →
Data retention): the policy promises at most 14 months.

Adding ads, other SDKs or any new kind of data means updating the Privacy Policy before that
version is released, and changing the Play Data safety answers with it.
