# 🐂 BULL RUN — Product Roadmap

Goal: many players, strong retention, viral sharing, optionally App-Store-ready.

**Sequencing principle:** fix leaks before pouring water — persistence and variety
before meta-hooks, meta-hooks before acquisition pushes, acquisition before monetization.

**Deliberately out of scope** (static hosting, no backend): multiplayer, accounts,
cloud sync, server leaderboards (the daily share-string substitutes socially),
replacing emoji art (it's the brand — revisit only when App Store icons force it),
localization, ads.

---

## ✅ SHIPPED — Sprint 0: the growth-loop MVP

- **Seeded RNG** (mulberry32 + `grand()`): runs reproducible from a seed; visuals/audio
  stay on `Math.random` so they never consume game entropy
- **Save / resume**: ids+flags serialization (card defs hold functions), map-node
  granularity, RNG call-count snapshot ⇒ resuming mid-combat restarts the *same* fight;
  RESUME button on menu
- **Mobile-responsive layout**: single ≤720px breakpoint, viewport-aware hand fan,
  tap-to-target hint, tappable relic tooltips, dvh-fitted combat screen
- **Daily Challenge**: date-hashed seed (same run worldwide), 7 rotating modifiers
  (ZIRP, Meme Stock Monday, Crypto Winter…), one scored attempt/day then practice mode
- **Share P&L**: end-of-run share string written as a trading recap (clipboard +
  `navigator.share`)
- **Voice pass**: game-over as a brokerage liquidation notice, ticker tape reacts to
  career record, run history in localStorage

---

## ✅ SHIPPED — Phase 1: Foundation & Variety

- **Branching DAG map with path commitment**: procedural 9/10/8-floor acts (Act 3 is now a
  real act, not one boss node); 3 seeded path tracks down a 4-column grid; constraints
  enforced (acts open with fights, guaranteed pre-boss rest row, ≥1 shop + mid-act rest,
  2 elites on middle/late rows); SVG edges show taken/open/abandoned paths
- **Content variety**: 8 new normal enemies in per-act pools (Short Seller, FOMO Mob swarm,
  Crypto Bro, Pension Fund, Stagflation, Algo Bot, Rating Agency, Liquidity Crisis);
  2 new elites (Activist Investor, The Whale); new Act 2 boss **BLACK MONDAY** (escalating
  crash cycle) — each act now has a distinct boss; events 5→14 (incl. the Red Tape curse);
  relics 8→22 (incl. Severance Package: survive lethal once per run)
- **Real card upgrades**: all 43 cards have bespoke ★ versions via an `UPGRADES` override
  table (Market Order 6→9, Junk Bonds 5×→7× Debt, All In keeps your hand, Leveraged Play
  loses Exhaust…); saves store a single boolean and rehydrate through `applyUpgrade`

**Moves:** sessions/player, run completion; a player's 5th run should still contain new content.

## ✅ SHIPPED — Phase 2: The Comeback Loop

- **Meta-progression & unlocks** (`br_meta`): 3 runs → Derivatives Desk card pack; reach
  Act II → Executive Perks relic pack; win a run (or play 5) → THE VULTURE. Reward pools
  computed per call, filtered by character + unlocks; unlock reveals on end screens;
  menu profile strip — every run ends with a green number going up
- **2nd character: THE VULTURE 🦅**: HP 70, starter deck with Leverage Up + Junk Bonds,
  innate Vulture's Eye (2 block per Debt gained), 12 exclusive cards with bespoke
  upgrades (Chapter 11, Debt Ceiling, Carrion Call, Toxic Yield…); character select
  screen with per-character Margin Level steppers
- **Margin Levels 1–10**: cumulative per-character ascension (Bear Market → Trading
  Fees → Overleveraged → … → Black Swan Era); win at ML N unlocks N+1
- **Hot Tips**: 8 consumables in 3 slots (Hot Tip, Circuit Breaker halts all enemies,
  Shred-It removes a card from the map…); ~30% post-combat drop, 2 sold per shop
- **Quality pass**: deck view during combat; codex deferred

**Moves:** D7/D30 retention, runs/player, % starting a 2nd character.

## ✅ MOSTLY SHIPPED — Phase 3: Reach & Virality

- ✅ **PWA**: `manifest.webmanifest` + cache-first versioned `sw.js` + real 192/512 PNG
  icons (bull-on-CRT, browser-rendered). Installs to home screen, runs fully offline —
  verified with an offline boot test. Bump `VERSION` in `sw.js` on every deploy.
- ✅ **Emoji path-grid share**: Wordle-style grid per act in the share string
  (🟩 clean fight / 🟧 under 50% HP / 💀 elite / 🛒☕❓ / 🟥 death / ✅❌ boss),
  built from per-node HP snapshots in the run path
- ✅ **Seed sharing**: non-daily share links carry `?seed=`; opening one shows a
  "PLAY SEEDED RUN" button (identical map/enemies/shops); COPY SEED on end screens
- ⏳ **Launch push + analytics** (the remaining work, ~4h, owner-driven):
  GoatCounter snippet (daily players + share CTR — would be the only external
  dependency; not added without owner sign-off). Then the posts: Show HN
  ("a full roguelike in one HTML file"), r/WebGames, r/slaythespire, itch.io mirror.

**Moves:** new players/week, share CTR (target >10% of daily finishers), daily DAU.

## PHASE 4 — Third Character, Depth & App Store (partially shipped)

- ✅ **3rd character: THE WHALE 🐋** — shipped. 85 HP institutional money; gold is
  ammunition via a new gold-cost card mechanic (`gcost`, gold chip on the card frame,
  affordability greying): Buy the Dip ($15: 18 dmg), Liquidity Wall, Bribe the Regulator
  (halts all enemies), Too Big To Fail (first death this combat costs $75 instead),
  Index Everything (damage = 10% of gold). Innate Platinum Card (+2 block per $ spend).
  11 exclusives with bespoke upgrades. Unlocked by winning as the Vulture (or 10 runs).
- ✅ **Balance pass via bot playtesting** — a block-aware greedy bot played 16 full
  honest runs: easy now reaches Act 2 reliably (bot even wins occasionally ⇒ humans
  clear it comfortably), normal stays a real challenge. Tweaks: easy enemies −10% HP,
  rest heal 30%→35%. Re-tune from daily-challenge metrics after launch.
- ⏳ **iOS via Capacitor** (~16–24h, requires Mac + Xcode + $99/yr Apple account —
  cannot be done from this environment): passes guideline 4.2 since the PWA already
  runs fully offline. **$4.99 paid up-front; web stays free as the funnel.** Haptics
  on hits; audio suspend on `visibilitychange`; shell in `/ios-shell` to keep the web
  product no-build.
- ✅ **Depth backlog — shipped**: Powers card type (6 persistent auras incl. per-character
  ones), Faustian boss trade-off relics (choice of 3 after Act I/II bosses), endless
  After-Hours Trading mode (stacking +20% HP/+1 Str loops), daily streaks 🔥, stats
  screen, codex with locked silhouettes, keyboard play. Still open: mid-combat save
  (needs data-driven enemy defs), MLs 11–20.
- ✅ **Graphics overhaul — shipped**: title boot cinematic, per-act living backgrounds,
  boss intro splashes, hit-stop, death dissolves, holo-foil rares with 3D tilt, custom
  SVG portraits for all six "faces", bull map-marker that walks your route, VT323
  terminal font, FX quality settings; 60fps verified on mobile viewport.

**Moves:** revenue, App Store rating, D90 retention.

---

## Effort summary

| Phase | Theme | Est. hours | Primary metric |
|---|---|---|---|
| ✅ 0 | Growth-loop MVP (shipped) | — | Run completion, shares |
| ✅ 1 | DAG map, variety, real upgrades (shipped) | — | Sessions/player |
| ✅ 2 | Meta, Vulture, Margin Levels, Hot Tips (shipped) | — | D7/D30 retention |
| ✅ 3 | PWA, path-grid share, seeds (shipped) — launch push pending | ~4 | New players, daily DAU |
| 4 | ✅ Whale + balance (shipped) — iOS app, depth pending | 30–45 | Revenue, D90 |
