# bjg-app-privacy

Public privacy policy site for the **BJG App** (a golf-related mobile app for iOS and Android, developed by Owl Technology Solutions).

This repo serves a single static page (`index.html`) over GitHub Pages. The URL we link to from the Google Play Console / Apple App Store Connect Privacy form points here.

## Contents

| File         | Purpose                                                                                  |
| ------------ | ---------------------------------------------------------------------------------------- |
| `index.html` | The privacy policy itself. Self-contained HTML5 with inline CSS, no JS, no dependencies. |
| `README.md`  | This file.                                                                               |
| `.gitignore` | Ignore OS junk and editor swap files.                                                    |

## Disclaimer

This is a **first draft generated programmatically by Claude on 2026-05-09**. It has not been reviewed by a lawyer. Before publishing the policy publicly or pointing the Google Play / App Store Connect privacy URL at it, have qualified legal counsel review and revise it. Until that review is done, the page itself shows a yellow "DRAFT - pending legal review" banner at the top; remove that banner (search for the `TODO` comment near the top of `index.html`) only once review is complete.

## Publishing to GitHub Pages

The easiest way to host this for free at a stable URL is GitHub Pages on a repo named `bjg-app-privacy`.

1. **Create the GitHub repo.** Sign in as the `owltechnologysolutions` org (or whichever account will own the public privacy site) and create a new, empty repository named `bjg-app-privacy`. Do not let GitHub initialize it with a README, license, or `.gitignore` (we already have those).
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

   That URL is what you paste into the Google Play Console **Privacy policy** field and the Apple App Store Connect **Privacy Policy URL** field.

If you'd rather host this somewhere else (Cloudflare Pages, Netlify, your own domain), the file is fully static; just upload `index.html` and serve it as the index.

## Updating the policy

1. Edit `index.html`.
2. Bump the **Last updated** date in the meta line near the top.
3. Commit and push to `main`. GitHub Pages rebuilds automatically (typically under a minute).
4. If the change is material (a new data type, a new third party, a new region), notify users in-app or by email per the "Changes to this policy" section.

## Important: keep this in sync with your store listings

Any time the App's actual data practices change, **all three** of the following have to be updated together:

1. This `index.html` policy.
2. The Google Play Console **Data Safety** form.
3. The Apple App Store Connect **App Privacy** form.

Examples of changes that require updating all three:

- Wiring Stripe in for real (financial info starts being processed).
- Adding push notifications (a new device identifier and a new permission).
- Adding any third-party analytics or attribution SDK.
- Adding location, camera, or any other device permission.

If the policy and the Data Safety form disagree, Google can reject the app or pull it from the store.

## Local preview

`index.html` is fully self-contained, so you can preview it by just opening the file in a browser:

- macOS: `open index.html`
- Windows: `start index.html`
- Linux: `xdg-open index.html`

No build step, no `npm install`, no server required.
