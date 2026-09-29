# Full-run prototype

Label: wayfinder:map

## Destination

A buildable spec (`.scratch/full-run/spec.md`) for the next playable: a full
one-year run whose start is very simple and which grows exponentially. It
specifies the whole-year skeleton (four quarters of three months, each quarter
ending in a boss, then optional endless play) with Quarter 1 and its boss in full
detail. Quarters 2–4 reuse the Manipulator as a placeholder boss. Design-log and
`CONTEXT.md` updates land as decisions settle. Building the spec is done after
this map, not inside it.

## Notes

- Domain: the rogue-market trading roguelike. Read `CONTEXT.md` and
  `docs/design-log.md` (rev 6) first; label design-log entries with its
  conventions (CONFIRMED, WORKING DIRECTION, EXPERIMENT, …).
- Problem being solved: information overload and constant analysis paralysis
  in `card-design-prototype.html`, made worse by starting in the deep end.
- Goals: most decisions easy, with occasional big tough ones; low constant
  pressure; big numbers and dopamine (going red is exceptional, usually
  deliberate) without every stock simply rising; unconfusing presentation;
  clear feedback on what happened; a clear game identity.
- Everything is open, including design-log CONFIRMED entries: "basic buying and
  selling never require an action card", turn-based over real time, and prices
  tending toward real value. A ticket's conclusion supersedes the log entry;
  mark the old entry superseded.
- Gameplay is decided by playing, not on paper. Prefer `prototype` tickets for
  anything about feel; use the `prototype` skill. Grill only where a real
  choice can be made without play.
- Perceived value is an idea under test. The glossary defines the term, but
  whether the market uses it (versus price following real value directly) is
  decided by prototype.
- Core identity is undecided between "hype vs truth" (stock-leaning) and "card
  engine multiplying gains" (game-leaning); the creator leans towards the
  latter but keeps both open.
- One starting class (likely Insider) in the spec.
- No course or deadline constraints.

## Decisions so far

<!-- one line per resolved ticket: [title](issues/NN-slug.md): gist -->

- [Research price-motion models for a wavy, readable market](issues/01-price-motion-models.md): real value drifts with health; price = real value × damped mean-reverting fad (momentum then overshoot); reports reveal value and close the gap over a few ticks.
- [Research what real quarterly reports and market news contain](issues/02-reports-and-news.md): reports reveal real value and prices react to beat/miss vs expectations, then drift; news moves perceived value (mood fades, fundamental shows in the next report); five-field report card and sector-impact news formats.
- [Research how deckbuilder roguelikes keep early decisions simple and ramp up](issues/03-roguelike-ramp.md): ordinary turns have one obvious question, hard choices live between encounters; mostly-common offers; boss shown upfront; targets grow ~×2.5 then flatten, and the overshoot from a multiplicative build is the dopamine.

## Not yet specified

- **Run economy and pressure**: starting capital, the exponential curve, what
  winning a month means (profit target? survival?), loss conditions, and how
  going red becomes rare without prices only rising.
- **Unlock pacing**: two stocks in Quarter 1 and when more stocks, cards and
  mechanics appear; how depth grows over the run.
- **Upgrades between months/weeks**: shop, drafts or guaranteed picks in the new
  structure.
- **Manipulator across a quarter**: asleep in month 1, waking with the player's
  wealth in month 2, the fight in month 3; the boss snowball; what beating it
  means; how the placeholder repeats for Quarters 2–4.
- **Easy decisions by design**: hand size, Focus, card count per turn, and how
  the UI makes likely-good moves visible at a glance.
- **Feedback and sequencing**: how events play out step by step (animation,
  event log, before/after deltas) instead of resolving in an instant.
- **Starting deck** for the starting class in the new structure.
- **Identity presentation**: name, theme (occult?), and how the chosen core
  shows on screen.
- **Endless-mode hook**: what continues after the fourth boss.

## Out of scope

- Final art and audio.
- New bosses for Quarters 2–4 (they reuse the Manipulator).
- Classes beyond the one starting class.
- A separate tutorial or onboarding flow (the simple Quarter 1 is the
  onboarding).
- Endless-mode tuning beyond "the run can continue".
- Meta-progression between runs.
- Monetisation.
