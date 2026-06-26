---
title: "Phase 6.2 — Hyprland Integration"
tags: [build-plan, stage-6, phase-6.2, hyprland]
status: "Not Started"
date_created: 2026-06-26
---

# Phase 6.2 — Hyprland Integration

Add windowrules that float and centre the Celestial terminal, assign it to a dedicated scratchpad workspace, and provide a toggle script to show/hide it with a single keypress.

## Task order

```
T6.2.01  Append windowrules to hypr/celestial.conf + add toggle keybind
T6.2.02  tools/toggle_celestial.sh
```

## Done when

The `celestial-plan` floating window auto-centres on launch; `Super + C` toggles the scratchpad workspace; `toggle_celestial.sh` launches the terminal if not running or toggles the workspace.
