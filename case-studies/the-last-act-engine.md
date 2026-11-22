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

<!-- Keep each section short: 2–5 sentences or a few bullets. Specifics beat adjectives.
     This page is about the ENGINE as a tool. Its users were your teammates. Mention the game only as the result. -->

## Problem

Our team of 8 needed its own C++ engine to build *The Last Act*, a 2D puzzle platformer where
players use light and shadow to get past obstacles. As tech lead, I planned and assigned the team's
technical work and built the engine's foundations: its architecture, a data pipeline for reading and
writing game data, and a C++ scripting system.

The core mechanic made this harder. Because the gameplay depends on lighting and shadows, the engine
needed to support that mechanic directly, not just draw sprites.

## Constraint

TODO: e.g. no third-party engine allowed, semester timeline, teammates with mixed C++ experience,
needing the engine usable before the game could be built on it.

## What I tested

TODO: How you approached the light-and-shadow mechanic (what you tried first, what you settled on),
and early versions of the architecture, data format, or scripting system.

## What failed

**My technical planning and delegation.** I came into the project without experience leading
engineering work, and it showed early on. The code wasn't planned out well enough up front, and the
way I split tasks between people wasn't efficient. Systems didn't fit together as cleanly as they
should have, and the team spent a lot of time **refactoring** code that a better plan would
have avoided.

The light-and-shadow mechanic was also a sustained struggle to implement.
TODO: one sentence on what specifically was hard about it (collision with shadows? performance? accuracy?).

## What I changed

Midway through the project, I changed how I handed out work. Instead of just assigning a feature,
I started talking through each one with the people building it:

- **What the feature needed** to work correctly in the game
- **How the systems and components would work together**, so each person knew what their code
  had to connect to

## What happened

With that clearer communication, the second half of the project had **far fewer integration
hiccups** than the first, and the engine shipped the game (see the gameplay link above).

**What I'd do from day one next time:** sit down with each team member before they start a
feature and agree on exactly what's expected and how it should be implemented. For example, how
the physics should behave and be structured, not just "build physics." Most of our refactoring came
from skipping that step early on.

TODO (optional): add a number if you have one, such as how long the project ran or how many
teammates used the scripting system or editor.
