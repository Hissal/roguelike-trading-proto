# Compare switchable presentation scenes

Status: resolved
Type: prototype

Question: Which presentation makes opportunities, uncertainty, exposure, and
card decisions easiest to read during the existing uncertain-market game?

## Delivered primary source

Branch: `codex/presentation-scenes`

Artifact: `presentation-prototype.html` (double-click to play).
Spec and validation: `../spec.md`.

Current round five: A Position bar, B Compact holdings, C Side dial. All use
annotated charts at the top, contribution bars below, and holdings adjacent to
trading. The green theme, bottom hand, bottom-right End Turn and card-first
targeting are shared. Secondary information remains in drawers. The engine
and all earlier presentation sets are preserved.

## Answer

**Final decision, September 27, 2026: scene C / Side dial is the winner.**
The creator explicitly accepted the final presentation and requested session
conclusion. Accepted playable: `presentation-prototype.html` at `6532402`.
Session findings and handoff: `docs/presentation-session-summary.md`.
The presentation question is resolved; historical feedback below documents the
path to that choice. Rival rules and implementation remain separate work.

Latest follow-up: creator says the presentation is great overall and C's radial
exposure works best. Set C as default, removed hand guidance/discard names/cancel
button and empty power text. Selected-hand overflow is addressed with bounded
grid sizing and selection styling that does not change border thickness. Actual
browser sizing still needs human confirmation; no new mechanics were added.

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

Round four: the creator confirmed improved fit, preferred B's graph annotations
and contribution bars, and requested tighter holdings/trading grouping and less
duplicate text. Round five is ready in `presentation-prototype.html`, with B as
the initial scene. Prior copies remain available. Await refinement feedback;
rival mechanics remain outside this experiment.

## Comments

September 27, 2026, conclusion: creator said “I think this is good now. scene C
with the radial dial is the winner.” Recorded the accepted baseline, five rounds
of experiments, discoveries, archive inventory and remaining verification limits.
No further gameplay changes were made during the documentation wrap-up.

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

September 27, 2026: applied the round-four feedback, including a protected graph
height, unified graph annotations, contribution totals, compact holdings near
execution, single exposure encoding per card, nearby archive buttons, and
simplified End Turn. Full-run source/DOM checks passed; visual review remains
unverified. Round four preserved unchanged.
