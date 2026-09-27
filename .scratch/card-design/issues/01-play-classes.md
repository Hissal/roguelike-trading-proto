# Play the three classes against the boss

Status: ready-for-human
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
