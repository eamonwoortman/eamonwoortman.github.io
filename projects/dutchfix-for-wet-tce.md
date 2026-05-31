---
title: "DutchFix for W:ET — TCE"
date: "2023-05-19"
category: "Modding"
tech: ["C++", "C"]
tags: ["Enemy Territory", "Mod", "Wolfenstein"]
links:
  - title: "GitHub Repository"
    url: "https://github.com/eamonwoortman/qmm_dutchfix"
image: "../wp-content/uploads/2016/12/video_games_weapons_spetsnaz_true_combat_elite_desktop_1440x900_hd-wallpaper-1127929-1024x640.jpg"
---

> A QMM plugin which fixes a number of nukes and exploits in ET:TCE.

---

## Background

**Dutchfix** is a QMM plugin I created with Merlin1991 to counteract a few nukes and exploits in the awesome True Combat Elite (TCE) mod.

> [TrueCombat:Elite (TCE)](http://www.truecombatelite.com/) is a modern world total conversion of the free, popular, stand-alone third-person shooter, Wolfenstein: Enemy Territory. That is, TCE is an entirely free game, made by gamers, for gamers.

## The Challenge

I was one of the community leaders of **TeamNeelix** (later GoNe), and we owned a couple of game servers which were quite popular. Unfortunately, when the mod was first released, it had some exploits and nuke vulnerabilities that could be used to crash a server.

As a server owner, you're naturally going to get targeted by people who want to cause harm. With help from the community, we figured out how the exploits worked.

## The Approach

Since TCE was a **closed-source project**, we needed a way of fixing it without access to the source code. Fortunately, the commands used to exploit the servers were all server commands, meaning we could intercept them via a hook between the engine and the mod.

We used [Quake3 Multimod (QMM)](https://sourceforge.net/projects/qmm/) to create a plugin that:

- Inspected all server commands
- Filtered and blocked exploit commands
- Optionally **automatically banned nukers**

---

## Links

- [GitHub Repository](https://github.com/eamonwoortman/qmm_dutchfix)
