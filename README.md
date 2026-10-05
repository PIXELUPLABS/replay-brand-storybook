# Replay brand guidelines -

The Replay (Sunset HQ Corp.) brand guidelines as a static site, built by PIXELUP.

Live: https://replay-brand-guidelines.vercel.app

## What's here

| Path | What it is |
|---|---|
| `index.html` | The whole guidelines site: pages, styles and scripts in one file. Fonts, the logo and the paper grain are embedded. |
| `assets/` | Illustrations and their hover videos, mockups (preview and full-resolution PNG), textures, Geist fonts, `brand.md`, the cover artwork. |
| `email/` | Images used by the email templates and the email signature. Copied emails load them from this site until they're on replay.ai. |
| `og.jpg` | The link preview image (the 1.0 Cover). |
| `vercel.json` | Caching and `noindex` headers. |

There is no build step: Vercel serves the folder as it is.

## Deploying

```bash
npx vercel deploy --prod
```

Run it from this folder. The Vercel project is `replay-brand-guidelines` in the **pixelup's projects** team. `.vercelignore` keeps `.env*` and `.vercel` out of the upload.

## Email images on replay.ai

Email templates and signatures should load their images from `https://www.replay.ai/images/email/`. To switch:

1. Copy `email/` from this repo into `public/images/email/` in the Replay site repo and deploy it.
2. In `index.html`, set `const REPLAY_IMAGES_LIVE=true;`. The deployed site also detects the files on its own; the flag is for places that can't check, like claude.ai.

## Licensing

STK Bureau Serif is a licensed typeface and is embedded in `index.html` (the trial cut the Replay site uses). Keep this repository private unless the licence allows redistribution. Geist and Geist Mono are under the SIL Open Font License (`assets/fonts/OFL.txt`).
