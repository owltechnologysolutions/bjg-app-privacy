# bjg-app-privacy

Public privacy policy site for the **Golf Ranch App**, published by **Blue Jeans Golf** (BJG). Owl Technology Solutions (OTS) maintains this repo on BJG's behalf. BJG is the data controller; OTS is the vendor.

This repo serves a single static page (`index.html`). The canonical, production privacy-policy URL is set by BJG — most likely **`https://bluejeansgolf.com/privacy`**. Confirm with BJG before pasting any URL into the Google Play Console or Apple App Store Connect Privacy form.

The GitHub Pages URL produced by this repo (`https://owltechnologysolutions.github.io/bjg-app-privacy/`) is a **staging / preview** for OTS-side testing and lawyer review only. It should **not** be the URL submitted to the stores in production.

## Source of truth

The drafting source-of-truth was `bjg-app-claude/docs/privacy-policy.md`; that file has been replaced with a pointer to this repo. Future edits should land **here**, in `index.html`, and the markdown should **not** diverge.

## Contents

| File         | Purpose                                                                                  |
| ------------ | ---------------------------------------------------------------------------------------- |
| `index.html` | The privacy policy itself. Self-contained HTML5 with inline CSS, no JS, no dependencies. |
| `README.md`  | This file.                                                                               |
| `.gitignore` | Ignore OS junk and editor swap files.                                                    |

## Disclaimer

This draft was prepared by OTS engineers describing the app's actual data flows in plain language, then translated into HTML on 2026-05-09. It has **not** been reviewed by a lawyer, and OTS is not a law firm. Before publishing publicly or pointing the Google Play / App Store Connect privacy URL at it, BJG's qualified legal counsel must review and revise it. Until that review is done, the page itself shows a yellow "DRAFT — pending BJG legal review" banner at the top; remove that banner (search for the `TODO` comment near the top of `index.html`) only once BJG's counsel approves. Items flagged `[BJG TO FILL IN]` in the page text need either a factual answer from BJG or a legal-entity-name decision before publication.

## Publishing to GitHub Pages (staging / preview only)

GitHub Pages on a repo named `bjg-app-privacy` is the simplest way to give BJG's counsel a stable URL to review the live-rendered page during drafting. **It is staging, not production.** The production URL is set by BJG (likely `https://bluejeansgolf.com/privacy`).

1. **Create the GitHub repo.** Sign in as the `owltechnologysolutions` org and create a new, empty repository named `bjg-app-privacy`. Do not let GitHub initialize it with a README, license, or `.gitignore` (we already have those).
2. **Push this folder up.** From inside `bjg-app-privacy/`:

   ```bash
   git remote add origin git@github.com:owltechnologysolutions/bjg-app-privacy.git
   git branch -M main
   git push -u origin main
   ```

   (Use HTTPS instead of SSH if you prefer: `https://github.com/owltechnologysolutions/bjg-app-privacy.git`.)
3. **Enable Pages.** In the GitHub repo, go to **Settings -> Pages**. Under **Build and deployment**, set **Source** to **Deploy from a branch**, then choose **Branch: `main`** and **Folder: `/ (root)`**. Save.
4. **Wait ~1 minute.** GitHub will build the site and surface its URL on the same Pages settings screen. The default URL is:

   ```
   https://owltechnologysolutions.github.io/bjg-app-privacy/
   ```

   This URL is for **OTS-side review and BJG counsel review** only. **Do not paste it** into the Google Play Console **Privacy policy** field or the Apple App Store Connect **Privacy Policy URL** field for the live submission. The store-listing URL must be the production URL BJG configures (likely under `bluejeansgolf.com`). Confirm with BJG before either store submission.

If BJG would rather host the production page somewhere other than `bluejeansgolf.com` (Cloudflare Pages, Netlify, a different subdomain), the file is fully static; just upload `index.html` and serve it as the index. The same staging-vs-production distinction still applies.

## Updating the policy

`index.html` in this repo is the source of truth. Do **not** edit any other copy of the policy — the markdown that previously lived at `bjg-app-claude/docs/privacy-policy.md` is now a pointer to this repo and should not diverge.

1. Edit `index.html`.
2. Bump the **Last updated** date in the meta line near the top.
3. Commit and push to `main`. GitHub Pages rebuilds the staging URL automatically (typically under a minute). Production hosting (BJG's domain) is updated separately by BJG.
4. If the change is material (a new data type, a new third party, a new region), notify users in-app or by email per the "Changes to this policy" section, and coordinate with BJG so the production URL goes out in step.

## Important: keep this in sync with your store listings

Any time the Golf Ranch App's actual data practices change, **all three** of the following have to be updated together:

1. This `index.html` policy (and, once BJG hosts production, the copy served at BJG's domain).
2. The Google Play Console **Data Safety** form.
3. The Apple App Store Connect **App Privacy** form.

Examples of changes that require updating all three:

- A new third-party processor (e.g. enabling HubSpot sync once BJG closes the D-2 decision).
- Adding push notifications (a new device identifier and a new permission).
- Adding any third-party analytics or attribution SDK.
- Adding location, camera, or any other device permission.

If the policy and the Data Safety form disagree, Google can reject the app or pull it from the store. The OTS-internal notes for filling out these forms live in the meta repo at `bjg-app-claude/docs/app-store-privacy-form-notes.md`.

## Local preview

`index.html` is fully self-contained, so you can preview it by just opening the file in a browser:

- macOS: `open index.html`
- Windows: `start index.html`
- Linux: `xdg-open index.html`

No build step, no `npm install`, no server required.
