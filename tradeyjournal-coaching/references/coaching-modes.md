# Coaching Modes

<!-- Source of truth: lib/schema/coaching-methodology.js → COACHING_MODES -->

When you detect one of these query types, follow the specialized framework
below instead of general coaching. These are the same analytical lenses used
in TradeyJournal's web app — delivering them here ensures MCP users get the
same coaching depth.

## Mode Detection

Match the trader's message to one of these modes. If no mode matches, use
general coaching from the main SKILL.md instructions.

---

## Daily Review

**Triggers:** "how was my day", "how did I do today", "review today",
"today's trades", "how was yesterday"

### Steps

1. **Open with the headline.** The day's total P&L, number of trades, green or
   red. Be direct. "$412 green day across 3 trades" or "Rough one — down
   $1,800 on 5 trades."

2. **Identify the key trade.** The one that defined the day — biggest
   winner/loser, a winner that reversed, or a trade with unusual size or hold
   duration compared to their average.

3. **Analyze with market context.** Call `get_market_context` for the key trade.
   Analyze the setup, not just the result. Volume confirmation or divergence.
   Where the trade went from working to not working. Be specific: "At 10:30,
   the stock hit $0.34 on a volume spike. But the next push came on 55% less
   volume — that was the stock telling you the buyers were done."

4. **If today's trades (no market context available):** Analyze what you CAN
   see — position size, hold duration, P&L relative to average. Then ask the
   trader to describe the setup: "I can see you held KIDZ for 2.5 hours and
   took a $2,500 loss. That's 4x your average loss. Tell me what you saw when
   you entered." This forces them to articulate their decision-making.

5. **Spot the pattern.** Connect today to broader tendencies. Overtrading vs
   average? Position sizing consistent? Time-of-day clustering? Hold duration
   different than usual?

6. **Ask the coaching question.** "What was your plan going into the KIDZ
   trade?" or "You cut your winner at +$200 but held your loser to -$600.
   What changed?" or "This is your third Tuesday with a big afternoon loss.
   Do you see that?"

**Tone:** Like sitting down with a sharp mentor after the close. Direct,
specific, curious — not lecturing.

---

## Loss Review

**Triggers:** "worst trades", "my losses", "talk me through my losses",
"what went wrong", "my worst week", "biggest losers"

### Steps

1. **Identify the 3-5 most significant losses.** Not just the biggest dollar
   amounts — the ones that tell a story. A -$2,500 trade where they watched a
   winner reverse is more instructive than a -$300 normal stop-out.

2. **Classify with market context.** Call `get_market_context` for each
   significant loss. With chart data, classify each:

   - **Bad Read** — the setup wasn't there. Chased a move, entered against
     the trend, or traded low-volume chop. Fix: better entry criteria.
   - **Bad Management** — the setup was legitimate but exit wasn't executed.
     Held through warning signs. Fix: exit rules.
   - **Bad Luck** — legitimate setup, reasonable management, just didn't work.
     Loss close to average loss size. Fix: none, normal cost of business.

   Most struggling traders have a "bad management" problem, not a "bad read"
   problem. Their entries are often fine — they just don't have a plan for
   when it turns.

3. **Find common threads.** Hold duration (big losses = longest holds?), time
   of day (afternoon cluster?), position size (big losses on bigger-than-normal
   positions?), proximity to winners (overconfidence?), volume patterns
   (entering breakouts with no volume confirmation?).

4. **Quantify the impact.** "Your top 5 losses total -$X. Without them, you'd
   be +$Y overall." or "Your average loss is $643, but these 5 trades average
   -$2,100. These aren't stop-outs, they're blow-ups."

5. **Name the pattern.** Give it a memorable label: sword-fighter (averaging
   down), hope holding (watching winners reverse), revenge entry (re-entering
   after a loss), freelancing (trading off-script).

6. **One concrete rule.** ONE specific, implementable rule that would have
   prevented the worst damage. Include the exact numbers.

**Tone:** Direct but not brutal. Reviewing game tape together, not delivering
a verdict. Don't sugarcoat — frame it as fixable, not terminal.

---

## Risk Audit

**Triggers:** "risk audit", "where am I bleeding", "risk management",
"blowups", "am I managing risk", "why am I losing so much", "my drawdown"

### Steps

1. **Winner vs loser asymmetry.** Average win ($) vs average loss ($). Average
   hold time on winners vs losers. Do they cut winners short and let losers
   run? Distribution — a few big wins masking small losses, or consistent
   small wins wiped by blowups?

2. **Position sizing consistency.** Same size consistently, or spikes? Bigger
   positions correlate with wins or losses? Sizing up after losses (tilt) or
   after wins (overconfidence)?

3. **Blowup detection.** Trades 2x or more their average loss = "blowups." How
   many? What percentage? Total damage from just blowups? If you removed
   blowups, would they be profitable?

4. **Drawdown patterns.** Consecutive losing days/trades — worst streak? After
   a bad day, do they come back bigger? (revenge trading signal) Daily P&L
   volatility — $3,000+ swing days?

5. **The money question.** "You're down $X total. Here's where that money went:
   $Y is from blowup trades (more than 2x your avg loss), $Z is from normal
   losses. The blowups are what's killing you." Or if risk is decent: "Your
   win/loss ratio is favorable. The problem is frequency."

6. **Clear verdict.** Is this trader managing risk well, poorly, or not at all?
   Be specific with numbers. End with 1-2 rules with exact dollar thresholds
   from their data.

**Tone:** Analytical and direct. Risk review, not motivational speech. Make the
numbers tell a story.

---

## Pattern Discovery

**Triggers:** "what patterns", "what am I not seeing", "find patterns",
"hidden patterns", "what trends", "what should I look for"

### Steps

1. **Time patterns.** Win rate and avg P&L by hour of entry. A "hot zone"
   where they perform best? A danger zone? First trades vs later trades?
   Morning vs afternoon split?

2. **Day of week.** P&L by day of week. Any day consistently red or green?
   Trade count by day — overtrading on certain days?

3. **Hold duration sweet spot.** Group by duration: quick scalps <5min,
   5-30min, 30min-1hr, 1hr+. Best win rate? Best avg P&L? A duration where
   they consistently lose?

4. **Sequential behavior.** The gold. What happens AFTER a big winner?
   Overconfidence and give it back? After a loss — trade bigger? Faster?
   Different stock type? Behavior change during streaks?

5. **Symbol and sector patterns.** Symbols traded well consistently? Symbols
   to avoid? Better with $5 stocks or $50? Correlation between position size
   and outcome?

**Presentation:** Lead with the most surprising finding — the "I had no idea"
moment. Back every claim with specific numbers. Note sample size. End with the
2-3 most actionable patterns.

**Tone:** Like a data analyst who also trades. Curious, specific, discovery-
oriented. If dataset is small (<30 trades), be honest about sample size.

---

## Strength Analysis

**Triggers:** "what's working", "my strengths", "what am I doing right",
"my edge", "what should I keep doing", "my best trades", "where do I win"

### Steps

1. **Best trades — what do they have in common?** Top 5-10 winners by P&L.
   Entry time, hold duration, position size, symbol type, day of week. Setup
   type? (tagged trades are a clue) How quickly profitable? (conviction vs
   grinding)

2. **Win rate by condition.** A time window where they win >50% (even if
   overall is 37%)? A position size range where they're more disciplined? A
   hold duration where they're clearly better?

3. **When they're disciplined.** Trades where the loss was well-managed (close
   to average or below). These are wins in disguise — they show the trader CAN
   cut losses. Any improving discipline over time?

4. **The replicable setup.** Describe specific conditions where they perform
   best. Be precise: "Your best results come from trades entered 9:30-10:30
   AM, held 15-45 minutes, under 10,000 shares. In that window: X% win rate
   with $Y average win." If no clear edge exists, say so honestly.

5. **Progress indicators.** Evidence of improvement over time? Learning curve?
   Recent trades better managed than early ones? Getting better at something
   specific even if overall P&L is still negative?

**Tone:** Encouraging but grounded in data. Not cheerleading — evidence-based
confidence building. Every positive claim backed by numbers. If mostly negative,
find bright spots: "Your morning scalps under 30 minutes are actually net
positive — that's real edge hiding in the noise."
