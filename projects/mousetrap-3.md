---
title: "Mousetrap 3"
date: "2017-01-01"
category: "Anticheat"
tech: ["C++", "C", "PHP", "MySQL"]
tags: ["Anticheat", "Mod", "QMM", "Return To Castle Wolfenstein"]
links:
  - title: "GitHub Repository"
    url: "https://github.com/eamonwoortman/mousetrap-rtcw"
image: "../wp-content/uploads/2017/01/MT_logo-e1484078040197.png"
---

> Mousetrap3 was the third iteration of an anti-cheating system I created for Return to Castle Wolfenstein 1.0.

---

## Overview

**Mousetrap3** is a multi-component anti-cheat system containing:

1. **Anti-cheat client** — detects known cheats and injectors
2. **Server mod** — bans cheaters and communicates with the back-end
3. **PHP/MySQL back-end** — stores bans persistently

## The Problem

Return to Castle Wolfenstein 1.0 had **no anti-cheat system** when I started this project. To catch cheaters, we had to:

- Manually monitor players
- Repeatedly record demos
- Collectively decide whether a player was cheating

This was a painful process — caught cheaters could easily spoof their banned IPs and try again under a different nickname.

## The Approach

I had the idea of checking the client by studying cheat source codes from known cheat websites. These sources hooked in between the engine and the client mod. I figured I could do the same and somehow communicate findings to the server.

### Client Hook

The result was a simple client hook that:

- 🔑 **Generated a GUID** from the player's hard drive
- 🔍 **Scanned the process list** for known injectors
- 📋 **Scanned loaded modules** for known cheats
- ⚙️ **Scanned for activated cheat variables**
- 📤 **Sent a list of client variables** to the server

Once the client analysed the player's instance, it sent the result to the server.

### Server-Side

The Mousetrap server would:

- **Kick** the cheating player
- **Ban by GUID** — sending it to the back-end
- **Enforce variable limits** on the 4 variables known to be used for warping or misuse:
  - `cl_maxpackets`
  - `rate`
  - `cl_timenudge`
  - `cg_shadows`

Instead of using QMM, I created a "Frankenstein library" that did the same thing as the client hook, but for the game mod on the server side.

### Back-End

The back-end was a collection of simple **PHP scripts** connected to a **MySQL server**.

## Reflection

I did this project in **2009** and I wasn't the experienced developer I am now — it was all a bit messy. In hindsight, the server was not super secure (although the data was obscured).

The setup worked quite well, but people were reluctant to install it because it required manual installation. Most server admins didn't want to cooperate because they were afraid of losing players.

In the end, I shut the project down due to lack of interest and started the [RTCW 1.0PB project](./rtcw-1-0pb.md), which worked better anyway.

---

## Links

- [GitHub Repository](https://github.com/eamonwoortman/mousetrap-rtcw)
