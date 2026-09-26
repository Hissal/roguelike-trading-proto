# Compare switchable presentation scenes

Status: ready-for-human
Type: prototype

Question: Which presentation makes opportunities, uncertainty, exposure, and
card decisions easiest to read during the existing uncertain-market game?

## Delivered primary source

Branch: `codex/presentation-scenes`

Artifact: `presentation-prototype.html` (double-click to play).
Spec and validation: `../spec.md`.

Current round three: A Guild board has a bottom hand; B Command room has a
right-hand column; C Arcane exchange has a top hand. All scenes use dark game
styling, card icons, card-first targeting, and a fixed viewport with secondary
information in modal drawers. The scene switcher preserves the same live state.
The market engine and both earlier presentation sets are preserved.

## Answer

Round one: the creator preferred B's grouped company information and solid
layout, with A's palette also favored. C's bright appearance was uncomfortable.
See `docs/presentation-round-one-feedback.md` for the full findings.

Round two: C's aesthetic and card-first selection were preferred, but extensive
whole-page scrolling made it unplayable. The creator requested a compact third
set with main gameplay on one screen and secondary details in menus.

Round three is ready in `presentation-prototype.html`; C is the initial scene.
Actual visual fit remains unverified. Await human screen-fit and menu feedback.
Rival mechanics remain outside this experiment.

## Comments

September 26, 2026: source parsing and temporary in-memory checks passed for
the full run, accounting, action handlers, and state-preserving scene switches.
Visual/browser verification could not run because the browser tool rejected
the local file URL and explicitly prohibited workarounds. This is a reviewable
prototype, not a visually verified or production-ready UI.

September 26, 2026, follow-up: the requested second set is implemented. Temporary
in-memory checks passed for all scenes through a full run, local trading, card
selection/targeting, reveal expiry, and switch preservation. Visual review remains
unverified under the previously reported browser restriction. Await human
comparison of this new gamification ladder.

September 26, 2026, third pass: rebuilt the page as a fixed viewport with three
hand placements and a shared card-first interaction. Restored icons and added
company/reference drawers. Full-run source/DOM stand-in checks passed. Actual
screen-fit, native modal focus and visual playability remain unverified under
the previously reported browser restriction. Prior round preserved unchanged.
