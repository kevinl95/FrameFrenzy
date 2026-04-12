# FrameFrenzy

Frame Frenzy turns a YouTube video into a live sliding-tile puzzle. The video keeps moving while the board is scrambled, and the round ends when the video does.

## Local use

This project is a static site. You can open [framefrenzy.html](framefrenzy.html) directly in a browser, but YouTube embeds are more reliable when served over HTTP.

One simple option:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/framefrenzy.html`.

## Browser compatibility notes

- Touch input now uses Pointer Events when available, with a touch fallback for older mobile browsers.
- Video playback now tries to start with sound on by default. If a browser blocks delayed autoplay with audio, the game shows a one-tap resume prompt.
- Clipboard sharing falls back to `document.execCommand('copy')` when the async Clipboard API is unavailable.
- The app respects `prefers-reduced-motion` and no longer disables zoom at the viewport level.
- Some YouTube videos still cannot be embedded because the video owner disables playback in iframes. That is a platform restriction, not an app bug.

## Cloudflare Pages deployment

This repo is a static site with no build step. If Cloudflare only offers you the Worker-style setup flow, this repository is now configured to deploy that way using static assets.

Recommended settings:

1. Project name: `FrameFrenzy`
2. Build command: leave it blank if Cloudflare allows it. If the field is required, use `exit 0`.
3. Deploy command: `npx wrangler deploy`
4. Root directory / path: `/` or `.` if the UI wants a relative path.

About the deploy command field:

- If your logs say `Executing user deploy command`, you are in the Workers build flow, not the normal Pages static-site flow.
- This repo now includes [wrangler.jsonc](wrangler.jsonc), which tells Wrangler to deploy the repository as a static-assets Worker.
- Because of that config file, `npx wrangler deploy` is now the correct deploy command in the Worker setup flow.
- Do not use `npx wrangler deploy .` for this repo.

Notes:

- The Worker name in the dashboard should match the `name` field in [wrangler.jsonc](wrangler.jsonc), which is `FrameFrenzy`.
- The repository now includes [index.html](index.html) so the root URL resolves correctly and redirects to [framefrenzy.html](framefrenzy.html).