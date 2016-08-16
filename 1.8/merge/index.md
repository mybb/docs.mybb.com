---
layout: page
title:  "Merge System"
categories: []
toc: false
---

## Merge System Guides
{% include category_big.html category="merge" sort="order" %}
<br />

## About the MyBB Merge System
The MyBB Merge System allows for easy merging of an existing forum (be it MyBB or another forum software) into a MyBB <b>1.8</b> forum. The Merge System automatically converts the data from the other forum software (if applicable) into a MyBB-friendly format.
**Only the 1.8 Merge System is supported, all other versions aren't supported anymore.**

The following forum software are supported by the MyBB Merge System:

- bbPress
- FluxBB
- Invision Power Board 3
- Invision Power Board 4 (Pre-Release)
- MyBB 1.8 (Merge)
- phpBB 3
- punBB
- SMF 1
- SMF 2
- Vanilla
- vBulletin 3
- vBulletin 4
- WoltLab Burning Board 3
- WoltLab Burning Board 4
- Woltlab Burning Board Lite 2
- XenForo

The MyBB Merge System uses "modules" to take you through the conversion process. This makes it easier for you to choose what you want converted over, and what you don't want converted. You will also notice that some modules have "dependencies," which means it requires the displayed modules to be run before it can run itself.

The modules that are included for each forum software vary based on what that forum supports in comparison to MyBB. For instance, not all software have a "calendar" feature, so only those that do have a module that transfers over the calendar events.
