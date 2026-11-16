# Google Analytics (GA4) Setup Plan

Goal: track basic traffic and see which specific page each visitor opens (not just the index page).

## Part 1: What you do (about 10 minutes)

1. Open https://analytics.google.com and sign in.
2. Go to **Admin → Data streams**, then click your existing **web stream**.
   - If you have no web stream yet: **Admin → Create → Property**, name it "Portfolio", then **Add stream → Web** and enter your site's live URL.
3. Copy the **Measurement ID** from the top right of the stream page. It looks like `G-XXXXXXXXXX`.
4. Send me:
   - The Measurement ID.
   - Where the site is hosted (GitHub Pages, Netlify, Vercel, etc.) and the live URL.
5. Optional: tell me if you want click tracking on nav menu items, project cards and outbound links (LINE, email, social).
6. Optional: decide whether you need a cookie banner (relevant for EU/UK visitors). It can be added later.

## Part 2: What Claude does

1. Add the GA4 snippet to the `<head>` of every page:
   `index.html`, `dior.html`, `dior-addict.html`, `novatrade.html`, `pect.html`, `reels.html`, `tumi.html`, `technical-school.html`, `new-project.html`.
2. Make each page's `<title>` clear and unique, so reports show readable page names.
3. Skip tracking on localhost, so your own testing does not pollute the data.
4. Optional: add click events for nav, project cards and outbound links.
5. Start the site on localhost and confirm each page sends its own `page_view` request.

## Part 3: After it is built

1. Commit and push to GitHub, and let the site deploy.
2. Open the live site, then check **GA4 → Reports → Realtime**.
3. Visit a few different pages and confirm each appears as a separate page path.
4. Later, view **Reports → Engagement → Pages and screens** to see views per page.

## Notes

- The Measurement ID is public and appears in the page source, so sharing it is safe.
- GA4 can take 24–48 hours to show data in standard reports. Realtime is immediate.
