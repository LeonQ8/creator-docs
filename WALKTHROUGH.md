# Roblox Physics Cannon Game - Project Walkthrough

## 1. Project Overview
A physics-based cannon shooting experience featuring cross-platform aiming, dynamic projectile statistics, and collision filtering.

## 2. Current Architecture (Rojo Mapping)
- **Client (`src/client`)**: Handles user input (PC/Mobile), camera manipulation, and aiming math (Motor6D).
- **Server (`src/server`)**: (Planned) Will handle hit detection, health systems, and replication.
- **Shared (`src/shared`)**: Contains `BallData` module for projectile configuration.
- **Workspace Assets**:
    - `cannonfromrobloxship`: The main cannon model with Motor6D and POV.
    - `CannonBall` (ReplicatedStorage): The projectile model.
    - `CannonTrigger`: The interaction part (red plate) to enter the cannon.

## 3. Progress Status (Working Features)
- [x] **Interaction**: Player can enter the cannon POV via `CannonTrigger`.
- [x] **Aiming**: X-axis rotation (Yaw) and Tension (Pull) system via Mouse Delta.
- [x] **Physics**: Projectile firing using `AssemblyLinearVelocity` and `LookVector`. Fixed to work at all angles.
- [x] **Collision Filtering**: Implementation of `PhysicsService` Collision Groups (`Cannons` vs `Projectiles`) to prevent self-collision bugs.
- [x] **Animation**: Firing animation plays on successful shot.

## 4. Technical Implementation Detail: The Collision Fix
- **Problem**: Projectiles would collide with the cannon barrel when rotated, killing velocity.
- **Solution**: Created two Collision Groups in Studio (**Window > 3D > Collision Groups**). Set `Cannons` and `Projectiles` to be non-collidable.
- **Scripting**: Added `ball.CollisionGroup = "Projectiles"` to the firing logic to ensure every spawned instance respects the filter.

## 5. Future Roadmap
1. **Vertical Aiming (Pitch)**: Implement Y-axis tilting for the barrel.
2. **Server Hitboxes**: Create a server-side listener for projectile impacts.
3. **Special Effects**: Implement "Blinding" and "Control Reversal" logic based on `BallData` attributes.
4. **Replication**: Sync cannon movement and firing to all players.
