# Tahoe guide — landing page

Marketing/orientation page for the Tahoe Now guest guide
([tahoe-guestbook.vercel.app](https://tahoe-guestbook.vercel.app)). Written for two
readers at once: guests who just booked and want to know what the link in their
booking message does, and prospective guests weighing the house.

One static `index.html`, no build step, no dependencies. Visuals reuse the guide's
own design tokens (IBM Plex Sans/Mono, `#f4f4ef`, the single green accent); photos
are copies of the guide's processed WebP assets.

## Run it

```sh
python3 -m http.server 4322
# → http://localhost:4322
```

## Rules carried over from the product repo

- One filled accent on the page (the "Open the guide" CTA); everything else outline.
- No credentials of any kind on this page — it links to the guide, which gates them.
- `og:` URLs are absolute (relative ones are dropped by messengers, not resolved).
- Copy is in the hosts' voice: verdict first, no hedging, guests' own words.
