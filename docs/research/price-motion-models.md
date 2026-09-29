# Price-motion models for a wavy market

Research note, 2026-09-29. Question: which simple stochastic models give prices
a wavy, randomised motion biased toward a target, how can **real value** drift
with company health instead of jumping at reports, and which are cheap to
implement and tune in a browser game?

Vocabulary follows `CONTEXT.md`: **real value** (hidden worth per share),
**perceived value** (what investors believe; pushed by news and momentum,
pulled back by reports), and the price follows perceived value.

## TL;DR

- The finance literature already has the exact architecture the design wants:
  Summers (1986) models the log price as **fundamental value plus a
  mean-reverting "fad"**, `p = p* + u`, with `u` a first-order autoregressive
  (AR(1)) process. In game terms: price = real value + a zero-mean,
  self-correcting mispricing. That is the recommended backbone.
- The AR(1) fad is the discrete-time **Ornstein–Uhlenbeck (OU)** process. It is
  one line of code per tick, and its two knobs map to player-readable ideas:
  **half-life** (how fast a gap closes) and **wobble size** (how noisy the path
  is).
- **Hype then pullback** falls out of adding one momentum term (a "velocity"
  on the fad). It turns the AR(1) into a damped oscillator: news kicks the
  price, the price keeps rising for 2–4 ticks, then falls back and slightly
  undershoots. This matches the underreaction-then-overreaction pattern in
  Hong & Stein (1999) and Barberis, Shleifer & Vishny (1998).
- **Post-earnings-announcement drift (PEAD)**: a report should *reveal* real
  value, and perceived value should close the gap **over several ticks**, not
  jump. Ball & Brown (1968) and Bernard & Thomas (1989) document this drift.
- **Real value** should drift continuously with a hidden **health** variable.
  Health is either a slow OU process or a two- or three-state Markov regime
  (Hamilton 1989). Reports then show where value already went, instead of
  moving it.
- To keep the player mostly profitable without every stock rising: keep the
  fad zero-mean, give the **health** mix both signs, and let profit come from
  *knowing the gap*, not from drift. Summers' model predicts negative serial
  correlation in returns, meaning the gap is predictable to anyone who knows
  `p*`. The Informed and insider cards already sell that knowledge.

## Where the prototype is now

In `card-design-prototype.html`, each tick applies roughly
`rawMarket = 0.12*(value - price) + pressure + noise + shock`. Here `noise` is
a deterministic sawtooth (`((step*17 + i*11) % 13 - 6) * 0.12`), and `shock`
is a report jump. The `0.12*gap` term is already the deterministic half of a
discrete OU step. Its half-life is `ln 0.5 / ln 0.88 ≈ 5.4` ticks (computed).
The missing pieces are true random noise with a memory (so the motion looks
wavy rather than jittery), momentum, gradual report absorption, and a moving
real value.

## 1. Mean-reverting noise: Ornstein–Uhlenbeck / AR(1)

**Source.** The OU process comes from Uhlenbeck & Ornstein (1930), a model of
Brownian-particle velocity: `dX = -θ X dt + σ dW`. Gillespie (1996) gives an
update that is *exact* for any time step Δt, not just an approximation:
`X(t+Δt) = μ·X(t) + σ_X·n`, where `μ = exp(-Δt/τ)`,
`σ_X² = (cτ/2)(1 − μ²)`, and `n` is a standard normal draw. Summers (1986)
uses the same process, as `u_t = a·u_{t−1} + v_t` with `0 < a < 1`, for the
gap between price and fundamentals. Deviations "tend to persist but not grow
forever".

**Game form.** Treat the fad `u` (the perceived-minus-real gap, in log or
percent terms) as an AR(1):

```js
// Per company state: u = fad (perceived − real, as a fraction of real value)
const a = Math.pow(0.5, 1 / HALF_LIFE);   // HALF_LIFE in ticks, e.g. 4
const s = WOBBLE * Math.sqrt(1 - a * a);  // WOBBLE = typical |u|, e.g. 0.06
function stepFad(c, rng) {
  c.u = a * c.u + s * gauss(rng);
  c.perceived = c.real * Math.exp(c.u);   // log-space keeps prices > 0
  c.price = c.perceived;                  // plus card/boss effects
}
```

`gauss` is Box–Muller: `sqrt(-2 ln U1) · cos(2π U2)` (Box & Muller 1958). Use a
seeded PRNG (for example mulberry32) so a run can be replayed.

**Why it reads well.** With `a = 0.5^(1/h)`, `h` is literally "ticks for a gap
to halve". Scaling the noise by `sqrt(1 − a²)` makes `WOBBLE` the stationary
standard deviation, because the AR(1) variance is `s²/(1 − a²)`. So the two
sliders are independent: one sets speed and one sets size. Because the noise
carries memory, the path wanders in smooth-ish swells rather than
tick-to-tick jitter. A larger `h` gives longer, lazier waves.

**Hype then pullback.** A news event adds a one-off kick, `c.u += HYPE`. The
fad then decays geometrically toward 0. That is only *half* of the shape: the
jump is instant and the price never keeps rising after the news. For the full
shape, see §2.

**Cost.** One multiply, one Gaussian draw per company per tick.

## 2. Momentum and overreaction: a damped fad

**Sources.**
- Jegadeesh & Titman (1993) find that past winners keep outperforming over
  3–12 months (momentum).
- De Bondt & Thaler (1985) find that extreme past winners underperform over
  3–5 years (overreaction, then reversal).
- Cutler, Poterba & Summers (1990) model "feedback traders" whose demand
  depends on past returns. This produces positive short-horizon and negative
  long-horizon autocorrelation.
- Hong & Stein (1999): news diffuses slowly (underreaction), trend-chasers
  exploit it, and "their attempts at arbitrage must inevitably lead to
  overreaction at long horizons".
- Barberis, Shleifer & Vishny (1998) produce both underreaction (conservatism)
  and overreaction (representativeness) in one belief model.

**Game form.** Give the fad a velocity `v`: momentum carries it on, and the
pull toward real value bends it back. This is a discrete damped oscillator,
equivalent to an AR(2) model:
`u_{t+1} = (1+φ−κ)·u_t − φ·u_{t−1} + noise`.

```js
// φ = momentum carry (0..1), κ = pull toward real value (0..~0.5)
function stepFad(c, rng) {
  c.v = PHI * c.v - KAPPA * c.u + SIGMA * gauss(rng);
  c.u = c.u + c.v;
  c.perceived = c.real * Math.exp(c.u);
}
function hype(c, size) { c.v += size; }   // news pushes velocity, not level
```

**Hype then pullback, measured.** Impulse response to `v += 1` from rest
(computed in a scratch simulation):

| φ (momentum) | κ (pull) | Peak | Peak tick | Undershoot | Trough tick |
|---|---|---|---|---|---|
| 0.5 | 0.35 | 1.15 | 2 | −0.20 | 7 |
| 0.6 | 0.25 | 1.35 | 2 | −0.28 | 8 |
| 0.7 | 0.15 | 1.70 | 3 | −0.40 | 11 |
| 0.8 | 0.10 | 2.19 | 4 | −0.72 | 14 |

So a single "rumour" card produces a rise over several ticks, a peak, a fall
back past real value, then settling. This is the momentum-then-reversal
pattern. Stability requires `0 ≤ φ < 1` and `0 < κ < 2(1+φ)`. The motion
oscillates (overshoots) when `(1+φ−κ)² < 4φ`. Otherwise it glides back
without undershooting. That condition follows from the AR(2) characteristic
roots.

**Readability knobs.**
- `φ` is "how long hype keeps running". The peak comes later and is bigger as
  `φ` rises.
- `κ` is "how hard reality pulls back".
- The undershoot depth is roughly the "hangover" after hype.

For a short run of about 15–20 ticks, φ ≈ 0.6, κ ≈ 0.25 gives a full
hype–peak–pullback arc inside about 8 ticks. That is readable within one
match.

## 3. Post-earnings-announcement drift: reports reveal, perception catches up

**Sources.** Ball & Brown (1968) first noticed that abnormal returns keep
drifting after an earnings announcement: up for good news, down for bad.
Bernard & Thomas (1989) test whether this is a risk premium and conclude it
is better explained by a *delayed price response*. Conservatism in Barberis,
Shleifer & Vishny (1998), meaning slow updating of beliefs in the face of new
evidence, gives a behavioural reason.

**Game form.** A report does not change real value. It publishes it (or a
noisy estimate of it). Perceived value then closes a fraction of the
remaining gap each tick for a few ticks, on top of the normal fad:

```js
function onReport(c) {
  c.revealed = c.real * (1 + REPORT_NOISE * gauss(rng)); // optional noise
  c.drift = { ticks: DRIFT_TICKS, rate: DRIFT_RATE };     // e.g. 4 ticks, 0.35
}
function stepReport(c) {
  if (!c.drift?.ticks) return;
  const target = Math.log(c.revealed / c.real);  // ≈ 0 if report is accurate
  c.u += c.drift.rate * (target - c.u);          // close part of the gap
  c.drift.ticks--;
}
```

Optionally the report day itself can close only the first slice, for example
40% of the gap, as a visible jolt, with the rest as drift. That keeps the
"report jolt" as a market force while making it partly tradeable *after* the
news. The player then has a reason to act on a report instead of only before
it.

## 4. Regime changes

**Source.** Hamilton (1989) models the parameters of an autoregression as
"the outcome of a discrete-state Markov process": occasional discrete shifts
in growth rate, driven by a hidden state.

**Game form.** Use it in two places, both cheap:

1. **Company health regimes** (drives real value, §5): states such as
   `thriving / steady / struggling`, each with its own value drift, plus a
   small per-tick switch probability.
2. **Market mood regimes** (drives perceived value): `calm / frothy / panicky`.
   Each has its own `WOBBLE`, `φ` and fad bias. Frothy raises φ (hype runs
   longer). Panicky gives negative hype kicks and bigger wobble.

```js
const P = { steady:{thriving:.04, struggling:.04}, thriving:{steady:.08}, struggling:{steady:.08} };
function stepRegime(c, rng) {
  for (const [to, p] of Object.entries(P[c.health] || {}))
    if (rng() < p) { c.health = to; return; }
}
```

A per-tick switch probability `p` gives an expected stay of `1/p` ticks. That
duration is the readable knob: "a good stretch lasts about 12 ticks".

## 5. Real value that drifts with company health

**Sources.** The standard continuous-time model of a fundamental with trend
and noise is geometric Brownian motion, `dV/V = μ dt + σ dW`. It is the
underlying-asset model in Black & Scholes (1973). Merton (1976) adds rare
jumps to it, a *jump-diffusion*, for discrete news. Hamilton-style regimes
(§4) make the drift `μ` depend on a hidden state.

**Game form.** Put health in charge of the *drift* of real value, not its
level:

```js
// Option A: continuous health h ∈ roughly [-1, 1], itself a slow OU
c.h = aH * c.h + sH * gauss(rng);                 // HEALTH_HALF_LIFE ~ 10–20 ticks
const mu = G_BASE + G_HEALTH * c.h;               // e.g. 0.002 + 0.02*h per tick
c.real *= Math.exp(mu + VALUE_NOISE * gauss(rng)); // VALUE_NOISE small, e.g. 0.005

// Option B: regime health (§4)
const MU = { thriving: 0.02, steady: 0.0, struggling: -0.02 };
c.real *= Math.exp(MU[c.health] + VALUE_NOISE * gauss(rng));

// Rare genuine events (Merton-style jump), used sparingly and telegraphed:
if (rng() < JUMP_P) c.real *= Math.exp(JUMP_SIZE * gauss(rng));
```

Real value then curves smoothly, and a report tells you where it has been
heading. The existing report event text ("contained repair", "deeper damage")
can set or nudge `c.h` or `c.health` instead of applying a shock. Keep
`VALUE_NOISE` well below `WOBBLE`: real value should look like a slow tide
under a choppy surface. Otherwise the player cannot tell the two apart.

## 6. Other cheap options considered

- **Smoothed noise (Perlin 1985 value/gradient noise).** Deterministic and
  very smooth, but not biased toward a target on its own. It would need
  adding on top of the OU pull. The AR(1) already gives smooth, bounded
  wander with one parameter, so Perlin adds little.
- **Random walk with a pull (Euler-discretised OU).** Same as §1, but with
  `u += -θ·u·Δt + σ·√Δt·n`. It is accurate only for small `θΔt`. Gillespie's
  exact form (`a = e^{−θΔt}`) costs the same and never overshoots, so prefer
  it.

## 7. Parameters that control readability

| Knob | Meaning for the player | Suggested start | Effect if too high |
|---|---|---|---|
| `HALF_LIFE` (fad) | Ticks for a mispricing to halve | 4–6 | Gaps never close within a match; the edge feels fake |
| `WOBBLE` (fad sd) | Typical % gap between price and value | 4–8% | Noise drowns every signal |
| Signal-to-noise: `|hype kick| / (per-tick noise)` | Can I see a card's effect? | ≥ 3 | (too low) Cards look like they did nothing |
| `φ` momentum | How long hype runs | 0.5–0.7 | Long bubbles, big crashes |
| `κ` pull | How hard reality bites | 0.2–0.35 | Stiff, unwavy prices |
| `DRIFT_TICKS`, `DRIFT_RATE` | How long a report keeps moving the price | 3–5, 0.3–0.4 | Reports feel instant (rate→1) or ignored (rate→0) |
| Health half-life / regime stay | How long a company's trend lasts | 10–20 ticks | Trends are undetectable (too short) or static (too long) |
| `G_HEALTH` vs `WOBBLE` | Does value move more than noise? | Value drift per match ≈ 1–2× WOBBLE | Trend swamps trading or is invisible |
| Clamp on `|u|` | Hard cap on mispricing | 25% | (none) Rare absurd spikes |

Seed the RNG per run so playtests can replay the same market, and the design
log can refer to specific seeds.

## 8. Keeping the player mostly profitable without every stock rising

1. **Profit from the gap, not the drift.** In the Summers model the fad
   produces *negative* serial correlation in excess returns: "as prices revert
   to fundamental values, negative excess returns result" (Summers 1986). A
   player who knows or estimates real value therefore has a positive expected
   edge: buying at `u < 0`, the expected gain over `k` ticks is about
   `(1 − a^k)·|u|`. This is the designed source of profit. It works in both
   directions, including stocks that trend down.
2. **Zero-mean fad, mixed health.** Keep the fad noise and hype kicks centred
   on zero across the deck. Draw each run's companies from a health mix, for
   example 40% thriving, 30% steady, 30% struggling, with a small positive
   `G_BASE`. The market then drifts gently up overall while individual names
   fall. Since the prototype appears long-only (buy/sell of owned shares),
   struggling companies are traps to avoid or dips to time, not shorts.
3. **Information buys edge.** Informed, Leak and Clean read already reveal
   real value or report direction. Under this model their value is exactly
   `|u|` times the fraction the market will close before the match ends. Make
   sure `HALF_LIFE` is short relative to the remaining ticks, so that
   information pays out within a match.
4. **Hype is a two-sided tool.** With the damped fad, pumping a stock gives a
   profitable window (peak around tick 2–4) followed by a predictable hangover.
   Selling into the peak rewards reading the curve. Holding through punishes
   greed, without the game needing a separate "crash" rule.
5. **Tune by Monte Carlo.** Simulate a naive "buy when price < revealed
   value, sell at ≥" bot over about 1,000 seeded runs. Target something like
   65–75% profitable runs for a competent player, and about 50% for random
   play. This is a design target, not a sourced figure.

## Recommendation

Build one layered model, in this order. Each layer is independently testable.

1. **Real value**: `real *= exp(μ(health) + small noise)`, with health a slow
   OU (or three-state regime). Reports stop moving value and start revealing
   it.
2. **Perceived value = real × exp(u)**, where `u` is the **damped fad**
   (§2: `v = φv − κu + σn; u += v`). Start with φ ≈ 0.6, κ ≈ 0.25,
   σ ≈ 0.01–0.015. News, cards and boss moves act by kicking `v` (hype) rather
   than setting price.
3. **PEAD**: on a report, close about 40% of the gap to revealed value on the
   day and the rest over 3–4 ticks.
4. Optional later: a market-mood regime that swaps φ and σ.

This keeps the price as "real value plus a self-correcting belief error",
which matches the CONTEXT.md framing. It gives hype-then-pullback without
special rules, and it makes the player's edge the thing the cards already
trade in: knowing the gap.

## Sources

- Uhlenbeck, G. E., & Ornstein, L. S. (1930). On the theory of the Brownian
  motion. *Physical Review*, 36, 823–841. https://doi.org/10.1103/PhysRev.36.823
- Gillespie, D. T. (1996). Exact numerical simulation of the Ornstein–Uhlenbeck
  process and its integral. *Physical Review E*, 54, 2084.
  https://doi.org/10.1103/PhysRevE.54.2084
- Summers, L. H. (1986). Does the stock market rationally reflect fundamental
  values? *Journal of Finance*, 41(3), 591–601. Equation (5) is the fad model,
  and the negative-autocorrelation result is on p. 595.
  https://doi.org/10.1111/j.1540-6261.1986.tb04519.x
- Cutler, D. M., Poterba, J. M., & Summers, L. H. (1990). Speculative dynamics
  and the role of feedback traders. *American Economic Review*, 80(2), 63–68.
  https://www.nber.org/papers/w3243
- De Bondt, W. F. M., & Thaler, R. (1985). Does the stock market overreact?
  *Journal of Finance*, 40(3), 793–805.
  https://doi.org/10.1111/j.1540-6261.1985.tb05004.x
- Jegadeesh, N., & Titman, S. (1993). Returns to buying winners and selling
  losers. *Journal of Finance*, 48(1), 65–91.
  https://doi.org/10.1111/j.1540-6261.1993.tb04702.x
- Hong, H., & Stein, J. C. (1999). A unified theory of underreaction, momentum
  trading, and overreaction in asset markets. *Journal of Finance*, 54(6),
  2143–2184. https://doi.org/10.1111/0022-1082.00184
- Barberis, N., Shleifer, A., & Vishny, R. (1998). A model of investor
  sentiment. *Journal of Financial Economics*, 49(3), 307–343.
  https://nicholasbarberis.github.io/bsv_jnl.pdf
- Ball, R., & Brown, P. (1968). An empirical evaluation of accounting income
  numbers. *Journal of Accounting Research*, 6(2), 159–178.
  https://doi.org/10.2307/2490232
- Bernard, V. L., & Thomas, J. K. (1989). Post-earnings-announcement drift:
  delayed price response or risk premium? *Journal of Accounting Research*,
  27 (Supplement), 1–36. https://ideas.repec.org/a/bla/joares/v27y1989ip1-36.html
- Hamilton, J. D. (1989). A new approach to the economic analysis of
  nonstationary time series and the business cycle. *Econometrica*, 57(2),
  357–384. https://doi.org/10.2307/1912559
- Black, F., & Scholes, M. (1973). The pricing of options and corporate
  liabilities. *Journal of Political Economy*, 81(3), 637–654.
  https://doi.org/10.1086/260062
- Merton, R. C. (1976). Option pricing when underlying stock returns are
  discontinuous. *Journal of Financial Economics*, 3(1–2), 125–144.
  https://doi.org/10.1016/0304-405X(76)90022-2
- Box, G. E. P., & Muller, M. E. (1958). A note on the generation of random
  normal deviates. *Annals of Mathematical Statistics*, 29(2), 610–611.
  https://doi.org/10.1214/aoms/1177706645
- Perlin, K. (1985). An image synthesizer. *SIGGRAPH Computer Graphics*, 19(3),
  287–296. https://doi.org/10.1145/325165.325247

**Verification notes.** I read the Summers (1986) equations directly from the
paper's text. Hong & Stein, Cutler–Poterba–Summers, Bernard & Thomas,
Barberis–Shleifer–Vishny and Hamilton were checked against publisher or NBER
abstracts. I could not open the Gillespie (1996) full text. Its update rule is
the standard exact OU discretisation given in the paper's abstract framing,
and it is stated here without equation numbers. The citations for Ball &
Brown, Black & Scholes, Merton, Box & Muller and Perlin are standard
bibliographic records that were not re-fetched. The impulse-response table and
the 5.4-tick half-life are my own computations.
