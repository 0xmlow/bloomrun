# Minting BLOOM RUN as a playable NFT on OpenSea

The game already meets every requirement for an OpenSea playable: it is one
self-contained `MLOW_Bloom_Run_NFT.html` file with zero external requests, and
every sandbox-sensitive call (`localStorage`, `navigator.vibrate`) is guarded, so
it runs inside OpenSea's sandboxed iframe with no changes. OpenSea reads the
`animation_url` field and renders it interactively on the item page.

You have two routes. Pick one.

## Route A — No-code, recommended (Manifold Studio)

Manifold pins your file to IPFS and wires up `animation_url` for you, and you mint
on your own contract (not a shared one), which is what serious collectors expect.

1. Go to **studio.manifold.xyz**, connect the wallet you want to mint from.
2. **Create a contract** (ERC-721) once. Name it (e.g. "MLow — Evolution of fLOWers").
3. **Create New** → upload **`MLOW_Bloom_Run_NFT.html`** as the artwork.
   - Set the **preview image** to `bloomrun_poster_16x9.png` (this is what shows
     in feeds/thumbnails; the HTML is what plays on the item page).
   - Title: `BLOOM RUN — NYC Taxi Edition`
   - Description + traits: copy from `metadata.json` in this repo.
   - External link: `https://bloomrun.mlow.xyz/`
4. Mint. Manifold pins the HTML + image to IPFS and builds the metadata.
5. The token appears on OpenSea automatically. Open the item page → it plays.

## Route B — Manual control (pin it yourself)

Use this if you want to own the IPFS pins and metadata directly.

1. **Pin the two assets** to IPFS (Pinata.cloud or NFT.Storage, both free):
   - `MLOW_Bloom_Run_NFT.html`  → note its CID
   - `bloomrun_poster_16x9.png` → note its CID
2. Edit **`metadata.json`** (in this repo): replace
   - `REPLACE_WITH_GAME_CID`   with the HTML's CID
   - `REPLACE_WITH_POSTER_CID` with the poster's CID
3. **Pin `metadata.json`** to IPFS → note its CID. This is your `tokenURI`.
4. Mint on a contract that returns `ipfs://<metadata-CID>` for the token:
   - Easiest: **thirdweb.com/dashboard** → deploy an NFT Collection contract →
     mint with the metadata CID, or
   - Your own deployed ERC-721 with `tokenURI` set to the metadata CID.
5. OpenSea will fetch the metadata and render the playable on the item page.

## OpenSea display notes

- `animation_url` (the HTML) is the interactive asset shown on the item page.
- `image` (the poster) is the thumbnail in galleries, feeds, and search.
- `background_color` is set to the game's ink black (`0D0D0D`) for a clean frame.
- After minting, if the item shows the image but not the game, hit
  **"Refresh metadata"** on the OpenSea item page (it caches on first load).
- Use the **exact same** `MLOW_Bloom_Run_NFT.html` you host at bloomrun.mlow.xyz
  so the on-chain artwork and the public link are byte-identical.
