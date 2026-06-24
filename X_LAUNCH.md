# Launching BLOOM RUN on X

Inline "player" cards only render for domains X has manually allowlisted. For
everyone else the card falls back to image + tap-to-open. So the play in feed is:
post a looping gameplay clip as native media, with the play link in the text.

## 1. The gameplay clip (the part that moves in-feed)

Native video and GIFs autoplay in the timeline. A 8 to 12 second loop of real
play does more than any card.

**Record it (Mac):**
1. Open `https://bloomrun.mlow.xyz/MLOW_Bloom_Run_NFT.html` full screen.
2. `Cmd + Shift + 5` → select a tight rectangle around the play area → Record.
3. Play a clean 8 to 12 seconds: collect a few fLOWers, trigger Bloom Mode once.
4. Stop. You get a `.mov` on the desktop.

**X media specs to hit:**
- Length: keep it under 2:20 (8 to 12s is ideal for a loop).
- Format: MP4 (H.264) or GIF. MP4 is sharper and smaller.
- Aspect: square (1:1) or portrait (4:5) reads best on mobile.
- Send me the `.mov` and I will trim, loop, size, and export an X-ready MP4.

**Posting:** attach the clip, then put the link in the text so the click goes
straight to the playable:

> drive the art taxi up manhattan. collect fLOWers, hit bloom mode, take times
> square. playable nft, runs in your browser ↓
> https://bloomrun.mlow.xyz/

(Tip: a link plus native video shows the video, not the link card. That is what
you want here.)

## 2. The link-out card (when you post just the URL)

Already configured as `summary_large_image`: tweeting `https://bloomrun.mlow.xyz/`
shows the full 1200x675 "PLAYABLE NFT" poster, tap opens the live game. This card
type needs no approval and always renders.

- **Preview before posting:** DM the URL to yourself. The card renders in the DM.
- **Cache:** if you posted an older/broken version, add `?v=2` to force X to
  re-scrape (e.g. `https://bloomrun.mlow.xyz/?v=2`).

## 3. Player-card approval (long shot)

If you want to chase the true inline player later:
- X does not run a public "apply for player card" form anymore; it is granted
  case by case, mostly to media/partners, and rarely to individual domains.
- The card is already valid (`twitter:player` tags are kept, commented, in
  `index.html`). If a player card is ever enabled for `bloomrun.mlow.xyz`, flip
  `twitter:card` back to `player` and uncomment those three tags. One commit.
- Practical reality: lead with the native gameplay clip. It outperforms a player
  card in the feed anyway because it autoplays without a tap.
