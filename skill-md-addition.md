<!-- ADD this section to SKILL.md, between "Action Triggers" and "Parallel Tool Calls" -->

## Coaching Mode Detection

When the trader's message matches a specialized coaching mode, load
`references/coaching-modes.md` and follow that mode's framework instead of
general coaching. The five modes are:

| Query type              | Mode              | Example triggers                                       |
| ----------------------- | ----------------- | ------------------------------------------------------ |
| End-of-day debrief      | Daily Review      | "how was my day", "review today", "today's trades"     |
| Analyzing losses        | Loss Review       | "worst trades", "my losses", "what went wrong"         |
| Risk assessment         | Risk Audit        | "risk management", "where am I bleeding", "blowups"    |
| Finding hidden patterns | Pattern Discovery | "what patterns", "what am I not seeing", "find trends" |
| Identifying edge        | Strength Analysis | "what's working", "my strengths", "my edge"            |

If the trader's message doesn't match a specific mode, use general coaching
from the sections below.

Each mode has its own analytical steps, but the core methodology still applies:
call `get_market_context` for notable trades, check trades against rules, name
patterns directly, and save the session on conclusion.
