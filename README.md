# BLOOM RUN — NYC Taxi Edition

A playable NFT by **MLow** (Evolution of fLOWers · Blossom). Drive the art taxi up
Manhattan; every pedestrian who sees the rooftop sign is an impression. Collect
fLOWers, trigger Bloom Mode, take over Times Square.

## Files

| File | Role |
|------|------|
| `MLOW_Bloom_Run_NFT.html` | The game. **Fully self-contained** — all art is embedded as base64, zero external requests. This is the canonical NFT artifact (pin this exact file to IPFS). |
| `index.html` | The page you tweet. Holds the `twitter:player` card meta tags that make the game embed inside an X post. |
| `bloomrun_poster_16x9.png` | 1200×675 preview image used by the card (`twitter:image` / `og:image`). |
| `.nojekyll` | Tells static hosts to serve files verbatim. |

## Live URL

Card + game are served from **https://mlow.xyz/bloomrun/**

- Tweet `https://mlow.xyz/bloomrun/` (the bare folder = `index.html`).
- X scrapes the player meta tags and embeds the game in the timeline.

## Deploy to mlow.xyz

Upload the four files into a `/bloomrun/` directory at the site root so the paths
resolve as:

```
https://mlow.xyz/bloomrun/                       -> index.html (tweet this)
https://mlow.xyz/bloomrun/MLOW_Bloom_Run_NFT.html -> the game (embedded by X)
https://mlow.xyz/bloomrun/bloomrun_poster_16x9.png -> preview image
```

### Twitter / X checklist
- **Serve over HTTPS** (X requires it for player cards).
- The host must **not** send `X-Frame-Options: DENY` or a restrictive
  `Content-Security-Policy: frame-ancestors` on these files, or the embed renders
  blank. (GitHub Pages / Netlify defaults are fine; check your own server.)
- **Validate before posting:** paste `https://mlow.xyz/bloomrun/` into a DM to
  yourself — the card preview renders there without posting publicly.
- **Cache busting:** if you tweeted a broken link earlier, X cached the failure.
  Append `?v=2` to force a fresh scrape.

## As an NFT

`MLOW_Bloom_Run_NFT.html` needs no server — it runs from a single file. For the
mint, pin **that exact file** to IPFS and use the IPFS URI as the token's
`animation_url`. Set `external_url` to `https://mlow.xyz/bloomrun/` so the
marketplace links back to the playable card.
