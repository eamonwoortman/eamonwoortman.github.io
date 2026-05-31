---
title: "Resato Waterjet Virtual Training"
date: "2017-01-29"
category: "Simulation"
tech: ["C#", "Unity3D", "StrangeIOC"]
tags: []
links:
  - title: "Little Chicken — Case Study"
    url: "http://www.littlechicken.nl/en/cases/resato-waterjet-virtual-training/"
  - title: "GitHub — RestSharp.Unity Fork"
    url: "https://github.com/eamonwoortman/RestSharp.Unity"
image: "../wp-content/uploads/2017/01/Craft_ResatoACM_Tafel02-1024x576.png"
---

> The first in a line of machine simulations which trains people how to use heavy machinery.

---

## Overview

**Resato Waterjet Virtual Training** was a full 3D simulation of one of Resato's watercutting machines.

The project goal was to create a simulation in which trainees could learn to work with the machines without actually being on-site. Most importantly, the simulation would allow trainees to **safely work with the machine** without getting themselves or others in danger.

## Architecture & Technical Details

### StrangeIOC Framework

The Resato project was an opportunity for us to work with the relatively unknown **StrangeIOC** framework — an inversion of control framework for Unity that uses events or signals and contexts to define game behaviour.

### Reusable Component System

This application had to be designed so we could **re-use components** for a new line of machines. My job was to create a system in which we could easily define behaviour by adding components to machines.

We ended up designing a system that used:

1. **Events** to change a data model
2. **Data changed events** to let the world respond to those changes

### Backend Communication

I also created the communication between the app and the back-end using [my own fork](https://github.com/eamonwoortman/RestSharp.Unity) of the **RestSharp** library, due to incompatibility issues between Unity and the original library.

---

## Links

- [Case Study — Little Chicken Game Company](http://www.littlechicken.nl/en/cases/resato-waterjet-virtual-training/)
- [GitHub — RestSharp.Unity Fork](https://github.com/eamonwoortman/RestSharp.Unity)
