---
title: "Stage 6 — The Ascension"
tags: [build-plan, stage-6, os-integration]
status: "Not Started — begin after Stage 5 VERIFY.md passes"
date_created: 2026-06-24
---

# Stage 6 — The Ascension

Connect Celestial Blueprint to the OS layer: global hotkeys, Hyprland integration, desktop notifications, a phone-as-VPS deployment, and always-on background service. The planner becomes a system-level tool, reachable from anywhere in the workflow.

**Prerequisite:** All of Stages 1–5 complete. P6.1/P6.2 additionally require `cb` CLI (T3.1.04). P6.4 is optional.

---

## Phase dependency graph

```
T1.8.01 + T3.1.04
├─► P6.1 Hotkey      → T6.1.01 → T6.1.02
│   └─► P6.2 Hypr   → T6.2.01 (extends T6.1.01 conf)
│                    → T6.2.02
├─► P6.3 Notif       → T6.3.01 → T6.3.02 (also needs T1.6.07)
├─► P6.4 Phone VPS   → T6.4.01 → T6.4.02      [OPTIONAL]
└─► P6.5 Always-On   → T6.5.01 → T6.5.02
                                → T6.5.03 VERIFY (deps T6.1.02, T6.2.02, T6.3.01, T6.5.02)
```

---

## Phases and task count

| Phase | Title | Tasks |
|-------|-------|-------|
| P6.1 | Global Hotkey / Launcher | 2 (T6.1.01–02) |
| P6.2 | Hyprland Integration | 2 (T6.2.01–02) |
| P6.3 | Notifications | 2 (T6.3.01–02) |
| P6.4 | Phone-as-VPS (optional) | 2 (T6.4.01–02) |
| P6.5 | Always-On Service | 3 (T6.5.01–03) |
| **Total** | | **11 tasks** |

---

## Full task index

| ID | Title | Depends on |
|----|-------|------------|
| T6.1.01 | `hypr/celestial.conf` keybind fragment + `hypr/link_hypr.sh` | T1.8.01, T3.1.04 |
| T6.1.02 | `docs/keybinds.md` | T6.1.01 |
| T6.2.01 | Windowrules + toggle keybind appended to `hypr/celestial.conf` | T6.1.01 |
| T6.2.02 | `tools/toggle_celestial.sh` | T1.8.01 |
| T6.3.01 | `tools/notify.sh` — CYCLE chronicle → desktop notification | T1.8.01 |
| T6.3.02 | `ChroniclePanel.tsx` — Web Notification after CYCLE POST | T1.6.07, T6.3.01 |
| T6.4.01 | `Dockerfile` (multi-arch) + `docker-compose.arm.yml` + `.dockerignore` | T1.8.01 |
| T6.4.02 | `docs/phone-vps.md` | T6.4.01 |
| T6.5.01 | `systemd/celestial-backend.service` + `link_service.sh` | T1.8.01 |
| T6.5.02 | `tools/celestial_startup.fish` + `docs/automation.md` Stage 6 section | T6.5.01 |
| T6.5.03 | `BUILD_PLAN/STAGE_6_ASCENSION/VERIFY.md` | T6.1.02, T6.2.02, T6.3.01, T6.5.02 |

---

## Stage 6 done when

The backend starts on login (systemd service active); `$mainMod + P` opens a floating Celestial terminal from anywhere in Hyprland; a desktop notification fires after each CYCLE chronicle; the tool can optionally run on the phone over Tailscale.
