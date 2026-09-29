# Research price-motion models for a wavy, readable market

Status: resolved
Type: research

## Question

What simple stochastic models give prices a wavy, randomised motion biased toward a target value (e.g. mean-reverting noise, momentum and overreaction, post-announcement drift), and how could real value drift gradually with company health rather than jumping at reports? Which are cheap to implement and tune in a browser game, and what parameters control readability?

## Answer

Findings: branch `research/price-motion-models`, file
`docs/research/price-motion-models.md`.

Summers (1986) splits log price into fundamental value plus a mean-reverting
AR(1) "fad", which matches real value and perceived value. The recommendation
has three layers:

- Real value drifts with a slow company-health process (an OU process or a
  Markov regime), with rare jumps for big events.
- Perceived value is real value × exp(damped fad): `v = φv − κu + σn; u += v`,
  starting at φ≈0.6 and κ≈0.25. One news kick runs up for 2–4 ticks, overshoots
  and pulls back (momentum, then overreaction).
- A report reveals real value and closes about 40% of the gap that day. The rest
  drifts, as in post-earnings drift.

Tunable knobs: half-life and wobble size. Profit comes from knowing the gap, not
from prices rising. Cards and boss moves should push the fad's velocity instead
of setting the price.
