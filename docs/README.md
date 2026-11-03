# KwiklyDoc website (GitHub Pages)

| File | Use |
|---|---|
| `index.html` | Marketing page. Use it as the App Store **Marketing URL**. |
| `privacy.html` | Privacy policy. Use it as the **Privacy Policy URL** (required). |
| `support.html` | Support and FAQ. Use it as the **Support URL** (required). |
| `404.html` | Page GitHub shows for unknown addresses. |
| `assets/` | Stylesheet and icons. |

## Before publishing: replace three placeholders
Search all files in `docs/` and replace:

| Placeholder | Replace with | Where |
|---|---|---|
| `SUPPORT_EMAIL` | Your support address, e.g. `help@yourdomain.com` | Every page (footer, privacy contact, support) |
| `APP_STORE_URL` | Your App Store link, e.g. `https://apps.apple.com/app/id1234567890`. Until launch, use `support.html` | `index.html` (two buttons) |
| `APP_STORE_ID` | The numeric ID, then uncomment the `apple-itunes-app` meta tag | Optional, every page head |

Also set the same email in `KwiklyDoc/AppInfo.swift` → `AppLinks.supportEmail`, and the page URLs in `AppLinks.privacyPolicy` and `AppLinks.support`.

For the official "Download on the App Store" badge, download it from Apple's marketing resources (developer.apple.com/app-store/marketing/guidelines) and use it in place of the button. Don't redraw it.

## Publish on GitHub Pages
1. Push this project to a GitHub repository. The site can live in a public repository even if the app code is private; put just `docs/` in a separate public repo if you prefer.
2. Repository → Settings → Pages → Build and deployment → Source: **Deploy from a branch** → Branch: `main`, folder **`/docs`** → Save.
3. After a minute the site is at `https://<username>.github.io/<repository>/`:
   - Privacy Policy URL: `https://<username>.github.io/<repository>/privacy.html`
   - Support URL: `https://<username>.github.io/<repository>/support.html`
   - Marketing URL: `https://<username>.github.io/<repository>/`
4. Open each page on your phone and check the links before pasting them into App Store Connect.

`.nojekyll` makes GitHub serve the files as they are.

## Keeping the privacy policy in sync
The in-app policy (`KwiklyDoc/AppInfo.swift`) is the source. After changing it, regenerate the pages from the project root:

```
python3 Tools/Website/build_site.py .
```

This rewrites `index.html`, `privacy.html`, `support.html` and `404.html`, so replace the placeholders again afterwards (or edit the template in the script once).
