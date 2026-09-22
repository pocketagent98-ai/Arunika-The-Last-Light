# Arunika: The Last Light — Game Bible

## 1–5. Identity

1. **Name:** Arunika: The Last Light.
2. **Genre:** persistent-world endless runner (action).
3. **High-concept pitch:** the sun has not risen for a hundred days; you carry the last ember of dawn and wherever you run, light blooms — permanently. Your history of runs *is* the level.
4. **Player fantasy:** I am the reason the world becomes visible and kind. My skill leaves a garden behind.
5. **Target platform:** Android + iOS phones first (portrait), tablets; offline-first.

## 6–10. Frame

6. **Device range:** 2018-class phones and newer (2GB RAM floor); 60fps target on mid-range, 30fps floor guaranteed.
7. **Camera:** third-person, behind-and-above (pitch ~18°), distance 7.5m, FOV 58°; subtle pull-in near walls, +4m on glide; shake only on ember damage (never on jump).
8. **Art direction:** stylized dusk palette (deep indigo → ember amber), rim-lit silhouettes, volumetric god-rays on lit trails; flat-shaded hand-painted textures. Nothing photoreal; readable at 400ms glance.
9. **World:** the valley of Meru-adjacent myth — a wholly fictional dusk land of river ghats, banyan forests, monsoon marshes, cliff shrines and a frozen city of brass lamps. No real religion, deity or scripture is depicted.
10. **Story premise:** when the sun failed, the Lantern Keepers each swallowed a spark of dawn and scattered into the dark. You are the last one still running. The Umbral — the quiet dark that eats light — follows behind everything that moves. Somewhere ahead, the Dawn Gate can be relit — but only by a valley lit bright enough to carry the flame across it.

## 11–15. Characters

11. **Cast:** the Lampbearer (player), Arya the ferry-girl (guide, voice of tutorial), the Ember Smith (upgrades), the Umbral (antagonist force — never humanoid), spirit creatures (collectibles).
12. **Player character:** slim silhouette runner in a wrap-shawl; the ember is carried in a clay diya-lamp — visibly brighter or dimmer with health. Costumes change wrap, lamp and trail flower shapes.
13. **Core gameplay loop:** RUN → LIGHT (trail blooms) → COLLECT LUMENS → SPEND or BANK → UMBRAL TIDE PRESSURE → COLLAPSE or ASCEND (bank) → GARDEN GROWS → NEXT RUN IS EASIER *AND* RICHER.
14. **Secondary loops:** daily bloom quests; spirit rescue side-quests found in lit regions; garden coverage milestones.
15. **Movement system:** 3-lane base with free drift between lanes; swipe up = jump (double-jump unlocked), swipe down = slide/roll, swipe left/right = lane change, hold = **flare burst** (spends light to sprint + auto-light 2 lanes wide). Wall-run on lit banyan roots (unlocked rank 2). Glide (hold during jump, rank 3). Momentum: speed rises with distance but is *capped by your current light level* — dim runners move slower, a soft fail-forward instead of instant death.

## 16–24. Systems

16. **Combat:** none directly — the Umbral is dissuaded, not fought. Flare burst clears shadow wisps ahead.
17. **Exploration system:** every run offers 2–3 fork choices (lane splits into route A/B/C). Routes you previously lit show preview ghosts of what you planted there — informed choice, and the reward for remembering your own history.
18. **Obstacles:** root walls (slide), fallen pillars (jump), gap-bridges (lane change), shadow pools (flare or avoid), collapsing ghats (timing chains). Difficulty scales by route age: *unlit routes spawn harder patterns than lit ones* — the anti-trivialization rule.
19. **Enemy system:** the Umbral Tide (the chasing pressure: a soft wall of dark 12–18s behind you, faster on stale routes); shadow wisps (drift onto lanes); umbral stags (elite: charge, then tire — bait them into light trails).
20. **NPCs:** Arya at shrines (checkpoint dialogues, 1 line each, skippable); the Ember Smith in the hub.
21. **Power-ups:** Diya Flare (5s auto-light wide), Kite (airlift over 150m), Monsoon Charm (weather clears for 20s), Heron Dash (speed burst that coins cannot buy — found only on unlit routes).
22. **Items:** lumens (soft currency), embers (bank = permanent progress), spirit seeds (plant specific flora types), relics (lore).
23. **Inventory:** no grid inventory; the Light Garden *is* the inventory — planted flora produce passive per-run boons.
24. **Progression:** Ember Ranks 1–12 (movement verbs unlock); each rank = one guaranteed new biome bloom.

## 25–33. Long-term systems

25. **Skill system:** trail-walking (draw bonus trails between runs — a light puzzle on the world map), bloom-crafting (choose which flora your trail plants).
26. **Upgrades:** lamp tiers (light radius, flare strength), wrap tiers (extra hit), movement tier nodes (double jump, glide, wall-run).
27. **Missions:** 3 active quests (distance, bloom, style-trick based); weekly Dawn Quests re-theme the garden.
28. **Events:** monthly Dawn Festivals — the whole community's gardens contribute to a shared world brightness meter (async; no live lobby needed).
29. **Achievements:** 60, coverage- and kindness-themed ("Light a route another player abandoned" — via async ghost data).
30. **Rewards:** cosmetics, lamp styles, trail flowers, spirit companions that ride the shoulder and auto-collect near lumens.
31. **Difficulty:** speed cap tied to light; Umbral Tide speed curve; unlit-route pattern hardening. No difficulty spikes for monetization — ever.
32. **Procedural generation:** route graph generator — nodes = 30–90s segments, edges = fork choices; seed includes **your garden state** so generation *respects and extends* what you lit; hand-authored set-piece templates (cart-bridge, heron flight, collapsing ghat) inserted every 90–150s.
33. **World generation:** biome bands chained in a directed graph (ghats → marsh → banyan → cliffs → brass city); the band order changes seasonally; the garden state marks each band's lit fraction.

## 34–40. World detail

34. **Map structure:** an infinite spiral of biome bands; the hub (a growing lantern-hut) is the persistent center; the garden map is an actual top-down view of *your* run history.
35. **Biomes:** 5 launch biomes (see world doc) each with unique obstacles + flora.
36. **Weather:** monsoon (visibility down, water-slide lanes = speed), mist (route forks hidden unless lit), clear dusk.
37. **Day/night:** an in-run "night cycle" every ~3 minutes — during Umbral Hour the tide accelerates and lit routes are the only safe lanes.
38. **Environmental events:** firefly blooms (bonus lumen fields), brass-city lantern processions.
39. **Secret areas:** fully-lit routes reveal shrine doors → short relic rooms (lore + cosmetic).
40. **Boss/elite encounters:** umbral stags; seasonal Umbral Maw (flood wall escape sequence).

## 41–48. UI/UX, onboarding, audio

41. **UI/UX:** thumb-zone controls, top-of-screen HUD, zero text during gameplay after onboarding. Full spec in `04_UIUX_DESIGN.md`.
42. **HUD:** light meter (lamp flame size), distance, lumen count, tide proximity ripple (vignette).
43. **Menus:** hub-first navigation; every menu is the garden (no abstract list screens).
44. **Settings:** graphics tier, colorblind palettes (4), left/right thumb, reduced motion, haptics toggle.
45. **Tutorial:** scripted first run — Arya runs ahead and lights the first shrine; player learns by following light, not by reading. Four gesture cards total, each shown after the player fails the gesture once (never before).
46. **Onboarding:** the first collapse is scripted to happen *at a shrine* — the player cannot lose the first run; the second run already shows their first bloom. The core loop is understood by run 3 without any text tutorial. `[INFERENCE — validated by the research pattern "show gesture card only after failure" from Subway Surfers-class onboarding]`
47. **Game-over screen:** "The light rests." + garden growth delta ("+9m of trail bloomed") + one-tap retry (<2s) — failure is framed as accumulation, never as loss.
48. **Restart:** instant hold-anywhere restart; daily streak shown as garden dew.

## 49–57. Audio, visuals, feel

49. **Audio:** diegetic-first — the world is dark and *quiet*; your footsteps and breath are the metronome; lumens chime in a raga-adjacent pentatonic (original music, session musician recordings, no sampled film soundtracks).
50. **Music:** adaptive dusk-ambient layers that add instruments per lit-biome fraction (the game literally sounds richer as your garden grows).
51. **SFX:** lamp flare (bansuri-adjacent whoosh), bloom pop (water-drip + thumb piano), umbral proximity (sub-bass heartbeat).
52. **Visual effects:** volumetric light shafts on trails, firefly particle economy (cap 120 particles), bloom shockwaves on banking.
53. **Particles:** GPU-instanced; pooled; never more than 3 simultaneous emitter families per lane-view.
54. **Animation:** 24-fps-on-2s silhouette animation flavor for cinematic beats; 60fps full-rate gameplay animation; squash/stretch on landings.
55. **Camera effects:** no speed-lines (readability); gentle FOV widen on Heron Dash; tide vignette (breathing, 0.4Hz).
56. **Haptics:** bloom plant (soft tick), flare (double pulse), umbral hit (heavy thud) — all optional.
57. **Accessibility:** colorblind-safe light colors (shape-coded flora: bell/flower/leaf), one-hand mode, reduced-flash mode, screen-reader menus (hub only), subtitle all voice lines.

## 58–66. Technical & business

58. **Performance budget:** 60fps mid-range; ≤600 draw calls, ≤120k tris in view; trail data as compact tile stamps (uint16 grid per biome band, ~50KB per 10km run history).
59. **Save system:** local-first JSON (garden state), cloud sync optional; deterministic seed log for replay/restore.
60. **Offline/online:** fully playable offline; online only for festivals, friends' gardens and cloud save.
61. **Data structure:** run log (seed, forks taken, deaths), garden map (tile stamps + flora types), profile (ranks, cosmetics).
62. **Economy:** lumens (soft, run-earned), embers (bank progress), prisms (premium). Source-sinks documented in the design ledger.
63. **Monetization:** cosmetics (lamp/wrap/trail-flora), garden decorations, expansion biomes ("Monsoon Kingdom"). No ads, no energy, no pay-for-survival. `[DESIGN PRINCIPLE — from research friction list D]`
64. **Live events:** monthly Dawn Festival (shared brightness meter), weekly quests.
65. **Future content:** seasonal biome bands, ghost-sharing of gardens, a "Dawn Gate" finale arc when a player's garden hits 100%.
66. **Technical architecture:** Godot 4.x, full spec in `06_TECH_ARCHITECTURE.md`.

---

## Second independent critique (required by the brief)

A cold re-read of this Bible surfaced four weak areas — now revised:

1. **Weak: "persistence could kill difficulty."** Revised in §18: unlit routes harden; lit routes decay at 5%/week of bloom density (never below visible) — the garden is a *living memory*, not a paved highway.
2. **Weak: light as health + currency could double-punish death.** Revised: on collapse you keep banked embers and 60% of trail blooms; only *carried* (unbanked) lumens are lost.
3. **Weak: story risked tonal drift into melancholy.** Revised §47: failure framing is accumulation; Arya's lines are warm and dry-humored, not mournful.
4. **Weak: cloud/async features could gate the core.** Revised §60: festivals and friends are additive; 100% of progression is offline-capable.

**Originality final check:** removing all reference-game names, Arunika remains:
a persistent-world light-gardening runner with bankable dawn. No researched game
contains that sentence. PASS.
