# Small Engine — first playable prototype

Open **trading-prototype.html** in a modern browser (double-click the file).
No installation, build, server, account, or internet connection is needed.

This throwaway prototype implements experiment 1 from
[the accepted plan](docs/prototype-planning.md): operate a small engine.
It asks whether allocating limited information and influence across overlapping
opportunities produces understandable, interesting decisions. No human evidence
or design verdict exists yet.

## Try it

1. Read the opening news and select a company.
2. Set a whole-share quantity. Buy and sell at the displayed quote; the preview
   includes the 0.5% fee. Spend cash across opportunities as you see fit.
3. Use Investigate to reveal live underlying value. Use Influence while a company
   is revealed to activate the equipped Informed Influence modifier.
4. Advance the market when ready. There is no action timer. Inspect the news,
   price changes, power durations, and positions after each advance.
5. Finish 18 steps for closing settlement and a short result view. Restart repeats
   the same scenario and restores cash and both power supplies.

Allow roughly 5–10 minutes for the first trial. Refreshing loses progress.
Keep the separately labelled debug disclosure closed during playtests.

## Observe before expanding

- Can you explain a trade using public evidence and a power, without a facilitator?
- Which plausible alternative did you pass over because of limited cash or powers?
- Did the synergy affect your choice, or did you repeat the same sequence blindly?
- Could you explain a disappointing outcome? What would you try differently?
- If you reached the target, did it make further decisions less interesting?

Profit alone is not evidence of engagement. Replays here are confounded by
scenario familiarity. Experiment 2 and fresh variants await user feedback.

## Verification performed, September 26, 2026

Both inline JavaScript blocks parsed under Node. A temporary direct simulation
smoke check exercised purchases, partial sales, average-cost accounting,
unaffordable/oversized trade rejection, a full 18-step session and closing
settlement, two-use power exhaustion, three-step revelation and Influence expiry,
boosted versus ordinary Influence, unchanged underlying value under Influence,
and fresh-state resource restoration. All checks passed. An ordinary-trade run
and a no-trade run had identical market quotes at all 18 steps.

**UI verification remains unperformed.** The browser automation tool rejected
the local file URL because its security policy allows only HTTP/HTTPS and forbids
workarounds for the blocked action. No screenshot inspection, browser console
check, click-through session, or restart-button verification is claimed.
The direct simulation checks do not substitute for those UI checks.

No production test suite, dependencies, or general engine was added. The file is
the runnable source. See [ASSUMPTIONS.md](ASSUMPTIONS.md) for exact temporary rules.

Only the first checkpoint is implemented: no card draws, upgrade selection,
real-time mode, shops, multi-day progression, or expanded content.
