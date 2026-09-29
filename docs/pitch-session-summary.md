# Pitch session summary (27–28 September 2026)

This session built the Monday pitch, not the game. No prototype code changed.
It records the pitch decks and what they contain, plus the design ideas and
wording decisions that came up while building them. Labels follow the
[design log](design-log.md) conventions. An idea the creator proposed or accepted
in this session is not a finished rule. Pitch examples use illustrative numbers,
not prototype output.

## What was built

All decks are private claude.ai artifacts in the Slides format. The notes are in
Finnish in every deck.

| Deck | Slides | Target time | Link |
| --- | --- | --- | --- |
| Full, Finnish | 13 | 4:30 | https://claude.ai/artifact/78UwPLikCcmSkSbEWyiAzj |
| Full, English | 13 | 4:30 | https://claude.ai/artifact/XtSkRMqdr5zt9sERFAZEgS |
| Short, Finnish | 9 | 3:30 | https://claude.ai/artifact/39fxHmkLLKzCNQGpfFxv6j |
| Short, English | 9 | 3:30 | https://claude.ai/artifact/EZbeqrvgYvqkm2KGJTSwtL |
| Short, boss revealed late, Finnish (the latest) | 10 | 3:35 | https://claude.ai/artifact/1aopTswrF1ppu9DX9GaFeV |

- A standalone speaker-notes page follows the full 13-slide deck:
  https://claude.ai/artifact/3pD8YyHcvkW9hmcarVXL4s
- The closing slide uses a prototype screenshot. It shows the Insider class,
  seed 1, after six turns.

### Deck structure (full version)

1. Cover: "Rogue Market", a trading roguelike (pörssi-roguelike).
2. What it resembles, in two cards revealed row by row:
   - Real-world trading: buy low, sell high; news moves prices; value is perceived.
   - Balatro: each deck plays differently; bosses test your build; numbers grow
     outrageous.
3. Three core mechanics: a living market, supernatural cards, and growth
   between days.
4. Core loop: action → result → reward/punishment, repeated every turn. Below it
   is one quarter: day 1, upgrade, day 2, upgrade, day 3 boss fight. An arrow
   loops back with "× 4 quarters = one year, then endless mode".
5. News example: the forecast is a very long winter. Lumen Grid (power utility)
   goes +12 %, Harbor Freight (sea freight) −15 %, and Frostline (ski resorts)
   +25 %. The audience question is "Where do you invest?"
6. Manipulator example: you own 10 shares of Lumen Grid, bought at 100 $, and the
   price is now 140 $. The audience question is "Buy more, hold, or sell?" The
   reveal shows the dump: buying more loses 500 $, holding loses 50 $, selling at
   the top gains 400 $. The price then drifts back toward the real value
   (≈ 102 $).
7. Feedback loops, drawn as triangles. The cards are labelled positive or
   negative only, never "helps you" or "hurts you":
   - Two snowballs: yours and the rival's (both positive).
   - Hype (positive) vs. correction (negative).
   - Your engine (positive) vs. rival pushback (negative), across the whole run.
8. Business model, then the close with the playable prototype and questions.

The short decks drop the news example, the hype vs. correction slide and the
business slide. The reveal slide's note names correction as the negative loop,
and the business model is spoken on the closing slide. The boss-revealed-late
deck hides the Manipulator until the reveal: the example is just "your stock is
rising". It also adds the business slide back.

## Design ideas and decisions from this session

### Run structure: three days per boss, four bosses per year

- WORKING DIRECTION (creator-proposed). Each boss is fought over three days, with
  an upgrade between days:
  - Day 1 is preparation and making money.
  - On day 2 the boss notices you as a visible threat. The day is slightly
    harder and the boss may have a small effect.
  - Day 3 is the full boss encounter, won or lost.
- WORKING DIRECTION (creator-proposed). This maps onto a financial calendar:
  - One boss is one quarter, and its three days are the quarter's months.
  - Four bosses make one year, which is the standard win. Endless mode follows.
- Relation to earlier decisions: this concretises §7's season/rival structure and
  the "multiple bosses per run" discussion. It is not yet a rule for boss count,
  day length or how a quarter ends.
- The creator noted that this mirrors Balatro's ante structure: two ordinary
  rounds, then a boss.

### Boss snowball: a gap in the current prototype

- CONFIRMED intent (creator): if the player does nothing about it, the boss
  should start to snowball. It profits, gains capital and runs bigger pumps.
- HUMAN EVIDENCE: the current Manipulator does not snowball when left unchecked.
  This is a missing piece of the boss design, not a balance tweak.
- The pitch presents the rival's snowball as a positive loop.

### Market framing: forces, not good or bad

- CONFIRMED framing (creator):
  - Hype and correction are counteracting market forces, not a bad loop and a
    good loop.
  - With shorting, either direction can profit a player who reads it right.
  - "Positive" and "negative" loop describe the loop's direction, never whether
    it helps or hurts the player.
- CONFIRMED (creator): in the pitch the pump can benefit the player too. The
  rival snowball is not framed as a direct attack on the player.

### Value wording

- The pitch calls the game's hidden value "todellinen arvo" (real value) on game
  slides such as the pump chart and the correction loop. It is described as the
  company's value per share, based on how the company is really doing.
  "Underlying value" and "hidden value" were rejected as odd.
- The real-world comparison says "koettu arvo" (perceived value), because real
  companies have no known true value.
- The core mechanics slide says plain "arvo" (value).
- DEFERRED: `CONTEXT.md` and the prototype UI still say "underlying value". No
  glossary change was requested.

### Name

- Working name "Rogue Market", chosen over "Market Rogue". It reads as "a market
  gone rogue" and still hints at the roguelike genre.
- DEFERRED: occult or "dark" names such as Dark Pool or Occult Capital. The
  creator likes the theme, but the prototype does not convey it yet.

### Comparisons

- The creator has not played Balatro or Insider Trading, so comparisons are
  framed as "seems similar in". Real-world trading supplies the market
  intuition; Balatro supplies the game-mechanic structure.
- Balatro facts used:
  - Blinds are score targets.
  - The boss blind adds a restricting rule.
  - Different starting decks play differently.
  - Numbers grow outrageous.
  - There is an endless mode after the win.
- Contrast for questions: the Manipulator is an active rival, not a restriction.
- "Short runs" was dropped as a comparison. The creator wants short runs, but
  the prototype's information overload makes play slow and thoughtful. This is a
  known tension.
- Insider Trading is kept only for Q&A: it is the closest existing game, but its
  deck drives the market, while ours moves on its own.

### Business model

- CONFIRMED for the pitch: about €10 one-time purchase on PC (Steam), later
  expansions with new bosses, classes and cards. No microtransactions. The
  in-game shady shop is not related to real money.

### News as a design idea

- PROPOSED EXAMPLE: a general, non-company news item such as a long winter
  forecast, which changes several companies' value in different directions.
  This fits the earlier news-rework idea: quarterly reports, an indirect generic
  news feed and sentiment. It is not in the prototype, where news is
  company-specific.

## Presentation craft learned

- Less text on slides. The audience reads or listens, not both, so detail
  belongs in speech.
- Reveal one element per click. Builds only work on elements positioned
  absolutely on the slide.
- One audience question per example, open for anyone to answer, with a fallback
  answer if nobody speaks. Voting was ruled out as too slow.
- Deck speaker notes collapse plain line breaks. `<br>` inside the `<aside>`
  keeps them; the creator found this.
- Rendering glitches sometimes appeared in Present mode: cyan stripes under
  built-in elements, and a slide crossfade stuck halfway. They vanished when a
  screenshot forced a redraw, so they are likely compositing glitches rather
  than slide content. Mitigations:
  - Present from Chrome or Edge in fullscreen.
  - Don't click faster than the animations finish.
  - Swap "rise" builds for "fade" if the glitch persists.

## Open after this session

- Which deck version was presented, and any feedback from the pitch or the
  Q&A.
- Pitch feedback on the three-day and quarter structure and the boss snowball.
- Implementing the boss snowball in the prototype, and possibly day 1 and day 2
  before a boss day.
- Whether to rename "underlying value" to "real value" in `CONTEXT.md` and the
  prototype.
