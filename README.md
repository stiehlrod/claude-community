# Claude Community

A collection of general-purpose Claude Code slash commands useful for any developer.

## Available Commands

| Command | Description |
|---------|-------------|
| `/spotify-organizer-bot` | Organize Spotify library into mood-based and smart playlists |
| `/contract-analyzer-bot` | Analyze contracts for dangerous, invasive, and unreasonable clauses |
| `/discount-finder` | Find coupons, promo codes, cashback, and savings strategies |

## Installation

### Copy commands to your Claude Code config

```bash
# Clone the repo
git clone https://github.com/stiehlrod/claude-community.git

# Copy commands to your Claude config
cp claude-community/commands/* ~/.claude/commands/
```

### Or symlink for easy updates

```bash
ln -s /path/to/claude-community/commands/* ~/.claude/commands/
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
