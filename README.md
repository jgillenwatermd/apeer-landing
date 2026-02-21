# aPeer Landing Page

Static marketing site for [apeer.app](https://apeer.app). Pure HTML + CSS, no build step.

## Files

```
index.html      — Landing page
privacy.html    — Privacy policy
styles.css      — All styles (shared between pages)
favicon.svg     — Favicon (teal rounded square with "a")
```

## Local Preview

Open `index.html` directly in a browser, or use any local server:

```bash
# Python
python3 -m http.server 8000

# Node (npx, no install)
npx serve .
```

Then visit `http://localhost:8000`.

## Deployment

### Vercel

```bash
npm i -g vercel
cd apeer-landing
vercel
```

Set the custom domain to `apeer.app` in the Vercel dashboard under Settings > Domains.

### Netlify

1. Go to [app.netlify.com](https://app.netlify.com)
2. Drag and drop the `apeer-landing` folder
3. Set custom domain to `apeer.app` in Site settings > Domain management

### GitHub Pages

1. Push this repo to GitHub
2. Go to Settings > Pages
3. Set source to the main branch, root directory
4. Configure custom domain `apeer.app`

For all hosts: point your DNS for `apeer.app` to the host's servers (CNAME or A record as instructed by the provider).

## URLs for App Store Connect

- **Marketing URL**: `https://apeer.app`
- **Privacy Policy URL**: `https://apeer.app/privacy.html`

## TestFlight Link

Update the `#testflight` placeholder href in both `index.html` (two instances) once you have the public TestFlight link. Replace with:

```
https://testflight.apple.com/join/YOUR_CODE
```

## Open Graph Image

Create a `og-image.png` (1200x630) and place it in the root directory. The meta tags already reference `/og-image.png`.
