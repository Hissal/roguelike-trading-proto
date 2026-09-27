# Compare switchable presentation scenes

Status: ready-for-human
Type: prototype

Question: Which presentation makes opportunities, uncertainty, exposure, and
card decisions easiest to read during the existing uncertain-market game?

## Delivered primary source

Branch: `codex/presentation-scenes`

Artifact: `presentation-prototype.html` (double-click to play).
Spec and validation: `../spec.md`.

Current round four: A Exposure ledger, B Price story, C Position instruments.
Only company-card presentation varies. The green theme, bottom hand, bottom-right
End Turn and card-first targeting are shared. Exposure bars and explicit held
shares highlight open positions. Secondary information remains in drawers.
The engine and all three earlier presentation sets are preserved.

## Answer

Round one: the creator preferred B's grouped company information and solid
layout, with A's palette also favored. C's bright appearance was uncomfortable.
See `docs/presentation-round-one-feedback.md` for the full findings.

Round two: C's aesthetic and card-first selection were preferred, but extensive
whole-page scrolling made it unplayable. The creator requested a compact third
set with main gameplay on one screen and secondary details in menus.

Round three: the creator confirmed the fixed-screen experience was much nicer.
Default sizing was too small; exposure needed stronger emphasis. The creator
requested a shared green shell and three company-card presentation experiments,
and explicitly asked to keep the current copy available.

Round four is ready in `presentation-prototype.html`; A is the initial comparison.
The old copy remains in `presentation-round-three-prototype.html`. Await human
100%-zoom and company-card comparison feedback. No round-four winner is selected.
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

September 27, 2026: implemented the shared green board with responsive scaling,
bottom hand and bottom-right End Turn; three new company-card designs combine
exact values with exposure and price-impact graphics. Added Sell All through
the existing sale action. Full-run in-memory checks passed; visual sizing on
the creator's monitors remains unverified. Round three preserved byte-for-byte.
