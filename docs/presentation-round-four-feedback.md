# Presentation round four: creator feedback

Source: creator feedback and four screenshots, September 27, 2026. Preserved
artifact: `presentation-round-four-prototype.html`, commit `d405928`.

The fit was much better. Sell All was appreciated. B's right-side Actual and
No cards graph labels were especially liked; the duplicate legend below the
graph was unnecessary. Contribution bars were preferred, with total card impact
in the same area but without its explanatory subtitle.

Bulky panels squeezed the graph. Price and chart should remain at the top,
movement below, and holdings should sit near Buy/Sell. Keep the report brief
close to this interaction cluster. Compact shares, invested value and percentage
without repeated prose. Exposure should use one encoding: a bar, or a small
side dial replacing it entirely. Remove redundant card-play guidance and the
turn fraction from End Turn. Group Activity and News archive together.

## Implemented refinement

Round five applies these common improvements to all scenes, retaining three
holdings treatments: stacked bar, compact bar/statistics, and side dial. The
graph has a nonshrinking minimum height, with a smaller minimum on short/narrow
viewports; a company-local scroll fallback remains for constrained screens.
Future-outcome concealment and the market engine are unchanged.

The human evidence establishes improved round-four fit, not round-five visual
validation. Source and in-memory checks passed; actual browser review remains
blocked by the previously reported file-URL restriction.
