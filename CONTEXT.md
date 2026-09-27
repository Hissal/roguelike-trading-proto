# Roguelike Trading

A financial trading game where players interpret opportunities and combine
supernatural powers into profitable strategies.

## Language

**Synergy**:
An interaction between powers that makes their combined use support a strategy
beyond their separate standalone benefits. It may be explicitly described or
emerge from how their effects work together.

**Engine building**:
Developing a set of interacting powers that supports a strategy over repeated
decisions. Synergies feed the engine; accumulating unrelated standalone powers
does not by itself constitute engine building.

### Classes and cards

**Class**:
A playable identity built around a theme: its hand rules (hand capacity, Focus
per turn), a deck drawn from the Card pool plus its Class cards, and optionally
a small passive rule.
_Avoid_: Deck preset, character

**Custom class**:
A sandbox Class the player assembles freely from every card, hand rule and
passive, with no balance limits.

**Card pool**:
The shared set of cards any Class may put in its deck, in any number of copies
or none.

**Class card**:
A card that only one Class can use; it expresses that Class's theme.

**Retain**:
A card keyword: the card stays in hand through End Turn instead of being
discarded.

**Burn**:
A card keyword: once played, the card leaves the match instead of going to the
discard pile.
_Avoid_: Destroy, exhaust

**Focus**:
The per-turn budget a player spends to play cards; each card has a Focus cost,
and a Class sets how much Focus each turn grants.
_Avoid_: Mana, plays, card usage

**Informed**:
The state of an Influence or Suppress played while the company's revealed value
lies beyond the current price in its direction, which locks in its stronger
amount.

**Empowered**:
The state in which the next card you play uses its stronger, empowered version
instead of its normal one.

### Price and effects

**Market forces**:
The background movement of a company's price that belongs to neither player nor
boss: correction toward underlying value, report jolts and fluctuation.

**Boss effect**:
A price or rule effect caused by the boss, separate from Market forces.

**Player effect**:
A price or rule effect caused by the player's cards, separate from Market
forces.

**Effect**:
Anything active on a company, the player or the boss, from any source. Each
Effect has exactly one timing (Duration, Next tick, Immediate or Persistent);
whether it has Stacks is independent of its timing.

**Duration effect**:
An Effect that lasts a stated number of ticks, which is always visible and can
be extended.

**Next-tick effect**:
An Effect that shapes only the coming tick, then ends; shown as next-tick and
never extendable.

**Immediate effect**:
A one-shot Effect that resolves the moment it is applied and is never shown as
active. A boss's Immediate effect is foretold only by its telegraphed move.

**Persistent effect**:
An Effect that stays until something removes it; shown with ∞ instead of a tick
count.
_Avoid_: Infinite, permanent

**Instance**:
One application of an Effect. A target can hold several instances of the same
Effect at once, each with its own timing.
_Avoid_: Stack (for repeated applications)

**Stack**:
A count inside a single Effect instance that grows or shrinks, such as a Pump's
stacks.

**Buff / Debuff**:
An Effect on the player or the boss themself rather than on a company, shown in
that side's own box.
