---
title: "GameMonkey ScriptMod"
date: "2017-02-13"
category: "Modding"
tech: ["C++", "C", "GameMonkey"]
tags: ["Enemy Territory", "Mod", "QMM", "Wolfenstein"]
links:
  - title: "ModDB Page"
    url: "http://www.moddb.com/mods/gamemonkey-scriptmod/"
  - title: "GitHub Repository"
    url: "https://github.com/eamonwoortman/gmscriptmod/"
image: "../wp-content/uploads/2017/01/GMSM_logo.jpg"
---

> GameMonkey ScriptMod is a Quake3Multimod (QMM) plugin, which allows server admins to define the server behavior by script.

---

## Overview

**GameMonkey Scriptmod** is a project where we implemented the scripting language [GameMonkey](http://www.gmscript.com/) into a [Quake3 Multimod](https://sourceforge.net/projects/qmm/) plugin.

[Quake3 Multimod](https://sourceforge.net/projects/qmm/) is a plugin manager which sits between the Quake3 engine and the actual game mod. This allows plugin developers to hook any behavior into roughly any Quake3-based game without having to modify the mod.

[GameMonkey](http://www.gmscript.com/) is an embedded scripting language that looks similar to C, making it easy to work with for programmers and others.

## Motivation

We started the project because we wanted more control over server behavior. We already had a PHP bot tailing the server logs, but this was slow and grew complicated quickly.

## Features

GameMonkey Scriptmod featured:

- ✅ **100% scriptable admin interface**
- ✅ **Scriptable Rcon-like interface**
- ✅ Interface for **clan members** (besides ref login)
- ✅ Interface for **clan friends** (besides ref login)
- ✅ **Access to filesystem** through `.gm` script functions
- ✅ Works with **ALL Enemy Territory mods** (etmain, etpro, etbub, shrubmod, tce, etc.)
- ✅ **Easy to modify** — no C/C++ knowledge necessary
- ✅ **Change server behavior without restart** — modify script files live
- ✅ **Simple syntax** — not as complicated as LUA
- ✅ **Many script examples** included
- ✅ **Fast** — GameMonkey is one of the fastest scripting languages
- ✅ **Define custom commands** — e.g., `/ban ID`, `/kick ID`, `drop ID`
- ✅ **Create individualized game server mods**
- ✅ **Exchange scripts** with other server admins
- ✅ **Client-to-client private chat**
- ✅ **IRC-like channel chat**

## Team

I developed this project with another developer: **Apologet**. Apologet started the project and later involved me. Later we got help from **im2good4u** and **Dr.Evil**.

---

## Links

- [GitHub Repository](https://github.com/eamonwoortman/gmscriptmod/)
- [ModDB Page](http://www.moddb.com/mods/gamemonkey-scriptmod/)
