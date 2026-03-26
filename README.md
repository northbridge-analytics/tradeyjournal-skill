# TradeyJournal Coaching Skill

A coaching methodology skill for the [TradeyJournal](https://tradeyjournal.com) MCP connector. Teaches Claude how to run structured trading investigations using TradeyJournal's tools — including VWAP/volume market context, behavioral pattern identification, rule compliance checking, and persistent coaching memory.

## Requirements

- **TradeyJournal MCP connector** must be connected. This skill provides workflow instructions for TradeyJournal's 15 tools — it does nothing on its own.
- A TradeyJournal account (free tier works — all tools are unlocked).

## What This Skill Does

Without the skill, Claude has access to TradeyJournal's tools but decides on its own how to use them. With the skill, Claude follows a structured coaching investigation:

1. **Identifies outlier trades** from preloaded performance data
2. **Pulls market context** (VWAP, volume profiles, gap analysis) for notable trades — in parallel
3. **Coaches against price action**, not just execution data ("you held past the 9:10 AM volume cliff" vs. "you held too long")
4. **Checks trades against your rules** and names violations with specifics
5. **Saves coaching sessions** with dense summaries that persist across conversations

The investigation happens by methodology, not by chance.

## Install

### Claude.ai / Claude Desktop

1. Download this repo as a ZIP (Code → Download ZIP)
2. Go to Settings → Capabilities → Skills
3. Upload the `tradeyjournal-coaching` folder (or the ZIP)
4. Ensure TradeyJournal connector is connected

### Claude Code

Copy the `tradeyjournal-coaching/` folder to `~/.claude/skills/`

### Other Platforms (OpenAI Codex, ChatGPT, etc.)

The Agent Skills spec is an open standard. Place the `tradeyjournal-coaching/` folder in your platform's skills directory.

## Connect TradeyJournal

If you don't have the connector yet:

1. Visit [tradeyjournal.com](https://tradeyjournal.com) and create an account
2. In Claude Desktop: Settings → Extensions → Add MCP connector → search "TradeyJournal"
3. Authorize via OAuth

## License

MIT
