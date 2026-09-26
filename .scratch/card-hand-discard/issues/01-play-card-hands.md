# Play the bounded card-and-discard experiment

Status: needs-triage
Type: prototype

Question: Do temporary varied hands create worthwhile trading choices and a
meaningful unused card throughout the run?

Spec: `../spec.md`. Playable: `card-hand-prototype.html` on prototype branch
`codex/card-hand-discard`. Prior playable: `trading-prototype.html`, unchanged.

## Answer

Creator playtest: better than before, but predictable all-in concentration made
many cards irrelevant. Suppress created useful preparation for a future entry;
Echo offered little reason to split capital. See `docs/card-hand-playtest.md`.
The authorized follow-up is `.scratch/uncertain-market/spec.md`.

Implementation is complete. Seven powers,
a 14-card deck, three-card hands, up to two plays, and one tick per turn are
available in a portable HTML file. Three optional guided walkthroughs demonstrate
choice, Echo targeting, and effect duration. Verification and limitations are
recorded in `README.md` and the spec. No browser/visual verification is claimed.

## Human checkpoint

Play one complete ordinary run. Report a difficult discard, a plausible
alternative target or combination, whether late turns remained interesting,
and whether earlier effects mattered to later hands. Watch dead Extend/Echo
draws, Suppress's usefulness, and recurring Influence's strength. Stop for this
feedback before adding systems or expanding the experiment.
