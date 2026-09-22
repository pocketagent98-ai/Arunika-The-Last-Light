# Research Report — 12 Endless Runner / Action-Runner Games

Method: each game was analyzed as a *player-first* breakdown (loop, controls,
progression, economy, UX). Facts are tagged `[VERIFIED]` (public record),
`[INFERENCE]` (reasoned, not directly measurable) or `[UNVERIFIED]`.
No copyrighted assets, characters, maps or code were extracted from any game.

---

## 1. Temple Run (Imangi Studios, 2011)

- iOS Aug 4 2011, Android Mar 27 2012; designed by Keith Shepherd & Natalia Luckyanova, art by Kiril Tchangov; ~4 months of development. `[VERIFIED]`
- **Loop:** RUN → AVOID → COLLECT → TURN → FAIL → RETRY. Coin/meter score, power-ups (magnet, boost, invisibility), simple objectives. `[VERIFIED]`
- **Controls:** swipe to turn/jump/slide + **tilt to lean** for narrow paths and edge coin lines. The tilt-lean is the franchise's signature input.
- **Why it works:** one-thumb play, instant restart, the "evil monkeys" chase gives fear-forward momentum without combat.
- **Friction:** tilt is unreliable on cheap devices; ported Android build had crash/heat issues. `[VERIFIED]`
- **Lesson taken:** *chase pressure makes simple inputs exciting* — but device-independent inputs only.

## 2. Temple Run 2 (Imangi Studios, 2013)

- iOS Jan 16 2013. `[VERIFIED]` Added curves, mine-cart and zip-line sections, per-environment visuals, save-me mechanic.
- **Lesson taken:** *set-piece interludes inside a run* (mine cart) reset attention and create memorable beats; secondary currency for meta upgrades.

## 3. Subway Surfers (Kiloo / SYBO, 2012)

- Released May 24 2012, Unity engine; 2.7bn downloads by Dec 2019; most-downloaded mobile game of the 2012–2019 decade; "World Tour" city changes every 3–4 weeks since Jan 2013. `[VERIFIED]`
- **Loop:** 3-lane lane-swap under/over trains; keys revive; hoverboard = 30s crash shield; missions + word hunt + weekly hunts. `[VERIFIED]`
- **Why it works:** extreme session speed (death→retry < 4s), daily/weekly appointment loops, character crew collection, friend leaderboards.
- **Friction:** ad-revive pop-ups interrupt flow. `[INFERENCE]`
- **Lesson taken:** *lane-based readable danger + the fastest possible retry*; live-service seasons.

## 4. Sonic Dash (Hardlight / Sega, 2013)

- iOS Mar 7 2013, Android Nov 26 2013; Unity. `[VERIFIED]`
- **Loop:** lane-runner with **ring banks, dash attacks, springers**; up/down swipes double as attacks on enemies.
- **Why it works:** a known mascot lowers the curiosity gap; "dash into enemies" converts avoidance into aggression — risk-free offense.
- **Lesson taken:** *let the player occasionally attack what usually only threatens them* (empowerment beats).

## 5. Despicable Me: Minion Rush (Gameloft, 2013)

- iOS Jun 13 2013. `[VERIFIED]` Lanes + free-run areas, **underwater sections, competitive minion races, boss battles** (Vector etc.). `[VERIFIED]`
- **Lesson taken:** *mode variety inside one control scheme* keeps a license fresh; but film-license humor carries much of the appeal — not transferable by design.

## 6. Jetpack Joyride (Halfbrick, 2011)

- iOS Sep 1 2011. `[VERIFIED]` 2D physics runner: **hold to rise, release to fall** — one-button physics.
- **Loop:** coins → gadgets (head start, coin magnet...) → missions → vehicle pickups (Profit Bird, Lil' Stomper...).
- **Why it works:** physics input creates *continuous* tension (not discrete swipes); missions gave the genre its first real mid-term goal ladder; a visible "end" of the mission list gave closure. `[VERIFIED]`
- **Lesson taken:** *continuous analog input* (hold/release) feels deeper than discrete taps; mission ladders structure long-term play.

## 7. Alto's Odyssey (Team Alto / Snowman, 2018)

- iOS Feb 21 2018 ($4.99 premium), Android Jul 25 2018 as F2P; Apple Design Award 2018; Unity. `[VERIFIED]`
- **Loop:** physics sandboarding, **wall-riding chains, wind systems, tornado lift, water physics**; no fail-chase — falling short ends the run.
- **Why it works:** *flow-state zen* design, weather as gameplay, biome traversal rules changing mid-run, minimalist onboarding (2 icons).
- **Lesson taken:** *atmosphere and traversal verbs (wall-ride, glide) can replace a chaser as the pressure source*; weather = dynamic level grammar.

## 8. Talking Tom Gold Run (Outfit7, 2016)

- **Loop:** lane-runner + **house-building meta** — collected gold funds a visible home that visibly evolves.
- **Why it works:** kids see *cumulative* progress in a tangible artifact, not just numbers.
- **Lesson taken:** *a persistent, visible meta-artifact* is the strongest retention device in the genre — we adopt it as the core mechanic (our Light Garden), but place it *inside the runs themselves*, not in a separate menu.

## 9. Lara Croft: Relic Run (Simutronics / Square Enix, 2015)

- May 25 2015, Unity; parkour combos, **vehicles, combat, boss fights (T-Rex)**, multiple routes; loading masked by dive-in sequences. `[VERIFIED]`
- **Lesson taken:** *route choice mid-run* (multiple paths) makes the world feel authored; boss set-pieces create shareable memories. Complexity hurt clarity, though. `[INFERENCE]`

## 10. Rayman Adventures (Ubisoft, 2015)

- Search-action hybrids of platforming and exploration; incredible animation craft and level variety.
- **Lesson taken:** *hand-crafted set-piece density* can coexist with an infinite runner's procedural base; tactile animation sells weight. `[INFERENCE]`

## 11. Into the Dead 2 (PikPok, 2017)

- Runner-shooter with **narrative chapters, weapon meta, companions**.
- **Lesson taken:** *light narrative structure* converts a score-chaser into a "journey" for players who don't care about leaderboards. `[INFERENCE]`

## 12. Canabalt (Adam Saltsman, 2009) — the genre's root

- One-button proto-runner; proved the loop RUN→JUMP→FAIL→RETRY needs nothing more than speed and rooftops. `[VERIFIED]`
- **Lesson taken:** the *minimum viable emotional core* is acceleration + rhythm + rooftops-narrow escapes.

---

## Comparative Analysis

| Axis | Best in class | Pattern |
|---|---|---|
| Input model | Jetpack Joyride (analog hold) | Continuous > discrete for depth |
| Readability | Subway Surfers (lanes) | Telegraphed danger, 250–400ms reaction windows |
| Retry speed | Subway Surfers | Death→restart under 4s |
| Mid-term goals | Jetpack Joyride missions | Tiered, finite, visible ladders |
| Meta artifact | Talking Tom Gold Run house | Persistent visible growth |
| Set-pieces | Temple Run 2 carts / Relic Run bosses | 20–40s scripted beats every ~2min |
| Atmosphere | Alto's Odyssey | Weather/light as grammar |
| Narrative | Into the Dead 2 | Chaptered, light |
| Live service | Subway Surfers World Tour | 3–4 week seasons |

**A. Common patterns:** auto-run forward, escalating speed, collectible economy,
quick retry, mission ladders, unlockable characters/skins.
**B. Repeated features:** magnets, multipliers, revive currency, daily rewards.
**C. Differentiators:** physics input (JJ), lean-tilt (TR), lanes+trains (SS),
weather traversal (Alto), bosses (Relic/Minion), meta-building (Tom).
**D. Friction:** forced ads mid-loop, energy systems, pay-gated difficulty, tilt
unreliability, F2P grind walls.
**E. Improvable:** retry speed, honest difficulty (no artificial spikes), fewer
interruptive ads, meaningful choices beyond lane selection.
**F. Underused ideas:** world persistence across runs, player-authored level changes,
light/dark as resource, route consequences that last, photo/exploration modes,
asynchronous social play that isn't just a leaderboard.
**G. Opportunity:** *nobody in the genre makes the world itself remember the player.*
Persistence exists only as base-building menus (Tom) — never inside the playable
world. That is our design gap.

## Ethics note

All design insights above are general principles (loop structure, input models,
retention structures). No deceptive patterns (fake difficulty, dark patterns,
energy pressure) were adopted; Arunika's monetization is cosmetic + expansion
content only. Factual claims carry `[VERIFIED]` tags with public-record sourcing;
gameplay-feel claims are marked `[INFERENCE]`.
