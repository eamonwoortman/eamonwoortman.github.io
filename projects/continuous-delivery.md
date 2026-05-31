---
title: "Continuous Delivery"
date: "2017-02-13"
category: "DevOps"
tech: ["C#", "TeamCity", "Unity3D"]
tags: ["Continuous Delivery", "Little Chicken Game Company", "TeamCity", "Unity3D"]
links: []
image: "../wp-content/uploads/2017/01/tc_unity.png"
---

> A build pipeline which would automatically test and build a Unity3D game.

---

## Overview

**Continuous Delivery** was a project I was tasked with at [Little Chicken Game Company](http://www.littlechicken.nl/en/) to create a build pipeline for our Unity3D projects.

Prior to this point, there were no automated systems in place to facilitate game builds.

## Implementation

A former colleague had already tried **TeamCity** and was successful in making builds. After he left, I started over and began utilizing TeamCity for our builds.

The pipeline worked as follows:

1. **Source Control** — TeamCity would pull source code from CVS
2. **Build Jobs** — Execute automated jobs on the pulled source
3. **Unity Build** — One job would build the Unity project using the Unity Editor's command line interface
4. **Distribution** — Another job would upload the successful build to a build storage website from which we could download new builds to our devices

## Results

| Metric | Before | After |
|--------|--------|-------|
| Production build time | **4–8 hours** (manual) | **8 minutes** (automated) |
| Development bugs | Significantly more | Significantly fewer (unit testing) |
| Build creation errors | Frequent manual mistakes | Consistent, automated |

The improvements were dramatic:

- ⏱ **Production build time reduced from 4–8 hours to 8 minutes**
- 🐛 **Significantly fewer bugs and errors** during development (thanks to unit testing)
- 🔄 **Consistent build creation** — no more manual steps to forget
