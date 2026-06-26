---
title: "Phase 6.3 — Desktop Notifications"
tags: [build-plan, stage-6, phase-6.3, notifications]
status: "Not Started"
date_created: 2026-06-26
---

# Phase 6.3 — Desktop Notifications

After a CYCLE chronicle is saved, fire a desktop notification summarising the blueprint name and the "Next session:" action extracted from the cycle body. Two delivery mechanisms: a shell script (`tools/notify.sh`) for CLI/Hermes use, and a browser Web Notification from the frontend (`ChroniclePanel.tsx`) for in-session use.

## Task order

```
T6.3.01  tools/notify.sh — query API, extract next-action, call dunstify
T6.3.02  ChroniclePanel.tsx — Web Notification after CYCLE chronicle POST
```

## Done when

Running `tools/notify.sh` after a CYCLE chronicle fires a dunst/desktop notification. The frontend fires a Web Notification in-browser after saving a CYCLE chronicle (with permission granted).
