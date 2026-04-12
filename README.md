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
- Video playback is muted for better autoplay compatibility on mobile browsers and embedded contexts.
- Clipboard sharing falls back to `document.execCommand('copy')` when the async Clipboard API is unavailable.
- The app respects `prefers-reduced-motion` and no longer disables zoom at the viewport level.
- Some YouTube videos still cannot be embedded because the video owner disables playback in iframes. That is a platform restriction, not an app bug.

## Cloudflare Pages deployment

The repository includes a GitHub Actions workflow at [.github/workflows/deploy-cloudflare-pages.yml](.github/workflows/deploy-cloudflare-pages.yml). It deploys the repository root to Cloudflare Pages on pushes to `main` and on manual runs.

Set these before enabling the workflow:

1. Create a Cloudflare Pages project for this repo.
2. Add a GitHub repository variable named `CLOUDFLARE_PAGES_PROJECT` with the Pages project name.
3. Add a GitHub secret named `CLOUDFLARE_ACCOUNT_ID` with your Cloudflare account ID.
4. Add a GitHub secret named `CLOUDFLARE_API_TOKEN` with a token that can deploy Pages projects.

Recommended token scopes:

- `Cloudflare Pages:Edit`
- `Account:Read`

If your default branch is not `main`, update the branch trigger in [.github/workflows/deploy-cloudflare-pages.yml](.github/workflows/deploy-cloudflare-pages.yml).