# Spotify Organizer Bot

## Purpose
Automatically organizes your Spotify library into mood-based and smart playlists using genre classification.

---

## Features

### 1. Mood-Based Playlists (5 playlists)
- **Energetic** - High-energy rock, metal, punk, electronic
- **Chill** - Ambient, lo-fi, jazz, acoustic
- **Happy** - Pop, dance, disco, funk
- **Sad** - Emo, sad indie, melancholic tracks
- **Focus** - Classical, instrumental, soundtrack

### 2. Smart Playlists (3 playlists)
- **Recent Favorites** - Your recently saved tracks
- **Discover Weekly Archive** - Saves Discover Weekly before it refreshes
- **Top Tracks** - Your most played songs

### 3. Fresh Rotation Playlists (NEW)
- **~15 songs per playlist** - manageable listening sessions
- **Bi-weekly refresh** - new songs every 2 weeks
- **No repeats** - tracks play history, never repeats songs from previous rotations
- **Draws from your library** - pulls from your larger mood playlists
- **Rolling history** - songs become eligible again after ~3 months (6 rotations)

Example rotation cycle:
- Rotation 1 (Jan 1-14): Songs 1-15
- Rotation 2 (Jan 15-28): Songs 16-30 (songs 1-15 excluded)
- Rotation 3 (Jan 29-Feb 11): Songs 31-45 (songs 1-30 excluded)
- ...and so on

### 4. Cross-Playlist Duplicate Detection
- Find songs that exist in multiple playlists
- Option to automatically remove duplicates (keeps first occurrence)
- Can target specific playlists or scan all playlists

### 4. Cleanup Features
- Duplicate track detection and removal
- Organized library management

---

## Location
`/Users/jennicastiehl/bots/spotify-organizer`

---

## Usage

### Initial Setup
```bash
cd /Users/jennicastiehl/bots/spotify-organizer
source venv/bin/activate
python organize.py
```

### Run Organizer
```bash
./bot.py all
```

The bot will:
1. Authenticate with Spotify
2. Analyze your library
3. Create/update mood playlists
4. Create/update smart playlists
5. Report duplicate tracks

### Fresh Rotation Commands
```bash
# Create/refresh rotation playlists (run every 2 weeks)
./bot.py rotate

# Create rotation for specific mood only
./bot.py rotate --mood chill

# Force new rotation (even if 2 weeks haven't passed)
./bot.py rotate --force

# View rotation history
./bot.py rotate --history

# Reset history (make all songs eligible again)
./bot.py rotate --reset
```

### Find Cross-Playlist Duplicates
```bash
# Find duplicates across ALL playlists
./bot.py cross-duplicates

# Find duplicates in specific playlists only
./bot.py cross-duplicates --playlists "Playlist 1" "Playlist 2"

# Find AND remove duplicates (keeps first occurrence)
./bot.py cross-duplicates --remove

# Combine: specific playlists + remove
./bot.py cross-duplicates -p "Chill Vibes" "Road Trip" -r
```

---

## Configuration

Edit `config.yaml` to customize:

```yaml
playlists:
  energetic:
    name: "🔥 Energetic"
    genres: ["rock", "metal", "punk", "electronic", "edm"]

  chill:
    name: "😌 Chill Vibes"
    genres: ["ambient", "lo-fi", "jazz", "acoustic", "indie"]

# Fresh Rotation Settings
rotation:
  enabled: true
  songs_per_playlist: 15        # Songs per rotation playlist
  refresh_days: 14              # Days between rotations
  history_rotations: 6          # How many rotations before songs can repeat (~3 months)

  # Which moods get rotation playlists
  moods:
    - energetic
    - chill
    - happy

  # Playlist naming
  naming:
    prefix: "🔄 Fresh"          # e.g., "🔄 Fresh Chill"
```

---

## Technical Details

### Authentication
- Uses Spotify OAuth with client credentials
- Credentials stored in `config.yaml` (not committed)
- Requires Spotify Developer app registration

### Mood Classification
- Genre-based analysis (uses track genres from Spotify)
- Fallback to artist genres if track genre unavailable
- Custom mapping of genres to moods

### Rotation History Tracking
- SQLite database stores song IDs and rotation dates
- Each rotation tagged with date and mood
- Query excludes songs from last N rotations
- Automatic cleanup of old history

### Dependencies
- `spotipy` - Spotify API client
- `python-dotenv` - Environment configuration
- `pyyaml` - Configuration management
- `sqlite3` - Rotation history database

---

## Files

```
spotify-organizer/
├── organize.py          # Main organizer script
├── rotate.py           # Fresh rotation logic
├── genre_moods.py      # Genre-to-mood mapping
├── config.yaml         # User configuration (gitignored)
├── config.example.yaml # Configuration template
├── rotation_history.db # SQLite rotation tracking (gitignored)
├── requirements.txt    # Python dependencies
└── README.md          # Documentation
```

---

## Limitations

- Mood classification based on genres (may not be 100% accurate)
- Requires Spotify Premium for full API access
- Rate limited by Spotify API (handles automatically)
- Cannot access Audio Features API (uses genre workaround)

---

## Maintenance

The bot can be run:
- **Manually** when you want to organize
- **Weekly** via cron for automatic maintenance
- **After adding new music** to keep playlists fresh

### Suggested Schedule
```bash
# Full organization (monthly)
0 9 1 * * cd /Users/jennicastiehl/bots/spotify-organizer && ./bot.py all

# Fresh rotation refresh (every 2 weeks)
0 9 1,15 * * cd /Users/jennicastiehl/bots/spotify-organizer && ./bot.py rotate
```

---

## Privacy & Security

- ✅ All processing happens locally
- ✅ No data sent to external services (except Spotify API)
- ✅ Credentials stored locally only
- ❌ Do NOT commit config.yaml with credentials

---

## Support

For issues:
1. Check Spotify API credentials
2. Verify library access permissions
3. Review bot.log for errors
4. Ensure Spotify Premium account active
