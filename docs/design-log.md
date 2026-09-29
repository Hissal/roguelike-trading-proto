# Roguelike Trading Game — ROLLING DESIGN DOCUMENT

Revision: 6  
Last updated: 28 September 2026 (Europe/Helsinki)  
Status: Adopted living design record for this repository.  
Stable repository path: `docs/design-log.md`

Adopted at the user's request and backfilled from repository records on
27 September. Based on the [unchanged imported revision 3](sources/chatgpt-project/history/roguelike-trading-game-design-log.md).
Historical decisions are retained unless later evidence explicitly revises them.
The backfill records accepted direction, experimental rules, creator feedback,
and remaining uncertainty separately; implementation alone is not acceptance of
a final-game rule. Source links accompany the repository additions.

## 1. Maintaining this living record

Read this document before continuing the design. It is a rolling summary and decision record, not a finished GDD or pitch script. Later explicit user decisions supersede earlier entries.

At the end of each substantive design session:
1. Update the relevant current-state sections, not just the history.
2. Label ideas accurately: CONFIRMED, WORKING DIRECTION, PROPOSED EXAMPLE, DEFERRED, OPEN, EXPERIMENT, or HUMAN EVIDENCE. State whether acceptance concerns the broader design or a particular prototype.
3. Never promote an assistant suggestion to a confirmed decision without user acceptance. General approval does not settle every illustrative number or implementation detail.
4. Record new decisions, rationale, rejected/superseded directions, remaining questions, and a useful next step in a dated session entry.
5. Increment the revision and update the date. Keep this stable filename and update the existing document where possible.
6. Update this repository file directly. The imported sources remain historical snapshots; changes here do not update attachments in the former web project.
7. Preserve unresolved alternatives. Do not reopen settled priorities without explaining a concrete reason.

Use user instructions as authoritative. Treat course materials as guidance or requirements according to their actual wording; do not invent a grading rubric. This document distinguishes design intent from implemented experiments and reported playtest evidence. None of the experiments establishes final balance.

## 2. Quick current-state summary

- CONFIRMED: financial-market trading roguelike. Clever trading, large profits, cash flow, and powerful combinations lead; pressure supports that fantasy.
- CONFIRMED: independently behaving market; ordinary player trades do not influence prices by default. Certain upgrades can grant price influence.
- CONFIRMED: accessible, streamlined signals; extensive trading knowledge is not required. Experienced players can infer more from consistent evidence.
- CONFIRMED: prices tend toward changing underlying value; the exact value is not automatically visible. Estimation and information matter; value and short-term price prediction are different.
- CONFIRMED: days are encounters, with between-day upgrades. Turn-based play with varied cards and hand discard is the current prototype direction; real time remains a later comparison, not a rejected final-game option.
- CONFIRMED: guaranteed upgrades without spending profits. Knowledge includes capabilities, analysis, and specialisations; exact XP/resource delivery remains a WORKING DIRECTION.
- CONFIRMED: a supernatural deck supplies changing powers and encourages improvisation. Basic buying and selling never require drawing an action card.
- CONFIRMED: ordinary runs start with a small deck; introductory tutorial teaches basics first and introduces cards near its end. Shady shop is the primary deck-customisation source, with encounters and especially bosses also supplying cards.
- CONFIRMED: analysis, insider tips, and prophecy are distinct. Ordinary advantages use ordinary channels; the deck stays supernatural.
- CONFIRMED loop directions: profits enable greater earning power; market correction stabilises prices; threatened rivals push back; conditional recovery support helps struggling players without changing established market rules.
- WORKING DIRECTION: seasons with rival defeat before a deadline; takeover is the taught default. Company destruction remains a desired alternate route requiring definition.
- CONFIRMED: season expiry and financial collapse are baseline losses; optional endless continuation after standard victory is required.
- CONFIRMED design pillar: synergies and engine building support clever profitable plays; reading opportunities and uncertainty serve those interactions. See [planning](prototype-planning.md) and the [domain glossary](../CONTEXT.md).
- CONFIRMED design intent: concentrated and diversified positions should both have situational uses and risks; repetitive all-in rotation is not the intended central game.
- EXPERIMENT / HUMAN EVIDENCE: uncertain, staggered reports and sharp price reactions improved the creator's perceived agency, position sizing, and protective card use. This supports the direction, not a proof of balance.
- CONFIRMED prototype presentation: C / Side dial was accepted on 27 September; the presentation checkpoint is complete. Final art, audio, and production platform remain OPEN.
- EXPERIMENT: one tick per turn, draw three/play up to two, recurring 14-card deck, and a 12-turn authored market underpin the current playable. These do not settle final card circulation, run length, or market equations.
- EXPERIMENT / HUMAN EVIDENCE: the current playable prototype release is `card-design-prototype.html` (published on GitHub Pages). Classes (Insider, Gambler, Financier, Custom) draw on one shared card pool plus Class cards, with Focus per turn and effects that stack as instances. The creator found the classes play differently, liked Insider most, and saw one very strong Financier run. See [the card-design spec](../.scratch/card-design/spec.md) and [the glossary](../CONTEXT.md).
- OPEN: final cards and circulation rules, progression economy, market tuning, acquisition process, boss structure, run length, title, and monetisation. The next prototype topic is bounded rival-profit/offensive play; its rules are unselected.

## 3. Pitch context and requirements

### Confirmed logistics
- Solo pitch with supporting slides, Monday 28 September 2026.
- Five minutes total, including speaking, pauses, slide changes, demos, and audience interaction. The teacher will cut off at five minutes.
- Questions have a separate flexible window afterward.
- No prototype is required for the assignment. Optional prototypes have now been built and creator-playtested; they provide examples and evidence without becoming an assignment deliverable.
- The user initially reported no official assignment brief or rubric and substantial freedom. The subsequently supplied teacher pitch slides add explicit guidance, recorded below.
- The pitched game must not be the same game as the GDD assignment.

### Content priorities
- Core mechanics, core gameplay loop, positive feedback loop, and negative feedback loop must be clearly communicated (user requirement and course emphasis).
- Other class topics include monetisation, core/extra/wish scope prioritisation, and iterative design; the available lessons are not the complete course.
- Likely open with a compelling one- or two-sentence concept statement.
- Use game comparisons to build familiarity, explaining exactly what each comparison illustrates.
- Use visual references, a gameplay example/mockup, and explanatory diagrams as useful. The accepted C / Side dial prototype now provides a representative gameplay screen; final pitch visuals, assets, and slide order remain open.
- Audience engagement matters because classmates will watch many pitches. Brief interaction is strongly preferred, but the exact interaction is open and must fit within the five minutes.

### Teacher guidance from Pitch FIN.pdf
- Audience: classmates, developers/players; basic gaming knowledge can be assumed.
- Activate the audience through interaction.
- Keep slides clear, concise, readable, and consistent; use strong contrast and avoid filling them with text, pictures, or animation.
- Organise information simply (the teacher invokes a rule of three); reveal information progressively where useful.
- Every image should serve a purpose. Use diagrams, including loops or progression.
- Slides support the presenter; do not read them verbatim. Rehearse and time the presentation, ideally with a listener.

### Presentation proposals, not locked decisions
- A short audience trading choice could demonstrate agency, an information advantage, or a boss response.
- Have a fallback if nobody responds and leave rehearsal margin under five minutes.
- Illustrate one concrete scenario even while the time model is undecided.
- Reserve deep corporate mechanics and expansion ideas for questions rather than crowding the pitch.
- Presentation language and slide software/file format remain open; do not infer them from the Finnish source material.

## 4. Concept, fantasy, and design principles

### Confirmed
Trading means financial markets, such as stocks and crypto, not merchant travel or item bartering. Some recognisable market behaviour is desirable so prior experience can provide useful intuition. Considerable liberties are welcome, especially supernatural abilities such as future sight.

The player should primarily feel clever: recognising an opportunity, choosing useful tools, and combining upgrades to profit. Tension and financial pressure support that experience. Large profits, growing numbers, and cash flow are central sources of satisfaction.

### Proposed framing
“Read the market, build an unfair advantage, and turn smart trades into increasingly outrageous profits.” This is assistant-proposed wording, not a final approved hook.

### Design considerations raised, not fully specified
- Give public information enough consistency for meaningful basic decisions; privileged information should add an advantage.
- Prefer success the player can explain over unexplained luck.
- Market realism serves gameplay rather than requiring a faithful simulator.
- Upgrades should change how the player trades as well as how much money they earn.
- Bosses should encourage different uses of a build rather than arbitrarily disable it.
- Supernatural deckbuilding is now accepted; combat, engine, platform, and final art style are not selected.

### Confirmed market and information standards — 26 September
- Public signals must support understandable decisions before information upgrades. Challenge comes from deciding how and when to act, not requiring specialist jargon or chart-pattern expertise.
- Events have understandable directional implications, while timing, magnitude, and competing influences preserve uncertainty. These are game-design standards, not promises about real financial markets.
- Market price is observable. Underlying value can change with events and is not automatically shown exactly. Prices tend toward it rather than matching it immediately; the numerical model is OPEN.
- Estimating value gives analysis and information upgrades a purpose. Correctly identifying undervaluation does not guarantee a rise before today's closing.
- Analysis can make existing evidence easier to interpret; experienced players may infer the same relationships without that upgrade and choose other upgrades instead.
- Interpretation of public evidence is different from revealing unavailable facts. Player experience cannot substitute for a genuinely nonpublic fact or supernatural future knowledge.
- Ordinary player transactions have no default price influence. Influence is an upgrade/build direction. The earlier trade-size price-impact balancing proposal is set aside.

### Proposed ordinary-day illustration (not final rules)
A factory interruption depresses a company's price. Public news says replacement parts are expected today, with possible delays. Privileged information confirms arrival before closing but not timing or recovery size. The player chooses whether to buy now, enter partially, wait, or pursue another opportunity. Competing uses of capital and uncertainty must keep this from becoming an obvious buy-and-wait solution. No particular delivery event, power, number, or payoff is fixed.

## 5. Day structure and real-time versus turn-based play

Confirmed day-level structure: trading day / encounter → results → upgrade opportunity → next trading day.

This is a run-progression loop, not yet a complete moment-to-moment core-loop specification. A candidate core loop is: assess market information → choose and manage trades → observe results → adjust positions and strategy → reassess. Exact actions and rewards need definition.

| Model | Discussed strengths | Discussed risks |
| --- | --- | --- |
| Real time | Timing, changing prices, managing an open position, choosing when to cash out | Frantic monitoring and attention demands could dominate thoughtful choices |
| Turn based | Reading information, planning, capital allocation, readable ability combinations | Could become a solved calculation or a blind bet with insufficient information |

The initial design left timing open. Repository playtests subsequently established
turn-based hands and discard as the preferred prototype direction. The current
experiment uses one tick per turn; this is not one turn per day and does not
settle the final game's timing. Real-time comparison remains unperformed and
available for later exploration. See [first playtest](first-playtest.md) and
[the direction record](next-prototype-direction.md).

Current experimental action loop: inspect public news, quotes, exposure, and the
hand → trade and play up to two powers, with ordinary trading available between
plays → End Turn discards unused cards and resolves one market tick → observe
price movement, reports, and effects → draw a fresh hand and reassess. Closing
settles remaining positions. This supplies a concrete moment-to-moment example;
between-day upgrades and full run progression are still outside the playable.

Proposed comparison: use equivalent scenarios and abilities; test whether players understand why they profited, whether their choices mattered, and whether tension supports thoughtful play.

## 6. Progression, knowledge, and supernatural cards

### Confirmed effects versus delivery systems
The original categories—trading capabilities, information, and rule-changing powers—remain useful descriptions of effects. They are not three mutually exclusive acquisition systems. For example, analysis, an insider tip, and prophecy all provide information through different means.

| System / channel | Accepted role | Examples and limits |
| --- | --- | --- |
| Knowledge / expertise | Capabilities, analysis, and trading specialisations that develop the trader | Shorting, access to instruments, clearer news interpretation, reduced broker fees; exact upgrade roster is OPEN |
| Supernatural deck | Changing access to extraordinary powers; adapt the strategy to the hand as well as the market | Foresight, reversal, protection, or price influence are illustrative effects, not final card designs |
| Ordinary news, tips, encounters | Deliver ordinary evidence, nonpublic information, and contextual rewards | Contacts need not constitute a separate relationship or spying progression system |

### Guaranteed progression and purchase economy
CONFIRMED: players receive upgrades without spending their profits. Paid purchases can add to this progression.

WORKING DIRECTION: XP yields a choice of knowledge upgrades (choose one of three was suggested); profits primarily purchase supernatural cards through the shady shop. Exact XP sources, thresholds, selection sizes, and pacing remain OPEN. A separate upgrade resource, optionally purchasable with profits, remains an alternative.

The earlier one-free-upgrade-between-days plus paid extras model remains a simple fallback baseline, not a second guaranteed payout stacked automatically on top of XP. Between-day upgrade opportunities remain accepted; the delivery rules have not been finalised.

Design concern: XP per transaction could incentivise meaningless trading; profit-based XP could amplify an already successful run. These are concerns to test, not adopted restrictions or a chosen XP formula.

### Knowledge should be exciting in its own right
CONFIRMED: knowledge is broader than permission to trade new assets. It includes:
- Capabilities: e.g. shorting or conditional orders.
- Analysis: clearer event implications, affected-company links, and credibility distinctions.
- Specialisations: lower broker fees or gamified benefits supporting particular trading styles. Realistic justification is welcome but strict realism is not required.

User rationale: real broker activity tiers inspired reduced-fee specialisations. No provider-specific fees or thresholds are established game rules or independently verified reference facts here.

PROPOSED EXAMPLES: better returns for holding longer, frequent-trading efficiencies, or protection for diversified holdings. Exact effects and eligibility are undecided. Fees should be visible before a trade (assistant recommendation).

### Analysis, insider tips, and prophecy — confirmed distinction
- Analysis: infer from public evidence, potentially with clearer UI or interpretation.
- Insider tip: obtain a specific nonpublic fact through an ordinary source.
- Prophecy: supernatural knowledge unavailable by ordinary means.

Credible information is not automatically a guaranteed price outcome. The exact disclosure of certainty and source reliability remains to design. Contacts/relationships/spying are optional ideas, not accepted additional systems.

### Supernatural deck and acquisition — confirmed direction
- Basic buying and selling are available independently of cards.
- Draw variation encourages daily improvisation so an established strategy is not completely solved.
- The playable deck stays supernatural; ordinary advantages use ordinary channels.
- Normal runs begin with a very small functional deck.
- A predetermined introductory tutorial run teaches ordinary trading first, then introduces a few cards near its end for the player to try. Exact tutorial duration and sequence remain OPEN.
- The shady shop is the primary way to customise the deck using profits. Encounters and especially bosses can also award cards.
- Displayed offers, rerolls, and card removal are proposed shop functions; stock size, costs, and availability are OPEN.
- Tarot-like presentation is a visual/framing proposal, not a commitment to literal tarot, final lore, or art direction.

Illustrative synergy: shorting knowledge enables profit from a fall; analysis identifies a vulnerable company; prophecy reveals the event's timing. This illustrates knowledge supporting powers, not three final upgrades.

### Final-game card-handling questions
These questions were initially deferred for prototyping. The bounded experiment
below now supplies one tested implementation; final-game choices remain OPEN:
- Does the discard pile reshuffle when the draw pile is empty? Are some cards exhausted for the day?
- Is a new hand drawn each turn? Are unused cards discarded or retained?
- In real time, are draws timed, cards on timers, or hands manually discarded/refreshed?
- What is the maximum hand size, and what happens when it is full?
- Can abilities or other actions invoke extra draws, and at what cost?
- What resets between days, and how do upgrades affect circulation?

The former assistant's opening-hand, timed/phase draws, hand-retention, and
once-per-day suggestions were not accepted final rules. The subsequent repo
experiment deliberately selected its own draw/discard defaults. Turn-based
hands are the current prototype direction; real time remains a later comparison.
Evaluation still asks whether players improvise enjoyably, access combinations,
and manage cards without losing track of the market. No prototype is required
for Monday.

### Repository card experiment — implemented, not final rules

The [card-hand experiment](../.scratch/card-hand-discard/spec.md) replaced the
initial two-use power supply with two copies each of Investigate, Influence,
Suppress, Stabilize, Accelerate, Extend, and Echo. Draw three, play up to two,
discard played and unused cards, and reshuffle the discard pile when needed.
Activated effects persist through discard. Ordinary trades remain available
without cards. Informed Influence still rewards combining revelation and
influence; these are test tools, not the final supernatural roster or a settled
acquisition channel for every effect.

The creator preferred the card version but often found little reason to use
cards beyond supporting one obviously rising asset. Suppress offered preparation
on a different asset. After market uncertainty increased, the same cards gained
more useful offensive/protective roles without a rebalance; Stabilize became
more useful, though suppressing upside remained awkward. See
[card feedback](card-hand-playtest.md) and [market feedback](uncertain-market-playtest.md).
Final starter decks, circulation, shops, knowledge progression, and tutorial
sequencing remain unresolved or unimplemented despite these experimental defaults.

## 7. Seasons, rivals, and the run endpoint

### Evolution and current working direction
The initial alternatives were a finite season and a rival-company takeover. The current direction combines them: defeat/acquire the active rival before the season ends. The calendar supplies urgency; takeover supplies a visible objective.

A deadline limits trading opportunities even in turn-based play. It does not decide the real-time question.

Potential structure: ordinary trading days under the rival's influence → active boss encounter → rival defeated → next season or standard-run victory → optional endless continuation.

WORKING DIRECTION (creator-proposed, 28 September): each boss is fought over three days with an upgrade between days. On day 1 you prepare and make money. On day 2 the boss notices you as a visible threat, which is slightly harder and may bring a small boss effect. Day 3 is the full boss encounter, won or lost. This maps to a financial calendar: one boss is one quarter, its three days are the quarter's months, and four bosses make one year. That year is the proposed standard win, followed by endless mode. The pitch presented this structure; boss count, day length and quarter-end rules are not locked. See [the pitch session summary](pitch-session-summary.md).

The exact number of seasons/bosses needed for standard victory is OPEN beyond the four-quarter proposal above. Do not assume the first acquisition necessarily completes the whole run. Multiple bosses per run, variable boss order, and different starting targets have all been discussed.

### Replay and onboarding proposals from the user
- Randomised boss order could make runs different.
- A fixed introductory boss until the player first defeats it could let beginners learn a stable opponent before entering random rotation.
- Different targets each run or multiple acquisitions could extend replayability.
- None of the precise sequencing, unlock conditions, or boss counts is locked.

### Endless mode
CONFIRMED non-negotiable: the player must be able to continue endlessly after standard victory.

Discussed alternatives: more seasons with randomised bosses, or boss-free continued trading. Selection remains open. Retaining the same build/capital and preserving the recorded win after a later loss are assistant-recommended interpretations; exact transition and scoring rules still need confirmation.

## 8. Boss design

### Confirmed intent
Boss encounters must play differently from an ordinary harder day. Boss modifiers and active “attacks” should make the player adapt to what the rival does rather than repeat the same earning routine.

### Working direction
CONFIRMED intent (creator, 28 September): a boss left unchecked should snowball. It profits, gains capital and runs bigger pumps. HUMAN EVIDENCE: the current Manipulator does not snowball, which is a missing piece of the boss design rather than a balance tweak.

The active rival can influence ordinary days before the encounter. Its full active attacks occur during the confrontation. The distinction between background influence and active encounter needs specification.

Some bosses may defend themselves only; more aggressive bosses may attempt a counter-takeover. Counter-takeover is an encounter-specific possibility, not a third universal failure rule.

### Proposed encounter principles
- Telegraph intentions or provide discoverable clues.
- Make interventions change market decisions, not just increase required profit.
- Provide multiple responses, including ways to turn an attack into an opportunity.
- Avoid making a specialised build automatically helpless.
- A single failed response should usually create a recoverable setback; immediate defeat needs clear justification.

### Three example bosses accepted as a useful base, not final designs

| Boss | Possible influence/attack | Possible counterplay | Example failure |
| --- | --- | --- | --- |
| The Manipulator | Pumps an asset, attracts buyers, then dumps holdings | Anticipate reversal, short it, trade the temporary rise, or avoid it and earn elsewhere | Being trapped in the reversal destroys needed capital or wastes the remaining season |
| The Monopolist | Controls supply, restricts it, then floods the market | Trade around releases, switch assets, exploit the rival's overcommitment | Overconcentration leaves the player unable to exit on useful terms before an obligation/deadline |
| The Information Broker | Issues misleading/conflicting reports | Check evidence, use privileged information, wait selectively, take an opposing position | Following false signals loses capital, or waiting for certainty consumes the season |

These are illustrative financial-game mechanics, not claims about realistic corporate behaviour. They must remain readable and have meaningful counterplay.

## 9. Winning, losing, and acquisition routes

### Current baseline losses — accepted by the user
1. Season expires before takeover (or another explicitly permitted rival-defeat route).
2. Financial collapse.

Exact financial-collapse threshold is OPEN. Bankruptcy is the “you died” analogue. Debt could briefly avert it and offer recovery, but borrowing rules, limits, interest, and repayment are undecided. Zero cash is not automatically the chosen loss test.

### Takeover — taught default
The user supports these three clear approaches:
1. Accumulate enough capital and buy out the company / acquire a controlling holding.
2. Undermine its valuation so that control becomes affordable.
3. Turn the boss's attack against it, creating profit or weakening it enough to complete acquisition.

These can be routes to one goal rather than three separate victory conditions. A 51% threshold was only an illustrative simplified rule; the exact percentage, voting structure, share supply, and purchase process are not fixed.

### New alternate victory direction: company eradication
The user wants total eradication of the rival company considered as a viable/desirable alternative for some builds, while takeover remains the taught default. This is a desired direction requiring design, not a complete mechanic.

Open questions:
- What counts as eradication: insolvency, liquidation, zero remaining assets, or another explicit game state?
- Must destruction be caused by the player, or can a market event satisfy it?
- What reward distinguishes destruction from acquiring a functioning company?
- How does the route remain legible and avoid becoming either always preferable or a consolation prize?
- How does this alternate route change deadline wording and boss balance?

Acquisition should likely yield a benefit, but no reward has been selected. Do not assume passive income, inherited upgrades, or ownership bonuses without a decision.

This new direction revises the earlier assistant suggestion that weakening/crashing the company must always be followed by a purchase. That requirement may apply to the acquisition route; it must not rule out deliberate eradication.

### Deferred / optional mechanisms
- Shareholder support: combine purchased shares with voting support earned through encounter objectives. Interesting but adds complexity; reserve for later, not needed in the pitch.
- Distressed sale: force a financial weakness that opens an acquisition opportunity. Optional boss behaviour, not necessary now.
- Counter-takeover: some aggressive rivals may try to acquire the player's company; others only defend. It should have visible progress and counterplay. Exact loss resolution is open.

### Player company as class — tentative user proposal
The player may enter the run with a company functioning as their “class.” This could support counter-takeovers and different starting strategies. Company bonuses, starting tools, liabilities, ownership, and unlocks have not been designed. Do not present this as a fully confirmed class system.

## 10. Feedback loops — accepted directions, implementation open

Positive feedback reinforces change; negative feedback counteracts change or stabilises a variable. Rewards, punishments, deadlines, random crashes, and scheduled difficulty increases are not automatically feedback loops.

### Positive: profit builds earning power
CONFIRMED conceptual direction: profitable trades → more capital and purchasing power → larger positions and stronger purchased tools → greater potential profits → more capital.
This describes potential rather than guaranteed returns. Guaranteed knowledge progression also exists independently of spending profits.

### Negative: market correction
CONFIRMED baseline behaviour: price rises above changing underlying value → corrective selling pressure strengthens → price moves down toward that value → corrective pressure weakens. Below underlying value, corrective buying pressure can act in the opposite direction.
This stabilises asset prices, not necessarily player wealth. Explain it as ordinary fictional-market behaviour rather than a separately named player ability. Value remains uncertain to the player and can change with events; correction is a tendency, not an assured timed payout.

### Negative: rival response to threat
CONFIRMED direction: takeover threat rises → rival strengthens defence/interference → takeover progress is checked or pushed back → threat falls → defensive pressure eases.
The response must react to current threat; a scheduled permanent difficulty increase alone is not this loop. Exact threat measures and responses are OPEN. Prefer resistance connected to threatening the rival rather than punishing all money-making. Preserve counterplay and ways to exploit interventions.
Unresolved risk: saving up for one instantaneous purchase could bypass the response; the eventual acquisition design must consider this.

### Negative: conditional recovery support
ACCEPTED direction: financial stress rises → assistance becomes more available/effective → successful use improves finances → stress falls → assistance recedes.
Support can be distributed across certain knowledge upgrades, actionable news/information, and contextual encounters. It is not a universal rule that lower wealth grants more XP.
A hidden helper is acceptable in principle and need not announce itself. CONFIRMED design standard: it changes access to opportunities/information while preserving established market rules; it should not secretly force a purchased asset to rise. The player still recognises and acts on the opportunity. Exact triggers, safeguards, and whether all forms appear are OPEN.
Illustrative conditional upgrade: lower fees while reserves are low, with the benefit receding on recovery. Not a final upgrade specification.

### Pitch treatment
Accepted direction: foreground profit-driven growth versus responsive rival resistance; acknowledge correction as market behaviour and keep recovery support secondary. Final diagrams and specific boss actions remain unfinished. The prototypes exercise market correction and trading/power interactions. Rival resistance, conditional recovery, and the full progression loop remain unimplemented; none of these loops has established balance.

### Set-aside candidate
The earlier large-player-trade → adverse price impact loop is not adopted; it conflicts with the current default of no player price influence. Do not revive it silently.

## 11. Scope and open design questions

### Current pitch focus
Financial-market roguelike; clever trading; day encounters and upgrades; knowledge progression and supernatural deckbuilding; accessible independent markets; adaptable boss encounters; season deadline and takeover goal; financial collapse; endless continuation. Mention alternate eradication if it can be explained clearly without crowding the pitch.

### Deferred expansion / complexity
Shareholder voting, detailed distressed-sale mechanics, broader acquisition empires, extensive classes, and multiple special corporate systems. Their existence in discussion does not make them core requirements.

### Outstanding decisions
- A representative single-day trading/card sequence exists in the prototype; between-day results and upgrade choices still need definition.
- Exact market model, assets, and uncertainty tuning; accessible signals and no required specialist knowledge are settled principles.
- Specific starter capabilities, information abilities, and rule-bending powers.
- Specific boss actions and final visuals illustrating the accepted causal feedback-loop directions.
- How and when the active boss encounter begins; whether the player chooses the timing.
- How many bosses/seasons complete a standard run and what happens after each victory.
- Acquisition mechanics and ownership display; alternate eradication definition and rewards.
- Collapse/debt/recovery rules; optional counter-takeover implementation.
- XP/resource delivery, knowledge choices, shop economy, and spending on cards versus retaining takeover capital.
- Final card circulation and timing: one bounded draw/discard/reshuffle model has been implemented and creator-playtested; alternatives and final-game selection remain open.
- Company/class system and between-run progression (neither finalised).
- Endless format, difficulty escalation, and victory-record preservation.
- Audience, setting/tone, title, production platform, final visual/audio direction, monetisation, and core/extra/wish scope. The prototype main-screen baseline is now accepted C / Side dial; browser packaging is an experiment choice, not a production-engine decision.
- Pitch language, slide tool, final hook, timing, interaction, example and visuals.

### Current prototype, presentation, and evidence

**Accepted presentation:** [C / Side dial](../presentation-prototype.html), playable
revision `6532402`, with the [session conclusion](presentation-session-summary.md)
recorded at `75a44a1`. A dark green fixed board groups each company's quote,
readable chart, price contributions, holdings, and trades. Holdings include a
single compact side exposure dial and Sell All. The card hand is at the bottom,
End Turn at bottom right; card-first targeting supports re-click/Escape cancel.
Secondary news, company information, activity, and settings use scrolling drawers.
Viewport-responsive sizing and reduced repeated copy preserve room for graphs.
Comparison scenes and four earlier rounds are preserved as experiment evidence.

**Accepted communication direction:** show exact signed contributions and the
same-step price without this tick's price cards. A card can soften a fall while
the final quote still falls. The “No cards” annotation starts from the same
previous quote; it is not a whole-run alternate history. Keep current market
information separate from hidden future outcomes. Investigate reveals current
value while active, not future news resolutions.

**Temporary market/accounting:** three assets, 12 turns, $1,000 starting capital,
a $100 reference profit target, whole shares, 0.5% trading fees, and closing
settlement. Staggered public reports have seeded uncertain follow-throughs;
ordinary trades do not determine outcomes. The current engine remains the
[uncertain-market experiment](../.scratch/uncertain-market/spec.md), unchanged by
the presentation pass. Its authored event schedule, probabilities, correction,
volatility, and card numbers remain tunable test choices. The prototype contains
no rival, shorting, shop, knowledge progression, acquisition, or endless mode.
Their omission does not cancel broader design intentions.

**Human evidence:** creator feedback supports clearer attribution, more meaningful
risk and position sizing, and the selected presentation. There is no observed
classmate/novice study, universal device-fit result, or demonstrated strategic
balance. Scenario familiarity and seed selection confound comparisons. Shortening
the first test also compressed event timing, so its effects cannot be attributed
solely to presentation or session duration.

**Recorded technical checks:** prior sessions checked parsing, accounting,
replay/seed behaviour, trade independence, card conservation, contribution sums,
and shared state across scene switches using simulation and temporary DOM checks.
The presentation handoff records engine equality with the uncertain-market file.
These are historical verification records, not fresh execution in this backfill.
Agent browser layout/playthrough verification was unavailable in those sessions;
creator screenshots and feedback are the visual evidence. No production or
cross-device readiness is claimed.

## 12. Reference games and research context

These are study references, not instructions to copy mechanics or evidence that this game must use cards. Research was discussed in this conversation; links below support rechecking. Exact version-sensitive rules should be verified if reused prominently.

| Reference | Discussed relevance | Sources |
| --- | --- | --- |
| Balatro | Finite standard victory at Ante 8, optional endless continuation; bosses test builds with restrictions; combinations yield huge numbers | https://www.playbalatro.com/faq ; https://balatrogame.fandom.com/wiki/Gameplay_rules |
| CloverPit | Debt deadlines, charms, strong payout presentation, separate progression/escape objectives, endless play | https://store.steampowered.com/app/3314790/CloverPit/ ; https://cloverpit.wiki.gg/wiki/Endings |
| Insider Trading | Closest comparison: stock-themed roguelike deckbuilding, days, between-day drafting, weekly targets, player-created price movement | https://store.steampowered.com/app/3166810/Insider_Trading/ |
| The Invisible Hand | Trading-firm fantasy, news and privileged information, shorting, daily targets, coworker competition, manipulation | https://store.steampowered.com/app/628200/The_Invisible_Hand/ |
| Luck be a Landlord | Income combinations versus increasing obligations; basic twelfth-payment milestone, later landlord boss progression | https://store.steampowered.com/app/1404850/Luck_be_a_Landlord/ ; https://luck-be-a-landlord.fandom.com/wiki/Landlord |
| Offworld Trading Company | Winning by buying out opponents; tension between investing in growth and buying rival shares | https://www.offworldgame.com/game/gameplay |

Important comparison: Insider Trading describes its deck as determining market movement. Our possible distinction is interpreting an independently behaving market and exploiting it with tools, information, and powers. Independent market interpretation is now an accepted direction for our game; the exact simulation is open. The external game comparison is retained research context and should be rechecked if used prominently.

CloverPit research found conflicting guide counts for early drawer milestones. Do not repeat those counts as settled facts. Its broader distinction between debt survival, persistent progression, and escape was the useful design lesson; exact ending spoilers are unnecessary for this pitch.

## 13. Project source map

- Pelisuunnittelu 102 Summary.pdf: core and feedback loops, rewards/punishments, iterative design. Do not treat it as the full course.
- GDD base.pdf: concept, gameplay, 2–5 mechanics and interactions, rules, diagrams, monetisation, visuals, scope. Its six-minute statement is superseded by the actual five-minute pitch limit. Its reference-image counts are template guidance, not automatically mandatory slide counts.
- Game Design Concept & Pitch Template.docx.pdf: audience, differentiation, experience, style, progression, systems, product and production considerations.
- Pitch FIN.pdf: direct teacher pitch guidance; five-minute cutoff, audience, clarity, visuals, rehearsal, and a different game from the GDD task.
- [This living log](design-log.md): current design decisions, experiment status, evidence, and open questions. User corrections always take precedence.
- [Imported source index](sources/chatgpt-project/README.md): original school PDFs, searchable extracts, historical revision 3 and session 01, and former project configuration.
- [Prototype planning](prototype-planning.md), [first playtest](first-playtest.md), [card playtest](card-hand-playtest.md), and [uncertain-market playtest](uncertain-market-playtest.md): rationale and creator feedback for the mechanics experiments.
- [Presentation session conclusion](presentation-session-summary.md) and its linked round feedback: accepted UI, archived versions, evidence limits, and next experiment boundary.
- [Main README](../README.md): opening the playables and technical verification details. [CONTEXT.md](../CONTEXT.md) remains the domain glossary; experiment specifications in `.scratch/` describe temporary rules rather than a second final-game specification.
- The older prototype planning document cites two additional Downloads references. They were not among the six supplied imports; this backfill uses the repo's recorded planning and does not claim those references were imported.

## 14. Decision history

### 23 September 2026 — Initial project setup (retained)
Established the financial trading roguelike premise, solo five-minute slide-supported pitch, separate question window, Monday deadline, and no prototype requirement. Created the living log. At this point the fantasy, mechanics, and run objectives were open.

### Design discussions after setup, consolidated 25 September 2026
- Established days as encounters and upgrades between days.
- Prioritised cleverness over pressure, money-making fantasy, large numbers, recognisable market behaviour with supernatural liberties.
- Accepted the three upgrade categories. Left real time versus turn based explicitly open for future prototypes.
- Explored agency quotas, bankruptcy, rivals, finite seasons, and acquisition as possible objectives.
- Made endless continuation a firm requirement.
- Researched reference games; standard victory can be separate from stopping a successful build.
- Explored combining season deadlines and boss acquisitions, background boss influence, active attacks, randomised bosses, introductory fixed boss, and different endless formats.
- Read Pitch FIN.pdf and added teacher guidance.

### 25 September 2026 — Latest user decisions and revision 2
- Accepted season expiry and financial collapse as the clear baseline losses.
- Supported selective aggressive counter-takeovers, with other bosses remaining defensive.
- Suggested player company as run class; retained as tentative.
- Supported direct acquisition, valuation reduction, and exploiting boss attacks as clear takeover routes.
- Deferred shareholder support from pitch scope; distressed sale remains optional.
- Introduced total company eradication as a desired alternate route for some builds, with takeover taught by default.
- Requested a comprehensive rolling project-source document usable and updateable by future sessions. Replaced the initial brief with this consolidated record.

### 26 September 2026 — Revision 3: market agency, progression, cards, and loops
- Confirmed independent market behaviour by default, with price manipulation available through upgrades; basic trades do not require cards.
- Confirmed approachable, consistent signals and optional expert inference. Information upgrades may clarify public evidence or reveal unavailable information through appropriate channels.
- Confirmed guaranteed upgrades without spending profits; accepted knowledge capabilities, analysis, and specialisations. XP/choice-based knowledge plus paid supernatural cards is the working delivery direction, not a final economy.
- Accepted a supernatural deck for draw-driven improvisation; ordinary channels remain ordinary. Accepted analysis / insider tip / prophecy distinction.
- Accepted small starting decks in ordinary runs, primary shady-shop customisation, and card rewards through encounters and especially bosses. Tutorial introduces trading before cards.
- Explicitly deferred card handling and time model to prototype testing; rejected premature commitment, not any particular eventual circulation rule.
- Accepted positive profit-compounding direction and three balancing layers: market correction, rival response, and conditional recovery assistance.
- Confirmed uncertain, changing underlying value and distinction between value estimation and predicting price timing. Recovery help preserves market consistency and player agency.
- Prior takeover, destruction, loss, and endless-mode directions retained. No new numeric card rules, acquisition thresholds, boss counts, or run lengths chosen.
- Next useful task: illustrate a boss confrontation and how trading success becomes takeover progress, without over-specifying implementation.

### 26 September 2026 — Repository planning and small-engine playtests (backfilled)

Sources: [planning](prototype-planning.md), [first playtest](first-playtest.md),
[temporary assumptions](../ASSUMPTIONS.md).

- Confirmed synergies and engine building as core pillars; chose bounded creator
  experiments before a larger slice or novice testing.
- Implemented Investigate, Influence, and Informed Influence with manual market
  advance in a portable HTML experiment. This tests operating a supplied engine,
  not assembling one through progression.
- Creator found a mysterious/overloaded opening, limited independent value for
  Investigate, and an uninteresting tail after powers/target were exhausted.
- Revised from 18 to 12 steps, simplified presentation, and showed exact power
  attribution plus the same-step counterfactual. Creator reported substantially
  clearer effects; pacing and strategic success were not established.
- Favoured varied turn-based card hands and discard next. Modifier selection and
  real-time comparison remained deferred; the original fixed experiment order
  was superseded.

### 26 September 2026 — Card hands and uncertain markets (backfilled)

Sources: [card feedback](card-hand-playtest.md),
[market feedback](uncertain-market-playtest.md), and their linked specs.
Implemented card checkpoint `e2160bc`; market checkpoint `e0f5169`.

- Tested a recurring 14-card deck with seven powers, three-card hands and up to
  two plays per one-tick turn. Better card flow did not resolve obvious all-in
  investment in a predictable rising asset.
- Creator rejected repetitive concentrated rotation as the central experience;
  both concentration and diversification should have situational value and risk.
- Added staggered news, seeded uncertain follow-throughs, and consequential moves
  before reactive exits. Retained cards and accounting to probe the market change.
- Creator reported stronger tension, understandable losses, smaller commitments,
  more spreading of investments, and more useful protection. This supports the
  market direction, not a claim that diversification is now always balanced.
- Quieter intervals, dividends, capital commitments, and revised Stabilize
  behaviour remain candidates; no rebalance or extra economy was adopted.
- Agreed sequence: visual comparison and human selection, then a bounded
  rival-profit/offensive-play experiment. Rival information and rules remained open.

### 26–27 September 2026 — Five presentation rounds (backfilled)

Sources: [round 1](presentation-round-one-feedback.md),
[round 2](presentation-round-two-feedback.md),
[round 3](presentation-round-three-feedback.md),
[round 4](presentation-round-four-feedback.md),
[final conclusion](presentation-session-summary.md).

- Round 1: preferred grouped per-company information and dark colors; hidden
  graphs and scattered information undermined readability.
- Round 2: preferred the more game-like aesthetic and card-first targeting;
  whole-page scrolling interrupted decision context.
- Round 3: fixed-screen board improved play; small type and missed residual
  holdings exposed sizing and exposure-visibility problems.
- Round 4: viewport-responsive sizing improved reported fit. Creator preferred
  chart annotations, contribution bars, Sell All, and holdings near trades.
- Round 5: consolidated those choices, reserved graph space, reduced duplicate
  explanations, and fixed hand presentation. Creator explicitly accepted
  **C / Side dial** on 27 September. Presentation checkpoint complete.
- Market/card mechanics were preserved. This selects the prototype presentation,
  not final art direction, strategic balance, or a rival design.

### 27 September 2026 — Revision 4: adopt and backfill the living log

- Imported six supplied source files and archived former project configuration.
- At the user's subsequent request, adopted this log in the repository and
  backfilled the prototype and presentation work above.
- Updated current-state sections as well as history. Preserved imported revision
  3 and the original session record unchanged, with their source hashes intact.
- Retained broader progression, takeover, recovery, and endless-mode intentions
  while separating them from the smaller implemented experiments.
- No mechanics, playables, pitch deck, or final-game decisions were added by this
  documentation change. Next-work options remain bounded as below.

## 15. Next useful work

Pitch built 28 September; see [the pitch session summary](pitch-session-summary.md). Record the pitch feedback here when available. The strongest new prototype candidates from the pitch work are:
- a boss that snowballs when left unchecked;
- the three-day boss arc (prepare, boss notices you, boss fight).

The presentation checkpoint is complete. Start from accepted C / Side dial;
reopening layout exploration is not the default next task.

The agreed next prototype topic is **rival-profit and offensive play**: can an
opponent create reasons to influence assets beyond the player's own holdings?
Before implementing, select public rival information, whether intentions are
commitments, legal actions/reactions, action order, and closing profit comparison.
This is a bounded experiment candidate, not a completed rival specification or
an automatic replacement of the broader takeover/season objective.

EXPERIMENT (27 September, awaiting human playtest): these choices were made in a
grilling session and built as `boss-rival-prototype.html`.
- One boss day against The Manipulator; beat its closing profit.
- Its holdings are visible, and its moves are committed.
- Its unique powers are separate from the player's cards and include
  rule-bending ones.
- Telegraphs name the kind of move but not necessarily the target, so the
  player can't simply join a pump and dump.
- It uses public information only.

Rules, untuned numbers, and the playtest questions are in
`../.scratch/boss-rival/spec.md`. DEFERRED at the user's request: an *insider*
boss that trades toward hidden value, noted as an interesting exploration.

HUMAN EVIDENCE (round 2, concluded): the creator called the boss experiment a
very successful test.
- The game is much more interesting with the boss.
- Difficulty feels about right: one narrow loss and one +$416 win. Don't
  retune before testing with first-time players.
- The bigger boss effects and the merged Hostile Audit felt influential.
- Final tweaks: Wiretap lasts 2 turns, and an occasional bait combo (the player
  joins a pump → Halt → Dump).

This is prototype evidence for the boss/rival direction, not a final boss
design or a final balance.

HUMAN EVIDENCE (round 1 playtest): the boss made play far more dynamic and
changed the creator's plans, and beating its profit felt like a real boss
fight. It was far too easy, though, and the pump could be exploited without
risk. Round 2 is awaiting a playtest. It has restricted boss information plus a
Wiretap reveal card, a variable-length pump followed immediately by a dump,
situational Halt, and a stronger boss that dodges news.

Session conclusion and card-design handoff: `boss-session-summary.md`.

Creator-proposed next-session candidates (not built):
- Card improvements with premade deck presets for different play styles.
- A news rework: quarterly-style reports, an indirect generic news feed, and
  investor-sentiment comments, so trading is less "dodge the binary report".
- No fuller run before the pitch; the one boss scenario across many seeds is
  enough to demonstrate the idea.

The earlier suggestion to illustrate a Manipulator confrontation remains useful
for explaining the intended rival feedback loop in the pitch. It is not an
instruction to implement a full boss/acquisition system next. Pitch preparation
still needs a concrete example, final framing, loop diagrams, audience interaction
with fallback, and timed notes under five minutes. Choose work according to the
user's next request and the pitch deadline; a rival build is not a pitch requirement.

Card design concluded (27 September): the current prototype release is
`card-design-prototype.html` with three classes; see revision 5 above and
`../.scratch/card-design/`. DEFERRED creator follow-ups:
- A Manipulator power that clears player effects or shortens their durations,
  to counter stacked engines such as the Financier's.
- A hard mode where the boss is much more dangerous.
- Trade UI feel: share-quantity entry is clunky; revisit buy/sell sizing
  controls in a later session.

Real-time comparison, final circulation, between-day progression, modifier choice,
and balance work remain open. Continue with a question and human checkpoint;
completed UI acceptance does not authorize an unbounded implementation sequence.

### 27 September 2026 — Revision 5: card design and classes

- Confirmed (prototype scope, creator decisions in a grilling session): prices
  have three sources, Market forces, Boss effects and Player effects. Effects
  have one timing (Duration, Next tick, Immediate, Persistent), with stacks
  separate from timing, and they combine as instances, so any card can be
  played on any valid target. Focus replaces "play 2 cards". Retain, Burn and
  Empowered are card keywords. The hand is capped at 5.
- Confirmed: a Class is a theme, hand rules, a deck from the shared pool
  (any copy counts) plus Class cards, and a passive. Class cards may be
  stronger than pool cards. A Custom class has no limits.
- Changes to earlier decisions: Stabilize now cancels all Market forces;
  Accelerate pulls 50% of the gap as a Player effect; Extend lengthens every
  Duration effect on a company, the boss or you; Echo clones onto any target;
  Hostile Audit is a debuff (draw 1 fewer, −1 Focus). The boss brain is
  unchanged.
- Experimental numbers: every card number, class deck and passive in the spec.
- Human evidence: one game per class. The classes play differently; Insider
  was most enjoyable; one Financier run led by over +$1,000 (possibly luck);
  Gambler felt unlucky. The creator declared the phase complete after small
  fixes, making this the current prototype release.
- Agent checks: rule fuzz clean; boss unchanged against a passive player;
  simple heuristic win rates Insider 41%, Gambler 53%, Financier 34%.
- New proposals (not accepted as rules): a boss power that clears the player's
  effects or shortens durations; a hard mode.
- Next useful step: wider playtests of the release, especially the Financier's
  stacking line, before adding boss counters.

### 28 September 2026 — Revision 6: pitch built

- Confirmed (creator, for the pitch):
  - The working name is Rogue Market. Occult or "dark" names are deferred until the prototype conveys that theme.
  - Wording: "todellinen arvo" (real value) is the in-game value, the company's value per share based on how it is really doing. "Koettu arvo" (perceived value) is used for real-world trading, and plain "arvo" (value) on the core mechanics slide. "Underlying value" and "hidden value" were rejected as odd.
  - Business model: about €10 one-time purchase on PC (Steam), later expansions with bosses, classes and cards, no microtransactions.
  - Market framing: hype and correction are counteracting forces, not good or bad for the player; with shorting, both directions can pay. Positive or negative describes a loop's direction, not its effect on the player.
- Working direction (creator-proposed): three days per boss (prepare, boss notices you, boss fight) with upgrades between days. One boss is one quarter, and four quarters make one year, the standard win, followed by endless mode (§7).
- Human evidence and design gap: the boss should snowball when left unchecked, and the current prototype boss does not (§8).
- Observation: the prototype's information overload works against the short, fast runs the creator wants. "Short runs" was therefore dropped as a Balatro comparison.
- Proposed example: general, non-company news (a long winter forecast) that moves several companies in different directions. It fits the news-rework candidate in §15.
- Deferred: aligning `CONTEXT.md` and the prototype UI ("underlying value") with the pitch wording.
- Built: Finnish and English decks in full and short versions, a short Finnish version where the boss is revealed late, and a speaker-notes page. The session summary lists them.
- Open: which deck was presented and the pitch feedback.
- Next useful step: record the pitch feedback, then consider a boss snowball and a day 1/day 2 lead-in as the next prototype topic.

### Template for future session entries
Date / revision:
- Confirmed decisions and rationale:
- Changes to earlier decisions:
- Experimental implementation choices:
- Observations and evidence limits:
- New proposals (not accepted):
- Deferred or rejected ideas:
- Open questions:
- Next useful step:

## 16. Adopted documentation arrangement

`docs/design-log.md` is the living design entrypoint, adopted on 27 September 2026.
Update relevant current-state sections and append concise dated history after
substantive design work. Increment the revision when making a substantive update.
Record final design intent, temporary experiment settings, and evidence at their
actual scope; do not infer acceptance from code existing or a test passing.

The imported revision 3, dated session 01, PDFs, and former project instructions
remain preserved sources in `docs/sources/chatgpt-project/`. Their older workflow
instructions and claims to be current do not override this adopted arrangement.
The source manifest continues to describe those unchanged originals.

Repository playtest and presentation records retain detailed historical evidence;
this log links to them instead of rewriting their past-tense status. When a later
decision supersedes one, update the current-state summary and record why. Preserve
unresolved alternatives. `CONTEXT.md` remains the domain vocabulary and the README
the playable/technical entrypoint. No separate ADR is created merely to duplicate
this adoption; use the existing repository domain-documentation rules when needed.
