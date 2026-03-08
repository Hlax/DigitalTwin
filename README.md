# Digital Twin

A governed creative system that explores identity through artifacts over time.

This repository is for the **scaffolding and deployment foundation** of the Twin.
It is not just a content generator and it is not a fully autonomous agent.
The Twin generates, critiques, evaluates, remembers, and proposes.
Harvey reviews, approves, stages, and publishes.

## Product Surfaces

- **Private Studio** — the private operator interface
- **Habitat Staging** — the preview environment for staged artifacts and habitat concepts
- **Public Habitat** — the curated public-facing site

## Core System Layers

- Foundation / ontology
- Runtime
- Governance
- Product surfaces
- Build and scaffolding

## Recommended Read Order

Start here:

- `docs/00_start_here.md`

Then move through:

1. `docs/01_foundation/`
2. `docs/02_runtime/`
3. `docs/03_governance/`
4. `docs/04_product/`
5. `docs/05_build/`
6. `docs/agents/`

## Suggested Stack for V1

- TypeScript monorepo
- Next.js apps
- Supabase for Postgres, auth, and storage
- Vercel for deployment
- One TypeScript runtime/orchestration layer for V1
- GPT for early runtime generation
- Provider adapter pattern for image tooling

## First Scaffold Success

The first scaffold milestone is successful when:

- Studio auth works
- one session can run
- one artifact can be generated and stored
- critique and evaluation records are stored
- memory/lineage wiring exists
- review and publication state transitions work
- the Public Habitat deploys successfully

The Public Habitat may initially be a blank white page with a large:

**Hello Twin!**

## Important Principle

Approval and publication are not the same thing.
Staging and public release are not the same thing.
System proposals and implementation changes still require Harvey approval.
