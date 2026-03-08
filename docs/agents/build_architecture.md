# Phase 5 --- Twin Build Architecture

This document translates the Twin architecture into a **practical build
plan** for implementation.

Earlier phases defined:

-   Ontology (what exists)
-   Runtime (how the system behaves)
-   Governance (how the system is supervised)
-   Product surfaces (how users interact with it)

Phase 5 defines **how engineers and coding agents should actually build
the system**.

------------------------------------------------------------------------

# 1. Build Philosophy

The Twin should be built in layers.

Each layer must be stable before the next layer depends on it.

Recommended order:

1.  Database + Data Model
2.  Runtime Engine
3.  Judgment Layer
4.  Memory + Archive System
5.  Studio Interface
6.  Publication Surfaces

This prevents UI work from blocking core system behavior.

------------------------------------------------------------------------

# 2. Core System Packages

Recommended repo packages:

packages/core\
Domain models and shared logic.

packages/agent\
Runtime orchestration and session execution.

packages/memory\
Memory records, archive logic, return sessions.

packages/evaluation\
Critique processing and evaluation signals.

packages/ui\
Shared UI components.

------------------------------------------------------------------------

# 3. Application Layer

apps/studio\
Private interface used by Harvey.

apps/habitat-staging\
Preview environment for staged artifacts.

apps/public-site\
Public habitat.

------------------------------------------------------------------------

# 3A. Locked V1 Stack

V1 implementation should use:

- TypeScript as the primary language
- Next.js for apps/studio, apps/habitat-staging, and apps/public-site
- Supabase for Postgres, authentication, and storage
- Vercel for deployment of the application surfaces
- shared package-based domain logic inside the monorepo
- one runtime orchestration layer in TypeScript for V1

Model/tool strategy for V1:

- GPT-based generation for writing and concept artifacts
- image generation through a provider adapter interface
- Krea may be used as an image provider, but provider integrations must remain modular
- Python is optional later and should not be required for the first scaffold

Agents should not introduce extra services, distributed workers, or a separate Python operator layer unless explicitly required by the build contract.

------------------------------------------------------------------------

# 4. Runtime Engine

The runtime engine runs creative sessions.

Responsibilities:

-   start session
-   load context
-   choose mode
-   generate artifact
-   run critique
-   compute evaluation signals
-   update state
-   store results

Session pipeline:

Assess State → Select Mode → Generate → Critique → Evaluate → Store →
Review Queue

------------------------------------------------------------------------

# 5. Judgment Layer

The judgment layer processes artifacts after generation.

Pipeline:

Artifact Generation\
↓\
Self Critique\
↓\
Evaluation Signals\
↓\
Human Approval

Each stage must remain independent.

------------------------------------------------------------------------

# 6. Memory System

Memory stores:

-   artifacts
-   sessions
-   ideas
-   threads
-   archive entries

Memory enables:

-   idea recurrence
-   lineage tracking
-   archive resurfacing

------------------------------------------------------------------------

# 7. Archive System

The archive pauses inactive threads.

Archived threads can later:

-   revive
-   branch
-   remain archived

Return sessions may periodically scan the archive for resurfacing ideas.

------------------------------------------------------------------------

# 8. Studio Interface

The studio is the operator control panel.

Features:

- start sessions
- review artifacts
- annotate work
- manage projects
- ingest sources
- approve outputs for retention
- mark outputs as needs_revision
- reject outputs for intended use
- archive outputs without deletion
- mark outputs approved_for_publication
- publish only outputs already approved_for_publication
- review staging habitat proposals
- promote approved staging releases to public

This interface should be built **before public habitat**.

The studio is the required human governance layer for:
- artifact review
- publication review
- staging release review
- system proposal review

------------------------------------------------------------------------

# 9. Publication Pipeline

Publication requires two stages:

approved_for_publication\
published

The public site only displays artifacts that pass both stages.

------------------------------------------------------------------------

# 10. Build Order

Recommended build order:

Step 1 --- Database schema\
Step 2 --- Runtime session loop\
Step 3 --- Artifact generation pipeline\
Step 4 --- Critique + evaluation system\
Step 5 --- Studio interface\
Step 6 --- Archive + return logic\
Step 7 --- Staging habitat\
Step 8 --- Public habitat

------------------------------------------------------------------------

# 11. Anti-Patterns

Avoid:

-   mixing critique and evaluation
-   merging approval and publication
-   storing runtime logic in the UI
-   bypassing memory updates

These break the Twin architecture.

------------------------------------------------------------------------

# 12. V1 Success Criteria

V1 is successful when the system can:

- run creative sessions
- generate writing, image, or concept artifacts
- critique and evaluate outputs
- store memory and lineage
- allow human review in the studio
- preserve approval history
- stage artifacts and habitat proposals safely
- publish curated outputs intentionally
- deploy a public habitat that may initially remain extremely simple

At the end of the first scaffold milestone, the public habitat may still be a minimal page such as a blank white site with a large "Hello Twin!" message.

At that point the Twin becomes a **governed creative system with working scaffolding**, rather than a simple generator or static website.