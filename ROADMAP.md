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

## PHASE 2 — The Comeback Loop (~35–45 hrs)

*Make losing produce progress. The D7/D30-retention phase.*

| Feature | Design | Est. |
|---|---|---|
| **Meta-progression & unlocks** | `br_meta` in localStorage. Ladder: 3 runs → "Derivatives Desk" card pack; first Act 2 → relic pack; first win → unlock 2nd character. Reward pools computed per-run, filtered by unlocks. Menu profile strip. Every run ends with a green number going up. | 6–8h |
| **2nd character: THE VULTURE 🦅** | Distressed-debt investor — Debt is fuel, not poison. HP 70; starter deck includes Leverage Up + Junk Bonds; innate relic: +1 block per Debt gained. 12 exclusive cards (*Chapter 11*: convert Debt→Strength; *Debt Ceiling*: Debt stops ticking this combat; *Predatory Loan*: Debt as an enemy status). `CHARACTERS` table, `char:` tag on cards, char-select screen. | 10–14h |
| **Margin Levels (ascension 1–10)** | Per-character difficulty ladder: ML1 Bear Market (+15% enemy HP) … ML8 Audit Season (curse card per act) … ML10 Black Swan Era. `ML_MODS` table — same plumbing as daily modifiers. | 5–6h |
| **Hot Tips (consumables)** | 3 potion slots: 📞 Hot Tip (10 dmg), 💉 Liquidity Injection (+2 Capital), 🧯 Circuit Breaker (enemy skips a turn), 🗞 Shred It (remove a card on the map). ~30% combat drop + 2 shop slots. Ids serialize trivially. | 5–6h |
| **Quality pass** | Deck view during combat, fast-mode toggle, codex with ❓ silhouettes teasing locked content. | 4–5h |

**Moves:** D7/D30 retention, runs/player, % starting a 2nd character.

## PHASE 3 — Reach & Virality (~25–35 hrs remaining)

*Mobile + daily shipped in Sprint 0; what remains is packaging and the push.*

| Feature | Design | Est. |
|---|---|---|
| **PWA** | `manifest.webmanifest` + `sw.js` (cache-first, versioned) + real 192/512 PNG icons — the first deliberate break of the single-file rule (SW must be a separate same-origin file). Home-screen install + offline; dress rehearsal for the App Store. | 4–6h |
| **Emoji path-grid in share string** | Wordle-style: one emoji per node visited (🟩 clean fight / 🟧 survived <50% HP / 💀 elite / 🟥 death), boss ✅/❌. Needs per-node HP snapshots in `pathTaken`. | 3–4h |
| **Seed sharing** | `?seed=` URL param into `startGame`, COPY SEED on end screens — streamer/community challenge tooling, zero backend. | 3–4h |
| **Launch push + analytics** | GoatCounter snippet (daily players, share CTR — the only external dependency). Then: Show HN ("a full roguelike in one HTML file"), r/WebGames, r/slaythespire, r/wallstreetbets-adjacent, itch.io mirror. Time the posts AFTER PWA + path-grid ship. | 4h |

**Moves:** new players/week, share CTR (target >10% of daily finishers), daily DAU.

## PHASE 4 — Third Character, Depth & App Store (~50–70 hrs)

| Feature | Design | Est. |
|---|---|---|
| **3rd character: THE WHALE 🐋** | Gold-as-combat-resource archetype: *Buy the Dip* (costs $15 + 1⚡), *Too Big To Fail* (fatal hit costs $75 instead). Unlocked by winning as Vulture. | 10–14h |
| **iOS via Capacitor** | Passes guideline 4.2 because post-PWA it's a real offline game. **$4.99 paid up-front; web stays free as the funnel** (no IAP/account complexity). Costs: $99/yr dev account, Mac+Xcode. Haptics on hits; audio suspend on `visibilitychange`; shell quarantined in `/ios-shell` so the web product stays no-build. Real icon art is the one mandatory art spend. | 16–24h |
| **Depth backlog** (pick by metrics) | Powers card type (persistent auras), boss trade-off relics, mid-combat save (after making enemy defs data-driven — remove the `inflation` closure), endless mode ("After-Hours Trading"), MLs 11–20, second Act 1 boss. | 15–20h |

**Moves:** revenue, App Store rating, D90 retention.

---

## Effort summary

| Phase | Theme | Est. hours | Primary metric |
|---|---|---|---|
| ✅ 0 | Growth-loop MVP (shipped) | — | Run completion, shares |
| ✅ 1 | DAG map, variety, real upgrades (shipped) | — | Sessions/player |
| 2 | Meta, Vulture, Margin Levels, Hot Tips | 35–45 | D7/D30 retention |
| 3 | PWA, path-grid share, seeds, launch | 25–35 | New players, daily DAU |
| 4 | Whale, iOS app, depth | 50–70 | Revenue, D90 |
