# Air Haven website

A one-page site for Air Haven (air duct cleaning and HVAC restoration in Central Florida). It's rebuilt from her Squarespace draft and keeps the same sections, copy and navy/blue look.

To preview it, open `index.html` in any browser.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole site: hero with estimate card, services, about, signs it's time, review, FAQ, contact |
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

**To use her domain (airhavenfl.com):**

The domain currently points to her Squarespace site. Its DNS records go to Squarespace's servers, and `www` points to `ext-sq.squarespace.com`. Switching it over means editing those records wherever the domain is managed, most likely in her Squarespace **Domains** settings. After the switch, the Squarespace site stops showing on airhavenfl.com.

1. In the repo on GitHub, go to **Settings → Pages → Custom domain**, enter `airhavenfl.com` and save.
2. In her domain's DNS settings, replace the Squarespace records with the ones GitHub lists in its "Managing a custom domain for your GitHub Pages site" guide. These are `A` records for the bare domain and a `CNAME` record for `www` pointing to `nilzet10.github.io`.
3. Once the domain is working, turn on **Enforce HTTPS** on the same Pages settings screen.
4. Delete the `noindex` line in `index.html` (see the checklist above).

## Adding an online estimate form later

GitHub Pages can't receive form submissions, so for now visitors call or text. To collect requests online, either:
- sign up for a form service like [Formspree](https://formspree.io), which emails her each request, and point a form at it, or
- move hosting to Netlify, which has built-in forms.

Both would also use `thanks.html` as the page people see after sending a request.
