# 🎶 Music Explorer

A dark-themed, Spotify-inspired web app for discovering songs, viewing lyrics, and building your own playlist — all in the browser.

## Features

- **Search** — Look up any song or artist using the Spotify Web API. Results appear as a grid of track cards with album art.
- **Suggested Artists** — On load, the home page shows a curated grid of artists from a few default genres (pop, OPM, hip-hop). This section is hidden once you perform a search.
- **Now Playing Player** — Clicking a track loads it into an embedded Spotify player docked at the bottom of the page, along with an "Add to Playlist" button. The player and search results reset when the page is reloaded — nothing carries over on refresh.
- **Lyrics Lookup** — Clicking a track also fetches its lyrics from the `lyrics.ovh` API and displays them alongside the player.
- **My Playlist** — Add tracks to a personal playlist from the player bar; view and manage it on a dedicated page.
- **Recent Search History** — Every search you make is saved and viewable on its own page.
- **Persistent Data** — Your playlist and search history are saved in `localStorage`, so they're still there when you come back. The currently playing track and search results are intentionally *not* saved — reloading the page always starts fresh.

## Pages

| Page | Description |
|---|---|
| `index.html` | Home page — search bar, suggested artists, track results grid, persistent player |
| `history.html` | Shows your recent search terms |
| `playlist.html` | Shows all songs you've added to your playlist |

## How It Works

1. On load, the app requests an access token from Spotify using the Client Credentials flow, then loads the Suggested Artists grid.
2. When you search, it queries the Spotify Search API, hides the Suggested Artists section, and displays matching tracks as cards.
3. Clicking a track loads it into the embedded Spotify player at the bottom and fetches its lyrics from the `lyrics.ovh` API.
4. Adding a track to your playlist, or searching, updates `localStorage`, which the History and Playlist pages read from directly. Reloading the page clears the search results and player, but keeps your playlist and history intact.

## Tech Stack

- Plain HTML, CSS, and JavaScript (no frameworks)
- Spotify Web API (search + artist lookup + track embeds)
- lyrics.ovh API (lyrics lookup)
- Browser `localStorage` for playlist and search history persistence

## File Structure

```
music_explorer/
├── index.html       # Home page
├── style.css         # Styling for home page (grid, suggested artists, player)
├── script.js          # Search, suggested artists, lyrics, playlist/history logic
├── history.html      # Recent search history page
├── history.css        # Styling for history page
├── playlist.html      # My playlist page
└── playlist.css        # Styling for playlist page
```
