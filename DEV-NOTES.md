# Dev notes (internal)

Not meant to be public-facing. Lives in the repo for context.

## Why we moved off Shopify

Shopify's monthly subscription, theme limitations, and 250-country dropdown made the storefront feel heavier than the workshop itself. Buyers were converting on Etsy anyway. So:

- **luma-isla.com** → portfolio site that tells the story and showcases the work.
- **lumaisla.etsy.com** → checkout. Already handling 80%+ of orders. Has reviews, mobile-optimized checkout, gift cards, and search built in.

Net effect: one less platform to maintain, one less monthly fee, faster page loads, full control of design.

## Stack decisions

- **No build step.** Static HTML/CSS/JS. Editable from any text editor, deployable from any static host. Zero dependencies means zero supply-chain surface area, zero `npm install` waits, zero breaking changes from a framework update.
- **Inter only.** The live Shopify site used Inter for everything (300–800 weights). Kept the same — buyers already recognize the type.
- **CSS variables for tokens.** All color, type scale, and spacing live in `:root` at the top of `assets/styles.css`. Want to repaint the site? Edit five values, you're done.
- **Fluid typography & spacing.** `clamp(min, preferred, max)` everywhere. No breakpoint jumps; everything scales smoothly from 320px to 4K.
- **Native `<details>` for FAQ.** No JS needed for the accordion. Works without JavaScript at all (progressive enhancement). One CSS rule rotates the `+` icon on `[open]`.
- **IntersectionObserver for scroll reveals.** ~30 lines of JS, no library. Honors `prefers-reduced-motion`.

## Palette (from live luma-isla.com computed styles, May 2026)

| Token | Hex | Where it came from |
|-------|-----|---------------------|
| `--bg` | `#fdf8f0` | `rgb(253, 248, 240)` — body background |
| `--ink` | `#2a1f0e` | `rgb(42, 31, 14)` — primary text |
| `--navy` | `#0e1a2b` | Hero & footer dark background |
| `--gold` | `#d4a23e` | Hero ornament accent |
| `--bronze` | `#8a5a2b` | Sampled from product photography |

## Site map

Single-level. No sub-pages, no `/blog/`, no `/products/`. Etsy owns the product listings — we link out.

```
/  (index.html)
├── /collections.html
├── /our-story.html
├── /process.html
├── /commissions.html
└── /faq.html
```

## To-do before going live

- [ ] Replace dark gradient placeholders with real photography (top 12 pieces minimum)
- [ ] Swap generic `https://lumaisla.etsy.com` links for individual listing URLs (15 of them in index.html, ~5 per collection block)
- [ ] Verify Etsy shop URL is exactly `lumaisla.etsy.com` (or update if different)
- [ ] Add favicon (drop `favicon.ico` and `favicon.svg` in root)
- [ ] Set up real newsletter (form currently just shows visual confirmation — no backend)
- [ ] Add Open Graph image — recommended path: `images/og-card.jpg` (1200×630), then reference in `<head>` of each page
- [ ] Submit sitemap to Google Search Console after deploy

## Newsletter integration options

The newsletter form currently captures the email visually but doesn't send it anywhere. To wire it up, pick one:

- **Mailchimp embed.** Replace the form `<form>` action with their endpoint. ~5 min.
- **Buttondown / ConvertKit.** Same — copy their embed.
- **Cloudflare Worker + Resend.** ~20 min, free under 3k emails/month, owns nothing on a third-party platform.
- **Formspree.** Drop-in `action="https://formspree.io/f/YOUR_ID"`. Free tier.

## Accessibility audit

- All interactive elements are reachable by keyboard.
- `<details>` is native — screen readers announce expanded/collapsed state correctly.
- Buttons and links have visible hover and focus states.
- `prefers-reduced-motion` disables scroll-reveal animations.
- Color contrast: ink-on-cream is 12.4:1, gold-on-navy is 7.8:1. Both pass AAA.
- One known gap: dark-on-dark gold accent (`--gold-2` on `--bg`) is 4.1:1 — passes AA for large text, borderline for body. Keep accents large.

## Performance

- No external JS libraries.
- One Google Fonts request (Inter, multiple weights). Preconnect tags included.
- Inline CSS variables, no @imports.
- Average page weight: ~30KB HTML + 20KB CSS + 1KB JS. Faster than any Shopify theme by an order of magnitude.

When real images go in, set `loading="lazy"` on every `<img>` below the fold.

---

## v2 — Modern editorial refresh (June 2026)

A visual modernization pass. **No content rewrites, same palette, same Etsy-first
model.** What changed:

- **Type system.** Added **Fraunces** (display serif, optical sizing) for all
  headings; **Inter** stays for body/UI. This is the single biggest "less
  template-y" change.
- **De-blocked the layout.** `--bg-2`/`--bg-3` nudged much closer to `--bg` so
  alternating sections read as one continuous canvas instead of hard bands. More
  whitespace, hairline separators, softer card shadows.
- **Editorial split hero** on the homepage (copy left, feature image right, stat
  badge) replacing the centered block.
- **Image-first everywhere.** Every card, hero, and stage now has a real `<img>`
  pointing at `images/`. Missing files fall back to the original gradient via
  `onerror="this.remove()"` — nothing ever shows a broken-image icon.
- **Featured collection card** spans full width (`.collection--feature`); process
  teaser is now a connected timeline (`.flow`) instead of four boxes.
- **All homepage section cards link to the Etsy storefront.**
- Added `favicon.svg` + `theme-color`, Open Graph tags on the homepage.

### Image workflow
See `images/IMAGES.md`. One rule: drop a correctly named file into `images/`,
commit, done — no HTML editing.

### To-do (updated)
- [x] Image slots wired site-wide with graceful gradient fallback
- [x] Favicon added (`favicon.svg`)
- [x] Open Graph tags on homepage
- [ ] Add the actual photos to `images/` (see `images/IMAGES.md` for filenames)
- [ ] Add `images/og-card.jpg` (1200×630) for social sharing
- [ ] Swap generic Etsy links for individual listing URLs when ready
- [ ] Wire up the newsletter form to a real backend
