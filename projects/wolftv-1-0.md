---
title: "WolfTV 1.0"
date: "2017-02-13"
category: "Modding"
tech: ["Assembly"]
tags: ["Anticheat", "Return To Castle Wolfenstein"]
links: []
image: "../wp-content/uploads/2017/01/wolftv_1.0-e1484075412783.png"
---

> WolfTV_1.0 was a modified WolfTV binary which was compatible with RtCW 1.0.

---

## Overview

**WolfTV_1.0** is a cracked version of the amazing [WolfTV](http://www.geeteevee.com/readme.php) by Brad "FonFon" Whitehead.

WolfTV is a streaming server which allowed a large (if not unlimited) amount of players to spectate a live match. Without WolfTV, you couldn't accommodate that many players in a single game server.

## The Problem

The original version created by FonFon was not compatible with Return to Castle Wolfenstein 1.0. Despite its flaws, there were still many players who played RtCW 1.0 competitively.

One of these players, **Orange**, asked me to see if we could make it work for RtCW 1.0.

## The Solution

After some debugging with **OllyDbg** and trial and error, I managed to:

1. **Bypass the protocol check** — allowing the WolfTV server to accept RtCW 1.0 clients
2. **Modify connection information** — changing what was sent on connect and to the master server

This resulted in a working WolfTV server for RtCW 1.0.

Unfortunately, after searching for a while, I was unable to find any remaining binaries of this project.
