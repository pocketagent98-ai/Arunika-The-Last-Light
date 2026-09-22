# Technical Architecture — Godot 4.x

Engine: **Godot 4.x** (no strong reason to deviate — free, mobile-proven,
GDScript + typed, easy headless testing). Target: Android + iOS portrait,
offline-first.

## Scene structure

```
res://
  boot/            Boot.tscn, Splash.tscn
  hub/             Garden.tscn, Smith.tscn, MapScreen.tscn
  run/             Run.tscn (arena root)
  run/player/      Player.tscn
  run/world/       BandRenderer.tscn, PatternLibrary/ (30+ authored patterns)
  run/entities/     Umbral.tscn, Stag.tscn, Spirit.tscn
  shared/          HUD.tscn, Transition.tscn, Settings.tscn
  assets/          meshes/ (from Blender GLTF), materials/, audio/, fonts/
  data/            biomes.json, patterns.json, flora.json, missions.json
```

## Node hierarchy (Run.tscn)

```
Run (RunDirector.gd)
├── WorldRoot (BandRenderer)
│   ├── BandA/B/... (procedural band containers)
│   └── PropPool (pooled obstacles & flora)
├── Player (PlayerController)
├── Camera (CameraRig)
├── UmbralWall (UmbralTide)
├── TrailSystem (GardenTrail)
└── HUD
```

## Core scripts & responsibilities

| Script | Responsibility |
|---|---|
| `run_director.gd` | run lifecycle, seed, speed curve, event bus |
| `player_controller.gd` | input → state machine (ground/air/slide/wall-run/glide/flare) |
| `input_service.gd` | touch decoding (swipe recognizer, hold zones), replay recording |
| `camera_rig.gd` | follow, FOV glide, tide vignette driver |
| `route_generator.gd` | seeded route graph: band chain, forks, pattern slots, set-pieces |
| `garden_trail.gd` | live trail stamping + garden state read/write |
| `garden_store.gd` | persistence: tile stamps (RLE-packed), flora, decay, coverage % |
| `umbral_tide.gd` | chase pressure, Umbral Hour acceleration, stale-route speedup |
| `enemy_director.gd` | wisps, stags spawn/retire (pool-based) |
| `item_director.gd` | lumens, pickups, magnet curves |
| `save_system.gd` | JSON local save + optional cloud, seed-log for restore |
| `ui_manager.gd` | HUD, transitions, pause/results flow |
| `audio_manager.gd` | adaptive music layers, SFX bus, ducking |
| `object_pool.gd` | generic pooling for props/particles/entities |
| `perf_monitor.gd` | frame-time tracker, auto quality stepdown |
| `analytics.gd` | abstraction (no-op local impl; pluggable remote, opt-in) |
| `config.gd` | settings, quality tiers, feature flags |

## Communication

- A single **event bus** (`Events` autoload, typed signals) — no node polls
  another node's internals.
- `route_generator` → `run_director`: "band_ready(band)".
- `garden_trail` → `garden_store`: "stamp(tile, flora)".
- `player_controller` → bus: "died"/"banked"/"flared".
- Cross-cutting (audio, HUD, perf) subscribes to the bus only.

## The persistence layer (the heart of the design)

- World is a grid of 10m tiles per biome band. A trail = list of
  `(band_id, tile_x, flora_type, timestamp)`.
- Stored as **run-length-encoded rows** in JSON, ~50KB per 10km history.
- On generation, `route_generator` asks `garden_store.lit_fraction(band)` and:
  (a) picks fork branches that extend lit threads, (b) hardens obstacle
  patterns on unlit branches (anti-trivialization), (c) applies 5%/week
  bloom decay (never below visible floor).
- Cloud sync = uploading the stamp log only; deterministic replay possible
  from seed + fork log.

## Save format (v1)

```json
{
  "version": 1,
  "profile": {"rank": 3, "wrap": "ghat_runner", "settings": {}},
  "garden": {"bands": {"<band_hash>": {"rows": ["...rle..."], "flora": {}}},
             "coverage": 0.17},
  "run_log": [{"seed": 7231, "forks": [0,1,1], "result": "banked", "m": 1840}],
  "missions": {"active": [], "weekly": {}}
}
```

## Testing strategy (the never-assume-code-works rule)

Every failed test must produce: problem, evidence, root-cause hypothesis,
proposed fix, fix, retest result — logged in `testing/LOGS.md`.

1. **Headless unit tests** (GUT framework, `godot --headless`): route generator
   determinism (same seed + garden ⇒ same route), garden encode/decode
   round-trip, decay math, RLE packing edge cases, mission triggers.
2. **CI loop**: GitHub Actions runs headless test suite on every push —
   public repo, free minutes.
3. **Playtest automation**: scripted input replays (recorded gesture streams)
   run the first 3 minutes of gameplay nightly; asserts: no crash, no
   impossible pattern (verified via a solver bot that *must* be able to
   survive 2 minutes at base speed on generated routes).
4. **Screenshot diffing**: capture 6 canonical frames per biome; fail the build
   on unexpected pixel delta > 5% (catches art regressions).
5. **UX critique checklist** (human, weekly): retry <2s, readability of
   obstacles at 400ms, HUD noise audit.
6. **Performance gates**: nightly 10-min soak on mid-range profile; auto-fail
   if p95 frame time > 18ms or memory grows >2% in 10 minutes.

## Performance strategy

- Quality tiers auto-selected; manual override.
- Object pooling for every repeated entity; no runtime `instance()` in hot loops.
- Logical collision (state machine + authored volumes), zero rigid bodies on player.
- Particle budget enforced by `perf_monitor`; instanced flora beyond 25m.
- Texture atlases per biome; single UMA material per flora family.

## Analytics & privacy

`analytics.gd` is an interface with a local no-op default. Remote analytics is
opt-in only, no PII, no advertising SDKs at all (no ads in the game).

## Development roadmap (16 weeks to soft launch)

1. W1–2: project skeleton, input service, player state machine, grey-box runner.
2. W3–4: route generator + one biome (Ghats), death/retry loop, GUT test rig.
3. W5–6: garden persistence (stamps, RLE, decay), hub garden view.
4. W7–8: Umbral tide, lumens/economy, missions v1; first playtest wave (n=10).
5. W9–10: biomes 2–3, upgrades (Smith), set-piece templates; solver bot.
6. W11–12: audio pass 1, tutorial/onboarding, accessibility settings.
7. W13–14: festivals (async), cloud sync, performance polish, screenshot diffs.
8. W15: soft launch (Android, single country), crash analytics triage.
9. W16: retention patch from data, iOS build, full launch prep.

## Prototype roadmap (first 10 days)

Day 1–2: player + lane movement + jump/slide in grey-box. Day 3–4: speed
curve + death + instant retry. Day 5: lamp light meter. Day 6–7: trail
stamping to disk (the core magic moment — validate this before anything).
Day 8–9: one fork + lit-preview ghosts. Day 10: internal demo decision gate.

## Risk analysis

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Persistence trivializes difficulty | Med | High | unlit-route hardening + 5%/week decay (designed in) |
| Trail data grows unbounded | Low | Med | RLE + compact per-tile records; 10km ≈ 50KB |
| Onboarding too slow vs Subway-class rivals | Med | Med | scripted no-fail first run; gesture cards only after failure |
| Godot mobile perf on 2GB devices | Med | High | logical collision, pooling, LOD plan, auto quality tier |
| Art cost of 5 biomes | High | Med | Blender procedural tilesets; billboards; 3 biomes at soft launch if needed |
| Sunset if garden coverage complete | Low | Low | seasonal re-themes + Dawn Gate finale arc |

## Future expansion

Garden ghost-sharing (visit friends' gardens async), seasonal biome bands,
a creation mode (trail-walking puzzle editor), and the community Dawn Gate
event when enough players' gardens hit 100%.
