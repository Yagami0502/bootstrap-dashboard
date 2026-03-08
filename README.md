# bootstrap-dashboard

A Codex skill for starting, rebuilding, restarting, and health-checking a dashboard service that runs from a Windows + WSL project.

## What it captures
- Start only the missing process instead of restarting everything blindly.
- Rebuild the frontend when the UI bundle changed.
- Verify readiness from real HTTP endpoints.
- Confirm the active engine and model from live runtime state.

## Install
1. Clone or download this repository.
2. Copy the repository folder into `~/.codex/skills/bootstrap-dashboard`.
3. Start a new Codex session so the skill can be discovered.

## Files
- `SKILL.md` - the skill itself
- `agents/openai.yaml` - UI metadata for skill lists

## Example prompt
- Start the dashboard service and confirm the local endpoints are healthy.
- Rebuild and relaunch the WSL dashboard after frontend changes.
