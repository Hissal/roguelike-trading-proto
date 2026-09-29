# Research what real quarterly reports and market news contain

Status: resolved
Type: research

## Question

What does a real quarterly report say about how a company is doing (headline figures, guidance, beats/misses), and how does general market news (weather, world events, sector news naming companies) differ from it? Which handful of signals could a non-expert player read at a glance, and how do real prices react to each?

## Answer

Findings: branch `research/reports-and-news`, file
`docs/research/reports-and-news.md`.

- **Quarterly report**: prices react to beat or miss *against expectations*, not
  to the raw figures. Hyped stocks take a much harder hit on a miss than they
  gain on an equal beat. After the jolt, prices keep drifting the same way for a
  while (post-earnings drift). Guidance, especially a cut, adds drift. The report
  reveals real value.
- **General news**: mood without new facts causes a dip that reverts. Substantive
  news (weather really does move utility demand) also changes future
  fundamentals. Sector news moves groups together, and smaller or linked firms
  (suppliers) react later. News moves perceived value.
- **Game-ready formats (suggestions)**:
  - Report card: Result BEAT/MET/MISSED, Revenue ▲▼▬, Profit ▲▼▬, Outlook
    Raised/Held/Cut, plus a one-line management quote.
  - News item: Headline; Affects ▲/▼ per sector or company; Kind Mood (fades) or
    Fundamental (shows up in the next report); Lasts N ticks.
  - Showing an expected figure before the report lets the player bet on beat or
    miss. Hiding an item's Kind is a lever for information cards.
