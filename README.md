# Luma-Isla Studios — luma-isla.com

The portfolio site for [Luma-Isla Studios](https://lumaisla.etsy.com), a veteran-owned, family-run sculpture workshop in Edmond, Oklahoma. Static HTML/CSS/JS — no build step, no framework, no dependencies. Purchases happen on the Etsy storefront; this site exists to showcase the work and tell the story.

## What's in here

```
luma-isla-site/
├── index.html         · Home
├── collections.html   · The five collections + section deep-dives
├── our-story.html     · Founder's letter and the workshop's history
├── process.html       · Print → sand & prime → finish → inspect & ship
├── commissions.html   · Custom orders, bulk, wholesale, press
├── faq.html           · 15 topics, native <details> accordion
├── assets/
│   ├── styles.css     · Shared design system (tokens, components)
│   └── site.js        · Mobile nav, scroll-reveal, newsletter UX
├── images/            · Product photos (drop in here when ready)
├── README.md          · This file
├── DEV-NOTES.md       · Internal notes (Shopify migration, decisions)
└── .gitignore
```

Every page links to the same `assets/styles.css` and `assets/site.js`, so a tweak to the design system updates everything at once.

## Run it locally

You don't need a build. Just open `index.html` in a browser, or serve the folder:

```bash
# Python 3
python3 -m http.server 8000

# or Node
npx serve .
```

Then visit `http://localhost:8000`.

## Deploy

### Option A — GitHub Pages (free, simplest)

1. Push this folder to a GitHub repo.
2. In the repo go to **Settings → Pages**.
3. Source: **Deploy from a branch**. Branch: `main`, folder: `/ (root)`.
4. Save. Your site will be at `https://<your-username>.github.io/<repo-name>/`.
5. To use the `luma-isla.com` domain: add a `CNAME` file (one line, just `luma-isla.com`) and point your DNS A records at GitHub Pages IPs ([instructions](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)).

### Option B — Cloudflare Pages (recommended for production)

1. Push to GitHub.
2. Sign in to Cloudflare → **Pages** → **Connect to Git**.
3. Pick the repo. Build command: *(none)*. Output directory: `/`.
4. Deploy. Site goes live in ~30 seconds.
5. Bind `luma-isla.com` in **Custom domains** — Cloudflare handles DNS automatically if the domain is on Cloudflare already.

### Option C — Netlify

Drag the folder into [app.netlify.com/drop](https://app.netlify.com/drop). Done. Add the custom domain in site settings.

## Migrating from Shopify

Heads up: `luma-isla.com` currently points at Shopify. Don't repoint DNS until the new site is deployed and tested.

Suggested cutover:

1. Deploy the new site to GitHub Pages / Cloudflare Pages / Netlify on a temporary preview URL.
2. Walk every page on desktop, tablet, mobile. Open the FAQ, test each accordion. Click every Etsy link.
3. Export your customer list and any analytics from Shopify (Settings → Customers → Export). Keep the CSV — you'll want it for the newsletter.
4. Change one DNS record at your domain registrar to point luma-isla.com at the new host. Propagation takes about an hour.
5. Cancel the Shopify subscription whenever you're ready. Your domain stays yours.

The FAQ on this site has a "Why Our Site Changed" topic that explains the move to returning customers.

## Editing content

Each page has its content inline. To change copy, open the page (`our-story.html`, `faq.html`, etc.) and edit the text directly. The design system is in `assets/styles.css` — color, type, spacing all controlled by CSS variables at the top.

### Adding a product photo

1. Drop the photo into `images/` (recommended: 1200px on the long edge, `.webp` or `.jpg`).
2. Find the placeholder block on the page — they look like:
   ```html
   <div class="piece-image"><div class="ph">Mater Dolorosa<br>Virgin Mary</div></div>
   ```
3. Replace with an `<img>`:
   ```html
   <div class="piece-image"><img src="images/mater-dolorosa.jpg" alt="Mater Dolorosa Virgin Mary statue"></div>
   ```

The image will fill the rounded card automatically.

### Linking each piece to its specific Etsy listing

Right now every piece card and collection tile points at `https://lumaisla.etsy.com` (the shop homepage). Once you have individual listing URLs, swap them in. They look like `https://www.etsy.com/listing/123456789/...`.

## Browser support

Modern evergreen browsers (Chrome, Firefox, Safari, Edge — last two major versions). Uses CSS `clamp()`, `aspect-ratio`, `backdrop-filter`, and native `<details>`. All have universal support as of 2026.

## License

All content (copy, photography, designs, brand) © Luma-Isla Studios. Code structure is yours to modify and deploy. Don't redistribute the site as a template.

## Contact

- Workshop email: <info@luma-isla.com>
- Etsy storefront: <https://lumaisla.etsy.com>
- Lucien's Tiny Treasures: <https://lucienstinytreasures.etsy.com>
