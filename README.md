# Claude Community

A collection of helpful Claude Code slash commands for everyday tasks. No coding experience required.

## What is this?

[Claude Code](https://docs.anthropic.com/en/docs/claude-code) is an AI assistant that runs in your terminal. Slash commands are shortcuts that give Claude specific instructions for common tasks—like having a personal assistant who already knows exactly what you need.

## Getting Started

**Note: Claude Code requires a paid subscription.** It does not work with the free tier.

Follow these steps in order to get set up.

### Step 1: Get a Claude subscription

Sign up for one of these plans at [claude.ai](https://claude.ai):
- **Claude Pro** ($20/month) - For individual use
- **Claude Team** ($25/user/month) - For teams
- **Claude Enterprise** - For organizations

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

### Step 6: Start Claude Code

```bash
claude
```

You'll be prompted to log in with your Claude account on first run. Once logged in, you can use any of the slash commands below!

### Optional: Make commands available globally

The commands above only work when you run `claude` from within the `claude-community` folder. To make them available everywhere:

```bash
cp ~/Github/claude-community/.claude/commands/* ~/.claude/commands/
```

Or use symlinks to get updates automatically:

```bash
ln -s ~/Github/claude-community/.claude/commands/* ~/.claude/commands/
```

## Usage

Invoke any command by typing it in Claude Code:

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

## Available Commands

| Command | Description |
|---------|-------------|
| `/bike-route` | Find bike routes based on terrain type, location, and weather conditions |
| `/contract-analyzer` | Analyze contracts for dangerous, invasive, and unreasonable clauses |
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
