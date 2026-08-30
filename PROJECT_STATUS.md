# PROJECT STATUS — FSOC Coarse-Alignment Tracking Simulator (SIH 26169)

> Every agent updates this file before ending a task. Keep it short and current — this is
> the first thing a new agent (or Mustafa) reads to understand where things stand right
> now. Do not let it become a changelog; that's what `phase_history.md` is for.

**Last updated:** 2026-08-30 — primary agent
**Current phase:** Foundation

## Module status

| Module | Status | Notes |
|---|---|---|
| `core/contracts.py` | Done — verified | All 5 dataclasses + TrackState enum, frozen; smoke-tested |
| `sim/` | Not started | |
| `disturbance/` | Not started | |
| `tracking/` | Not started | |
| `control/` | Not started | |
| `ui/` | Not started | |
| `telemetry/` | Not started | |

(Status values: Not started / In progress / Blocked / Done — pending review / Done —
verified)

## What's working right now

- Python 3.12 venv at `.venv/` with all runtime deps (OpenCV, NumPy, SciPy, filterpy, PySide6, PyInstaller) + pytest installed via pinned-free `requirements*.txt`.
- `core/contracts.py` defines every cross-module data shape (SimFrame, CameraState, TargetState, TrackResult, TelemetryPacket, TrackState) — immutable, unit-documented, smoke-tested.
- Context7 MCP wired in `opencode.json` (no key yet).

## What's blocked

- Graphiti / GitHub MCP — explicitly deferred by Mustafa; keys to be handed over in a separate task.

## Next up

1. `sim/` module — virtual scene, beacon motion, camera model, coordinate transforms (depends on `core/contracts.py` only).
2. `disturbance/` module — turbulence, vibration, sensor noise (can run parallel with `sim/`).
3. `tracking/` module — beacon detection + Kalman tracker + state machine.

## Known issues / tech debt

- No git repo initialized yet (repo-local decision pending).
- `requirements.txt` intentionally unpinned; if reproducibility bites later, freeze with `pip freeze`.
