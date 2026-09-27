# Play the three classes against the boss

Status: resolved
Type: prototype

Playable: `card-design-prototype.html` (open by double-click). Spec:
`../spec.md`. Pick a class on the start screen, or open with
`?class=insider|gambler|financier|custom&seed=N` to replay the same seed per
class. The menu has **Change class** and seed controls; **Cards ↗** is the
glossary with every empowered version.

## Question

Do Insider, Gambler and Financier feel clearly different against the same boss
day, and are they satisfying? Do the reworked rules (stacking instances, strong
Stabilize/Accelerate, Extend on everything, Echo anywhere, Focus) remove the
dead-card problem?

## What to look for

- Does each class suggest its own plan in the first two turns?
- Are there still hands with nothing worth playing?
- Stabilize (100% market) and Accelerate (50% gap): consequential now?
- Freeze + Extend, Stabilize + Accelerate, Empower/All in, Barrage/Frenzy: fun
  or degenerate?
- Financier with 1 Focus: tempo from paid cards, or starved?
- Is the timing/stack labelling on chips readable?
- Custom: try breaking it.

## Agent checks (not human evidence)

- Scripts parse; browser pane: picker, Gambler and Insider turns, Empower,
  Double or nothing, Frenzy, Foresight and Keep checked with no console errors.
  Wide layout only; narrow layout unchecked.
- 400-seed rule fuzz per class (random play, all targets including boss, self
  and cards): no negative cash, negative Focus, hand over 5, NaN prices or
  expired Duration effects left on a target.
- Boss unchanged: against a passive player the boss median is +$137 (p10 +$30,
  p90 +$267), 6.5% negative, identical to the boss prototype.
- Win rate against the boss, 400 seeds:

  | Class | Random play | Simple heuristic (concentrate, dodge reports, play everything on your holding) | Heuristic median profit | Boss median |
  | --- | --- | --- | --- | --- |
  | Insider | 12% | 41% | +$83 | +$131 |
  | Gambler | 20% | 63% | +$208 | +$154 |
  | Financier | 2% | 38% | +$180 | +$237 |

  Findings, not tuning targets: Gambler dumping a whole hand onto one holding
  (Frenzy, Barrage, Double or nothing) is the strongest simple line. Financier
  spends about $535 a day on cards, and its price pushes also lift the boss
  whenever it holds the same company (boss median +$237). Dividends paid to the
  boss are small (median $12).

## Answer (27 September 2026, creator playtest)

Phase complete: this is the current official playable prototype release,
published on GitHub Pages.

HUMAN EVIDENCE (one game per class, creator):
- "Overall it's decent and each class plays a bit differently." Insider is the
  most enjoyable.
- Financier was extremely powerful in its one run: stacking everything on one
  company and holding through everything led the boss by over +$1,000. It may
  have been luck; more testing is needed.
- Gambler was interesting but had bad luck. Hot tip should be an even gamble,
  usable offensively and defensively.
- Card tags were clipped on Insider and Gambler cards.

Final changes applied (see the spec): Hot tip reworked with a holder-based lean
(±$6, empowered ±$10 at 80/20), Triple or nothing when empowered, Legal team
at 1 Focus, Financier deck swaps one All in for Accelerate and adds Legal team,
and the tag clipping fix.

Agent re-check after the changes (400 seeds, simple heuristic player): win rate
Insider 41%, Gambler 53%, Financier 34%; boss unchanged against a passive
player (median +$137). The heuristic doesn't reproduce the creator's
+$1,000 Financier line, so that remains an open balance question.

Creator ideas for later (not built):
- Give the Manipulator a way to clear the player's effects and shorten their
  durations, to counter stacked Financier engines.
- A hard mode where the boss is a lot more dangerous.
- Trade UI feel: share-quantity entry is clunky (a Max button was tried and
  removed); revisit in another session.

Release polish after the playtest: effects on you moved to a full-width
"On you" line above the hand; the hand scrolls sideways on narrow screens.
