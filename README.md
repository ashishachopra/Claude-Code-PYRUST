# Rewriting Project Claw Code
<p align="center">
  <strong>Better Harness Tools, not merely storing the archive of leaked Claude Code</strong>
</p>

## Porting Status
The main source tree is now Python-first.

- `src/` contains the active Python porting workspace
- `tests/` verifies the current Python workspace
- the exposed snapshot is no longer part of the tracked repository state

The current Python workspace is not yet a complete one-to-one replacement for the original system, but the primary implementation surface is now Python.
This repository now focuses on Python porting work instead.

## Repository Layout
```text
.
├── src/                                # Python porting workspace
│   ├── __init__.py
│   ├── commands.py
│   ├── main.py
│   ├── models.py
│   ├── port_manifest.py
│   ├── query_engine.py
│   ├── task.py
│   └── tools.py
├── tests/                              # Python verification
├── assets/omx/                         # OmX workflow screenshots
├── 2026-03-09-is-legal-the-same-as-legitimate-ai-reimplementation-and-the-erosion-of-copyleft.md
└── README.md
```

## Python Workspace Overview
The new Python `src/` tree currently provides:

- **`port_manifest.py`** — summarizes the current Python workspace structure
- **`models.py`** — dataclasses for subsystems, modules, and backlog state
- **`commands.py`** — Python-side command port metadata
- **`tools.py`** — Python-side tool port metadata
- **`query_engine.py`** — renders a Python porting summary from the active workspace
- **`main.py`** — a CLI entrypoint for manifest and summary output

## Quickstart
Render the Python porting summary:

```bash
python3 -m src.main summary
```

Print the current Python workspace manifest:
```bash
python3 -m src.main manifest
```

List the current Python modules:
```bash
python3 -m src.main subsystems --limit 16
```

Run verification:
```bash
python3 -m unittest discover -s tests -v
```

Run the parity audit against the local ignored archive (when present):
```bash
python3 -m src.main parity-audit
```

Inspect mirrored command/tool inventories:
```bash
python3 -m src.main commands --limit 10
python3 -m src.main tools --limit 10
```

## Built with `oh-my-codex`
The restructuring and documentation work on this repository was AI-assisted and orchestrated with oh-my-codex, layered on top of Codex.
- **`$team` mode:** used for coordinated parallel review and architectural feedback
- **`$ralph` mode:** used for persistent execution, verification, and completion discipline
- **Codex-driven workflow:** used to turn the main `src/` tree into a Python-first porting workspace
