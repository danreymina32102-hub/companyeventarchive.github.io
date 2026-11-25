# Company Event Archive

Secure photo and video archive for company events. A single-page website (`index.html`) with employee, moderator and administrator sign-in, albums, uploads, bulk download, a sign-in page designer and a Sign-in Activity log.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole website (HTML, CSS and JavaScript in one file) |
| `manifest.webmanifest`, `icon.svg` | Lets phones add the site to the home screen like an app |
| `404.html` | Friendly "page not found" screen |
| `robots.txt`, meta tags | Ask search engines not to index the site |
| `.nojekyll` | Tells GitHub Pages to serve files as they are |
| `.github/workflows/pages.yml` | Optional automatic deploy with GitHub Actions |

## Publish on GitHub Pages

1. Create a new repository on GitHub (for example `company-event-archive`).
2. Upload **all files from this folder** to the repository root, including `.nojekyll` and the `.github` folder. Using `git`:
   ```bash
   git init
   git add .
   git commit -m "Publish Company Event Archive"
   git branch -M main
   git remote add origin https://github.com/YOUR-USER/company-event-archive.git
   git push -u origin main
   ```
3. In the repository open **Settings > Pages > Build and deployment > Source** and choose **GitHub Actions** (uses the included workflow). Or choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and ignore the workflow.
4. After a minute the site is live at `https://YOUR-USER.github.io/company-event-archive/`.

## Important: how data is stored on GitHub Pages

GitHub Pages hosts static files only, so there is no shared server database.

- On GitHub Pages the site runs in **"This device only"** mode: accounts, albums, photos, videos and the sign-in log are saved in each browser's own storage (IndexedDB).
- Data is **not shared between phones and computers**, and clearing browser data removes it.
- The cross-device **Live sync** and the shared sign-in log work when the site is opened through its Claude (claude.ai) published link, where shared storage is available.
- For live sync on your own GitHub domain you need a hosted backend (for example Firebase, Supabase or your own API). The storage calls are all in `put`, `del` and `initSyncData` inside `index.html`.

## Before going live

- Sign in as administrator (menu, top right of the home page, **Admin Access**) with the default account `admin` / `Admin@12345` and **change the password immediately** (Manage Access > Administrator account).
- Sign-in checks run in the browser, so treat this as a convenience gate, not strong security. Never commit private photos or real passwords to a public repository.
- Make the repository **private** if you do not want the page source public (GitHub Pages on private repos needs a paid plan).

## Browser support

Current Chrome, Edge, Firefox and Safari on Windows, macOS, Android and iOS/iPadOS (iOS 14+ recommended).
