---
layout: case-study
title: The Last Act Engine & Editor
permalink: /case-studies/the-last-act-engine/
kind: Flagship · Engine & Tools
team: Team of 8 · Tech Lead
tags: [C++, Engine Architecture, Data Pipeline, Scripting, Editor Tools]
youtube: zhnHcYWrH8g   # engine & editor showcase
links:
  - label: The Last Act gameplay (built with this engine)
    url: https://youtu.be/jFDeJiHGkOY
---

## Problem

Our team of 8 needed its own C++ engine to build *The Last Act*, a 2D puzzle platformer where players use light and shadow to get past obstacles. As tech lead, I planned and assigned the team's technical work and built the engine's foundations: its architecture, a data pipeline for reading and writing game data, and a C++ scripting system.

The core mechanic made this harder. Because the gameplay depends on lighting and shadows, the engine needed to support that mechanic directly, not just draw sprites.

## Constraint

- **No third-party engine.** Everything had to be built from scratch.
- **Strict rubrics.** The engine was graded on both functionality and usability, so it had to work and also be usable by the rest of the team.
- **A tight timeline and no prior experience.** The schedule was extremely tight, and none of us had built a game engine before.
- **A hard deadline inside the deadline.** The engine had to be usable by the end of the first trimester, because the game's initial prototype had to be built on it.

## What I tested

- **Architecture: ECS → traditional components.** I started with an entity component system. As the project took shape, I decided ECS was more than we needed: it added complexity our team and timeline couldn't afford, for performance benefits a 2D game of this size wouldn't use. I switched to a traditional component system that was simpler to build and easier for the team to work with.
- **Data: JSON throughout.** Game data was read and written as JSON for the whole project, which kept it human-readable and easy for the team to edit and debug.
- **Scripting: C++ only, Lua cut.** Alongside native C++ scripting, I started building a Lua scripting layer. I stopped it once I decided it wouldn't be used enough to justify the development time, and put that time into the C++ scripting the team actually relied on.
- **Light-and-shadow math.** The core mechanic needed shadows that were extremely accurate, because players had to rely on exactly where a shadow fell to get through the level. We worked out the shadows geometrically, ray casting from the light against occluding edges, so the game could test exactly what was lit and what wasn't.

## What failed

**My technical planning and delegation.** I came into the project without experience leading engineering work, and it showed early on. The code wasn't planned out well enough up front, and the way I split tasks between people wasn't efficient. Systems didn't fit together as cleanly as they should have, and the team spent a lot of time refactoring code that a better plan would have avoided.

**The light-and-shadow math.** This was the hardest technical problem on the project. Figuring out the math was difficult, and the bar was high: if a shadow was even slightly off, players couldn't use it reliably in gameplay. The answer was to compute shadows geometrically, not just visually. We cast rays from each light against the edges of the objects blocking it, which gave the shadows' exact shape. The shapes were precise enough that gameplay could test whether the player was in light or shadow.

## What I changed

Midway through the project, I changed how I handed out work. Instead of just assigning a feature, I started talking through each one with the people building it:

- **What the feature needed.** What it had to do to work correctly in the game.
- **How the systems fit together.** How the systems and components would work together, so each person knew what their code had to connect to.

## What happened

With that clearer communication, the second half of the project had far fewer integration hiccups than the first, and the engine shipped the game (see the gameplay link below).

The project ran for **8 months** with **8 team members**, and **all 8** of us built the game in the engine and its scripting system.

**What I'd do differently:** sit down with each team member before they start a feature and agree on exactly what's expected and how it should be implemented. For example, how the physics should behave and be structured, not just "build physics." Most of our refactoring came from skipping that step early on.
