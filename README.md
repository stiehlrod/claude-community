# Claude Community

Slash commands for everyday tasks. No coding experience required.

## What is this?

Slash commands are shortcuts that give Claude specific instructions for common tasks -- like having a personal assistant who already knows exactly what you need. Type `/meal-planner` and Claude plans your week. Type `/contract-analyzer` and Claude reviews your lease.

These commands work in [Cowork](https://claude.com/download) (Claude's desktop app) and [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (Claude's terminal tool). This guide covers Cowork.

**Requires a paid subscription** (Pro, Max, Team, or Enterprise). [Claim a free pass](https://claude.ai/referral/OuK8zcMZog) for 7 days of Claude Pro access.

## Setup

### 1. Download Claude Desktop

Get it from [claude.com/download](https://claude.com/download) (macOS or Windows). Sign in with your Claude account.

### 2. Install the commands

Open Terminal (Mac: Command + Space, type **Terminal**) or Command Prompt (Windows: Windows key, type **Command Prompt**). Paste this and press Enter:

```bash
mkdir -p ~/.claude/commands && cd /tmp && curl -L https://github.com/stiehlrod/claude-community/archive/main.tar.gz | tar xz && cp claude-community-main/.claude/commands/*.md ~/.claude/commands/ && rm -rf claude-community-main && echo "Done! Commands installed."
```

You should see `Done! Commands installed.` -- close Terminal and you're done with it.

### 3. Start using Cowork

1. Open Claude Desktop
2. Click the **Cowork** tab at the top
3. Click **"Work in a Folder"** and select a folder on your computer
4. Type `/` to browse commands, or just describe what you need

## Tips

- **Keep the app open** while Claude works -- closing it stops the task
- **Start with a test folder**, not your main files
- **Be outcome-oriented** -- "Summarize this spreadsheet by category" works better than step-by-step instructions
- Type `/schedule` to set up recurring tasks
- **Dispatch (Pro/Max):** Assign tasks from your phone and Claude works on your desktop while you're away

For more on Cowork, use `/cowork-guide` or visit the [Claude Help Center](https://support.claude.com/en/articles/13345190-get-started-with-cowork).

## Available Commands

| Command | Description |
|---------|-------------|
| `/backcountry-check` | Check backcountry skiing conditions - avalanche danger, weather, and CAIC forecasts |
| `/bike-route` | Find bike routes based on terrain type, location, and weather conditions |
| `/contract-analyzer` | Analyze contracts for dangerous, invasive, and unreasonable clauses |
| `/conversation-starters` | Get conversation questions organized by depth level |
| `/cowork-guide` | Step-by-step guide for setting up and using Claude Cowork |
| `/dinner-party` | Track guest allergies, intolerances, and diets - get safe recipes |
| `/discount-finder` | Find coupons, promo codes, cashback, and savings strategies |
| `/fodmap` | FODMAP diet navigator - restaurant menus and safe food choices |
| `/hike-finder` | Find hikes with optimal conditions based on weather and preferences |
| `/meal-planner` | Weekly meal plans with smart shopping lists and dietary preferences |
| `/pack-trip` | Generate a packing list based on destination, weather, and activities |
| `/product-finder` | Find best products by price, quality, reviews, and sustainability |
| `/research` | Evaluate research quality by sample size, controls, peer review, and citations |
| `/spotify-organizer` | Organize Spotify library into mood-based playlists |

## Examples

```
/meal-planner -p 4 -d vegetarian --pantry rice,beans
/contract-analyzer ~/Documents/lease.pdf
/discount-finder target
/fodmap Olive Garden
/hike-finder Denver, CO
/dinner-party add "Sarah" --allergies "gluten, dairy"
/research --health vitamin D supplementation
/backcountry-check Berthoud Pass
/product-finder standing desk --price --quality --sustainable
/conversation-starters first date
```

## Updating Commands

Re-run the install command from Step 2 to get the latest versions.

## Troubleshooting

**Commands not showing up?** Re-run the install command from Step 2, then restart Cowork.

## Contributing

Contributions welcome! Keep commands general-purpose, include documentation and examples, and test before submitting.

## Related Repos

- [claude-commands](https://github.com/oddballteam/claude-commands) - Professional commands for engineering teams

## Support This Project

If these commands make your life easier, consider [donating](https://account.venmo.com/u/Jennica-Stiehl).

## License

MIT License - Feel free to use, modify, and distribute.
