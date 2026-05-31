---
title: "RTCW 1.0PB"
date: "2023-05-19"
category: "Modding"
tech: ["Assembly"]
tags: ["Anticheat", "Return To Castle Wolfenstein"]
links:
  - title: "S4NDMOD — Punkbuster Anti-Cheat"
    url: "http://www.s4ndmod.com/wordpress/punkbuster-anti-cheat-software/"
image: "../wp-content/uploads/2017/01/wolf_10_pb.png"
---

> A cracked/reverse engineered 1.3 client so we can now use Punkbuster on the older RTCW 1.0 version.

---

## Overview

**RTCW 1.0PB** is a cracked RtCW 1.3 client/server binary which enables servers and players to use Punkbuster in the RtCW 1.0 version.

RtCW 1.0 is an older version that didn't feature Punkbuster or any other anti-cheat measures by design. After seeing people didn't want to use my own anti-cheat system (Mousetrap), I decided to try bringing Punkbuster into the picture.

The older 1.0 version did not differ that much from 1.3, and after earlier attempts with WolfTV_1.0, I figured I could do the same thing with Punkbuster.

## What Needed to Change

There were two things I had to do:

1. **Change the client** so it could join RtCW 1.0 servers
2. **Change the server** so it would pose as a normal 1.0 server

### Server Binary

To make the 1.3 server binary compatible with 1.0, I had to bypass the protocol check. This check prevented the client from joining servers with a different protocol.

I used [OllyDbg](http://ollydbg.de/) to find a specific error message: `ERROR: Protocol Mismatch Between Client and Server`. Once I found the message, I changed the assembly instruction responsible for comparing the two protocols (client/server) to always return true. This way any client would be able to connect to the server.

Finally, I changed the version and protocol so it would register to the master server as a 1.0 server.

### Client Binary

The client was easier — it only needed to receive a different server list. This was achieved by changing the filter RtCW sends to query servers from the master server.

## Outcome

After a couple of trials, **S4NDM4NN** and **AG3NT** offered to help out. They took over the project, added additional features, and offered a central place for the community.

Despite the fact it was working fine, people were not keen on using it — some experienced lag with Punkbuster. We also found out people generally don't like change: RtCW 1.0PB meant they had to download new binaries from some website, which many people simply didn't want to do.

---

## Links

- [S4NDMOD — Punkbuster Anti-Cheat Software](http://www.s4ndmod.com/wordpress/punkbuster-anti-cheat-software/)
