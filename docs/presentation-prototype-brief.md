# Next session: presentation scenes

Status: creator-requested next experiment; implementation belongs to the next
session. Read `uncertain-market-playtest.md` first.

## Question and creative scope

Which presentation makes simultaneous opportunities, uncertainty, exposure, and
card decisions understandable without losing the tension of the current market?

Build one visual prototype with multiple switchable scenes. The creator wants
vastly different presentation methods and to cycle through them in one place.
A scene means a presentation variant of the same game state, not a different
market scenario. Default to three structurally distinct variants, up to five if
there is a strong reason. Different hierarchy, layout, and interaction approaches
are welcome; different colors on the same card grid are insufficient.

Possible starting directions, not requirements: a compact trading terminal,
a spatial portfolio/opportunity board, and a report-timeline or decision-focused
view. The next agent is free to devise better alternatives. No winner is chosen.

## Stable behavior and comparable scenes

Use the current in-memory market/card engine from
`uncertain-market-prototype.html`. Preserve the previous playable and its history.
Keep market values, seeds, news, cards, costs, and action timing intact so that
presentation is the experiment. No dividends, lockups, volatility retuning, or
rival yet. A later experiment may mix quieter reports with sharp movements.

Scenes share one live state. Switching must not advance time, trade, discard,
reset positions, consume a card, change the seed, or expose hidden information.
Allow real local play through the existing in-memory engine so the user can judge
layouts during decisions. There is no external backend or persistent mutation.
Optional labelled snapshots may help compare dense and quiet states, but are not
a substitute for examining the same state across scenes.

Follow prototype/UI.md: floating bottom scene switcher with previous/next arrows,
wraparound, and scene name; keyboard arrows except when editing a field. Use
`?variant=` for reload-stable scene selection where supported by the portable
HTML environment; do not introduce a framework just for routing. Reserve space
so the switcher does not cover trading controls. Keep the artifact clearly
throwaway and trivially runnable, consistent with the repository's HTML demos.

## Information to make accessible

- All three companies' current and previous-tick quotes without selecting each.
- Signed movement; directional symbols and labels alongside color.
- Shares owned, portfolio exposure, fee-inclusive average entry price (cost basis
  divided by remaining shares), and clearly labelled unrealized profit/loss.
  Unowned positions show a dash for entry; selling fees are not included in open
  profit. At opening, indicate no prior tick instead of inventing a quote.
- Clear separation of known facts, unresolved outcomes, and upcoming report time.
- Active powers and remaining ticks, selected card target, remaining plays, and
  which cards will be discarded at end turn.
- News history and exact price-contribution breakdown available without making
  all text compete for attention at once.
- Current value only while Investigate reveals it; future outcomes and draw order
  stay hidden except in the separately labelled debug view.

The compact-row/table proposal in the conversation was one possible design,
not a constraint on all scenes. Use typography, spatial grouping, icons/shapes,
and color thoughtfully; retain labels so color is not the only cue.

## Evidence, delivery, and stopping point

Read `README.md` and `.scratch/uncertain-market/spec.md` for prior verification.
Previous numerical and DOM stand-in checks passed; actual agent browser visual
review was not performed. The user did play the artifact. At handoff an in-app
browser tab was open at the local file URL, but availability and access policy
must be checked afresh. Do not assume prior restrictions have disappeared or
bypass a tool rejection. If visual verification is available, inspect every
scene and switch through a shared state; otherwise report the limit precisely.

Use the prototype skill UI branch. Capture the new artifact and chosen defaults
on a prototype branch with a local issue pointer. Do not declare a winning scene
or advance to rival implementation without the next human checkpoint. Rival
profit competition follows the presentation phase; its information, intentions,
action order, and scoring rules still need a bounded design.
