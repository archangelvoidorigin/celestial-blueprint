---
title: "Phase 1.7 — Auth & Run"
tags: [build-plan, stage-1, phase-1.7, auth]
status: "Not Started"
date_created: 2026-06-24
---

# Phase 1.7 — Auth & Run

Secure the API with a bearer token and confirm the full stack launches in one command. T1.7.04 (Docker) is explicitly optional/deferred.

## Tasks

| Task | Produces | Depends on |
|------|----------|------------|
| T1.7.01 | `app/core/auth.py` — `require_auth` dependency | T1.1.04 |
| T1.7.02 | Auth applied to all routers + frontend token header | T1.7.01, T1.6.01 |
| T1.7.03 | `dev.fish` auto-copies `.env.example` if `.env` absent | T1.1.08 |
| T1.7.04 | `docker-compose.yml` (DEFERRED — skip unless needed now) | T1.4.08 |

## Auth model

Single bearer token from `CELESTIAL_AUTH_TOKEN` in `.env`. Empty token = open gate (dev). Set a long random string for any shared/network deployment. Frontend reads it from `VITE_AUTH_TOKEN` (Vite env injection).

## Phase done when

`fish dev.fish` starts backend + frontend; `GET /api/health` returns 200; `GET /api/blueprints` returns 401 without a token when `CELESTIAL_AUTH_TOKEN` is set. Proceed to Phase 1.8 (Verification).
