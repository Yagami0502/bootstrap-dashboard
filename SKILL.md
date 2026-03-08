---
name: bootstrap-dashboard
description: Use when a Windows plus WSL project dashboard must be started, rebuilt, restarted, or health-checked, especially when localhost endpoints are down, the loop state is unclear, or the UI must be served again after frontend changes.
---

# Bootstrap Dashboard

## Overview
Start the loop and dashboard deliberately. First inspect what is already running. Then start only what is missing and verify with HTTP health checks plus runtime state.

## Quick Reference
- Check loop state from `.auto-loop-state` before restarting anything.
- Rebuild frontend after UI changes with `cd dashboard/frontend && npm run build`.
- Start the dashboard from WSL repo root with `nohup python3 dashboard/server.py --host 127.0.0.1 --port 8787 > logs/dashboard-server.log 2>&1 &`.
- Verify `GET /`, `GET /api/status`, and `GET /api/settings` all return `200`.
- Report the engine and model from the live status payload, not from assumptions.

## Workflow
1. Resolve the real repo path and whether the project lives on Windows or inside WSL.
2. Read `.auto-loop-state` and current logs to see whether the loop is already running.
3. If the dashboard UI changed, build the frontend before starting the server.
4. Start the dashboard in WSL from the repository root.
5. Verify HTTP health, then confirm loop engine and model from `/api/status`.
6. Hand back the dashboard URL and the exact running state.

## Common Mistakes
- Declaring success before `200` responses are verified.
- Restarting the loop when only the dashboard process is missing.
- Forgetting to rebuild the frontend after Vue changes.
- Using the wrong host, port, or working directory.

## Example
Use when the user says: ?????????, ?dashboard ?????, or ???? WSL ??????????.
