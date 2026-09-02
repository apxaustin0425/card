# card.allphasellc.org

Digital business card for Andres Acuna — All Phase LLC / East Reading Boxing Club.
This is the URL that gets written to the NFC tags. **It never changes.**

## Deploy (one time, ~10 minutes)

1. Create a public GitHub repo (any name, e.g. `card`).
2. Upload every file in this folder to the repo root:
   `index.html`, `andres.vcf`, `preview.jpg`, `icon-180.png`, `icon-512.png`, `CNAME`, `README.md`
3. Repo → **Settings → Pages** → Source: *Deploy from a branch* → `main` / `/ (root)` → Save.
4. In **GoDaddy → allphasellc.org → DNS**, add:

   | Type  | Name | Value                    | TTL   |
   |-------|------|--------------------------|-------|
   | CNAME | card | `apxaustin0425.github.io.` | 1 hr |

   (Keep the trailing dot.)
5. Back in Settings → Pages, wait for the green check, then tick **Enforce HTTPS**.

Live at `https://card.allphasellc.org/` — usually within an hour.

## Write the NFC tags

NFC Tools (Android or iOS) → **Write** → *Add a record* → **URL/URI** →
paste `https://card.allphasellc.org/` → Write → hold tag to phone.

- Always `https://`, never `http://` — plain http triggers browser warnings.
- **Do not lock the tags.** Locking is permanent. Use password protection if you
  want tamper resistance.
- ~27 bytes on the tag. Even the cheapest NTAG213 (144 bytes) is 80% empty.

## Why a subdomain you own

The old card lived at a Manus CDN URL. When Manus went away, every tag pointing
at it died. `card.allphasellc.org` belongs to you: if this host ever fails, you
change one DNS record and every tag already in the wild keeps working.

## Updating the card

Edit `index.html` in GitHub's web editor and commit. Live in about a minute.
The URL does not change, so the tags never need rewriting.

## Files

| File | Purpose |
|---|---|
| `index.html` | The card. Club crest is embedded in the file — no image request on load. |
| `andres.vcf` | Powers the "Save my contact" button. |
| `preview.jpg` | 1200×630 link preview for texts and DMs. |
| `icon-180.png` / `icon-512.png` | Add-to-Home-Screen icon. |
| `CNAME` | Tells GitHub Pages the custom domain. |

## Deploy target

GitHub account: **apxaustin0425** — no existing repo is reusable (the two
Canal Creative repos are full-stack apps with a server layer; Pages serves
static files only). Make a fresh repo named `card`.

CNAME record value: `apxaustin0425.github.io.`

## TODO

- [ ] Re-add website tiles once allphasellc.org and eastreadingboxingclub.com serve a page
- [ ] Add a YouTube tile if a channel gets created
- [ ] Confirm All Phase LLC tagline and description
- [ ] Gym hours, if you want them on the card (the site project never got them)
