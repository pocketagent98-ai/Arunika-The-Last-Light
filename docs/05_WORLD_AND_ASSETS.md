# 3D World Specification & Asset Pipeline

## World scale & structure

The world is a ribbon of biome bands, each 60–120s of running distance
(~900–1800m at base speed 15 m/s), connected through fork choices. Player
corridor: 3 lanes × 1.1m = 3.3m wide path, 3m headroom. Verticality: ghat steps
(+/-4m), banyan canopy layer (+9m, wall-run), marsh dives (−2m, slide chains).

## Biomes (launch set)

1. **River Ghats** — stone steps, fallen pillars, oil-lamp posts; obstacles:
   step gaps (jump), pillar weaves (lane), collapsing step chains (timing).
2. **Monsoon Marsh** — water slides (speed lanes), reed walls (slide), rain
   sheets reducing visibility; flora: reed-bells (sound chimes).
3. **Banyan Reach** — canopy wall-runs on lit roots, hanging vine swings,
   root walls; flora: hanging lantern-flowers.
4. **Cliff Shrines** — narrow ledge lanes, wind gusts, bell puzzles; flora:
   cliff moss that marks safe ledges.
5. **Brass City** — frozen festival city; lantern processions, mechanical
   gates, brass floors that reflect lit trails (showcase biome).

## Per-biome content budget

Per 1km band: 8–12 obstacle patterns (from a 30-pattern authored pool per
biome), 2–3 forks, 1 set-piece slot, 40–70 flora stamp points, 1 shrine
(banking checkpoint) every ~90s.

## Lighting & atmosphere

- Single dominant directional "dusk" light (deep indigo); player lamp = real
  point light (radius scales with light resource); each planted bloom adds an
  emissive decal + cheap fake light (bloom material emission, no per-flower
  point lights).
- Fog: exponential height fog, color blends with garden lit-fraction (the
  further your garden has grown, the warmer the fog gets).
- Sky: two-layer gradient dome + parallax dusk clouds; no dynamic sky sim.

## Weather system

Three states per band (clear dusk, mist, monsoon) chosen by seed + season;
monsoon adds water-slide lanes + 15% speed; mist hides forks unless the
route is lit (a garden privilege).

## Asset list (major)

| Asset | Purpose | Dim (m) | Geo complexity | Materials | Anim | Collision | LODs |
|---|---|---|---|---|---|---|---|
| Lampbearer | player | 1.7 H | 4.5k tris | 3 (wrap, skin, lamp) | 28 clips | capsule | 2 |
| Arya | guide NPC | 1.6 H | 3k tris | 2 | 10 clips | none | 2 |
| Umbral wall | antagonist | n/a ribbon | shader plane | 1 (dissolve) | shader | kill zone | 1 |
| Umbral stag | elite | 1.9 H | 5k tris | 2 | 6 clips | box | 2 |
| Ghat tileset | biome 1 | 12m modules | 300–800 tris/pc | 2 | — | box | 2 |
| Pillar (3 variants) | obstacle | 2.5 H | 400 tris | 1 | — | box | 1 |
| Banyan root arch | biome 3 | 9 W | 1.2k tris | 2 | sway (shader) | box | 2 |
| Lantern-flower | flora ×6 | 0.4 | 120 tris | 1 emissive | bloom | none | 1 (billboard) |
| Shrine (bank point) | checkpoint | 4 H | 2k tris | 3 | ignite | trigger | 2 |
| Diya lamp prop | hub/upgrades | 0.3 | 200 tris | 1 emissive | flame | none | 1 |
| Spirit companions (×5) | shoulder pets | 0.2 | 250 tris | 1 | idle bob | none | 1 |

## Procedural generation plan (assets)

- All modular tilesets are generated in **Blender 4.x with Python scripts**
  (bpy) from parameter dictionaries (step height, pillar girth, root curvature)
  → guarantees uniform pivots, consistent scale, and auto-exports GLTF with
  LOD meshes decimated by ratio (50% / 20%).
- Flora: generated via Blender geometry-nodes presets (6 archetypes), baked
  to billboard-friendly meshes with emissive masks.
- The generator scripts live in `tools/blender/` in the future code repo;
  every asset carries a `meta.json` (tri count, LOD ratios, material slots)
  checked by the asset validator in CI.

## LOD & performance strategy

- LOD1 at 60% tri, LOD2 at 20%; billboards for flora beyond 25m.
- Occlusion: band-to-band doors let us cull everything behind the Umbral wall.
- Draw budget: ≤600 calls, ≤120k visible tris; particle cap 120 GPU-instanced.
- Texture budget: one 2k atlas per biome + one shared emissive atlas.

## Collision strategy

Gameplay collision is **logical lanes + height states**, not physics: the runner
is a state machine (ground/air/slide/wall-run/glide) checked against authored
collision volumes per pattern. No rigid-body physics on the player — physics
is only cosmetic (cloth, debris).

## Interactive objects

Lumens (magnet-curve toward player within 1.5m), shrine doors (lit-route
secrets), heron perches (Heron Dash pickup), processions (moving safe zones
in Brass City).

## Destruction

Collapsible ghats are pre-fractured clusters animated on trigger (no runtime
voronoi) — 5 pieces, 0.6s fall, never in the player's exact lane at fail time.
