# Trading prototypes

Start with the **[living design log](docs/design-log.md)** for current design
intent, accepted decisions, prototype findings, open questions, and the next
useful work. Revision 4 adopts the earlier project log and backfills the repo's
September 26–27 experiments; temporary prototype rules remain distinct from
final-game decisions.

The [imported ChatGPT project sources](docs/sources/chatgpt-project/README.md)
contain the school pitch/design materials, original PDFs with searchable text,
historical design and session notes, and archived former project instructions.
The source index explains their provenance and how they relate to later prototype
decisions.

## Switchable presentation experiment · round five

**Presentation checkpoint complete: C / Side dial is the selected winner.**
The creator accepted the final presentation on September 27, 2026. Read the
[session conclusion and next-session handoff](docs/presentation-session-summary.md)
for the work completed, discoveries, preserved versions, and validation limits.
The switchable file remains the primary source; the accepted playable is `6532402`.

Open **[presentation-prototype.html](presentation-prototype.html)** by
double-clicking it in a modern browser. It is a portable, throwaway HTML file;
no server, installation, or network access is needed.

- **A — Position bar:** holdings, value and exposure in a compact bar panel.
- **B — Compact holdings:** bar and shares alongside average entry
  and unrealized P/L, immediately above the transaction buttons.
- **C — Side dial (default):** a single small exposure dial beside the holdings figures;
  no duplicate exposure bar.

All three now use the favored right-side Actual / No cards graph annotations.
The graph has a protected minimum height; signed contribution bars and the
combined card effect sit directly beneath it. Holdings are grouped with trading
controls and the adjacent report brief. Repeated chart legends and instructional
subtitles have been removed. Activity and News archive are together at the top.
End Turn uses no turn fraction; the dots retain progress.

The previous set remains available unchanged as
[presentation-round-four-prototype.html](presentation-round-four-prototype.html)
at commit `d405928`. See [round-four feedback](docs/presentation-round-four-feedback.md).

Only company-card presentation changes. All scenes share the same green theme,
bottom card hand, and bottom-right End Turn button. Responsive typography and
controls grow with the viewport rather than leaving tiny content inside tall
panels. Start at **100% browser zoom** to compare the new default sizing.

Prominent exposure bars, shares-held labels and invested amounts make open
positions visible. Sell All closes the named company's remaining shares through
the existing sale action and fee rules. No additional market mechanics were added.

Every scene uses **select card, then select company**. Card icons are restored.
Click the selected card again or press Escape to cancel without
spending a play. Selection and trade quantities survive scene switches.
The hand omits redundant targeting instructions, discard-name lists and a cancel
button. Empty power rows are hidden. Selected cards use the same border width
as unselected cards, with constrained grid rows and content to prevent overflow.

The page uses a fixed viewport instead of a scrolling document. Quotes, charts,
holdings, price contributions, powers, trades and card targets stay on the board.
Company briefs, news history, card references, activity and session controls open
in a modal side drawer with its own scrolling. Closing it returns to the same
board and selection. Brief buttons show a report time and compact public headline.

Desktop compositions are designed around one-screen play. Below 900px wide,
all three quote summaries remain visible while company tabs show one detailed
asset at a time. Very small or dense viewports retain a local company-panel
scroll fallback so controls are reachable; the document itself never scrolls.
Actual viewport fit is **not visually verified** under the browser restriction.

All three use the same dark green palette. Graphs and exact price contributions are always
visible. A hollow chart marker and numeric quote show the price without that
tick's price cards, starting from the same previous quote. This is not a
whole-run simulation with every earlier card removed.

The creator preferred round one's B for its grouped asset information and solid
layout, liked A's dark colors, and found C's light palette uncomfortable and its
information difficult to use. The unchanged first set is preserved as
[presentation-round-one-prototype.html](presentation-round-one-prototype.html).
Its source is also captured at `bf04c5b`.
Round two is preserved in
[presentation-round-two-prototype.html](presentation-round-two-prototype.html)
and commit `51d351b`. The creator preferred C's aesthetic and card-first flow,
but found the page scrolling disorienting and the layout unplayable. See
[round-two feedback](docs/presentation-round-two-feedback.md).

**The previous version is kept unchanged**, as requested:
[presentation-round-three-prototype.html](presentation-round-three-prototype.html)
(`9731403`). Its successful no-page-scroll behavior, sizing problems, and exposure
feedback are recorded in [round-three feedback](docs/presentation-round-three-feedback.md).

Use the floating bottom arrows or keyboard Left/Right to cycle. The same live
session and selected company carry across scenes. Arrow keys stay native while
editing an input, select, textarea, or editable content. `?variant=A`,
`?variant=B`, and `?variant=C` select a scene on reload where browser file-URL
history updates are supported. Reload resets play; only scene selection survives.

The engine is copied unchanged from the uncertain-market playable. Previous-tick
quotes, fee-inclusive average entry, exposure, and unrealized profit are visible
for all companies. Contributions remain visible; news history and a public state
record are available in the drawers.
Debug spoilers remain separately labelled.

Source and in-memory smoke checks passed, including a full 12-turn run and
state-preserving scene switches. **Browser visual review remains unperformed:**
the browser tool blocked the file URL and prohibited workarounds. These checks
do not establish layout quality on their own. The creator's subsequent playtest
feedback selected C. See the
[presentation issue](.scratch/presentation-scenes/issues/01-compare-scenes.md).

The presentation checkpoint is concluded. Rival design is the next candidate
experiment; its rules remain undecided and no rival was implemented here.
Prototype branch: `codex/presentation-scenes`.

Latest human feedback: [uncertain-market playtest](docs/uncertain-market-playtest.md)
reports more tension, deliberate exposure choices, and more useful cards.
The [switchable presentation brief](docs/presentation-prototype-brief.md) defines
the current experiment; a bounded rival experiment follows presentation feedback.

## Current experiment: uncertain opportunities

Open **[uncertain-market-prototype.html](uncertain-market-prototype.html)** by
double-clicking it in a modern browser. No setup or server is needed.

The same three-card/two-play rules now run against independently developing
company stories. Watch the **Open questions & exposure** panel: it shows what is
unresolved, when reports arrive, and how much of your wealth each company risks.
News can move the price sharply before your next trade. Investigate reveals
current value, not future reports.

**Replay current seed** repeats outcomes. **New scenario** changes follow-throughs;
the card shuffle stays fixed. You can load a numbered seed to reproduce a run.
Optional guided tabs below the game demonstrate report gaps and ambiguous
selloffs. Those reset into labelled guided sessions.

Play a full run and report whether holding cash, splitting positions, sizing down,
or holding through a fall ever felt worthwhile—and whether all-in still felt
obviously best. More losses alone would not establish an improvement.

The [spec](.scratch/uncertain-market/spec.md) records exact temporary rules and
verification. Both scripts parsed; numerical checks across 128 seeds and DOM
stand-in checks passed. Actual browser playthrough and visual layout remain
unverified. No dependencies or test suite were added. Earlier playables below
are preserved unchanged.

The [card-hand feedback](docs/card-hand-playtest.md) also records the proposed
rival-profit goal. It is a separate candidate, not part of this market-only pass.

## Previous experiment: three cards, two plays

Open **[card-hand-prototype.html](card-hand-prototype.html)** in a modern browser
by double-clicking the file. No installation, server, or internet is needed.

This bounded experiment asks whether varied temporary hands create meaningful
trading choices and a card you wish you could keep. It implements the
[agreed experiment spec](.scratch/card-hand-discard/spec.md).

1. Select a company and read the news. Trade freely at the displayed quote.
2. Draw three cards and play up to two on eligible companies. Select another
   company to change the card target; disabled cards explain why they cannot play.
3. End turn to discard unused cards and resolve one market tick. Activated
   effects persist for their stated durations. A fresh hand arrives each turn.
4. Inspect the card contribution breakdown and active commitments. The deck
   contains two of each of seven powers and reshuffles the discard when needed.
5. Finish 12 turns for automatic closing settlement, then share your feedback.

Optional guided walkthrough tabs below the game demonstrate choosing two cards,
Echo targeting, and Extend/expiry using arranged opening hands. They reset the
session and are labelled as guided. Use **Restart playtest** for the ordinary
seeded deck. Keep debug inspection closed during playtests.

Ask after playing: Which discard was difficult? Did the later turns still offer
choices? Did a past commitment shape a new hand, or did the same pair dominate?
Stop at this feedback checkpoint before expanding the experiment. Restart
repeats both market and draw order; familiarity affects subsequent results.

Verification: both scripts parsed; temporary direct smoke checks passed for the
seven powers, play limits, Echo, expiry, Extend, shaping/floor arithmetic,
60 full action-policy runs, deck conservation and reshuffles, closing accounting,
trade independence, pure transitions, and deterministic restarts. In-memory DOM
stand-in checks passed for rendering and handlers across a session, restart,
opening concealment, and guided action sequences. These are not an actual browser
playthrough or visual check; those remain unperformed. No test suite was added.

The previous playable below is preserved unchanged. Its reported human results
are historical evidence, not results for the new card experiment.

## Previous experiment: operate a small engine

Open **trading-prototype.html** in a modern browser (double-click the file).
No installation, build, server, account, or internet connection is needed.

This throwaway prototype implements experiment 1 from
[the accepted plan](docs/prototype-planning.md): operate a small engine.
It asks whether allocating limited information and influence across overlapping
opportunities produces understandable, interesting decisions. The creator has
played the initial version twice and subsequently tried the feedback revision.
See [playtest notes](docs/first-playtest.md) and
[the next prototype direction](docs/next-prototype-direction.md).

## Try it

1. Read the opening news and select a company.
2. Set a whole-share quantity. Buy and sell at the displayed quote; the preview
   includes the 0.5% fee. Spend cash across opportunities as you see fit.
3. Use Investigate to reveal live underlying value. Use Influence while a company
   is revealed to activate the equipped Informed Influence modifier.
4. Advance the market when ready. There is no action timer. Inspect the news,
   price changes, power durations, and positions after each advance.
5. Finish 12 steps for closing settlement and a short result view. Restart repeats
   the same scenario and restores cash and both power supplies.

This revision shortens the session from 18 to 12 steps. Refreshing loses progress.
Keep the separately labelled debug disclosure closed during playtests.

## Observe before expanding

- Can you explain a trade using public evidence and a power, without a facilitator?
- Which plausible alternative did you pass over because of limited cash or powers?
- Did the synergy affect your choice, or did you repeat the same sequence blindly?
- Could you explain a disappointing outcome? What would you try differently?
- If you reached the target, did it make further decisions less interesting?

Profit alone is not evidence of engagement. Replays here are confounded by
scenario familiarity. The next endorsed direction is varied cards with hand
discard and turn-based play; its turn rules and card content remain open.

## Revision 2 — clearer consequences, shorter session

The selected company now shows market movement, base Influence, the Informed
Influence bonus, and actual movement separately after each advance. The hollow
chart marker shows the quote without that step’s active Influence, starting from
the same previous quote. It is not a whole-run alternate timeline. The breakdown
persists on the final affected step even after the power expires.

Accounting, activity, instructions, and earlier news are collapsed by default.
Powers sit beside trading controls, with an explicit synergy preview and active
bonus status. The main summary shows available cash and profit.

Revision checks: both scripts parsed; direct simulation checked same-step
counterfactual quotes, an overpriced asset falling despite boosted Influence,
contribution arithmetic, price-floor handling, final-tick feedback, ordinary-trade
independence across all 12 steps, and closing settlement. An in-memory DOM stand-in
exercised rendering and handlers through powers, a complete session, and restart,
including hidden-value concealment at opening and the synergy preview. All passed.
This was not an actual browser or visual layout check; that remains unverified.

## Initial-version verification, September 26, 2026

Both inline JavaScript blocks parsed under Node. A temporary direct simulation
smoke check exercised purchases, partial sales, average-cost accounting,
unaffordable/oversized trade rejection, a full 18-step session and closing
settlement, two-use power exhaustion, three-step revelation and Influence expiry,
boosted versus ordinary Influence, unchanged underlying value under Influence,
and fresh-state resource restoration. All checks passed. An ordinary-trade run
and a no-trade run had identical market quotes at all 18 steps.

**Agent browser UI verification remains unperformed.** The creator has played
both versions and reported their experience. The browser automation tool rejected
the local file URL because its security policy allows only HTTP/HTTPS and forbids
workarounds for the blocked action. No screenshot inspection, browser console
check, click-through session, or restart-button verification is claimed.
The direct simulation checks do not substitute for those UI checks.

No production test suite, dependencies, or general engine was added. The file is
the runnable source. See [ASSUMPTIONS.md](ASSUMPTIONS.md) for exact temporary rules.

Only the first checkpoint is implemented: no card draws, upgrade selection,
real-time mode, shops, multi-day progression, or expanded content.
