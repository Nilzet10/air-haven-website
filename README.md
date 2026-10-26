# Air Haven website

A one-page site for Air Haven (air duct cleaning and HVAC restoration in Central Florida). It's rebuilt from her Squarespace draft and keeps the same sections, copy and navy/blue look.

To preview it, open `index.html` in any browser.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole site: hero with the van photo, facts bar, services grid, signs it's time, about + review, FAQ, contact |
| `styles.css` | All styling (brand colors and fonts are at the top under `:root`) |
| `script.js` | Mobile menu and header shadow |
| `thanks.html` | Not used yet. It's the "thank you" page for when an online estimate form is added. |
| `favicon.png`, `apple-touch-icon.png` | Browser tab and phone home-screen icons, made from her logo |
| `images/` | Her photos, logo mark and the link-preview image (see `images/README.txt`) |

## Confirm before launch

- [x] **Phone number.** Confirmed as 407-637-4137. To change it later, find-and-replace both `407-637-4137` and `+14076374137` in `index.html` and `thanks.html`.
- [x] **Photos.** Added: the van, the technician with the blower, and the technician on the ladder.
- [x] **Logo.** Her logo mark is used in the header, footer, icons and link-preview image.
- [ ] **Before-and-after photos.** Dirty vs. clean duct shots would make a strong new section.
- [ ] **"Read More Reviews" button.** It's hidden until she has a Google reviews link. The button is saved in a comment in `index.html` (search `TODO`): paste in the link and uncomment it.
- [ ] **New copy I wrote.** The text from her draft is unchanged. These parts are new, so she should check they're accurate:
  - the three bullet points on each service card
  - the "Signs it's time for a cleaning" lists
  - the "what happens next" steps in the contact section
  - all FAQ answers (her draft only had the first question)
- [ ] **Extra details** she may want to add: email address, business hours, license/insurance info, and a list of the cities she serves.
- [ ] **Let Google list the site.** While it's a draft, `index.html` has a `<meta name="robots" content="noindex">` tag that keeps it out of search results. Delete that line at launch.

## Hosting: GitHub Pages

The site is published from this folder's GitHub repo with GitHub Pages, which is free.

**To update the site,** edit the files, then run these commands in this folder. The live site refreshes about a minute later.

```bash
git add -A
git commit -m "Describe the change"
git push
```

## Launching on airhavenfl.com

**How the domain is set up today (checked Oct 26, 2026):**
- Registered at **GoDaddy**; renews **Sept 6, 2027**. Keep auto-renew on.
- Its DNS is managed by **Squarespace** (the nameservers are `ns01–ns04.squarespacedns.com`), so the website records are edited in Squarespace.
- **Her email runs on this domain through Google.** These records must stay exactly as they are:
  - `MX` → `smtp.google.com`
  - `TXT` → `v=spf1 include:dc-bdaca08905._spfm.airhavenfl.com ~all`
  - `TXT` → `google-site-verification=…`

**Steps:**

1. **Verify the domain with GitHub** (recommended, so no one else can claim it). On github.com go to **Settings → Pages → Add a domain**, enter `airhavenfl.com`, and GitHub shows a `TXT` record (name like `_github-pages-challenge-Nilzet10`). Add that TXT record in Squarespace (step 2's screen), then click **Verify** on GitHub.
2. **Change the website records in Squarespace.** Log in to her Squarespace account and go to **Settings → Domains → airhavenfl.com → DNS** (labels may differ slightly).
   - Delete the **Squarespace Defaults** website records: the four `A` records (`198.185.159.144`, `198.185.159.145`, `198.49.23.144`, `198.49.23.145`) and the `www` `CNAME` → `ext-sq.squarespace.com`.
   - **Don't touch** the Google `MX` record or the `TXT` records.
   - Add these custom records:

     | Type | Host | Value |
     | --- | --- | --- |
     | A | @ | 185.199.108.153 |
     | A | @ | 185.199.109.153 |
     | A | @ | 185.199.110.153 |
     | A | @ | 185.199.111.153 |
     | CNAME | www | nilzet10.github.io |
3. **Point the GitHub site at the domain.** In the repo, go to **Settings → Pages → Custom domain**, enter `airhavenfl.com` and save.
4. **Wait for DNS** (usually minutes, sometimes a few hours). When GitHub's DNS check passes, tick **Enforce HTTPS** on the same screen.
5. **Let Google list the site.** Delete the `noindex` line in `index.html` and push.

After this, the `nilzet10.github.io/air-haven-website` link forwards to airhavenfl.com automatically.

**Before canceling anything at Squarespace:** her DNS lives on Squarespace's nameservers, and the SPF record suggests her Google email was set up through Squarespace. Canceling the Squarespace subscription could break her email and the website records. First check whether her Google Workspace is billed through Squarespace. If she wants to leave Squarespace completely, move the DNS to GoDaddy first and recreate the email records there.

## Adding an online estimate form later

GitHub Pages can't receive form submissions, so for now visitors call or text. To collect requests online, either:
- sign up for a form service like [Formspree](https://formspree.io), which emails her each request, and point a form at it, or
- move hosting to Netlify, which has built-in forms.

Both would also use `thanks.html` as the page people see after sending a request.
