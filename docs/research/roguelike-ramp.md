# How roguelike deckbuilders ramp complexity

Research note, 29 September 2026. Question: how do Balatro, Slay the Spire
(StS) and similar games keep early decisions simple, introduce depth
gradually, pace number growth, and structure antes/acts with bosses, while
avoiding analysis paralysis in ordinary turns? What transfers to this game's
planned run (one year = four quarters; each quarter = month 1 preparation,
month 2 boss wakes, month 3 boss fight; then optional endless)?

Status: RESEARCH, not a design decision. The "Transferable principles" and
"Proposals" sections are suggestions for the designer to accept or reject
(see [design-log section 1](../design-log.md) labelling rules).

Source quality: numbers come from the community wikis that cite game data
(balatrowiki.org, slaythespire.wiki.gg); designer intent comes from Mega
Crit's GDC 2019 slides, LocalThunk interviews, Sid Meier's GDC 2012 talk and
Mark Rosewater's "New World Order". Where only a search snippet (not the page
itself) was available, it is flagged.

---

## 1. Balatro — what it does, with numbers

### 1.1 The run skeleton: 8 antes x 3 blinds

- A run is 8 antes; each ante has a Small Blind, Big Blind and Boss Blind.
  Score targets are a base value per ante times **1x / 1.5x / 2x** for
  Small / Big / Boss ([Blinds and Antes][bal-blinds]).
- Small and Big Blinds "have no other effects and can be skipped to receive a
  Tag"; "Boss Blinds must always be played" ([Blinds and Antes][bal-blinds]).
  So two of every three fights are plain score checks, and only the third
  bends the rules.
- The boss for the ante is shown on the blind-select screen at the start of
  the ante ([Boss Blinds][bal-boss]) — the player knows the threat two fights
  (and two shops) in advance.
- Boss difficulty is gated by ante: only **8** bosses can appear in Ante 1;
  more join at Ante 2, 3, 4, 5 and 6. Ante 8 is always a **Showdown** boss
  (five special ones), which recur at Antes 16/24/32 in endless
  ([Boss Blinds][bal-boss]). Bosses rotate so none repeats before all have
  appeared once.
- Rewards are small and flat: $3 / $4 / $5 (Showdown $8), plus $1 per unused
  hand, plus interest of $1 per $5 held, capped at $5 (i.e. above $25 earns
  nothing more) ([Money][bal-money]). Starting money is $4.

### 1.2 The score curve (White Stake base chips)

| Ante | Base | x prev |
|---:|---:|---:|
| 1 | 300 | – |
| 2 | 800 | 2.7 |
| 3 | 2,000 | 2.5 |
| 4 | 5,000 | 2.5 |
| 5 | 11,000 | 2.2 |
| 6 | 20,000 | 1.8 |
| 7 | 35,000 | 1.75 |
| 8 | 50,000 | 1.4 |
| 9 (endless) | 110,000 | 2.2 |
| 10 (endless) | 560,000 | 5.1 |

Source: [Blinds and Antes][bal-blinds]; ratio column computed here. Higher
Stakes steepen it (Purple Stake Ante 8 = 200,000). Past Ante 8 a formula makes
the curve super-exponential, which is what eventually ends endless runs.

Observations:

- The target curve is **front-loaded exponential that flattens** in antes
  5–8 (x2.5 per ante early, x1.4 by the end). The player's engine is
  multiplicative (below), so late-game the player out-accelerates the target:
  that is where the "numbers go brrr" feeling comes from. The designer sets a
  modest curve and lets the *player's* build supply the explosion.
- Within an ante the step is gentle (1x → 1.5x → 2x), so each ante has a
  warm-up, a check and a spike.
- Endless flips this: the target outruns any engine, so endless is a
  "how far can you get" coda, not a second campaign.

### 1.3 Where the exponent comes from: chips x mult

- Score per hand = **chips x mult**; jokers fire left to right in the order
  +chips, +mult, then xMult ([Scoring][bal-scoring]). Additive bonuses feel
  good early; multiplicative ones (xMult) are what scale late — and their
  order matters, which is a depth layer invisible to beginners.
- Base hands are tiny: Pair 10 x 2, Flush 35 x 4, Four of a Kind 60 x 7;
  each Planet card adds a fixed amount to one hand type (e.g. Flush +15 chips
  / +2 mult) ([Poker Hands][bal-hands]). Three "secret" hands stay hidden in
  Run Info until first played — content revealed by discovery, not taught.

### 1.4 Keeping ordinary turns simple

- A round gives **4 hands, 3 discards, hand size 8** from a standard
  **52-card deck**, with **5** joker slots and **2** consumable slots
  ([Hands][bal-handsn], [Discards][bal-discards], [Hand size][bal-handsize],
  [Consumable slot][bal-cons], [Jokers][bal-jokers], [Red Deck][bal-red]).
  The in-round question is always the same: "what poker hand can I make from
  these 8 cards?".
- LocalThunk chose playing cards precisely because they are familiar: he
  describes standard cards as "a medium for emergent game design" and "a
  simple and familiar approach to strategy games that are usually very
  information dense" ([Rogueliker interview][rogueliker]). He rejected
  "gamery" fantasy/combat language — no health bars or attack numbers
  ([TouchArcade interview][toucharcade]). The in-round vocabulary is borrowed
  from something the player already knows.
- Jokers are **passive**: they were added mid-development as passive items
  after an upgrade-only system felt lacking ([Rogueliker][rogueliker]). A
  passive joker adds no per-turn decision; it just changes what the same
  decision is worth.

### 1.5 Where the big decisions live: the shop

- A shop appears after every blind, with **2 cards, 2 booster packs and 1
  voucher**; reroll starts at $5 and rises $1 per reroll, resetting next shop
  ([The Shop][bal-shop]).
- Money is scarce ($4 start, $3–5 per blind), and interest rewards *not*
  spending. So every shop is a small, legible trade-off (buy now vs. save for
  interest), with occasional high-stakes ones (a rare xMult joker vs. your
  economy).
- Shop joker rarity: Common 70%, Uncommon 25%, Rare 5%; legendaries only via
  a rare Spectral card ([Jokers][bal-jokers]). Most offers are simple; the
  powerful, complex ones are rare events.
- Skip-for-Tag on Small/Big Blinds is itself an optional big decision: trade a
  shop visit and money for a known reward.

### 1.6 Gradual depth across runs

- **150** jokers exist; **105** are available on the first run, **45** are
  unlocked by conditions ([Jokers][bal-jokers]). Decks unlock by winning runs;
  difficulty Stakes unlock one at a time per deck, White → Red → Green → …
  ([Unlocks][bal-unlocks]).
- The first run is the plain Red Deck and a limited boss pool; each new deck
  is a small rule change on the same skeleton.
- LocalThunk later added an "unlock all" option, calling it a "net positive"
  ([TouchArcade][toucharcade]) — unlock gating is for onboarding, not
  withholding.
- He credits Steam demo iteration: the game "became the strategy game it is
  now" through community feedback ([TouchArcade][toucharcade]).

---

## 2. Slay the Spire — what it does, with numbers

### 2.1 Tiny starter deck, tiny turn

- Ironclad starts with **10** cards: 5 Strike, 4 Defend, 1 Bash
  ([Ironclad][sts-ironclad]). Each turn: draw **5**, gain **3** energy, hand
  discards at end of turn ([StS 2 Mechanics][sts2-mech]; same core loop as
  StS 1 per [fandom Gameplay][sts-fandom-gameplay], search snippet only).
- Turn 1 of run 1 is therefore "attack or block?" with three basic cards. The
  only unique card (Bash) introduces exactly one keyword (Vulnerable).
- Enemies show **intents** (attack amount, block, buff, debuff) as icons above
  their heads ([StS 2 Mechanics][sts2-mech]). The hardest part of a combat
  turn — predicting the opponent — is answered on screen, so the turn becomes
  arithmetic, not guessing.

### 2.2 Acts, map, and a visible boss

- 3 acts (a 4th, the Heart, is gated behind beating Act 3 with the three
  original characters) ([Bosses][sts-bosses]). Each act is **17 floors**:
  floor 1 is always an easy-pool fight, floor 9 always treasure, floor 15
  always a rest site, floor 16 the boss ([Map Generation][sts-map]).
- Other floors: normal fight 53%, unknown 22%, rest 12%, elite 8%,
  merchant 5% ([Map Generation][sts-map]).
- The boss's portrait is on the map from the start of the act
  ([Bosses][sts-bosses]), so the whole act is preparation for a known fight.
- After an Act 1/2 boss: choice of **3 rare cards**, choice of **3 boss
  relics**, and a **full heal** ([Bosses][sts-bosses]). The boss relic pick is
  the run's biggest single decision, and it arrives after a fight, never
  inside one.

### 2.3 Card rewards: pick 1 of 3 (or none)

- After a fight the player chooses 1 of 3 cards and may take none
  ([fandom Gameplay][sts-fandom-gameplay], search snippet only).
- Base rarity: normal fight 60/37/3 (common/uncommon/rare), elite 50/40/10,
  shop 54/37/9 ([Cards][sts-cards]). A hidden "rare offset" starts at −5%,
  +1% per common rolled, resets on a rare ([Cards][sts-cards]; search snippet
  of the fandom page adds the +40% cap). Consequence: early rewards are almost
  all commons (simple), and the first floor of each act can never show a rare
  ([Cards][sts-cards]).
- Map choice (elite or not, rest or not) is the medium-sized, route-level
  decision; elites give better rewards at real risk.

### 2.4 Gradual depth across runs

- Characters unlock in sequence (e.g. Defect after a Silent run, Watcher
  after that) and cards/relics unlock by accumulated score per character
  ([Score][sts-score], search snippet only).
- **Ascension**: 20 levels, unlocked one at a time by beating Act 3; each
  level is cumulative and adds one legible modifier (A1 ~60% more elites; A2
  normal enemies hit harder; A3 elites; A4 bosses)
  ([Ascension][sts-ascension]). Mega Crit's GDC slide calls this "Player
  Skill Stratification", "Unlocked Sequentially" ([GDC 2019][gdc-sts]).
- **Neow** (start-of-run bonus): 2 options if the last run did not reach the
  first boss, otherwise 4, including a risk/reward and a boss-relic swap
  ([Neow][sts-neow]) — a single big, optional decision before any fight, and
  a gentle catch-up for struggling players.
- Mega Crit's balance goal: "Every card should have a place!" and "avoid
  anything too warping" ([GDC 2019][gdc-sts]).

---

## 3. Luck be a Landlord (Balatro's cited inspiration)

LocalThunk names Luck be a Landlord videos as an inspiration
([TouchArcade][toucharcade]). Its skeleton is the closest match to a
"quarterly bill": pay rent 12 times to win; rent starts at 25 coins and
reaches 777 by payment 12; spins between payments grow from 5 to 10; endless
rent starts at 1000 and rises 500 per payment ([Rent wiki][lbal-rent] —
search snippet only, the page itself was not fetchable). Between spins the
only decision is a small "add one symbol" pick. A single escalating deadline,
not an opponent, supplies all the pressure.

---

## 4. Design literature that explains why this works

- **Sid Meier, "Interesting Decisions" (GDC 2012)**: complicated decisions
  "one after the other" make a player "feel out of control"; simple ones at a
  slow pace bore them ([Game Developer summary][meier]). Good decisions are
  trade-offs, situational and personal; long-lasting decisions need clearer
  information; err toward giving the player enough information to be
  comfortable ([Game Developer summary][meier]).
- **Mark Rosewater, "New World Order" (2011)**: splits complexity into
  *comprehension* (what does this card do), *board* (how do things on the
  table interact) and *strategic* (how to use it well). Beginners are hurt by
  the first two; strategic complexity is invisible to them and therefore safe.
  "Just one card … can change the design tree from a few choices to a
  double-digit number." Complexity was moved off commons (what beginners see
  most) onto uncommons/rares ([New World Order][nwo]). A later Rosewater
  column (an April Fools piece, but restating real NWO practice) cites a
  default of ~20% of commons allowed to break red flags ([New New World
  Order][nnwo]).

---

## 5. Transferable principles

Each principle names the mechanism in the source games, then what it would
mean here.

1. **Ordinary turns ask one familiar question.** Balatro: "best poker hand
   from 8 cards"; StS: "block or hit, given the shown intent". Here: an
   ordinary month-1 turn should reduce to one readable question (e.g. "which
   one company do I back this tick?"), with the market's next move as legible
   as an StS intent. Hide the forecasting burden behind visible signals,
   in line with CONFIRMED "accessible, streamlined signals".
2. **Put the big decisions between fights, not inside them.** Both games
   reserve their hard choices (joker buys, boss relic, card draft, route) for
   shop/reward/map screens where there is no time pressure and the choice is
   1-of-2-to-4. Here: month transitions and the post-boss reward are where
   tough calls live; a trading turn should rarely be one.
3. **Most offers are simple; complex ones are rare events.** Balatro 70/25/5
   joker rarity; StS 60/37/3 with first-floor-no-rare; NWO pushes complexity
   off commons. Here: tag cards/powers with a complexity tier and let common
   offers be one-line, standalone effects; synergy-heavy or board-altering
   effects appear rarely and later.
4. **Start tiny and sparse.** StS 10-card deck with one special card;
   Balatro 5 empty joker slots and $4. Growth then comes from *adding* rather
   than the player needing to parse a full kit on turn 1. Here: first quarter
   with a handful of cards (the current 14-card deck and full Class kit is
   larger than StS's start) and empty power slots that fill over the year.
5. **Passive over active for most power.** Balatro jokers add no per-turn
   input. Here: most acquired powers should modify the value of the ordinary
   decision (e.g. "+x% on profitable sells") rather than add a new button to
   press each tick. Active cards stay few.
6. **Show the boss early.** Balatro shows the boss at ante start; StS shows
   it at act start. This turns months 1–2 into purposeful preparation and
   makes shop picks easy to judge ("does this help against the boss?"). Your
   "month 2 boss wakes up" can reveal it *fully* by month 2 at the latest,
   ideally teased in month 1.
7. **Two plain checks, then one rule-bender.** Balatro's 1x / 1.5x / 2x with
   rule changes only on the boss. Here: month 1 = plain target, month 2 =
   higher plain target plus boss telegraph, month 3 = boss rule. Low constant
   pressure; one spike per quarter.
8. **Modest target curve, multiplicative player engine.** Balatro targets
   grow ~x2.5 per ante early, flattening to x1.4, while chips x mult (and
   xMult) lets strong builds overshoot massively. Here: keep quarterly profit
   targets gently exponential and let compounding (profit → capital →
   bigger positions; multiplicative powers) produce the big numbers. The
   dopamine is the gap between target and result, not the target itself.
9. **Endless is a super-exponential coda.** Balatro Ante 9+ and LBaL
   endless rent escalate until the run ends. Here: after Q4, targets grow
   faster than any build so every endless run ends in a spectacular crash,
   with a "highest year reached" score.
10. **Depth across runs, one legible layer at a time.** Unlocked-at-start
    pool of 105/150 jokers; decks and Stakes/Ascensions unlock sequentially,
    one modifier each. Here: first run uses one Class and a reduced card
    pool; later Classes, cards and difficulty tiers unlock by finishing
    quarters/years. Offer an unlock-all switch (LocalThunk's "net positive").
11. **Scarce money makes shop choices simple but meaningful.** Balatro's
    small rewards plus capped interest create a constant "spend or save"
    question with an obvious default. Here, compatible with the CONFIRMED
    "guaranteed upgrades without spending profits": a separate, scarce shop
    currency could play this role.
12. **Catch-up without rule changes.** Neow gives more options after a good
    run and a safety choice after a bad one; StS full-heals after bosses.
    Here: fits the CONFIRMED "conditional recovery support" loop — e.g. a
    reset or bonus at each quarter start.

## 6. Proposals (illustrative numbers, not decisions)

- **Mapping.** Quarter ≈ ante; month 1 ≈ Small Blind (plain target, shop
  after), month 2 ≈ Big Blind (target x1.5, boss fully revealed, shop after),
  month 3 ≈ Boss Blind (target x2 plus boss rule, big reward after). Four
  quarters give 12 "blinds" — the same count as LBaL's 12 rent payments,
  shorter than Balatro's 24.
- **Target curve sketch.** With four quarters instead of eight antes, a
  per-quarter multiplier around x3–4 (e.g. 1 → 3.5 → 12 → 40 in target
  units) keeps the total ~40x, close to Balatro's Ante 1→5 span, leaving room
  for player engines to reach far bigger numbers. Needs playtesting.
- **Complexity budget per quarter.** Q1: basic buy/sell plus ~3 simple
  card types, one boss with a single rule. Q2: first synergy cards offered.
  Q3–Q4: rare, board-altering powers. Mirrors Balatro's ante-gated boss pool.
- **Decision sizes.** Ordinary turn: 1 choice from ≤3 options. End of month:
  pick 1 of 3 (skippable). End of quarter: one big pick (like the StS boss
  relic), shown alongside the next boss.

## Open questions

- How much of "analysis paralysis" in the current prototype comes from
  comprehension complexity (reading effects) vs. board complexity (stacked
  Effects across companies)? NWO suggests they need different fixes.
- Can the market's next move be telegraphed like an StS intent without
  breaking CONFIRMED "exact value is not automatically visible"? Uncertain
  intents (a range, or a direction only) are one option.

---

## Sources

- [bal-blinds]: https://balatrowiki.org/w/Blinds_and_Antes
- [bal-boss]: https://balatrowiki.org/w/Boss_Blinds
- [bal-money]: https://balatrowiki.org/w/Money
- [bal-shop]: https://balatrowiki.org/w/The_Shop
- [bal-jokers]: https://balatrowiki.org/w/Jokers
- [bal-unlocks]: https://balatrowiki.org/w/Unlocks
- [bal-hands]: https://balatrowiki.org/w/Poker_Hands
- [bal-scoring]: https://balatrowiki.org/w/Scoring
- [bal-handsn]: https://balatrowiki.org/w/Hands
- [bal-discards]: https://balatrowiki.org/w/Discards
- [bal-handsize]: https://balatrowiki.org/w/Hand_size
- [bal-cons]: https://balatrowiki.org/w/Consumable_slot
- [bal-red]: https://balatrowiki.org/w/Red_Deck
- [toucharcade]: https://toucharcade.com/2024/03/18/balatro-interview-mobile-port-localthunk-dlc-plans-updates-new-jokers-demo-feedback/
- [rogueliker]: https://rogueliker.com/balatro-interview/
- [sts-ironclad]: https://slaythespire.wiki.gg/wiki/The_Ironclad
- [sts2-mech]: https://slaythespire.wiki.gg/wiki/Slay_the_Spire_2:Mechanics
- [sts-fandom-gameplay]: https://slay-the-spire.fandom.com/wiki/Gameplay
- [sts-map]: https://slaythespire.wiki.gg/wiki/Map_Generation
- [sts-bosses]: https://slaythespire.wiki.gg/wiki/Bosses
- [sts-cards]: https://slaythespire.wiki.gg/wiki/Cards
- [sts-score]: https://slaythespire.wiki.gg/wiki/Score
- [sts-ascension]: https://slaythespire.wiki.gg/wiki/Ascension
- [sts-neow]: https://slaythespire.wiki.gg/wiki/Neow
- [gdc-sts]: https://media.gdcvault.com/gdc2019/presentations/Giovannetti_Anthony_SlayTheSpire.pdf
- [lbal-rent]: https://luck-be-a-landlord.fandom.com/wiki/Rent
- [meier]: https://www.gamedeveloper.com/design/gdc-2012-sid-meier-on-how-to-see-games-as-sets-of-interesting-decisions
- [nwo]: https://magic.wizards.com/en/news/making-magic/new-world-order-2011-12-05
- [nnwo]: https://magic.wizards.com/en/articles/archive/making-magic/new-new-world-order-2013-04-01

[bal-blinds]: https://balatrowiki.org/w/Blinds_and_Antes
[bal-boss]: https://balatrowiki.org/w/Boss_Blinds
[bal-money]: https://balatrowiki.org/w/Money
[bal-shop]: https://balatrowiki.org/w/The_Shop
[bal-jokers]: https://balatrowiki.org/w/Jokers
[bal-unlocks]: https://balatrowiki.org/w/Unlocks
[bal-hands]: https://balatrowiki.org/w/Poker_Hands
[bal-scoring]: https://balatrowiki.org/w/Scoring
[bal-handsn]: https://balatrowiki.org/w/Hands
[bal-discards]: https://balatrowiki.org/w/Discards
[bal-handsize]: https://balatrowiki.org/w/Hand_size
[bal-cons]: https://balatrowiki.org/w/Consumable_slot
[bal-red]: https://balatrowiki.org/w/Red_Deck
[toucharcade]: https://toucharcade.com/2024/03/18/balatro-interview-mobile-port-localthunk-dlc-plans-updates-new-jokers-demo-feedback/
[rogueliker]: https://rogueliker.com/balatro-interview/
[sts-ironclad]: https://slaythespire.wiki.gg/wiki/The_Ironclad
[sts2-mech]: https://slaythespire.wiki.gg/wiki/Slay_the_Spire_2:Mechanics
[sts-fandom-gameplay]: https://slay-the-spire.fandom.com/wiki/Gameplay
[sts-map]: https://slaythespire.wiki.gg/wiki/Map_Generation
[sts-bosses]: https://slaythespire.wiki.gg/wiki/Bosses
[sts-cards]: https://slaythespire.wiki.gg/wiki/Cards
[sts-score]: https://slaythespire.wiki.gg/wiki/Score
[sts-ascension]: https://slaythespire.wiki.gg/wiki/Ascension
[sts-neow]: https://slaythespire.wiki.gg/wiki/Neow
[gdc-sts]: https://media.gdcvault.com/gdc2019/presentations/Giovannetti_Anthony_SlayTheSpire.pdf
[lbal-rent]: https://luck-be-a-landlord.fandom.com/wiki/Rent
[meier]: https://www.gamedeveloper.com/design/gdc-2012-sid-meier-on-how-to-see-games-as-sets-of-interesting-decisions
[nwo]: https://magic.wizards.com/en/news/making-magic/new-world-order-2011-12-05
[nnwo]: https://magic.wizards.com/en/articles/archive/making-magic/new-new-world-order-2013-04-01
