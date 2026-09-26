# Prototype planning

Status: the bounded plan below records the original planning session. Experiment
1 and a feedback revision were subsequently authorized and implemented. Read
[playtest results](first-playtest.md) and
[the current next-experiment direction](next-prototype-direction.md) before
continuing. Those later records supersede the original implementation boundary
and the fixed order of subsequent experiments; the remaining text is historical.

## Reference material

- `C:/Users/hissa/Downloads/Roguelike_Trading_Game_Prototype_GDD.md`
- `C:/Users/hissa/Downloads/Prototype_Agent_Handoff.md`

These documents are references. Their build instructions do not override the
user's request to discuss the design before implementing it. Their test defaults
are proposals, not automatically accepted prototype requirements.

## Accepted direction — September 26, 2026

The central bet is that players enjoy combining information and supernatural
market manipulation into clever profitable plays. Reading opportunities supports
that experience. Synergies and engine building are core pillars: powers should
interact to support a strategy, rather than merely accumulate as independent
bonuses. Large builds are unnecessary for the first experiment, but the initial
scope must preserve and probe this pillar. Broader knowledge and deck progression
can follow the first small test of interacting powers.

The GDD's confirmed principles remain current intentions, but can be challenged
explicitly through concrete examples. Omitting a system from an experiment does
not remove it from the broader concept. Test shortcuts are not final design
decisions.

Initial iteration is for the creator, followed by a few observed players who
enjoy strategy games but lack financial expertise. A short introduction is
acceptable; subsequent observation should establish whether players can explain
their decisions without the facilitator interpreting the market for them.

Plan a sequence of small playable experiments, each with a question and stopping
point. The full three-day slice in the references is a possible destination, not
the minimum first build. Timing and card circulation remain open to experiments.
Add systems when they help answer the next question.

## Pitch constraint

The class pitch is September 28, 2026 and lasts five minutes. Prototyping before
then would help refine the idea and make the pitch less vague. Neither a prototype
nor highly refined mechanics is required for the pitch. A playable version that
classmates could try is a bonus, not a delivery requirement.

## Experience and evidence

- Opportunity selection is a major source of cleverness. Limited powers and
  capital should invite choosing between plausible opportunities.
- Explicit or implicit synergies must have a place in the experiment. Uncertainty
  management supports opportunity selection and interacting powers. A power can
  behave reliably as described while the surrounding market remains uncertain.
- Use a modest temporary profit target for a short session, with further upside
  after reaching it. Watch whether the target encourages interesting trades or
  simply encourages stopping. This does not settle final-game victory rules.
- Explain simple economic relationships, with some light inference by players.
  Keep exposure, timing, opportunity cost, and power use open to judgment. Avoid
  making financial vocabulary the primary challenge.
- Before expanding, look for players explaining a trade using evidence and a
  power, considering a plausible alternative, and naming something they want to
  try differently. Profit alone is insufficient evidence of engagement.

## Synergy and uncertainty

- Start with specialisation into repeated advantage: a persistent modifier
  interacts with a couple of active powers to support a recognisable strategy.
  Information combined with influence supplies a smaller combination within
  that strategy. The initial candidate effects are defined below.
- Resource-generating action loops remain a possible later direction. Any such
  loop should preserve a reason to read the market.
- Use two short passes: first provide interacting pieces together to test
  operating an engine, then offer a small upgrade choice to begin testing
  assembling an engine. Neither establishes long-run progression by itself.
- A well-reasoned trade may lose. Initial losses should be mainly attributable
  to legible timing and competing forces, with modest background randomness.
  Good reasoning improves prospects without guaranteeing profit, and a loss
  need not imply a player mistake.

## First test setup

All rules here are adjustable experiment settings, not final-game commitments.

- Investigate temporarily reveals an asset's underlying value. It does not
  guarantee when the price will correct.
- Influence applies upward price pressure over a few market steps. Other forces
  may oppose it. This deliberately replaces the reference's instant price jump
  for the initial experiment.
- Informed Influence is a persistent modifier that strengthens Influence when
  used on an asset currently revealed by Investigate. Make its contribution
  visible. Exact strength, duration, and interaction semantics remain test tuning.
- The first controlled pass provides the modifier and a small fixed supply of
  active powers, initially about two uses of each across several opportunities.
  It tests allocating powers and operating a synergy, not deck circulation.
- Capital permits pursuing more than one opportunity but not every opportunity
  at full size. Ordinary buying and selling remain available without cards.
- Start with manual market advance, no action timer, three assets, and overlapping
  opportunities. Players may inspect, trade, and use powers between steps.
- Use a fresh scenario variant in the second pass to reduce memorisation effects.
- Compare pausable real time once the decisions are understandable. A slow manual
  pass alone does not establish which timing model is preferable.

## Experiment sequence

Each stage depends on what the preceding test teaches. This is not a requirement
to build every stage before September 28.

### 1. Operate a small engine

Provide Investigate, Influence, and Informed Influence together using the first
test setup above. Observe whether players can use information to choose where and
when to commit limited powers and capital. Watch for automatic sequences that
ignore the market, unreadable outcomes, and stopping as soon as the target is met.

### 2. Choose a modifier

Provide the same active powers and let the player choose one persistent modifier
before playing a fresh scenario variant:

- Informed Influence strengthens Influence on an asset revealed by Investigate.
- Lasting Insight extends Investigate's revelation, allowing longer observation
  of changing underlying value and reconsideration of entry and exit timing.

Explain both effects plainly. Observe whether the player gives a reason for the
choice and changes their play to use it. Equal popularity is not required, and
choice frequency alone does not establish balance. These first two stages test
operating and beginning to assemble an engine, not full roguelike progression.

### 3. Introduce a small drawn hand

Keep manual market steps and comparable powers and market conditions. Test
whether drawing powers creates interesting improvisation or mainly prevents
useful actions. Choose initial circulation rules when this experiment becomes
the next useful test; no final hand model is selected by this plan.

### 4. Compare timing

For a controlled timing comparison, compare manual steps with pausable real time
while keeping the hand rules fixed. Do not introduce timing and circulation
changes in the same comparison and attribute the result solely to timing. Use
the reference GDD's comparison cautions, including order and scenario familiarity,
when preparing this test.

Later exploratory tests may instead develop two versions with similar core
mechanics but different game flows: one designed for turn-based play and one for
real-time play. Each may have scenarios suited to that flow. The question then
becomes which overall experience is promising, rather than isolating timing as
the cause of a preference. A turn-based flow may define action and turn boundaries
differently from the first experiment's unrestricted manual market advance.

Candidate switchable variants include:

| Treatment | Turn-based flow | Real-time flow |
| --- | --- | --- |
| No cards | Trading-only scenario | Trading-only scenario |
| Cards | Powers within the turn structure | Powers within continuous play |
| Hand turnover | Discard unused cards after each turn | A fitting turnover rule, to be designed |

This is an optional exploration menu, not a requirement to implement six scenes.
Select variants as earlier findings identify useful questions. The real-time
counterpart to end-of-turn discard remains open; do not assume a timed refresh
is automatically equivalent.

Switchable scenes or presets in one prototype could keep these versions easy to
try. The local prototype skill provides tabbed scenarios in its logic branch and
switchable variants in its UI branch; these are workflow patterns to adapt, not
an existing game-scene framework. Shared market and accounting mechanics can
remain consistent while scenario content and flow rules vary explicitly. The
packaging and exact implementation remain undecided.

## Stopping and expansion

Revise the current experiment before adding systems if players cannot explain
their decisions or cannot name a different approach they want to try. Look for
reasoned alternatives and understandable consequences as well as profit.

Stop wherever available pre-pitch time runs out. Prepare a concise account of
what was actually observed, one concrete example of a clever play if one was
observed, and remaining uncertainty. Separate intended experience from tested
findings; no playtest has been conducted during this planning session.

## Deferred scope and adjustable defaults

A full shop, knowledge progression, three-day run, standalone tutorial, and class
distribution are not initial requirements. Add them only if needed for the next
useful test. Bosses, acquisitions, advanced instruments, and long-run progression
remain broader concept questions rather than prerequisites for this experiment.

Prices, capital, profit target, scenario length, power uses, durations, strength,
and stacking or activation details remain adjustable test defaults. The initial
manual timing and fixed power supply do not settle final timing or deck rules.
The modifier's eventual place in the knowledge/deck progression system is open.

The reference browser implementation route remains a candidate, not a decision
made during this interview. Implementation details can be selected when building
is authorized, using the smallest approach that supports the current experiment.

## Planning handoff

The user considers the plan solid. No further design question is required to
close this bounded planning session. Future experiments can reopen their own
questions when useful; the full game need not be specified now. Approval of this
plan does not itself authorize prototype implementation. The next action awaits
a request to begin building or to revise the plan.
