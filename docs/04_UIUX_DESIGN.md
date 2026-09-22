# UI/UX Specification — Screen Architecture

Design rules: one-thumb portrait play; no text during gameplay after onboarding;
every menu is the garden (the persistent world doubles as the UI); every screen
specifies purpose, layout, hierarchy, states and accessibility.

## Flow

SPLASH → LOADING → (first run: ONBOARDING) → HUB (the Garden) → PLAY → PAUSE /
GAME OVER → RESULTS → upgrades & collection screens → back to HUB.

---

## 1. SPLASH
Purpose: brand + engine warm. Layout: black field, one ember dot that blooms into
the logo (2.2s, skippable after 1s). Loading state: none needed (async behind).
Accessibility: reduced-flash mode swaps bloom to crossfade.

## 2. LOADING
Purpose: garden hydration. Layout: progress shown as *trail lighting up on the
world map* (real data). Hierarchy: map > progress % > tip card (1 per load, from
a pool of 30). Error state: offline notice (game continues offline).

## 3. ONBOARDING (first run only — 90 seconds)
Purpose: teach by following light, not text. Arya (guide) runs ahead lighting
shrines; the player's thumb learns swipe-up/down/left/right through the "gesture
card after first failure" pattern (4 cards max, all optional). The run ends at a
scripted shrine — no fail state. One-handed from the first frame; left/right
thumb mirror offered on card 2.

## 4. HUB — The Garden (main menu)
Purpose: home, identity, progress-as-place. Layout: full-screen top-down view of
the player's actual lit world; camera orbits with drag. Hierarchy: (1) the garden
itself, (2) bottom dock (Play, Missions, Smith, Spirits, Shop), (3) top-right
profile. Buttons: 56dp minimum, thumb-reach bottom third. Navigation: dock +
context pin icons on blooms. Typography: 1 display face (custom, hand-drawn),
1 UI face (system). Spacing: 8dp grid. Color: dusk-indigo field, ember-amber
accents only on interactive elements. Iconography: line icons, 2px stroke.
Animation: blooms sway (idle, 0.2Hz). Feedback: press = soft haptic + 4% scale.
Empty state: a single glowing sprout and Arya's first line. Error state: cloud
sync badge only. Loading state: garden builds up tile-by-tile (<1.5s typical).
Accessibility: dock supports screen reader; garden pins are labeled.

## 5. PLAY (gameplay)
Purpose: the run. Layout: HUD top strip (light meter center, distance left,
lumens right); tide ripple = vignette bottom edge. Zero interactive chrome —
whole screen is input. Typography: 12sp numerals, 100ms count-up animations.
Feedback: bloom ticks (haptic optional), lamp flame size = light (no number
bars during play). Color system: interactive/danger shapes differ in geometry,
not color alone (colorblind-safe).

## 6. PAUSE
Purpose: breath + options. Layout: centered card (Resume / Restart / Settings /
Quit to Garden), garden coverage micro-map behind. All buttons 56dp. Error
state: none. Empty: none.

## 7. GAME OVER — "The light rests."
Purpose: frame failure as accumulation. Layout: (1) big line "The light rests.",
(2) growth delta panel — "+9 m trail bloomed · +140 lumens · +1 shrine",
(3) Retry (hold-anywhere, <2s), (4) Return to Garden. The delta panel always
leads — even a bad run *grew* something. Loading: instant (no ads, ever).

## 8. RESULTS → BANK (ascension)
When the player reaches a shrine instead of collapsing: the bank animation —
carried lumens pour into the garden as light; coverage % counts up; any new
biome band unlocking gets a 3s cinematic. Skippable.

## 9. UPGRADES — The Ember Smith
Purpose: spend lumens on lamp/wrap/movement tiers. Layout: the Smith's lantern
hut interior, upgrade tree as a literal hanging-lamp mobile; each lamp node =
1 upgrade, lit when affordable. Hierarchy: tree > cost chip > detail drawer.
Empty state: "The Smith waits for your first embers." Error: insufficient funds
grey + one-line earn hint (never a shop push).

## 10. CHARACTERS & COSTUMES
Purpose: identity. Layout: horizontal carousel of Lampbearer wraps; each
preview live-rotates. Buttons: equip = double-tap. Feedback: trail flower
preview strip under each wrap.

## 11. SPIRITS (companions) — inventory
Purpose: collection + per-run boons. Layout: shelf of resting spirits (each a
little lantern niche), tap to see boon, equip one. Empty state: "A lantern
waits for its spirit."

## 12. MISSIONS
Purpose: mid-term goals (3 active + weekly). Layout: three papyrus-strip cards;
progress bars 8dp. Feedback: completion = bloom burst animation on the card.
Error/empty: none possible (always 3 active).

## 13. MAP (garden overview)
Purpose: see your whole history + route planning. Layout: zoomable world map,
pinch/drag; lit fraction per biome band; fork routes the generator *will* offer
next run shown as ghost threads (this is the trail-walking planning screen).
Accessibility: 200% zoom for low vision.

## 14. EVENTS (Dawn Festivals)
Purpose: shared async community goal. Layout: one banner screen: community
brightness meter, your contribution, seasonal cosmetic. Offline state: "The
festival continues when you return."

## 15. SETTINGS
Purpose: comfort + control. Layout: grouped list (Graphics tier auto/low/med/high,
Colorblind palettes ×4, Left/Right thumb, Reduced motion, Reduced flash,
Haptics, Music/SFX sliders, Cloud sync, Delete-save with double-confirm).
All changes apply instantly with live preview.

## 16. PROFILE
Purpose: identity + stats. Layout: wrap portrait, runner stats (distance, blooms
planted, shrines lit, kindness stat: routes lit that others abandoned), rank
flame. Sign-in optional, only affects cloud + festivals.

---

## Ergonomics & production feel

- All primary actions in bottom 40% thumb arc; gameplay input = whole screen.
- 8dp spacing grid, 56dp touch targets, 12sp min body, WCAG AA contrast on dusk palette.
- Motion: nothing blocks input for more than 150ms; every transition is
  interruptible; retry is always <2s.
- The UI must feel hand-crafted (papyrus, clay, brass, cloth) — no default
  "mobile-game template" chrome. Fonts, borders and buttons are custom.
