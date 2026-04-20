<p align="center"><img src="https://github.com/user-attachments/assets/70fa6367-afd1-4d40-b923-ede9fe351957" alt="Meduseld" width="250"></p>

# Meduseld

We're a group of friends building software for server management, media streaming, and other things we find useful. Some of it is open source, the rest is internal tooling for our gaming group.

## Public Projects

### [Herugrim](https://github.com/meduseld-io/herugrim) <img src="https://github.com/user-attachments/assets/a992766f-24d7-4271-88b4-62333265a1bf" alt="Herugrim" width="28" align="top">

A Cloudflare Worker that lets you authenticate with Cloudflare Access using Discord. It wraps OIDC around Discord's OAuth2 API so Cloudflare Access can use Discord as an identity provider - no separate identity service needed.

Fork of [Erisa/discord-oidc-worker](https://github.com/Erisa/discord-oidc-worker) with several improvements:

- **Environment-based config** - all settings via Wrangler env vars and secrets, no credentials in source code
- **Admin role detection** - checks for a specific Discord role and includes `is_admin` in the JWT, so your app can do role-based access control without a separate admin system
- **Rich user claims** - the ID token includes a `discord_user` object with full profile data (ID, username, display name, avatar, discriminator) instead of just email
- **Dynamic OAuth scopes** - only requests `guilds.members.read` when admin detection is enabled, reducing permissions for simpler setups
- **No KV dependency** - signing keys are generated in-memory, no Cloudflare KV namespace to set up
- **Error handling** - all Discord API calls are validated with descriptive error responses
- **Health endpoint** - `GET /health` for uptime monitoring
- **Optional guild restriction** - limit access to members of specific Discord servers
- **One-click deploy** - deploy button in the README for quick Cloudflare Workers setup

If you're using Cloudflare Access and want Discord login, this is what you need. Check the repo [README](https://github.com/meduseld-io/herugrim#readme) for setup instructions.

**Tech**: Cloudflare Workers, Hono, Jose · **License**: MIT

### [FellowSync](https://github.com/meduseld-io/fellowsync) <img src="https://github.com/user-attachments/assets/19b8237d-3e5e-47cb-98b6-063807a54262" alt="FellowSync" width="28" align="top"> *(Alpha)*

A self-hosted Spotify listening party app. Create a room, share a code, and listen to music together in sync - everyone queues tracks, the host controls playback, and FellowSync keeps all listeners on the same song at the same position via the Spotify Web API.

Each friend group brings their own Spotify developer app credentials (BYOS - Bring Your Own Sync), so you don't need to apply for Spotify's extended quota. One person creates a Sync, shares the ID, and up to 5 others join through it.

- **Room system** - create or join rooms with a 6-character code, with synced play/pause/skip across all listeners
- **Shared queue** - everyone can search and add tracks, with drag-to-reorder, shuffle, play-next, and playlist auto-queue
- **Room modes** - Normal (free-for-all), Hear Me Out (alternating turns), DJ Mode (host only), and Blind Mode (hidden upcoming tracks)
- **Social features** - vote to skip with configurable thresholds, emoji reactions with floating animations, session stats, and activity log
- **Host controls** - promote listeners to host, kick users, transfer host on leave, and configure all settings mid-session
- **Character avatars** - deterministic "fella" avatars with 15+ color options, custom display names, and assignable badges
- **Encrypted credentials** - BYOS Client Secrets are encrypted at rest with Fernet
- **PWA support** - installable on mobile and desktop with an iOS install banner

All listeners need Spotify Premium. Check the repo [README](https://github.com/meduseld-io/fellowsync#readme) for self-hosting instructions (Linux, macOS, and Windows guides included).

**Tech**: Flask, React, Redis, Spotify Web API · **License**: AGPL-3.0

### [ExSpire](https://github.com/meduseld-io/exspire) <img src="https://github.com/user-attachments/assets/0f597755-d2a1-418d-bffa-b9e0ea4957ad" alt="ExSpire" width="28" align="top"> *(Alpha)*

A self-hosted expiry tracker. Add subscriptions, documents, warranties, memberships, and anything else with a deadline, then get email or push reminders before they lapse.

Items are displayed in a spire layout - the closest to expiring sit at the narrow top, widening as deadlines stretch further out. Color-coded urgency indicators (red ≤3 days, yellow ≤14 days, green for safe) make it easy to see what needs attention at a glance.

- **Recurring items** - set items to repeat weekly, monthly, or yearly. When they expire, the next occurrence is auto-created with reset notifications
- **Email and push reminders** - configurable days-before notifications via SMTP email or browser push (VAPID). Checked hourly by the server
- **Categories** - built-in presets (subscription, document, warranty, membership, insurance, domain, license) plus custom categories with color-coded badges
- **Mobile gestures** - swipe left to reveal edit/delete actions, pull down to refresh
- **Inline editing** - edit items directly in the spire without opening a separate form
- **Dark and light mode** - toggle in settings, with left/center/right spire alignment options
- **Admin panel** - view all users, their item counts, verification status, and individual items with urgency indicators
- **PWA support** - installable on mobile and desktop with a service worker

ExSpire has its own auth system (email/password with JWT) - no external identity provider needed. Check the repo [README](https://github.com/meduseld-io/exspire#readme) for setup instructions.

**Tech**: Express, React, SQLite · **License**: Source Available

### [Lembas](https://github.com/meduseld-io/lembas) <img src="https://github.com/user-attachments/assets/93bfeb12-4fd2-4350-9c6f-575bfe5adf69" alt="Lembas" width="28" align="top"> *(Alpha)*

A phone-first PWA for to-do lists and shopping lists. Switch between modes with a tap - your data stays separate and persists locally in the browser. No account needed.

- **Two modes** - To-Do for task lists, Shopping for grocery runs. Toggle between them with icons in the header
- **Regulars** - star frequently used items to save them. Tap a regular to quickly re-add it to your current list. Shared across both modes
- **Drag to reorder** - long-press to pick up an item, drag to rearrange. Drop on the trash zone to delete
- **Shopping features** - quantity, price, and aisle metadata per item. Check off items to move them into a dated shop with a running total. Shop history with expandable cards
- **Autocomplete** - regulars appear as suggestions while typing
- **Offline support** - fully functional offline as an installable PWA with service worker caching
- **No account needed** - all data stored in browser localStorage, no backend

**Tech**: React 19, Vite 6, @dnd-kit, localStorage · **License**: MIT

### [Letterboxderr](https://github.com/meduseld-io/letterboxderr) <img src="https://github.com/user-attachments/assets/a114a3f4-0091-46e6-8cc6-b2e890ef930f" alt="Letterboxderr" width="28" align="top"> *(Alpha)*

Sync your [Letterboxd](https://letterboxd.com) watchlist to [Seerr](https://github.com/seerr-team/seerr). Also works with [Jellyseerr](https://github.com/Fallenbagel/jellyseerr) and [Overseerr](https://github.com/sct/overseerr).

Movies and TV shows from your Letterboxd watchlist are automatically added to your Seerr watchlist, so you can browse and request them whenever you're ready.

- **Auto-sync** - background sync runs on a configurable interval, or trigger manually from the web UI
- **Multi-user** - each user signs in with their Seerr credentials and links their own Letterboxd username
- **Web UI and CLI** - browser interface for setup and monitoring, or run headless with a JSON config for cron jobs
- **Docker ready** - single container with Docker or Docker Compose, config via environment variables
- **Dry run mode** - log what would be synced without making changes

**Tech**: Python, Flask, Cloudscraper, Docker · **License**: MIT


## Internal Projects

The rest of our repos are private tools we use to manage a dedicated game server, media streaming, and system monitoring for our friend group.

- **meduseld-backend** - Flask API and control panel for managing a dedicated game server, Jellyfin SSO, system monitoring, and user management
- **meduseld-site** - Static frontend pages served via Cloudflare Pages (services hub)

## Contributors

[@quietarcade](https://github.com/quietarcade) · [@Hier0g1yphiK](https://github.com/Hier0g1yphiK) · [@glenwinters859](https://github.com/glenwinters859) · [@ThomasDrennan](https://github.com/ThomasDrennan)
