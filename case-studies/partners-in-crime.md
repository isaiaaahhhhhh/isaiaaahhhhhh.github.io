---
layout: case-study
title: Partners in Crime (Not Really...)
permalink: /case-studies/partners-in-crime/
kind: Constrained
team: Team of 5
tags: [C++, 2D, Split-Screen Multiplayer, Custom Engine, Rendering, Gameplay Systems]
video: /assets/video/Crackers_10sec_PARTNERS_IN_CRIME_NOT_REALLY.mp4
---

<!-- Keep each section short: 2–5 sentences or a few bullets. Specifics beat adjectives. -->

## Problem

A 2D split-screen multiplayer game. Each player needed their own view of the world, and the
game needed a full inventory system.

## Constraint

We had to build it in a DigiPen in-house engine that had **no support for multiple viewports or
cameras**. Split-screen wasn't a setting we could turn on. I had to extend the engine's renderer myself.

TODO: Any other limits: timeline, engine code you couldn't change, performance targets.

## What I tested

TODO: The approaches you tried for multi-viewport rendering, in order (e.g. render targets per player,
viewport/scissor switching, offsetting the camera per draw), and why each one didn't work.

## What failed

**Time.** Getting split-screen to work correctly in an engine that wasn't built for it took far longer
than I'd planned. I eventually got it working, but it used up so much of the project that I had very
little time left for anything else I wanted to contribute.

## What I changed

The engine could only render one view, so I simulated two views inside it:

1. **Per-player offsets.** Each game object gets a left and a right offset. Adding the offset
   displaces the object's position so it lands where it should appear in that player's half of the screen.
2. **Distance culling per player.** For each player, objects outside a set distance from that
   player are culled, so each half only draws what that player should see.
3. **Render each half.** The remaining objects are drawn into the left or right half of the screen,
   positioned relative to that player's location.

This gave the game working split-screen without needing true multi-camera support from the engine.

## What happened

Split-screen shipped and works correctly. The cost was time: solving it took most of my share of the
project.

TODO: one line on what you'd do differently, e.g. prototype the riskiest feature in week one, or
timebox it and ask for help sooner. Also confirm the inventory system: keep it in the card
description if you built it, or remove it.
