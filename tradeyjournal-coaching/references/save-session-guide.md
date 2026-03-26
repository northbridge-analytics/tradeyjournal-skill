# Market Context Guide

## Why Market Context Is Non-Negotiable

`get_market_context` returns VWAP, volume profiles, gap analysis, and intraday
price action for a symbol on a specific date. This is the tool that separates
TradeyJournal coaching from generic trading advice.

Without it, you can only describe _what the trader did_. With it, you can
describe _what the market was doing while they did it_. The difference is the
entire product.

## When to Call It

**Always call `get_market_context` when coaching on a specific trade.** The only
exceptions:

- Same-day trades (data requires T+1 settlement)
- Delisted symbols (API returns no data)
- API gaps (rare — say so directly if it happens)

For multi-trade reviews, call it for the top 3–5 trades by absolute P&L. Do
not skip it because the review is "broad" — the Weekly Review benchmark showed
this is exactly when Claude drops market context, and exactly when it matters
most.

## What the Tool Returns

- **VWAP** (Volume Weighted Average Price): Where institutional money traded.
  Entry relative to VWAP tells you if the trader was buying into strength or
  weakness.
- **Volume profile**: Volume by time interval. Volume cliffs (sharp drops) are
  exit signals. Volume surges confirm moves.
- **Gap analysis**: Pre-market gap percentage. Large gaps (>30%) have different
  behavior than grinds from open.
- **Key price moments**: Intraday highs/lows with timestamps. These anchor the
  narrative — "at 9:10 AM the stock made a new high on 79% less volume than
  the prior candle."

## Quality Benchmark: With vs. Without

### With Market Context (Target Quality)

"IBO gapped up +87% from $0.4133, opened at $0.7728 on 205M volume — 40x its
average. Your entry at $0.7343 was essentially at VWAP ($0.7332), which is
actually a solid read. The problem was the exit. At 9:10 AM, IBO printed a new
high at $0.89 on 79% volume dropoff from the prior 5-minute candle. That's the
classic warning: new price, no conviction. Buyers left and you were the last
one in. You entered at 52% of the day's range and exited at 12%."

Notice what this does:

- Cites specific prices and times
- Anchors entry relative to VWAP
- Identifies the exact moment the trade failed (9:10 AM volume cliff)
- Quantifies the range collapse (52% → 12%)
- Makes the pattern undeniable with the trader's own data

### Without Market Context (Below Standard)

"You held too long and turned a winner into a loser. Consider setting tighter
stops."

This is what any generic chatbot produces. No prices, no timing, no VWAP, no
volume evidence. The trader can dismiss it because there's nothing specific to
confront.

## How to Weave Market Data into Coaching

Do not dump the raw `get_market_context` output. Extract and integrate:

**Entry analysis**: Where did they enter relative to VWAP? Above VWAP on high
volume = chasing strength. Below VWAP on low volume = catching a falling knife.
At VWAP = solid institutional-level entry.

**Hold analysis**: What happened to volume while they held? If volume dried up
and they held, they were the last believer. If volume surged against them, they
were fighting the tape.

**Exit analysis**: Where was the signal to exit? Volume cliffs, VWAP breaks,
new highs on declining volume. Pinpoint the exact time and price where the
trade's thesis died.

**Pattern connection**: Connect the market data to the behavioral pattern. "You
added your 4th buy at 10:15 AM — 45 minutes after volume fell off a cliff at
9:30. The sword-fighter pattern isn't just about adding to losers, it's about
adding _after the market has already told you the trade is dead_."

## Multi-Trade Market Context

When reviewing 3+ trades, look for patterns across the market data:

- Are all the losses in the same volume environment? (Low-volume fades)
- Are entries consistently above or below VWAP? (Chasing vs. value)
- Do the winners have different volume signatures than the losers?
- Is there a time-of-day pattern in the failures?

These cross-trade observations produce the most powerful coaching moments
because they reveal _systematic_ behavior, not individual mistakes.
