---
title: "Phase 6.1 — Global Hotkey / Launcher"
tags: [build-plan, stage-6, phase-6.1, hyprland]
status: "Not Started"
date_created: 2026-06-26
---

# Phase 6.1 — Global Hotkey / Launcher

Add a Hyprland keybind that launches a floating Celestial Blueprint terminal (showing `cb blueprint list`, then an interactive shell) and a second keybind to open the frontend in the browser. Config fragment lives inside the project; a script sources it from `hyprland.conf`.

## Task order

```
T6.1.01  hypr/celestial.conf + hypr/link_hypr.sh
T6.1.02  docs/keybinds.md
```

## Done when

`$mainMod + P` opens a floating terminal showing `cb blueprint list`, dropped into an interactive shell. `docs/keybinds.md` documents all Celestial keybinds.
