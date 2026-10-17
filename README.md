# Tahoe guide — guest welcome page

English welcome page for guests arriving at Tahoe Tuolumne, sent as a link before
check-in. Production: https://tahoe-guide-landing.vercel.app/

The Vercel project is not connected to git — a push does not deploy. Deploy by hand:
`vercel deploy --prod` from this folder. `vercel.json` pins a no-op build, because
otherwise Vercel runs `npm run build` and fails (there is no package.json).
Guest guide: https://tahoe.ai-host.ai/

## Run locally

```sh
python3 -m http.server 4322
```

Open http://localhost:4322. One static `index.html`, no build step, no dependencies.
Visuals reuse the guide's own tokens (IBM Plex Sans/Mono, `#f4f4ef`, one green accent).

## What the page covers

A summary at the top links to each section, in the order a guest needs them:

- **Arriving** — directions, parking (4 cars, no street parking), the smart lock,
  Wi-Fi from the guide's booking link.
- **Your dog** — house pet rules and where dogs can and can't go
  (from `activities.yaml`'s `dogs:` field).
- **Ask the house** — the in-browser concierge: Talk on the Now screen, or Chat.
- **The guide** — Now, Nearby this week, House, Around, Book, My plan.
- **The TV** — the house's Roku channel on HDMI 1 in the living room.
- **A note from the owner** — Alex's goal for the house, a request for feedback and
  wishes, and his WhatsApp (+1 408 429-0090, "ABari").
- **Before you leave** — check-out at 10 AM and the checklist.

## Rules

- **Door code:** the page says "the code provided to you by Nicole" and never
  explains how the code is made. No Wi-Fi credentials or booking tokens here.
- **Phone line:** the concierge's phone number is off in the guide
  (`CONCIERGE_LINE_LIVE = false`). Don't offer calling it or "Hey Siri" here until it works.
- **Privacy:** match the guide's `/policy`. The guide counts which screens are opened,
  so don't say "no analytics".
- **Nothing dated:** keep weather, events, road closures and prices in the guide.
  Don't copy them onto this page.
- One filled button on the page ("Open the house guide").
- `og:` URLs are absolute, because messengers drop relative ones.
- No Russian version: `vercel.json` redirects `/ru` to `/`.

## Screenshots

`photos/g-*.webp` are phone captures of the live guide, taken at 390×844 @2x with
Playwright and saved as 640px WebP (`cwebp -q 72 -resize 640 0`). Block `/api/tally`
while capturing so the hosts' counters stay clean. Retake them whenever the guide's
screens change.
