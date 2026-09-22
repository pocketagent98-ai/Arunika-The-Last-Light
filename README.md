# Arunika: The Last Light — Complete Game Design Project

An original mobile endless-runner, designed from the ground up through structured
research of 12 successful games in the genre — without copying any of them.

## What this repo contains

| File | Content |
|---|---|
| `docs/01_RESEARCH_REPORT.md` | 12 games studied: mechanics, controls, progression, monetization, what works, what to learn |
| `docs/02_GAME_CONCEPTS.md` | 5 original concepts with trade-offs, and the final selection |
| `docs/03_GAME_BIBLE.md` | The complete Game Bible (all 66 sections) for the selected game |
| `docs/04_UIUX_DESIGN.md` | Full screen architecture and per-screen design specification |
| `docs/05_WORLD_AND_ASSETS.md` | 3D world specification, asset list, procedural pipeline |
| `docs/06_TECH_ARCHITECTURE.md` | Godot 4.x technical architecture, roadmaps, testing, performance, risk analysis |

## The one-line pitch

> You are the last Lampbearer. The sun has not risen for a hundred days. Where you
> run, light blooms — permanently. The world remembers every run you ever made,
> and the dark is always behind you.

## Design method

1. Research 12 endless runners (Temple Run, Temple Run 2, Subway Surfers, Sonic Dash,
   Minion Rush, Jetpack Joyride, Alto's Odyssey, Talking Tom Gold Run, Lara Croft:
   Relic Run, Rayman Adventures, Into the Dead 2, Canabalt).
2. Extract *design principles*, never assets, characters or maps.
3. Identify the gaps in the genre (world persistence, meaningful choice, light/dark as a resource).
4. Generate 5 original concepts, select one on originality x depth x feasibility.
5. Write the full Game Bible, UI/UX spec, world spec and technical architecture.
6. Second independent critique pass — weak areas revised (see end of the Bible).

## Verification status

- Design pipeline executed through the companion **Game Factory engine**
  (`GameFactory-Android` repo): **5/5 full pipeline runs passed** (12 tasks,
  15 output files, valid export ZIP each run) plus **26/26 unit tests green**.
- Facts about researched games are marked `[VERIFIED]` (checked against public
  sources such as Wikipedia), `[INFERENCE]` (reasoned from gameplay knowledge) or
  `[UNVERIFIED]` where noted.

## Legal / creative position

All game names and trademarks belong to their owners and are referenced for
research only. Arunika shares no characters, worlds, art, code, audio or names
with any reference game. The originality test from the design brief ("would this
still feel original if all references were removed?") passes — see the critique
section in the Game Bible.
