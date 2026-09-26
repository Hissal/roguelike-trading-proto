# Compare switchable presentation scenes

Status: ready-for-human
Type: prototype

Question: Which presentation makes opportunities, uncertainty, exposure, and
card decisions easiest to read during the existing uncertain-market game?

## Delivered primary source

Branch: `codex/presentation-scenes`

Artifact: `presentation-prototype.html` (double-click to play).
Spec and validation: `../spec.md`.

A is a trading terminal; B is a spatial exposure board; C is a market journal.
The bottom switcher and keyboard arrows cycle through the same live state.
The existing market engine and older playable files are preserved.

## Answer

Round one: the creator preferred B's grouped company information and solid
layout, with A's palette also favored. C's bright appearance was uncomfortable.
See `docs/presentation-round-one-feedback.md` for the full findings.

Round two is ready in `presentation-prototype.html`: A asset dossiers, B company
board, C tactics table. All are dark, group asset information and trading locally,
and show price contributions and without-this-tick's-cards quotes continuously.
The original set remains in `presentation-round-one-prototype.html` and `bf04c5b`.
No round-two winner is selected. Rival mechanics remain outside this experiment.

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
