# Faruuq's landing page — instructions for Claude

This repo is Ahmad Faruuq's personal landing page for AOA Real Estate (PropNex). It is live at
**https://aoarealestate.com/faruuq**. Leads from Faruuq's Facebook and Instagram ads land here to book a free 1-1 property consultation.

## How it's hosted

- Static site on Cloudflare Workers (static assets). No build step, no framework.
- Every push to the `main` branch goes live automatically in about a minute.
- `wrangler.jsonc` attaches this site to the route `aoarealestate.com/faruuq*`. **Don't change the route, the worker name or the assets directory.**
- The rest of aoarealestate.com is Aaron's page in a different repo (`theaaronoon/aoa-landing-page`). Never edit that repo. You may read it, because it's public and is the design template for this page.

## Files

- `public/faruuq/index.html` is the whole page, with CSS and JavaScript inline.
- `public/faruuq/assets/` holds images: photo, logos, review screenshots and reel covers.
- The page is served under `/faruuq/`, so **always use relative paths** such as `assets/photo.jpg`. Never use `/assets/photo.jpg`, because that would point at Aaron's site.
- Keep everything in this one HTML file plus the assets folder. Don't add frameworks, build tools or npm packages.

## Building the page the first time

If `public/faruuq/index.html` is still the temporary redirect page:
1. Copy `index.html` from `theaaronoon/aoa-landing-page` as the template. Keep its structure, sections, styles and scripts.
2. Replace every Aaron-specific detail with Faruuq's. That covers his name, photo, bio, CEA number, booking link, WhatsApp number, reviews, reels, page title and meta description.
3. Remove anything that is only true for Aaron, such as his haio.sg co-founder line, his press logos (unless Faruuq was featured too) and his PropertyGuru rating.
4. Ask Faruuq for any detail you don't have. Never make up numbers, reviews, awards or press mentions.

## Settings in the page (the `CONFIG` block near the bottom of index.html)

- `BOOKING_URL`: Faruuq's Cal.com link. The calendar embeds on the page automatically.
- `WHATSAPP`: his number with country code and no `+`, for example `6591234567`.
- `WA_MESSAGE`: the pre-filled WhatsApp text.
- `PIXEL_ID`: the Meta pixel. Ask Aaron which pixel to use before setting it.
- `VIDEO_URL`: optional 16:9 intro video. If empty, the page shows a placeholder box; remove that box before running ads.

## Rules for the content

- **CEA advertising requirements:** the footer must always show Faruuq's full name, his CEA registration number, "PropNex Realty Pte Ltd" and the agency licence number **L3008022J**.
- No promises of returns, guaranteed prices or "best" claims that can't be backed up.
- Reviews must be real and shown exactly as the client wrote them. Faruuq should have the clients' permission. Hiding dates is fine; rewriting the words is not.
- Use only Faruuq's own photos, videos and reviews, plus the shared AOA logo.
- Keep it simple and readable: white background, black text, one accent colour. Section order: hero → booking calendar → what you leave with → videos → reviews → FAQ → final call to action → footer.

## How to make a change

1. Pull the latest `main` first. Faruuq may have edited from another chat.
2. Make the change in `public/faruuq/index.html` (and `assets/` if needed).
3. Check that it works at phone width (390px) and desktop width (1280px). Nothing should spill off the side, and the menu, calendar and buttons must still work.
4. Commit with a short message that says what changed, then push to `main`.
5. Wait about a minute, then open `https://aoarealestate.com/faruuq/?v=<something new>` to confirm the change is live. The `?v=` part skips the cache.
6. Tell Faruuq in one or two lines what changed and that it's live.

If Faruuq asks for something that would affect Aaron's page or the shared domain (DNS, the main site, Cloudflare settings), don't do it. Tell him to ask Aaron.
