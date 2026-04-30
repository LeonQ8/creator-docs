# Game Idea: Base-Building Cannon Arena

## 1. The Core Loop
1.  **Map 1 (The Hub):** Players start in a shared "Hub" where they have their own bases.
2.  **Economics:** Bases display items ("brainrots") that generate passive income. Players use this money to buy upgrades and better cannonballs.
3.  **Social Interaction:** Players can walk around, visit each other's bases, and communicate.
4.  **Initiating a Challenge:**
    *   **Method A (The Battle Room):** Players walk into a dedicated "Battle Room" in the Hub to wait for opponents.
    *   **Method B (Direct Challenge):** When two players walk near each other, a **"Challenge"** button appears.
5.  **The Match:** Once a challenge is accepted, both players are teleported to **Map 2 (The Arena)**.
6.  **Combat:** They enter the Cannon POV and fight using their customized cannon settings and ammo.

## 2. Transition Mechanics
- **Interaction:** We will use `ProximityPrompts` for player-to-player "Challenge" buttons and `RemoteEvents` to handle the "Request -> Accept" logic.
- **Teleportation:** When both players agree, the server uses `TeleportService:TeleportAsync()` to send them to a private Arena instance.
- **Persistence:** All stats (Money, Ammo Types, Upgrades) are stored via `DataStoreService` so they are always available regardless of which Map the player is in.

## 3. Map Breakdown
- **Map 1:** Social Hub, Base Building, Money Generation, Shops.
- **Map 2:** Competitive Cannon Physics Arena.
