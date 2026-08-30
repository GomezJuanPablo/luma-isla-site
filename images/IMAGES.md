# Adding photos — the simple version

Every spot on the site that should hold a photo already points at a file in
this `images/` folder. **To add a photo, you only do one thing: put a correctly
named image in here.** No HTML editing.

If a file isn't here yet, that spot shows a tasteful bronze gradient instead of
a broken image — so you can add photos one at a time, in any order, and the site
always looks finished.

---

## How to add an image on GitHub (60 seconds)

1. Open this `images/` folder in your repo on GitHub.
2. Click **Add file → Upload files**.
3. Drag in your photo. **Rename it to match the exact filename below** (all
   lowercase, hyphens, `.jpg`).
4. Click **Commit changes**.
5. Refresh the site — the photo appears in its spot automatically.

To swap a photo later, upload a new file with the **same name**; it overwrites
the old one.

> Tip: keep filenames exactly as written. `Collection-Sacred.JPG` will NOT match
> `collection-sacred.jpg`.

---

## The filenames (copy these exactly)

### Homepage — `index.html`
| Filename | Where it shows | Best size (px) | Shape |
|---|---|---|---|
| `hero.jpg` | Big image next to the headline | 1200 × 1500 | tall (4:5) |
| `collection-sacred.jpg` | Featured wide collection card + Sacred section | 1600 × 1200 | landscape |
| `collection-wildlife.jpg` | Wildlife collection card | 1200 × 1440 | tall (5:6) |
| `collection-pet.jpg` | Pet Memorials collection card | 1200 × 1440 | tall (5:6) |
| `collection-fandom.jpg` | Cosplay collection card | 1200 × 1440 | tall (5:6) |
| `piece-mater-dolorosa.jpg` | Featured piece | 1000 × 1120 | near-square |
| `piece-st-joseph.jpg` | Featured piece | 1000 × 1120 | near-square |
| `piece-st-benedict.jpg` | Featured piece | 1000 × 1120 | near-square |
| `piece-lion-bust.jpg` | Featured piece | 1000 × 1120 | near-square |
| `piece-giraffe-bust.jpg` | Featured piece | 1000 × 1120 | near-square |
| `piece-doberman-memorial.jpg` | Featured piece | 1000 × 1120 | near-square |
| `piece-black-panther-set.jpg` | Featured piece | 1000 × 1120 | near-square |
| `piece-venom-bust.jpg` | Featured piece | 1000 × 1120 | near-square |

### Collections page — `collections.html`
Reuses the four `collection-*.jpg` files above. No page-specific files needed.

### Process page — `process.html` and Commissions page — `commissions.html`
These pages use a designed numeral / finish-swatch treatment instead of photos —
no image files needed. If you'd rather use real photos here later, just ask and
we'll wire the slots back in.

### Social share (optional, nice to have)
| Filename | Where it shows | Best size (px) | Shape |
|---|---|---|---|
| `og-card.jpg` | Preview image when the site is shared on text/social | 1200 × 630 | wide |

---

## A few quick photo tips

- **`.jpg` for photos** keeps files small and fast. Aim for under ~400 KB each.
- Shoot or crop close to the shape listed above. The site crops to fit, but
  matching the shape avoids awkward cropping (e.g. don't use a wide landscape
  shot for a tall card).
- Good light + a clean, simple background makes the bronze finishes pop.
- You don't need every file at once. Add your best 5–10 first; the rest stay on
  the gradient until you're ready.
