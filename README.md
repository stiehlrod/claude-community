# Claude Community

A collection of helpful Claude Code slash commands for everyday tasks. No coding experience required.

## What is this?

[Claude Code](https://docs.anthropic.com/en/docs/claude-code) is an AI assistant that runs in your terminal. Slash commands are shortcuts that give Claude specific instructions for common tasks—like having a personal assistant who already knows exactly what you need.

## Getting Claude Code

**Note: Claude Code requires a paid subscription.** It does not work with the free tier.

### Step 1: Get a Claude subscription

Sign up for one of these plans at [claude.ai](https://claude.ai):
- **Claude Pro** ($20/month) - For individual use
- **Claude Team** ($25/user/month) - For teams
- **Claude Enterprise** - For organizations

### Step 2: Install Claude Code

Once subscribed, open Terminal and run:

```bash
npm install -g @anthropic-ai/claude-code
```

(Don't have npm? Install [Node.js](https://nodejs.org/) first—download the LTS version.)

### Step 3: Start Claude Code

```bash
claude
```

You'll be prompted to log in with your Claude account on first run.

## Available Commands

| Command | Description |
|---------|-------------|
| `/contract-analyzer-bot` | Analyze contracts for dangerous, invasive, and unreasonable clauses |
| `/discount-finder` | Find coupons, promo codes, cashback, and savings strategies |
| `/hike-finder` | Find hikes with optimal conditions based on weather and preferences |
| `/pack-trip` | Generate a packing list based on destination, weather, and activities |
| `/product-finder` | Find best products by price, quality, reviews, and BBB ratings |
| `/research` | Evaluate research quality by sample size, controls, peer review, and citations |
| `/spotify-organizer-bot` | Organize Spotify library into mood-based and smart playlists |

## Installation

### New to Terminal? Start here

Terminal is an app on your Mac that lets you type commands.

1. Press **Command + Space** to open Spotlight
2. Type **Terminal**
3. Press **Enter**

A window will open. This is your terminal—you'll paste the commands below here.

### Step 1: Create a folder for the download

```bash
mkdir -p ~/Github
cd ~/Github
```

### Step 2: Download these commands

```bash
git clone https://github.com/stiehlrod/claude-community.git
```

### Step 3: Copy commands to your Claude config

```bash
cp ~/Github/claude-community/commands/* ~/.claude/commands/
```

### Alternative: Symlink for easy updates

If you want to get updates automatically when this repo changes:

```bash
ln -s ~/Github/claude-community/commands/* ~/.claude/commands/
```

## Usage

Invoke any command by typing it in Claude Code:

```
/discount-finder target
```

```
/contract-analyzer-bot ~/Documents/lease.pdf
```

```
/hike-finder Denver, CO
```

```
/pack-trip Hawaii 7 days beach and hiking
```

```
/product-finder standing desk under $500
```

```
/research --health vitamin D supplementation
```

```
/spotify-organizer-bot
```

## Contributing

Contributions welcome! When adding commands:

1. Keep commands general-purpose (not org-specific)
2. Include clear documentation
3. Add usage examples
4. Test before submitting

## Related Repos

- [claude-commands](https://github.com/oddballteam/claude-commands) - Professional commands for engineering teams

## License

MIT License - Feel free to use, modify, and distribute.
