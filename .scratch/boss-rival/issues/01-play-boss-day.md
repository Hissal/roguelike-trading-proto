# 01 — Play a boss day against The Manipulator

Status: resolved
Type: prototype

Play `boss-rival-prototype.html` (double-click). Round 1 had switchable
Exact/Partial/Hazy telegraphs; round 2 uses restricted info plus the Wiretap card.
The questions and the build are in `../spec.md`.

Report back on the spec's "What to look for" list, especially whether the boss
made you use cards on companies you didn't hold, and which telegraph mode felt
right.

## Comments

**27 Sep — round 1 playtest (creator):** The boss made the game much more
interesting and changed card and trade decisions, and beating its profit felt
like a boss fight. But it was far too easy on all telegraph levels, the pump was
exploitable risk-free, and the rule powers were too readable. Full notes and
round-2 decisions are in `../spec.md`. Round 2 rebuilt the boss:
restricted info plus the Wiretap card, the pump→dump operation, bigger
numbers, Hostile Audit, situational Halt, and a news-dodging, more profitable
boss. It is awaiting a second playtest.

**27 Sep — round 2 playtest and conclusion (creator):** The overall feel
improved and the difficulty now feels about right. The creator lost one game
narrowly, then won another by +$416 after a couple of strong plays. Tune it no
further before wider testing with first-time players. The boss powers felt
much more influential: the bigger values and merging the card-limiting attacks
both worked. Wiretap was too strong at 3 turns. When the creator went all in
on an active pump and the boss halted it, the creator expected a dump, but the
boss kept pumping. The creator wants that bait → Halt → Dump combo to happen
occasionally.

Final changes:
- Wiretap lasts 2 turns.
- When the player holds a company in a running pump, the boss has a 40% chance
  to halt it (if it didn't attack last turn and 2+ turns remain), pump once
  more, and dump the next turn while the player is locked in. That verified
  correctly in 107/107 simulated traps.

## Answer

**Verdict: a very successful test.** A telegraphed boss with unique powers made
the game much more interesting. It changed card and trade decisions, created
offense and defense, and beating its profit felt like a real boss fight rather
than a flat target. Restricted boss information plus a temporary reveal card
worked better than one fixed telegraph level. Difficulty is accepted as-is
pending first-time-player testing. The rules are in `../spec.md`.
