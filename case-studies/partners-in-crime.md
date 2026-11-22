---
layout: case-study
title: Partners in Crime (Not Really...)
permalink: /case-studies/partners-in-crime/
kind: Constrained
team: Team of 5
tags: [C++, 2D, Split-Screen Multiplayer, Custom Engine, Rendering, Gameplay Systems]
video: /assets/video/Crackers_10sec_PARTNERS_IN_CRIME_NOT_REALLY.mp4
---

## Problem

A 2D split-screen multiplayer game. Each player needed their own view of the world, and the game needed a full inventory system that worked for both players.

## Constraint

- **No multi-camera support.** The DigiPen in-house engine we had to use could only render a single view. Split-screen wasn't a setting we could turn on.
- **Engine code couldn't be changed.** I couldn't add split-screen to the renderer, so it had to be built entirely on top of the engine, in game code.

## What I tested

My first idea was to offset the game objects and draw the scene twice, once for each player's half of the screen. In practice it kept breaking in two ways:

- **The two views overlapped.** The players' "cameras" bled into each other instead of staying in their own halves.
- **The wrong data showed up in the wrong half.** Objects meant for one player's view were appearing on the other player's side of the screen.

## What failed

**Time.** Getting split-screen to work correctly in an engine that wasn't built for it took far longer than I'd planned. I eventually got it working, but it used up so much of the project that I had very little time left for anything else I wanted to contribute.

## What I changed

The missing piece was distance culling. Once each player's half only drew the objects near that player, the overlap and wrong-side problems went away. The final approach:

- **Per-player offsets.** Each game object gets a left and a right offset. Adding the offset displaces the object's position so it lands where it should appear in that player's half of the screen.
- **Distance culling per player.** For each player, objects outside a set distance from that player are culled, so each half only draws what that player should see.
- **Render each half.** The remaining objects are drawn into the left or right half of the screen, positioned relative to that player's location.

This gave the game working split-screen without changing the engine or needing multi-camera support.

## What happened

Split-screen shipped and works correctly. The cost was time: solving it took most of my share of the project.

I also built the inventory system, designed around two players sharing one world:

- **Either player can pick up an item.** Both players interact with the same items in the world.
- **Items go to the right player.** A picked-up item disappears from the world and appears in that player's own inventory, never the other's.
- **Items work from the inventory.** The player can then use the item correctly from their inventory.

**What I'd do differently:** at the time, I was set on solving it alone. Next time I'd timebox a risky problem like this and ask for help sooner. Getting there faster would have left me time to contribute much more to the rest of the game.
