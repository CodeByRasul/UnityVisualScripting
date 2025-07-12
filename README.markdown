# 3D Runner Game - Unity Project

## Overview
This project is a 3D runner genre game developed using the Unity platform. The objective is for the player to navigate through two levels, avoiding obstacles and collecting coins to reach the finish line. The game features two scenarios: one where the player successfully completes the levels and wins, and another where the player fails by falling off the platform or colliding with obstacles, requiring a level restart.

## Problem Definition
The game is designed as a 3D runner where the player must:
- Reach the finish line by avoiding obstacles and staying on the platform.
- Complete two levels with distinct difficulty and visual design.
- Experience two outcomes: winning by completing both levels or restarting upon failure.

## Planning
Inspired by classic mobile runner games like *Subway Surfers* and *Temple Run*, the game incorporates coin collection and obstacle avoidance. The gameplay flow is as follows:
1. The player presses the "Start" button to begin.
2. If the player's Y-position falls below zero (off the platform) or they collide with an obstacle, the level restarts.
3. Reaching the finish line advances the player to the next level.

A flowchart was used to guide development, outlining the game’s logic and progression.

## Implementation
The game was built using Unity’s internal features, with no external assets. Key components include:

### Scenes
- **Total Scenes**: 5
  - **Scene 1**: Start screen with a "Start" button to launch the first level.
  - **Scenes 2-3**: Gameplay levels with increasing difficulty and distinct visual designs.
  - **Scene 4**: End screen thanking the player for completing the game.
  - **Scene 5**: Additional scene (context not specified).

### Levels
- **Level 1**: A tutorial level introducing player controls, coin collection, and basic obstacles (randomized cubes). Features energetic music and sound effects for collisions.
- **Level 2**: More challenging with a darker visual theme and complex obstacles, including zigzag patterns.

### Code Structure
The game uses Unity’s Visual Scripting Tool for coding, with the player’s logic divided into four components:
1. **Movement**:
   - Uses `Input GetAxis` for keyboard-based movement.
   - Variables `forward speed` and `sidespeed` control movement along the Y and X axes.
   - `Vector3Create` and `Multiplier` nodes manage player velocity and position via the Rigidbody component.
2. **Falling**:
   - Detects if the player’s Y-position falls below the platform using `If`, `Transform: Get Position`, and `Vector3: Get Y` nodes.
   - Triggers a loss condition if the player falls.
3. **Restart**:
   - Uses `Scene Manager: Load Scene` with `Get Active Scene` to reload the current level upon failure.
4. **Obstacles**:
   - Handles collisions with `On Collision` and `Compare Tag` nodes to detect obstacle interactions.
   - Includes a `Timer` node (1-second delay) and `Toggle Flow` to disable player control post-collision.
   - Adds audio feedback with `Audio Source: Play One Shot`.

### Coins
- Coins use a `Rigidbody` with the `Trigger` function enabled.
- `On Trigger` and `Compare Tag` nodes detect coin collection.
- Variables (`Get Variable`, `Set Variable`) track collected coins.
- `Game Object Destroy` removes coins after collection.
- Coins feature a rotating animation using the `Animator` component.

### Audio
- Background music is implemented via the `Audio Source` component with the `Loop` function enabled.
- Sound effects play on obstacle collisions and coin collection.

## Testing and Debugging
Challenges faced during development included:
1. **Coin Rotation Animation**:
   - Initially unclear, resolved by adding an `Animator` component and configuring keyframes, guided by a YouTube tutorial.
2. **Background Music**:
   - Simplified by using the `Audio Source` component with a looping music file, following YouTube instructions.

## Reflection
Due to limited experience with Unity, several enhancements are desired but not yet implemented:
- **Purchasing System**: Allow players to spend coins on character upgrades, skins, or decor items.
- **Additional Levels**: Introduce more levels with unique styles, increasing difficulty, and distinct audio-visual themes.
- **Endless Mode**: Create a mode with progressively increasing difficulty.
- **Multiplayer Mode**: Enable competitive play based on points collected.
- **Chasing Mechanic**: Add a creature that pursues the player, inspired by *Subway Surfers* and *Temple Run*.

## References
- Focus, S. (2024). Free Cowbell samples, sounds, and loops. Available from [https://samplefocus.com/tag/cowbell](https://samplefocus.com/tag/cowbell) [Accessed 29 February 2024].
- Games, K. (2022). Creating Simple Animations (Unity Tutorial). Available from [https://youtu.be/JVFg9g4f-ME?si=WESn7E_Zcg1VN5bT](https://youtu.be/JVFg9g4f-ME?si=WESn7E_Zcg1VN5bT) [Accessed 24 February 2024].
- Penguins, S. (2022). How to Make a Game with Visual Scripting (E02) - Gameplay Loop - Unity 2021 Tutorial (Bolt). Available from [https://youtu.be/AnixBl5DNs?si=7j1OHZh1u3x2nv_9](https://youtu.be/AnixBl5DNs?si=7j1OHZh1u3x2nv_9) [Accessed 19 February 2024].