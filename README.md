# Neha Joy — React Portfolio | GitHub Pages

This package supports **two simple ways** to host directly on GitHub Pages without a gh-pages branch or a custom Actions workflow.

## Easiest: use the prebuilt `docs/` folder

1. Create/open the GitHub repository `Neha-joy/PORTFOLIO`.
2. Put the **contents of this ZIP** at the repository root (not inside another nested folder).
3. Commit and push to the `main` branch.
4. In GitHub **Settings > Pages**, choose **Deploy from a branch** and `main` / `/docs`, then Save.
5. Visit https://neha-joy.github.io/PORTFOLIO/ after publishing completes.

The `docs/` folder runs the same React portfolio through browser-loaded React, Lucide, and Babel modules (internet connectivity is required to load these CDN libraries). This option is immediately publishable without installing Node.

## Recommended for future edits: build optimized Vite output

From the folder containing `package.json`:

```powershell
npm install
npm run build
if (Test-Path docs) { Remove-Item docs -Recurse -Force }
Copy-Item dist docs -Recurse
git add .
git commit -m "Update portfolio"
git push origin main
```

The normal Vite production build is optimized and does not need CDN Babel. The `vite.config.js` contains the matching `base: '/PORTFOLIO/'` value.

## EmailJS

The three **browser-side** EmailJS IDs seen in the supplied screenshot are preserved in `.env.production` (for Vite builds) and `docs/main.jsx` (for the immediately publishable site):

- Service ID: `service_eqtu7c`
- Template ID: `template_g66nlle`
- Public Key: `YCRPNjG4OXPKWH2kI`

The EmailJS template should use `{{from_name}}`, `{{reply_to}}`, `{{subject}}`, and `{{message}}`, and be directed to `nehajoy002@gmail.com`. Confirm each ID matches EmailJS dashboard in case the screenshot transcription differs. Browser-side IDs are visible to visitors and are not secrets. Use EmailJS domain restrictions and abuse protection. Sending requires the EmailJS service and template to be active.

## Folder layout

- `docs/` — **ready to publish** on GitHub Pages from `main` / `/docs`.
- `src/` — editable React app.
- `public/` — CV included with the Vite build.
- `vite.config.js` — GitHub Pages path setting.
- `.env.production` — browser-side EmailJS settings used when building.
- `package.json` — commands for Vite development / production build.

Do not upload a `.env.local` file with any private account credentials.
