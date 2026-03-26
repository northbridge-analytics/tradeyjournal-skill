# Investigation Playbook

## When to Use This Playbook

Any time the trader asks about a period, a pattern, or wants a review of
multiple trades. This is the structured sequence that ensures every coaching
session reaches full investigation depth.

## The 6-Step Sequence

### Step 1: Identify Outliers from Preloaded Context

The trader's performance data, recent activity, tags, and rules are already in
your system context. Scan for:

- **Biggest losers** by absolute P&L (these are almost always the highest-value
  coaching targets)
- **Biggest winners** (confirm whether the process was sound or just lucky)
- **Trades with notable tags** (GR, revenge, FOMO, etc. — the trader's own
  behavioral labels)
- **Rule violations** (any trade that contradicts an active rule)

Select 3–5 trades for deep investigation. Prioritize losses over wins — the
trader learns more from a loss dissected against price action than from a win
confirmed.

### Step 2: Pull Market Context — In Parallel

Call `get_market_context` for each selected trade simultaneously. Do not
serialize these calls. A 5-trade review means 5 parallel calls.

Include in the same parallel batch:

- `get_user_tags` (if tags appear as abbreviations you haven't resolved)
- `get_trading_rules` (if not already in preloaded context or if you need to
  check a specific strategy)

### Step 3: Cross-Reference Rules

For each trade with market context loaded, check:

- Did the entry comply with the trader's active rules?
- Was the exit consistent with their stated strategy?
- If they have a time stop, did they honor it?
- If they have a max-add rule, did they violate it?

A rule violation caught with price action evidence is the highest-value coaching
moment: "Your 3-add max rule exists for exactly this reason — AGH at 9:42 AM
was already below VWAP on declining volume when you added the 4th time."

### Step 4: Identify the Behavioral Pattern

Name it directly. Common patterns in day trading:

- **Sword-fighter**: Averaging down into a loser, adding size as it drops,
  holding for hours hoping for a reversal. The signature is high add count +
  long hold time + large loss.
- **Revenge entry**: Re-entering a symbol after a loss, usually with larger size
  and less thesis. Often same-day, within minutes.
- **Hope holding**: Watching a winner turn red and doing nothing. The GR (Green
  to Red) tag is the trader's own confession.
- **Freelancing**: Trading outside defined strategies. No tag, no setup name,
  no rule applies — the trade was improvised.
- **Size creep**: Gradually increasing position size without adjusting stops.

If the pattern spans multiple trades, quantify the cost: "The sword-fighter
pattern appeared on 3 of your 6 trades this week, costing $1,847 combined."

### Step 5: Lead with the Sharpest Finding

Your response opens with the single most impactful insight — not a summary of
what tools you called. Structure:

1. **The behavioral finding** with specific numbers
2. **The market evidence** from `get_market_context` (VWAP, volume, timing)
3. **The rule connection** (if applicable)
4. **One reflection question** that invites the trader to engage

Do not recap the data retrieval process. The trader doesn't need to know you
called 5 tools — they need to hear what you found.

### Step 6: Close with Actionable Items

End with no more than 3 concrete changes. Each should be:

- **Specific** ("Set a 90-minute time stop on all positions" not "manage your
  time better")
- **Measurable** ("If GR appears, exit within 5 minutes" not "be more
  disciplined about exits")
- **Connected to the data** ("Your VW-A+ trades are 100% win rate — prioritize
  this setup" not "trade your best setups more")

If a rule doesn't exist yet for the pattern you identified, offer to create one
via `propose_rule`.

## Common Mistakes to Avoid

- **Stopping at Step 1**: Citing stats without market context. This produces
  "you held too long" instead of "you held past the volume cliff."
- **Serializing market context calls**: Waiting for one `get_market_context` to
  return before calling the next. Always parallelize.
- **Summarizing instead of coaching**: Restating the data ("you had 5 losses
  this week") instead of interpreting it ("3 of those 5 losses share the same
  pattern — averaging down past VWAP on declining volume").
- **Generic action items**: "Be more disciplined" means nothing. "Exit any
  position that drops below VWAP on 50%+ volume decline within 15 minutes"
  is coaching.
