# Three lenses on one market

Status: round two implemented; awaiting human presentation feedback.

## Round two (current)

The creator preferred B's per-asset grouping and layout, A's dark colors, and
rejected C's bright palette. They requested visible contribution breakdowns,
without-cards quotes, and another set progressing from standard to gamified.
See `docs/presentation-round-one-feedback.md` for the human evidence.

Current `presentation-prototype.html` contains A asset dossiers, B company
tiles, and C a tactics table. All scenes are dark, with price history, local
trading, average entry, exposure, unrealized P/L, powers, public evidence, and
unresolved outlooks grouped per company. Contributions stay expanded. Graphs
mark the without-this-tick's-cards quote with a hollow marker and connector;
the matching numeric quote and card delta are always visible. No full-run
counterfactual is implied. C adds card selection followed by an eligible target
button; choosing the card alone consumes nothing. Eligibility uses the original
engine. Scene switching preserves that choice and all three trade quantities.

The first set is preserved unchanged in `presentation-round-one-prototype.html`
and commit `bf04c5b`. The engine still matches the uncertain-market source.

Round-two temporary DOM stand-in checks passed through all 12 turns and 39 scene
renders. Each render contained three visible history graphs, three contribution
panels, and three local trade controls. Buy/sell and quantity handlers, card
arming and legal target handlers, fees, settlement, complete state preservation,
keyboard input exclusion, and Investigate reveal/expiry passed. Scripts parse
and `git diff --check` passes. These are source/in-memory checks, not browser
tests; the earlier browser security restriction still prevents visual review.

The sections below record round one's scope and verification.

Question: Which presentation makes simultaneous opportunities, uncertainty,
exposure, and card decisions understandable without losing market tension?

Primary artifact: `presentation-prototype.html` on branch
`codex/presentation-scenes`. Tracking issue:
`issues/01-compare-scenes.md`. Scope follows
`docs/presentation-prototype-brief.md` and the September 26 handoff.

## Defaults and scope

Three scenes: A terminal, B exposure board, C market journal. A is only the
initial comparison scene, not a selected winner. The new file preserves the
older playables unchanged and embeds the uncertain-market engine verbatim.
One in-memory state and one selected company serve all scenes. URL parameters
select presentation only. Reloading deliberately resets play.

No new mechanics, balancing, rival, snapshots, persistence, dependencies, or
production framework. This standalone throwaway artifact has no production
build; the switcher must not be promoted to production with a chosen design.

All three companies show current/previous quotes, labelled signed movement,
shares, exposure, fee-inclusive average entry, and unrealized P/L excluding
future selling fees. Opening has no previous quote. Public evidence and
unresolved outlooks are separate; the journal calendar extracts dates from
already-public outlooks, never future events. Current value appears only during
Investigate. Debug inspection is separately labelled and marks the session.

All scenes allow trades, target changes, card plays and end turn. Unused cards
are explicitly named before discard. Disclosures provide news history, exact
contributions, accounting, active effects, rules, and public comparison state.

## Verification, September 26, 2026

- Both scripts parse under Node; copied engine matches the previous source
  after trimming surrounding whitespace.
- Temporary in-memory DOM stand-in completed a 12-turn run with legal cards,
  buying and settlement, rendering all scenes at every tick (39 scene renders).
- Complete serialized engine state stayed identical across scene switches.
  Buy/sell handlers, fee-inclusive entry ($100.50 on a $100 quote), reset,
  keyboard field exclusion, and wraparound passed smoke checks.
- Revealed-value rendering and concealment were checked; generated HTML had no
  undefined/NaN output in the exercised run.
- No persistent test suite was added, consistent with the prototype skill.
- Actual browser playthrough, screenshot review, responsive layout, console,
  focus behavior, and file-URL scene persistence are **not verified**. The
  in-app browser rejected file navigation under its protocol security policy
  and explicitly forbade workarounds. No alternate serving route was attempted.

## Human checkpoint

Compare scenes during the same run, especially after buying several positions
and reaching a sharp report movement. Identify useful combinations, difficulty
finding information, and whether the card target or pending discard is unclear.
No winner is inferred from the implementation or automated checks. Stop before
rival design and implementation.
