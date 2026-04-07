# Claude Community

A collection of slash commands for everyday tasks. Works in both **Cowork** (desktop app) and **Claude Code** (terminal). No coding experience required.

## What is this?

Slash commands are shortcuts that give Claude specific instructions for common tasks -- like having a personal assistant who already knows exactly what you need. Type `/meal-planner` and Claude plans your week. Type `/contract-analyzer` and Claude reviews your lease.

These commands work in two places:
- **Cowork** -- Claude's desktop app (no terminal needed)
- **Claude Code** -- Claude's terminal tool (for people comfortable with the command line)

Both require a paid subscription (Pro, Max, Team, or Enterprise).

## Getting Started

### Option A: Cowork (Recommended -- no terminal required)

Cowork is built into the [Claude Desktop app](https://claude.com/download). You chat with Claude and point it at a folder on your computer -- it reads, creates, and modifies files for you.

#### Set up Cowork

1. **Get a paid subscription** at [claude.ai](https://claude.ai)
2. **Download Claude Desktop** from [claude.com/download](https://claude.com/download) (macOS or Windows)
3. **Open Claude Desktop** and click the **Cowork** tab at the top (next to Chat)
4. **Click "Work in a Folder"** at the bottom and select a folder on your computer
5. **Grant permissions** when prompted (read, edit, delete)

#### Install the commands (one-time setup)

You'll need to paste **one command** into Terminal to install the slash commands. After this, everything happens in the desktop app.

**Mac:** Press Command + Space, type **Terminal**, press Enter.
**Windows:** Press the Windows key, type **Command Prompt**, press Enter.

Paste this entire block and press Enter:

```bash
mkdir -p ~/.claude/commands && cd /tmp && curl -L https://github.com/stiehlrod/claude-community/archive/main.tar.gz | tar xz && cp claude-community-main/.claude/commands/*.md ~/.claude/commands/ && rm -rf claude-community-main && echo "Done! Commands installed."
```

You should see `Done! Commands installed.` -- that's it. Close Terminal and go back to Cowork.

#### Use the commands

In Cowork, type `/` to see all available commands, or click `+` > **Slash commands** to browse them.

**Cowork tips:**
- Keep the app open while Claude works -- closing it stops the task
- Start with a test folder, not your main files
- Be outcome-oriented: "Summarize this spreadsheet by category" works better than step-by-step instructions
- Type `/schedule` to set up recurring tasks
- **Dispatch (Pro/Max):** Assign tasks from your phone and Claude works on your desktop while you're away

For more details, use the `/cowork-guide` command or visit the [Claude Help Center](https://support.claude.com/en/articles/13345190-get-started-with-cowork).

### Option B: Claude Code (Terminal)

Claude Code runs in your terminal and supports the same slash commands. Choose this if you're comfortable with the command line.

**Note: Claude Code requires a paid subscription.** It does not work with the free tier.

Follow these steps in order to get set up.

### Step 1: Get a Claude subscription

Sign up for one of these plans at [claude.ai](https://claude.ai):
- **Claude Pro** ($20/month) - For individual use
- **Claude Team** ($25/user/month) - For teams
- **Claude Enterprise** - For organizations

**Want to try it first?** I have 3 free passes that give you 7 days of Claude Pro access. [Claim a free pass](https://claude.ai/referral/OuK8zcMZog) (requires credit card, cancel anytime).

### Step 2: Open Terminal

Terminal is an app on your Mac that lets you type commands.

1. Press **Command + Space** to open Spotlight
2. Type **Terminal**
3. Press **Enter**

A window will open. This is your terminal—you'll paste the commands below here.

### Step 3: Install Node.js

Node.js is required to run Claude Code. Download and install it from [nodejs.org](https://nodejs.org/)—choose the **LTS** (Long Term Support) version.

Run the installer and follow the prompts. When it's done, verify it worked by typing this in Terminal:

```bash
node --version
```

You should see a version number like `v20.x.x`. If you see an error, restart Terminal and try again.

### Step 4: Install Claude Code

Now install Claude Code by typing this in Terminal:

```bash
npm install -g @anthropic-ai/claude-code
```

Wait for it to finish (may take a minute).

### Step 5: Download and use these commands

Create a folder and download this repository:

```bash
mkdir -p ~/Github
cd ~/Github
git clone https://github.com/stiehlrod/claude-community.git
cd claude-community
```

### Step 6: Install commands globally (Recommended)

This step makes all commands available in every Claude Code conversation, no matter what folder you're in.

First, create the commands folder if it doesn't exist:

```bash
mkdir -p ~/.claude/commands
```

Then install the commands:

```bash
cp ~/Github/claude-community/.claude/commands/* ~/.claude/commands/
```

**That's it!** The commands are now installed.

### Step 7: Start Claude Code

Open Terminal and type:

```bash
claude
```

You'll be prompted to log in with your Claude account on first run. Once logged in, you can use any of the slash commands below!

---

## Troubleshooting

### "Command not found" when I type a slash command

The commands aren't installed. Open Terminal and run:

```bash
mkdir -p ~/.claude/commands && cd /tmp && curl -L https://github.com/stiehlrod/claude-community/archive/main.tar.gz | tar xz && cp claude-community-main/.claude/commands/*.md ~/.claude/commands/ && rm -rf claude-community-main
```

Then restart Cowork or Claude Code.

### Getting updates when new commands are added

Re-run the install command above -- it will overwrite your existing commands with the latest versions.

### Alternative: Auto-updating commands (Advanced)

If you're comfortable with Terminal and have `git` installed, you can clone the repo and use symlinks so commands update automatically:

```bash
mkdir -p ~/Github && cd ~/Github
git clone https://github.com/stiehlrod/claude-community.git
rm -f ~/.claude/commands/*.md
ln -sf ~/Github/claude-community/.claude/commands/* ~/.claude/commands/
```

To update, just run `git pull` from `~/Github/claude-community`.

## Usage

Invoke any command by typing it in **Cowork** or **Claude Code**. In Cowork, type `/` or click `+` > Slash commands to browse. Examples:

```
/discount-finder target
```

```
/fodmap Olive Garden
```

```
/fodmap find restaurants near downtown Denver
```

```
/contract-analyzer ~/Documents/lease.pdf
```

```
/bike-route -t gravel -l Boulder, CO
```

```
/hike-finder Denver, CO
```

```
/meal-planner -p 4 -d vegetarian --pantry rice,beans
```

```
/pack-trip Hawaii 7 days beach and hiking
```

```
/product-finder standing desk --price --quality --sustainable
```

```
/dinner-party add "Sarah" --allergies "gluten, dairy" --dislikes "mushrooms"
```

```
/dinner-party check "lasagna"
```

```
/dinner-party recipe "dinner party for 8"
```

```
/research --health vitamin D supplementation
```

```
/spotify-organizer
```

```
/spotify-organizer rotate --mood chill
```

```
/conversation-starters first date
```

```
/conversation-starters level 3
```

```
/backcountry-check Berthoud Pass
```

```
/backcountry-check Vail tomorrow
```

## Available Commands

| Command | Description |
|---------|-------------|
| `/backcountry-check` | Check backcountry skiing conditions - avalanche danger, weather, and CAIC forecasts for Colorado |
| `/bike-route` | Find bike routes based on terrain type, location, and weather conditions |
| `/contract-analyzer` | Analyze contracts for dangerous, invasive, and unreasonable clauses |
| `/conversation-starters` | Get conversation questions organized by depth level - from icebreakers to soul-searching |
| `/cowork-guide` | Step-by-step guide for setting up and using Claude Cowork |
| `/discount-finder` | Find coupons, promo codes, cashback, and savings strategies |
| `/fodmap` | FODMAP diet navigator - restaurant menus, safe food choices, and social eating guidance |
| `/dinner-party` | Track guest allergies, intolerances, and diets - get safe recipes and substitutions |
| `/hike-finder` | Find hikes with optimal conditions based on weather and preferences |
| `/meal-planner` | Weekly meal plans with smart shopping lists, budget options, and dietary preferences |
| `/pack-trip` | Generate a packing list based on destination, weather, and activities |
| `/product-finder` | Find best products by price, quality, reviews, BBB ratings, sustainability, and ethical practices |
| `/research` | Evaluate research quality by sample size, controls, peer review, and citations |
| `/spotify-organizer` | Organize Spotify library into mood-based playlists with fresh bi-weekly rotations |

## Contributing

Contributions welcome! When adding commands:

1. Keep commands general-purpose (not org-specific)
2. Include clear documentation
3. Add usage examples
4. Test before submitting

## Related Repos

- [claude-commands](https://github.com/oddballteam/claude-commands) - Professional commands for engineering teams

## Support This Project

If these commands make your life easier, consider supporting continued development by donating to [@Jennica-Stiehl](https://account.venmo.com/u/Jennica-Stiehl).

## License

MIT License - Feel free to use, modify, and distribute.
