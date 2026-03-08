# Repository Context

This repository contains the design and implementation of the **Digital Twin creative agent system**.

The Twin is a state-driven creative system that generates artifacts, evaluates them, and evolves ideas over time.

## Canonical System Documents

The following documents define the system architecture and should be treated as sources of truth:

Foundation:
- docs/foundation/twin_constitution_v0.md
- docs/foundation/glossary.md
- docs/foundation/repo_map.md

Architecture:
- docs/architecture/system_architecture.md
- docs/architecture/runtime_diagram.md
- docs/architecture/data_model.md

Core Runtime Systems:
- docs/systems/creative_state_model.md
- docs/systems/session_loop.md
- docs/systems/evaluation_signals.md
- docs/systems/memory_model.md
- docs/systems/idea_lineage.md
- docs/systems/archive_and_return.md

## Important Principles

Build agents working in this repository should:

- Follow the architecture defined in the documentation
- Avoid introducing new system concepts without updating the glossary and data model
- Treat canonical signals and entities as defined in the system docs
- Prefer extending existing systems rather than inventing new ones

If uncertainty exists, consult the architecture and system documents before implementing new behavior.