# SnapRecaller website

Static site for the App Store Connect URLs. Plain HTML/CSS: no build step, no JavaScript, no external fonts, scripts or trackers.

| Page | App Store Connect field |
| --- | --- |
| `index.html` | Marketing URL (optional) |
| `support.html` | Support URL |
| `privacy.html` | Privacy Policy URL |

## Placeholders

None left. The contact email is rohan@rohanspuri.com, and both "Download on the App Store" buttons in `index.html` link to https://apps.apple.com/app/id6811125288. That page shows as unavailable until the app is released.

The screenshots in `assets/` are real app captures (list, one-line filing, notification).

The App Store button is a plain text pill on purpose. If you want the official "Download on the App Store" badge, download the artwork from Apple's marketing resources site (https://developer.apple.com/app-store/marketing/guidelines/) and follow its usage rules. Don't draw your own version or add an Apple logo.

## Publish on GitHub Pages

1. Create a new **public** repository on GitHub, for example `snaprecaller`.
2. Push the **contents** of this folder (not the folder itself) to the repo's `main` branch, so that `index.html` is at the root. The app project is its own git repo, so copy the site somewhere outside it first rather than running `git init` in place:
   ```sh
   cp -R AppStore/website/ ~/snaprecaller-site   # copies .nojekyll too
   cd ~/snaprecaller-site
   git init -b main
   git add .
   git commit -m "SnapRecaller website"
   git remote add origin https://github.com/USERNAME/REPO.git
   git push -u origin main
   ```
3. On GitHub, open the repo's **Settings → Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, choose `main` and `/ (root)`, and save.
4. After a minute or so the site is live at:
   - `https://USERNAME.github.io/REPO/` (Marketing URL)
   - `https://USERNAME.github.io/REPO/support.html` (Support URL)
   - `https://USERNAME.github.io/REPO/privacy.html` (Privacy Policy URL)

Open all three in a browser before pasting them into App Store Connect.

`.nojekyll` tells GitHub Pages to serve the files as they are, without running Jekyll. Keep it.

## Notes

- Links and assets are all relative, so the site works under `/REPO/` or at a custom domain.
- The Open Graph image (`assets/og.png`, 1200 × 630) is also referenced relatively. Some link-preview services only accept absolute URLs, so once the address is final you can change `content="assets/og.png"` to the full URL in each page's `<meta property="og:image">`.
- If the privacy policy changes, edit `privacy.html` and update its "Last updated" date. It mirrors `PRIVACY.md` at the repo root.
