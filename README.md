# THE HAUNTING — multiplayer browser prototype

A dependency-free Node.js multiplayer prototype for 2–5 players (one ghost and 1–4 investigators). Each person plays on a separate browser. The server maintains the shared game state; clients poll it every 750 ms.

## Run locally

1. Install Node.js 20 or later.
2. Open a terminal in this folder.
3. Run `node server.js`.
4. Open `http://localhost:3000`.

To test on the same Wi-Fi, other players can open `http://YOUR-COMPUTER-LAN-IP:3000` (allow incoming TCP port 3000 in the computer firewall). For friends elsewhere, deploy this folder to any Node.js host with a public HTTPS URL (for example, a service that runs `node server.js` and exposes `PORT`). A local-only server is **not** accessible to remote friends without hosting or tunneling.

## How to play

- The first player creates a room and shares its 6-character code. Others join from the same URL. The host clicks **Start match**.
- The ghost sees the whole map. Click a room, spend energy to prepare it (about 12 seconds), then use whisper, flicker, slam, or apparition to generate fear and terror. At most three rooms may be haunted at once. Slam doors to split the team. At 75 terror, the ghost can possess an isolated player in a fully haunted room. The ghost then moves the possessed body and can attack others. Possession lasts 65 seconds unless broken.
- Humans see only their current room and can move between adjacent rooms using the map, movement buttons, or arrow/WASD keys. Search the Library, Cellar and Attic for three ritual seals. Go to the Chapel and start the ritual. Once it completes, the ghost manifests for 55 seconds. Throw three holy-water flasks (across the team) to banish it.
- Humans can also attempt an exorcism three times in the room occupied by the possessed body. The possessed player sees the Veil and can escape with five interactions.
- The ghost wins when every human is eliminated. The humans win when the manifested ghost reaches zero health.

## Prototype limitations

This is a playable mechanics test, **not** a production-ready game. The visuals are schematic; the possessed-player maze is currently a five-step interaction, not a navigable level; the ghost controls its manifested body through room buttons; fear and combat need playtesting and balancing; sessions and room state are held in server memory and reset when the server restarts. No voice chat, persistence, anti-cheat, matchmaking, or reconnect recovery. The server uses HTTP polling rather than WebSockets for zero-dependency hosting. All players should use voice chat separately for coordination.
