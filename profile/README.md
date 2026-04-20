### [Lembas](https://github.com/meduseld-io/lembas) <img src="[https://github.com/user-attachments/assets/INSERT_LEMBAS_LOGO_ASSET_ID](https://github.com/user-attachments/assets/93bfeb12-4fd2-4350-9c6f-575bfe5adf69)" alt="Lembas" width="28" align="top">


A phone-first PWA for to-do lists and shopping lists. Switch between modes with a tap - your data stays separate and persists locally in the browser. No account needed.

- **Two modes** - To-Do for task lists, Shopping for grocery runs. Toggle between them with icons in the header
- **Regulars** - star frequently used items to save them. Tap a regular to quickly re-add it to your current list. Shared across both modes
- **Drag to reorder** - long-press to pick up an item, drag to rearrange. Drop on the trash zone to delete
- **Shopping features** - quantity, price, and aisle metadata per item. Check off items to move them into a dated shop with a running total. Shop history with expandable cards
- **Autocomplete** - regulars appear as suggestions while typing
- **Offline support** - fully functional offline as an installable PWA with service worker caching
- **No account needed** - all data stored in browser localStorage, no backend

**Tech**: React 19, Vite 6, @dnd-kit, localStorage · **License**: MIT

### [Letterboxderr](https://github.com/meduseld-io/letterboxderr) <img src="https://github.com/user-attachments/assets/a114a3f4-0091-46e6-8cc6-b2e890ef930f" alt="Letterboxderr" width="28" align="top">

Sync your [Letterboxd](https://letterboxd.com) watchlist to [Seerr](https://github.com/seerr-team/seerr). Also works with [Jellyseerr](https://github.com/Fallenbagel/jellyseerr) and [Overseerr](https://github.com/sct/overseerr).

Movies and TV shows from your Letterboxd watchlist are automatically added to your Seerr watchlist, so you can browse and request them whenever you're ready.

- **Auto-sync** - background sync runs on a configurable interval, or trigger manually from the web UI
- **Multi-user** - each user signs in with their Seerr credentials and links their own Letterboxd username
- **Web UI and CLI** - browser interface for setup and monitoring, or run headless with a JSON config for cron jobs
- **Docker ready** - single container with Docker or Docker Compose, config via environment variables
- **Dry run mode** - log what would be synced without making changes

**Tech**: Python, Flask, Cloudscraper, Docker · **License**: MIT
