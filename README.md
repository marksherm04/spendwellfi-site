# SpendWellFi marketing site

Static site — no build step, no dependencies. Four pages:

- `index.html` — landing page (features, privacy promise, pricing, FAQ)
- `download.html` — post-purchase download page (Stripe redirects here)
- `privacy.html` / `terms.html` — legal pages

## Launch checklist (three replacements)

### 1. Create the Stripe Payment Link
1. Stripe Dashboard → **Payment Links** → **+ New**.
2. Add a product: "SpendWellFi" · one-time · **$69.00** (or your price).
3. Under **After payment** → "Don't show confirmation page" →
   redirect to `https://spendwellfi.com/download.html`.
4. Recommended toggles: collect email (default), allow promotion codes
   (for launch discounts), enable Link for one-click checkout.
5. Copy the payment link URL and replace
   `REPLACE_WITH_STRIPE_PAYMENT_LINK` in `index.html`.

No backend is required — Stripe hosts the entire checkout. Stripe's
receipt email gives buyers a record; the redirect lands them on the
download page.

### 2. Host the installers
Upload the installers somewhere durable and paste the URLs into
`download.html` (`REPLACE_WITH_WINDOWS_INSTALLER_URL`, `REPLACE_WITH_MACOS_DMG_URL`):

- Easiest: drop them in this site's folder (e.g. `/dl/SpendWellFi-setup.exe`)
  and use relative links — any static host serves them fine.
- Or use Cloudflare R2 / S3 if you want download stats.

Installers come from the app repo: `src-tauri/target/release/bundle/`
(NSIS `.exe` for Windows; build the `.dmg` on a Mac with `npm run tauri build`).

### 3. Update prices/copy
Search `index.html` for `$69` if you choose a different price, and make
sure the price in Stripe matches the page.

## Deploying

Any static host works. Two no-cost options:

**Cloudflare Pages** (recommended — also where `spendwellfi.com` DNS can live):
1. Push this folder to a GitHub repo.
2. Cloudflare Dashboard → Pages → connect the repo → framework "None" → deploy.
3. Add the custom domain `spendwellfi.com`.

**Netlify:** drag this folder onto app.netlify.com → set custom domain.

## Honest-marketing notes

- The FAQ answer about supported banks should be kept current with the
  parser's real coverage.
- The SmartScreen FAQ answer assumes code signing is live (Azure Artifact
  Signing). If you launch before signing is active, soften that answer.
- The 14-day refund promise appears on the pricing card, FAQ, terms, and
  download page — if you change the window, change all four.
