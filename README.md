# MR MOHA TECH Portfolio

Static portfolio site. View at `portfolio-mr-moha-tech.html` or root `/` (via index.html redirect).

## Vercel NOT_FOUND (404) Error Resolution

**Encountered**: Deploy to Vercel returned 404 on root URL.

**Root Cause**:
- Static sites require `index.html` at root.
- Main file `portfolio-mr-moha-tech.html` present but not default entrypoint.

**Fix Applied**:
```
index.html → meta redirect to portfolio-mr-moha-tech.html
```

**Why?** Vercel serves `/index.html` by default. Missing → 404.

**Alternatives**:
- Rename main file to `index.html`
- `vercel.json`: `{ "rewrites": [{ "source": "/", "destination": "/portfolio-mr-moha-tech.html" }] }`

**Warning Signs**:
- No `index.html` in root
- Custom HTML filenames
- No deployment config

**Test**: Open `index.html` locally → auto-redirects.

## Deployment
```
vercel --prod
```
Site live at root URL.

© 2025 MR MOHA TECH

## Full Deployment Guide (Vercel / Netlify)

### 1. Push to GitHub
```
git init
git add .
git commit -m "Initial portfolio deploy-ready"
gh repo create portfolio-mr-moha-tech --public --push --source=. --remote=origin
```
(Install GitHub CLI if needed: `winget install --id GitHub.cli`)

### 2. Vercel
- Go to [vercel.com](https://vercel.com) → New Project → Import GitHub repo
- **Root: `./`**, **Build: No build command**, **Output: `public` not needed**
- Deploy! Uses vercel.json for SPA routing.

**CLI**: `npm i -g vercel && vercel --prod`

### 3. Netlify
- [netlify.com](https://netlify.com) → New site from Git → GitHub repo
- **Branch: main**, **Build: No**, **Publish dir: `./`**
- Deploy! Uses netlify.toml.

**CLI**: `npm i -g netlify-cli && netlify deploy --prod --dir=.`

### Notes
- **Images**: Compress if >1MB: Install ImageMagick, then `magick mogrify -quality 85 images/*.jpeg`
- **Custom domain**: Add via dashboard.
- **Root URL**: Loads index.html → redirects to portfolio.
- All client-side routes handled by configs.

# mohatech
