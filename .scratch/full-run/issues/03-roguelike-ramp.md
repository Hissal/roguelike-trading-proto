# Research how deckbuilder roguelikes keep early decisions simple and ramp up

Status: resolved
Type: research

## Question

How do Balatro, Slay the Spire and similar roguelikes keep early-run decisions simple, introduce depth gradually, pace score/number growth exponentially, and structure antes/acts with bosses? What do they do to avoid analysis paralysis in ordinary turns while keeping a few big decisions?

## Answer

Findings: branch `research/roguelike-ramp`, file `docs/research/roguelike-ramp.md`.

- **Easy turns, hard choices between them.** A Balatro turn is always "best
  poker hand from 8 cards". Slay the Spire starts with 10 cards, draws 5 and
  shows each enemy's next move. The hard decisions sit *between* fights: the
  shop, pick 1 of 3 cards, the route and the boss relic.
- **Offers are mostly simple.** Rarity weights run about 60–70% common and
  3–5% rare, and the first floor of an act never offers a rare. Magic's "New
  World Order" says beginners are hurt by rules they must read and board
  interactions they must track, not by hidden strategy.
- **Structure.** Balatro's three blinds per ante are scored 1× / 1.5× / 2×. Only
  the boss changes the rules, and it is shown at the start of the ante. Slay the
  Spire shows its boss for the whole act.
- **Numbers.** Balatro's targets grow about ×2.5 per ante early, flattening to
  ×1.4. The score is chips × mult, so a good build overshoots the target, and
  the overshoot is the dopamine. Endless mode outscales any build.
- **Depth unlocks across runs**, one clear rule per unlock.
- **Proposal (not a decision):** quarters map to antes and months to blinds,
  with a per-quarter target of about ×3–4.
