# PHASE HISTORY — append-only session log

Every agent appends one entry here at the end of every task, in this format. Never edit
or delete a past entry — if something needs correcting, add a new entry that says so.
This is the debugging trail when something breaks two sessions later.

---

## 2026-08-30 — Scaffolding & tooling — primary agent

**Plan approved:** venv-over-uv toolchain, 7 deps, `core/contracts.py` (5 dataclasses + TrackState enum), Context7 MCP in `opencode.json`, contracts smoke test — executed with two approved amendments: gimbal limits on `CameraState`, `fov_rad` split into `fov_h_rad`/`fov_v_rad`.
**Changed:** `.gitignore`, `requirements.txt`, `requirements-dev.txt`, `opencode.json` (new); `core/__init__.py` + `core/contracts.py` (new); `tests/test_contracts_smoke.py` (new); `PROJECT_STATUS.md`.
**Verification:** `pip list` shows all deps (opencv 5.0.0.93, numpy 2.5.2, scipy 1.18.1, filterpy 1.4.5, PySide6 6.11.2, pyinstaller 6.22.2, pytest 9.1.1); import check `IMPORTS_OK`; `pytest tests -q` → 7 passed; `py_compile core/contracts.py` OK.
**Outcome:** Done — verified
**Notes for next session:** `TrackResult.error_px` is documented as boresight-relative (image center `width/2, height/2`), NOT raw pixels — `control/` feeds this straight into the PID loop, treat sign carefully. `CameraState` carries PID saturation bounds; clamp from the contract, never hardcode. Units: radians/meters/seconds, stated once in the `contracts.py` header. Graphiti/GitHub MCP deliberately NOT added (separate task, keys pending). Repo is not yet a git repo. Mind numpy 2.x + opencv 5.x pair when writing CV code.

---

### YYYY-MM-DD — <module/task short name> — <agent name/model>

**Plan approved:** <one line — what was approved before execution began>
**Changed:** <files/modules touched>
**Verification:** <what was run to check it worked, and the result>
**Outcome:** Done — verified / Done — pending review / Blocked / Rolled back
**Notes for next session:** <anything the next agent needs to know that isn't obvious
from the diff — a gotcha, a deliberate shortcut, a follow-up task>

---
