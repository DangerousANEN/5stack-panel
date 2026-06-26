# 5Stack Roadmap

This document outlines the planned features and architectural changes for the 5Stack ecosystem.

## Upcoming Features

### HUD Management & Editor
- **Goal:** Provide a comprehensive system for managing and creating custom HUDs for tournament broadcasts.
- **Components:**
  - `web`: Implement a HUD selection interface and an embedded HUD editor.
  - `api`: Store HUD configurations and provide endpoints for saving/loading custom designs.
  - `game-streamer`: Ensure HUD URLs are correctly structured to be consumed as OBS Browser Sources (e.g., `https://5stack.localhost/hud/<match_id>`).
- **Use Cases:** In-game HUDs, full-screen webcam layouts, operator camera overlays.

### Veto (Pick/Ban) Streaming
- **Goal:** Improve the Veto system to allow streaming of the pick/ban phase independent of the game server state.
- **Problem:** Currently, the Stream Deck integration and streaming setup require the game server to be running on the selected map, preventing the Veto process from being streamed before the map is chosen.
- **Solution:**
  - Decouple the Veto UI (in `web`) from the active game server state.
  - Expose a dedicated Veto observer URL for OBS (e.g., `https://5stack.localhost/veto/<match_id>`).
  - Allow tournament organizers to control the Veto flow via the panel before the game server provisions.

---
*Note: All cross-repository implementations must adhere to the source priority and update order specified in `AGENTS.md`.*