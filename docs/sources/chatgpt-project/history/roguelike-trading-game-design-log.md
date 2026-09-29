# Roguelike Trading Game — ROLLING DESIGN DOCUMENT

Revision: 3  
Last updated: 26 September 2026 (Europe/Helsinki)  
Status: Active design; intended as shared context for all project sessions.  
Stable filename: Roguelike_Trading_Game_Design_Log.md

## 1. Instructions for every future session

Read this document before continuing the design. It is a rolling summary and decision record, not a finished GDD or pitch script. Later explicit user decisions supersede earlier entries.

At the end of each substantive design session:
1. Update the relevant current-state sections, not just the history.
2. Label ideas accurately: CONFIRMED, WORKING DIRECTION, PROPOSED EXAMPLE, DEFERRED, or OPEN.
3. Never promote an assistant suggestion to a confirmed decision without user acceptance. General approval does not settle every illustrative number or implementation detail.
4. Record new decisions, rationale, rejected/superseded directions, remaining questions, and a useful next step in a dated session entry.
5. Increment the revision and update the date. Keep this stable filename and update the existing document where possible.
6. If direct project-source editing is unavailable, deliver an updated copy and tell the user to replace the old source. Do not claim that generating or saving a file automatically refreshed its project-source attachment.
7. Preserve unresolved alternatives. Do not reopen settled priorities without explaining a concrete reason.

Use user instructions as authoritative. Treat course materials as guidance or requirements according to their actual wording; do not invent a grading rubric. This document records design intent, not tested balance or implemented functionality.

## 2. Quick current-state summary

- CONFIRMED: financial-market trading roguelike. Clever trading, large profits, cash flow, and powerful combinations lead; pressure supports that fantasy.
- CONFIRMED: independently behaving market; ordinary player trades do not influence prices by default. Certain upgrades can grant price influence.
- CONFIRMED: accessible, streamlined signals; extensive trading knowledge is not required. Experienced players can infer more from consistent evidence.
- CONFIRMED: prices tend toward changing underlying value; the exact value is not automatically visible. Estimation and information matter; value and short-term price prediction are different.
- CONFIRMED: days are encounters, with between-day upgrades. Real time versus turn based remains OPEN for prototyping.
- CONFIRMED: guaranteed upgrades without spending profits. Knowledge includes capabilities, analysis, and specialisations; exact XP/resource delivery remains a WORKING DIRECTION.
- CONFIRMED: a supernatural deck supplies changing powers and encourages improvisation. Basic buying and selling never require drawing an action card.
- CONFIRMED: ordinary runs start with a small deck; introductory tutorial teaches basics first and introduces cards near its end. Shady shop is the primary deck-customisation source, with encounters and especially bosses also supplying cards.
- CONFIRMED: analysis, insider tips, and prophecy are distinct. Ordinary advantages use ordinary channels; the deck stays supernatural.
- CONFIRMED loop directions: profits enable greater earning power; market correction stabilises prices; threatened rivals push back; conditional recovery support helps struggling players without changing established market rules.
- WORKING DIRECTION: seasons with rival defeat before a deadline; takeover is the taught default. Company destruction remains a desired alternate route requiring definition.
- CONFIRMED: season expiry and financial collapse are baseline losses; optional endless continuation after standard victory is required.
- OPEN: exact cards and circulation rules, market model, acquisition process, boss encounter structure, run length, final visuals/title, and monetisation.

## 3. Pitch context and requirements

### Confirmed logistics
- Solo pitch with supporting slides, Monday 28 September 2026.
- Five minutes total, including speaking, pauses, slide changes, demos, and audience interaction. The teacher will cut off at five minutes.
- Questions have a separate flexible window afterward.
- No prototype is required. Prototyping is a proposed future design method, not a deliverable before the pitch.
- The user initially reported no official assignment brief or rubric and substantial freedom. The subsequently supplied teacher pitch slides add explicit guidance, recorded below.
- The pitched game must not be the same game as the GDD assignment.

### Content priorities
- Core mechanics, core gameplay loop, positive feedback loop, and negative feedback loop must be clearly communicated (user requirement and course emphasis).
- Other class topics include monetisation, core/extra/wish scope prioritisation, and iterative design; the available lessons are not the complete course.
- Likely open with a compelling one- or two-sentence concept statement.
- Use game comparisons to build familiarity, explaining exactly what each comparison illustrates.
- Use visual references, a gameplay example/mockup, and explanatory diagrams as useful. No final assets or slide order exist yet.
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

The user explicitly chose to leave this question open for prototyping. The earlier assistant preference for turn-based play is not a decision. Turn based could still have multiple decisions/ticks per day; one decision per day is not assumed.

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

### Explicitly deferred card-handling questions
The user requested these remain OPEN for prototype testing rather than speculative decisions before the pitch:
- Does the discard pile reshuffle when the draw pile is empty? Are some cards exhausted for the day?
- Is a new hand drawn each turn? Are unused cards discarded or retained?
- In real time, are draws timed, cards on timers, or hands manually discarded/refreshed?
- What is the maximum hand size, and what happens when it is full?
- Can abilities or other actions invoke extra draws, and at what cost?
- What resets between days, and how do upgrades affect circulation?

The assistant's opening-hand, timed/phase draws, hand-retention, and once-per-day suggestions were NOT accepted. Do not present them as defaults already chosen. Real time versus turn based is also still OPEN. Prototype evaluation should ask whether players improvise enjoyably, can access combinations sufficiently, and can manage cards without losing track of the market. No prototype is required for Monday.

## 7. Seasons, rivals, and the run endpoint

### Evolution and current working direction
The initial alternatives were a finite season and a rival-company takeover. The current direction combines them: defeat/acquire the active rival before the season ends. The calendar supplies urgency; takeover supplies a visible objective.

A deadline limits trading opportunities even in turn-based play. It does not decide the real-time question.

Potential structure: ordinary trading days under the rival's influence → active boss encounter → rival defeated → next season or standard-run victory → optional endless continuation.

The exact number of seasons/bosses needed for standard victory is OPEN. Do not assume the first acquisition necessarily completes the whole run. Multiple bosses per run, variable boss order, and different starting targets have all been discussed.

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
Accepted direction: foreground profit-driven growth versus responsive rival resistance; acknowledge correction as market behaviour and keep recovery support secondary. Final diagrams and specific boss actions remain unfinished. No balance or implementation has been tested.

### Set-aside candidate
The earlier large-player-trade → adverse price impact loop is not adopted; it conflicts with the current default of no player price influence. Do not revive it silently.

## 11. Scope and open design questions

### Current pitch focus
Financial-market roguelike; clever trading; day encounters and upgrades; knowledge progression and supernatural deckbuilding; accessible independent markets; adaptable boss encounters; season deadline and takeover goal; financial collapse; endless continuation. Mention alternate eradication if it can be explained clearly without crowding the pitch.

### Deferred expansion / complexity
Shareholder voting, detailed distressed-sale mechanics, broader acquisition empires, extensive classes, and multiple special corporate systems. Their existence in discussion does not make them core requirements.

### Outstanding decisions
- One concrete ordinary day: information, available actions, payoff, and upgrade choice.
- Exact market model, assets, and uncertainty tuning; accessible signals and no required specialist knowledge are settled principles.
- Specific starter capabilities, information abilities, and rule-bending powers.
- Specific boss actions and final visuals illustrating the accepted causal feedback-loop directions.
- How and when the active boss encounter begins; whether the player chooses the timing.
- How many bosses/seasons complete a standard run and what happens after each victory.
- Acquisition mechanics and ownership display; alternate eradication definition and rewards.
- Collapse/debt/recovery rules; optional counter-takeover implementation.
- XP/resource delivery, knowledge choices, shop economy, and spending on cards versus retaining takeover capital.
- Card draw, discard, reshuffle, hand limits, extra draws, and timing interactions: deliberately deferred for prototyping.
- Company/class system and between-run progression (neither finalised).
- Endless format, difficulty escalation, and victory-record preservation.
- Audience, setting/tone, title, platform, visual/audio direction, main screen, monetisation, core/extra/wish scope.
- Pitch language, slide tool, final hook, timing, interaction, example and visuals.

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
- This rolling document: evolving project decisions and open questions. User corrections always take precedence.

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

## 15. Suggested next session

Develop one broad boss example, preferably the Manipulator: what changes from ordinary trading, how the rival responds to threat, how trading results advance acquisition, and how the player can turn interventions into opportunities. Keep destruction as a desired alternate route without inventing its resolution. Use the example to ground the accepted feedback loops for the five-minute pitch.

Do not reopen precise card circulation or real time versus turn based without prototype evidence or an explicit user request. After the boss example, priorities are the representative screen/sequence, pitch framing, audience interaction, and timing—not implementing a prototype.

### Template for future session entries
Date / revision:
- Confirmed decisions and rationale:
- Changes to earlier decisions:
- New proposals (not accepted):
- Deferred or rejected ideas:
- Open questions:
- Next useful step:

## 16. Proposed documentation arrangement (not yet adopted)

User asked whether stable decision files should complement this rolling log. Assistant recommendation:
- Keep this stable filename as the sole current-state entrypoint; update relevant sections and concise dated history each session.
- Optionally keep immutable dated session records for accepted decisions, rationale, alternatives, and unresolved questions. These describe what was agreed at that time, not automatically what is current forever.
- Create separate numbered decision records only for consequential decisions needing durable rationale; avoid one file per small choice or duplicating the whole current design.
- On reversal, write a new record naming the superseded decision and update this rolling log. Preserve original historical text; never silently rewrite history or treat old decisions as permanently unchangeable.
- Latest explicit user instruction takes precedence. This log states the current design; archived records explain its history. Surface contradictions rather than resolving them by guessing.
- For this pitch-sized project, the log and its dated history may be sufficient. Additional archives are optional, not required deliverables or newly imposed workflow rules.

Revision 3 is a replacement upload candidate. Producing this file does not automatically replace the project's existing source attachment; the user plans to upload it.
