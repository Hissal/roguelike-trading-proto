# Presentation session conclusion — September 27, 2026

## Decision

The creator explicitly selected **scene C / Side dial** as the winner and
concluded the presentation session: “I think this is good now. scene C with the
radial dial is the winner.” The presentation checkpoint is complete.

Accepted playable: `../presentation-prototype.html`, scene C, on
`codex/presentation-scenes`. The final playable revision is **`6532402`**.
C is the default when no valid `?variant=` parameter is present; an existing
`?variant=A` or `?variant=B` still explicitly selects that comparison scene.
This documentation wrap-up does not change the accepted playable.

The scene switcher and other variants remain available as experiment evidence.
No production migration, merge to main, hosting, or rival implementation was
performed as part of concluding this session.

## What was built

Five rounds of portable HTML presentation experiments reuse the unchanged
uncertain-market engine. Scenes share the same in-memory game; switching does
not advance ticks, change outcomes, consume cards, or alter positions. Reloading
starts a new run. No backend, persistence, framework, or dependency was added.

1. **Different information structures:** trading terminal, exposure board, and
   market journal. The board's per-company grouping was preferred; the journal's
   bright palette and hidden graph were rejected.
2. **Increasing game presentation:** asset dossiers, company board, tactics
   table. C's aesthetic and card-first targeting won interest, but whole-page
   scrolling made it difficult to play.
3. **Fixed-screen compositions:** bottom, right-column, and top hands, with
   scrolling detail drawers. The creator confirmed the one-screen experience
   was much nicer. Default type/control sizes were too small on large monitors.
4. **Company-card experiments on a shared green shell:** viewport-scaled UI,
   bottom hand, bottom-right End Turn, exposure bars/dials, graph annotations,
   visual contributions, and Sell All. The creator confirmed much better fit.
5. **Consolidation and cleanup:** annotated graphs on all scenes, protected graph
   height, contribution bars and total card impact, holdings next to trading,
   one exposure representation per card, reduced copy, and final hand fixes.
   The compact side-dial version was explicitly selected.

## Accepted presentation and interactions

- Dark green theme; the purple theme was interesting for a possible magical
  direction, but it is not the selected baseline.
- Main gameplay in a fixed viewport. Company briefs, history, card references,
  activity and settings live in modal drawers with independent scrolling.
- Bottom card hand, visible card icons, and End Turn at bottom right. Turn dots
  carry progress; the button omits the redundant turn fraction.
- Select a card first, then a company. Re-click or Escape cancels selection.
  No separate cancel button or repeated instruction block.
- Consistent white hand state on one line, gold plays-left count on the next.
  The named discard list is removed; the end-turn area retains a discard count.
- Price and readable history graph at the top of each company. Right-side
  **Actual / No cards** labels replace the redundant below-chart legend.
- Active-power chips between graph and contributions; the row disappears when
  empty. Report countdowns remain visible.
- Exact signed price contributions with bars and their combined card impact.
  Removed repeated explanatory subtitles from the primary interface.
- Holdings grouped immediately above Buy/Sell/Sell All, near the report brief:
  shares, invested value, fee-inclusive average entry, unrealized P/L, and a
  **single compact radial exposure dial at the side**.
- Activity and News archive are adjacent. Sell All passes remaining shares to
  the original sale operation and fee calculation.
- Selected cards use bounded grid rows, shrinkable contents, and constant border
  thickness so selection styling does not increase their footprint. Full card
  descriptions remain available through the info buttons.

## What we learned

Whole-page scrolling disrupts the creator's decision context, not just their
convenience. Keep a stable board and disclose secondary information in place.
One company's information should stay together, with holdings especially close
to transaction controls. Frequently used actions should also be physically near
one another: hand/end turn, and activity/news.

Fixed-height panels alone do not make a readable screen. Small fixed text and
controls left large empty regions and required 140–170% browser zoom on the
creator's monitors. Viewport-responsive sizing improved the reported fit.
Bulky explanatory panels can squeeze the graph; reserve space for it and remove
duplicate labels before shrinking the essential data.

Exposure needs persistent visual emphasis. The creator overlooked shares still
held after a partial exit. Explicit holdings plus a single exposure indicator
and Sell All made that state clearer. A radial dial beside related figures uses
space better than a large dial combined with a duplicate bar.

Shapes and color work best alongside exact values, rather than repeating them
in several panels. The creator particularly liked direct graph annotations and
signed contribution bars. Concise state labels and effect chips were useful;
instructions that repeated an already-understood interaction became clutter.

## Mechanics and interpretation that must remain intact

The engine source still matches `uncertain-market-prototype.html`. Market seeds,
news, volatility, costs, card rules, draws, durations, action timing and closing
settlement were not redesigned. Sell All is a UI shortcut, not a new mechanic.

“No cards” is the quote **without this tick's price cards, from the same previous
quote**. It is not a whole-run timeline with all earlier cards removed. The
graph, markers and contribution total use the existing engine's `movement`
data, including rounding and the price floor. This distinction remains in the
company dossier even though redundant on-board explanations were removed.

Exposure is current position value divided by current wealth. Average entry
includes buying fees; unrealized P/L excludes future selling fees. Investigate
reveals current value only while active. Future outcomes and draw order remain
hidden outside the explicitly labelled debug view.

## Evidence and limits

**Human evidence:** repeated creator playtests and supplied screenshots established
the reported preferences, improved fit and readability, and final choice of C.
The last response accepts the final presentation. This does not establish
strategic balance, enjoyment for other players, or universal responsive fit.

**Agent checks:** script parsing; engine-source equality; byte-for-byte archive
checks; temporary in-memory DOM/simulation checks across full 12-turn runs and
39 scene renders per broad iteration. Checks covered shared-state preservation,
trades, partial sales/Sell All, accounting/settlement, card-first handlers,
cancellation, reveal/expiry, public-only data, drawer state, and markup order.
The last small change received parsing and structure checks. No persistent test
suite or production verification infrastructure was added.

**Browser limits:** the browser tool rejected local file navigation and expressly
prohibited workarounds. No agent browser screenshots, computed-layout tests,
console review, or visual overflow verification were performed. Supplied user
screenshots are human evidence, not agent browser execution. Very small/dense
screens retain a company-local scrolling fallback; narrow screens use company
tabs. Those adaptations remain unverified across devices.

## Preserved primary sources

| Artifact | Captured revision |
| --- | --- |
| `presentation-round-one-prototype.html` | `bf04c5b` |
| `presentation-round-two-prototype.html` | `51d351b` |
| `presentation-round-three-prototype.html` | `9731403` |
| `presentation-round-four-prototype.html` | `d405928` |
| `presentation-prototype.html` — accepted C | `6532402` |

Round-specific human feedback is in `presentation-round-one-feedback.md` through
`presentation-round-four-feedback.md`. Detailed implementation history and
validation are in `../.scratch/presentation-scenes/spec.md`; the resolved
experiment is `../.scratch/presentation-scenes/issues/01-compare-scenes.md`.
Earlier market and card playables remain unchanged.

## Next session handoff

Start from the accepted C presentation and read this summary, the presentation
spec, `uncertain-market-playtest.md`, and `card-hand-playtest.md`. Do not reopen
layout exploration by default or mistake old “await feedback” notes for current
status. Preserve the comparison artifacts and the accepted game's information
boundaries and interactions.

The previously agreed next topic is a **bounded rival-profit/offensive-play
experiment** after the presentation checkpoint. That checkpoint is now passed;
the rival's information, visible intentions, action order, legal actions and
scoring still need to be selected. No rival rules are implicitly chosen by this
UI work, and no rival implementation is authorized by this session wrap-up.
Begin that work when the creator requests the next experiment.
