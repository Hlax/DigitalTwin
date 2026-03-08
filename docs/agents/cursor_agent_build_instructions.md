# Cursor Agent Build Instructions

This document provides instructions for coding agents (such as Cursor)
to safely build the Twin system.

The repository contains canonical design documents describing the
system. Agents must treat those documents as the authoritative
specification.

------------------------------------------------------------------------

# 1. Canonical Document Order

Agents should read the documentation in this order:

1.  twin_constitution_v0.md
2.  glossary.md
3.  ontology_notes.md
4.  data_model.md
5.  system_architecture.md
6.  creative_state_model.md
7.  session_loop.md
8.  evaluation_signals.md
9.  governance docs
10. product docs

This order mirrors the system dependency chain.

------------------------------------------------------------------------

# 2. Build Strategy

Agents should implement the system in layers.

Layer 1 --- Database schema Layer 2 --- Core domain models Layer 3 ---
Runtime engine Layer 4 --- Judgment layer Layer 5 --- Memory and archive
Layer 6 --- Studio interface Layer 7 --- Publication surfaces

Agents should not begin UI work until core runtime logic is stable.

------------------------------------------------------------------------

# 3. Database Implementation

The data model document defines canonical entities.

Agents should:

-   map entities to database tables
-   preserve field names
-   preserve enums
-   avoid renaming entities without approval

Supabase/Postgres is the recommended implementation target.

------------------------------------------------------------------------

# 4. Runtime Responsibilities

The runtime engine must:

- start creative sessions
- load context
- generate artifacts
- run critique
- compute evaluation signals
- update memory
- stage artifacts for review

The runtime loop must remain **observable, auditable, and replay-friendly**.

For V1, coding agents should prioritize:
- explicit logging
- traceable state transitions
- clear session inputs and outputs
- reproducible storage of prompts, context, critique, and evaluation records

Do not assume full determinism once model providers and external tools are involved.
Instead, preserve enough structure that runtime behavior can be reviewed, debugged, and interpreted later.

------------------------------------------------------------------------

# 5. Judgment Separation Rules

Agents must not collapse the following layers:

Self Critique\
Evaluation Signals\
Human Approval

Each must remain separate components.

------------------------------------------------------------------------

# 6. Artifact Lifecycle

Artifacts should move through review-facing states such as:

draft → pending_review → approved / approved_with_annotation / needs_revision / rejected / archived / approved_for_publication

Approval and publication must remain separate concepts.

`approved_for_publication` means Harvey has intentionally cleared an artifact for possible public release.

Actual publication is a separate step governed by publication state.

For V1, publication state should remain separate from approval state and may include:
- private
- internal_only
- scheduled
- published

Agents must not collapse internal approval and external release into one status or one action.

------------------------------------------------------------------------

# 7. Studio Requirements

The private studio should allow Harvey to:

- start sessions
- review artifacts
- annotate outputs
- approve artifacts for retention
- mark artifacts as needs_revision
- reject artifacts for the intended use
- archive artifacts without deletion
- mark artifacts approved_for_publication
- publish only artifacts already approved_for_publication
- review staging habitat proposals
- promote approved staging releases to public

This interface should be implemented before the public habitat.

The studio is the main human governance surface for:
- artifact review
- staging review
- publication decisions
- system proposal review

------------------------------------------------------------------------

# 8. Safety Rules

Agents must not:

-   remove canonical entities
-   rename ontology concepts
-   merge evaluation and approval logic
-   bypass memory updates

Violating these rules breaks the architecture.

------------------------------------------------------------------------

# 9. Implementation Goal

The goal is a working system capable of:

-   running creative sessions
-   generating artifacts
-   evaluating outputs
-   storing memory
-   allowing human review
-   publishing selected artifacts
