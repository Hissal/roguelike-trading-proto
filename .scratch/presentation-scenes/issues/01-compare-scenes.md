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

Implementation is ready for comparison; the design question is not yet settled.
No winner has been selected. A is the initial scene only. The human can select
a scene or combine information hierarchy and interactions from different scenes.
Rival mechanics remain outside this experiment.

## Comments

September 26, 2026: source parsing and temporary in-memory checks passed for
the full run, accounting, action handlers, and state-preserving scene switches.
Visual/browser verification could not run because the browser tool rejected
the local file URL and explicitly prohibited workarounds. This is a reviewable
prototype, not a visually verified or production-ready UI.
