---
title: "Phase 6.4 — Phone-as-VPS (Docker ARM)"
tags: [build-plan, stage-6, phase-6.4, docker, arm]
status: "Not Started — optional phase"
date_created: 2026-06-26
---

# Phase 6.4 — Phone-as-VPS (Docker ARM)

**Optional.** Package the Celestial backend as a multi-arch Docker image (arm64 + amd64) for deployment on an Android phone running a Linux environment (Termux, UserLAnd, or a dedicated ARM server). Access is via Tailscale or SSH tunnel.

**Prerequisite:** T1.7.04 (`docker-compose.yml` — marked optional/deferred in Stage 1). If T1.7.04 was skipped, T6.4.01 creates `Dockerfile` and `docker-compose.yml` from scratch.

## Task order

```
T6.4.01  Dockerfile (multi-arch) + docker-compose.arm.yml
T6.4.02  docs/phone-vps.md
```

## Done when

`docker buildx build --platform linux/arm64,linux/amd64 .` succeeds; `docker compose -f docker-compose.arm.yml up` starts the backend; `docs/phone-vps.md` documents Tailscale access.
