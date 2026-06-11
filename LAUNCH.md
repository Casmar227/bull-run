# 🐂 BULL RUN — Launch Playbook

The game is live at **https://casmar227.github.io/bull-run/**. Everything below is
copy-paste ready. Fire posts on a Tue–Thu, mid-morning US-Eastern, and plan to hang
out in each thread for a few hours answering replies — the conversation is the launch.

> **Before posting (5 min):** register the GoatCounter site code `bullrun-game` at
> goatcounter.com (or edit the snippet near the bottom of `index.html` to your own
> code). That's the players/day + share-click dashboard.

---

## Show HN (Hacker News)

**Title:**
`Show HN: Bull Run – a Slay the Spire-like roguelike in one HTML file`

**Body:**

> I built a finance-themed roguelike deckbuilder that runs entirely from a single
> HTML file — no build step, no dependencies, no backend. View-source is the whole
> game: 72 cards, 3 characters, a procedurally branching map, meta-progression,
> and a seeded daily challenge, in ~250KB before gzip.
>
> Things that were fun to solve:
> - Save/resume with card definitions that contain functions: saves store ids+flags
>   and snapshot the seeded RNG's call count *before* each map node, so resuming
>   mid-combat reconstructs the exact same fight.
> - The daily challenge needs no server: the seed is a hash of the UTC date, so
>   everyone worldwide gets the same map, enemies, and shops, and results are
>   compared via a Wordle-style emoji share grid.
> - Every share link carries `?seed=`, so "play the exact run that killed me" is
>   just a URL.
> - All audio is procedural Web Audio (the trading-floor ambience is filtered noise
>   plus random sine beeps).
>
> It's a PWA, works offline, and the only external request is an optional
> no-cookie analytics counter. Would love feedback on the balance — an AI bot
> playtested it, but bots don't rage-quit.

*(Be ready for: SW update questions — navigations are network-first with cache
fallback, so deploys propagate immediately; "why emoji art" — it's the brand and
it's 0KB; balance criticism — point to the daily and ask for their seed.)*

---

## Reddit

### r/WebGames
**Title:** `Bull Run — a finance roguelike deckbuilder (free, no install, works offline, daily challenge)`
**Body:** Defeat the Federal Reserve. 72 cards, 3 unlockable investors, branching
map, Wordle-style daily run that's identical for everyone. Built in one HTML file.
Today's market condition is **{{check the menu}}** — post your P&L grid below.

### r/playmygame
**Title:** `[Web] Bull Run — Slay-the-Spire-like where you fight the Fed`
Lead with the boss GIF, link, then: "Looking for feedback on Act 2 difficulty and
whether the Vulture's Debt engine feels fair. Every end screen has a COPY SEED
button — if a run feels unfair, paste me the seed and I can replay it exactly."

### r/roguelikedev (Sharing Saturday thread)
Dev-angle comment: the seeded sub-stream RNG design (map/node streams so shop
contents don't depend on draw order), the DAG map generator with its constraint
pass, and the bot-playtesting harness used for balance. Link the repo.

### r/slaythespire
Only as an honest homage post: "I built a free browser StS-like about fighting
the Federal Reserve — here's what I stole from StS and what I changed." Read the
sub's self-promo rules first; lead with the map GIF.

---

## itch.io mirror (~30 min)

- New project → HTML game → upload a zip of `index.html` + `manifest.webmanifest`
  + `sw.js` + `icons/` (the game is self-contained; the SW won't activate in the
  itch iframe, which is fine).
- Viewport 960×800, fullscreen button ON, mobile-friendly ON.
- Page art: `icons/og-card.png` as cover, the three GIFs from `media/` inline.
- Tags: roguelike, deckbuilder, card-game, singleplayer, browser, daily-challenge.
- Description: reuse the README feature list. Link back to the GitHub Pages URL
  ("also playable free on the web — installs as an app").

---

## Community loop (weekly, ~15 min each)

- **House seed challenge:** every Monday post a seed link in GitHub Discussions
  ("This week's house seed: <url>?seed=XYZ — post your P&L grid"). Scout seeds by
  playing one act yourself, or ask me to bot-scout a cursed/god seed.
- **Streamer outreach:** 1–10k-sub StS/Balatro YouTubers; personalized message +
  a seed link ("here's a seed where the shop sells Ponzi Scheme on floor 2 —
  your viewers can play the same map"). One or two a week is plenty.

## Post-launch metrics to watch (GoatCounter)

| Event | Healthy signal |
|---|---|
| `run-start` / day | growth after each post |
| `run-won` ÷ `run-lost` | easy ≈ comfortable, normal ≈ 20–35% |
| `share-click` ÷ run-end | >10% — the viral loop works |
| `daily-start` / day | the retention ritual is forming |

If share-rate is low, the share button placement/copy is the first suspect.
If daily-starts stagnate while run-starts grow, brighten the daily button states.
