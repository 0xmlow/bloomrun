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

Card + game are served from **https://bloomrun.mlow.xyz/**

- Tweet `https://bloomrun.mlow.xyz/` (the bare folder = `index.html`).
- X scrapes the player meta tags and embeds the game in the timeline.

## Hosting — GitHub Pages on a custom subdomain

Served by GitHub Pages (`main` / root) on the custom domain in the `CNAME` file:

```
https://bloomrun.mlow.xyz/                        -> index.html (tweet this)
https://bloomrun.mlow.xyz/MLOW_Bloom_Run_NFT.html -> the game (embedded by X)
https://bloomrun.mlow.xyz/bloomrun_poster_16x9.png -> preview image
```

DNS (in Squarespace): a `CNAME` record `bloomrun` → `0xmlow.github.io`.
GitHub auto-provisions the HTTPS cert once that record resolves.

### Short link: mlow.xyz/bloomrun
Squarespace → Settings → Advanced → URL Mappings:
`/bloomrun -> https://bloomrun.mlow.xyz/ 301`. X follows the redirect and reads
the card from the subdomain.

### Twitter / X checklist
- **Serve over HTTPS** (X requires it for player cards).
- The host must **not** send `X-Frame-Options: DENY` or a restrictive
  `Content-Security-Policy: frame-ancestors` on these files, or the embed renders
  blank. (GitHub Pages / Netlify defaults are fine; check your own server.)
- **Validate before posting:** paste `https://bloomrun.mlow.xyz/` into a DM to
  yourself — the card preview renders there without posting publicly.
- **Cache busting:** if you tweeted a broken link earlier, X cached the failure.
  Append `?v=2` to force a fresh scrape.

## As an NFT

`MLOW_Bloom_Run_NFT.html` needs no server — it runs from a single file. For the
mint, pin **that exact file** to IPFS and use the IPFS URI as the token's
`animation_url`. Set `external_url` to `https://bloomrun.mlow.xyz/` so the
marketplace links back to the playable card.
