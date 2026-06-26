---
title: "Phase 6.5 — Always-On Service"
tags: [build-plan, stage-6, phase-6.5, systemd]
status: "Not Started"
date_created: 2026-06-26
---

# Phase 6.5 — Always-On Service

Start the Celestial backend automatically at login via a systemd user service. The service file lives inside the project; `link_service.sh` symlinks it to `~/.config/systemd/user/` (following the "everything in project" rule). A Fish startup check notifies if the service is unexpectedly down.

## Task order

```
T6.5.01  systemd/celestial-backend.service + link_service.sh
T6.5.02  Fish startup notification snippet
T6.5.03  BUILD_PLAN/STAGE_6_ASCENSION/VERIFY.md
```

## Done when

`systemctl --user status celestial-backend` shows active; Hyprland session starts with the backend already running; Fish prints a warning if it's down.
