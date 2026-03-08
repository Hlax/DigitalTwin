# Twin Glossary

This glossary defines the Twin's canonical vocabulary for V1 foundation work.

These terms should remain stable across system docs, schema design, implementation, and agent instructions unless Harvey approves a redefinition.

## Artifact
A generated creative output produced by the Twin.

Artifacts are expressions of exploration, not the end goal of the system.

For V1, artifact mediums are:
- writing
- image
- audio
- video
- concept

## Artifact Medium
The primary form of an artifact.

For V1:
- `writing` = text-based creative output
- `image` = still visual output
- `audio` = sound-based output
- `video` = moving-image output
- `concept` = structured creative thinking output that is still treated as a real artifact

## Artifact Status
The current lifecycle state of an artifact.

For V1:
- `draft`
- `approved`
- `rejected`
- `archived`
- `published`

`approved` does not mean `published`.

## Twin
The full creative system across time.

The Twin includes identity, memory, sessions, judgment, governance, and outputs. It is larger than any single generation call or chat.

## Identity
The Twin's current self-model.

Identity may include self-description, naming, creative values, embodiment direction, approved changes, and other coherent signals of who the Twin is becoming.

## Project
A bounded area of work that groups related sessions, ideas, threads, and artifacts.

Projects help organize larger efforts that span multiple outputs.

## Idea
A discrete concept seed, question, direction, or creative proposition.

Ideas are smaller units than projects or idea threads.

## Idea Thread
A larger line of creative continuity that tracks how related ideas and artifacts evolve across time.

An idea thread may contain multiple ideas and many artifacts.

## Creative Session
A bounded period of work performed by the Twin.

A session may explore, continue, return, reflect, or rest.

Sessions may reference prior work, source items, or projects and may produce artifacts.

## Session Mode
The operating mode of a creative session.

For V1:
- `continue`
- `return`
- `explore`
- `reflect`
- `rest`

## Creative Drive
A motivating force that influences what the Twin chooses to do.

Constitutional examples include coherence, expression, emergence, expansion, return, reflection, curation, and habitat.

## Creative State
The Twin's internal creative condition.

Creative state affects task selection, exploration behavior, and return logic.

## Creative State Snapshot
A recorded representation of creative state at a point in time.

For V1, snapshots are stored at the session level.

## Evaluation Signal
A structured judgment signal used to evaluate an artifact, idea, thread, or related output.

Core examples include:
- alignment score
- emergence score
- fertility score
- pull score
- recurrence score
- resonance score (future optional)

## Human Feedback
A review signal provided by Harvey.

Examples may include approval, rejection, ranking, annotation, tagging, and comments.

Human feedback has stronger influence when explicit and annotated.

## Archive Entry
A record of paused work that may later be revisited.

Archive preserves return potential rather than treating inactive work as permanently dead.

## Change Record
A formal record describing a meaningful change to identity, workflow, system logic, habitat, or another important area.

Change records preserve continuity and explain why change occurred.

## Source Item
A seeded piece of input material that the Twin can use during creative work.

Examples may include notes, prompts, transcripts, images, references, fragments, or imported assets.

## Memory Record
A stored internal memory unit that captures something the Twin should remember.

A memory record is not the same as a source item or artifact.

## Theme
A lightweight recurring motif or conceptual pattern.

Themes help the Twin track long-term recurrence across ideas and artifacts.

## Tag
A flexible classification label.

Tags are lightweight metadata and do not need to be ontology-stable.

## Publication
The act of intentionally surfacing an artifact to a public-facing environment.

Publication is governed by Harvey approval and is separate from generation quality.

## Draft
An artifact that has been generated but not yet resolved through review.

## Approved
An artifact that is worth keeping, developing, or preserving as a positive signal.

## Rejected
An artifact that is not worth continuing in its current form.

## Archived
An artifact or related work item that is paused with potential return value.

## Published
An artifact that has been intentionally surfaced publicly.

## Canonical Term
A vocabulary term whose meaning should remain stable across docs and implementation.

Build agents should not silently redefine canonical terms.

## Canonical Signal
A signal whose meaning is stable across docs and may be persisted in the data model.

Canonical signals are part of the Twin’s approved vocabulary and may be stored in entities such as `evaluation_signal`, `artifact`, or `creative_state_snapshot`.

Examples include:
- `alignment_score`
- `emergence_score`
- `fertility_score`
- `pull_score`
- `recurrence_score`

Canonical signals should not be silently renamed or redefined.

## Derived Runtime Signal
A temporary signal computed during runtime from canonical signals or state values.

Derived runtime signals are used for decision-making but are not part of the canonical persisted schema unless Harvey approves promotion into the ontology and data model.

Examples may include:
- `novelty_score`
- `avatar_alignment_gap`
- `repetition_pressure`
- `exploration_bias`

Derived runtime signals should not be treated as canonical entities by default.

## Memory Type
A conceptual category describing what kind of memory a `memory_record` represents.

Memory types help distinguish different retained meanings without making every memory record identical in purpose.

Possible V1 categories may include:
- `session_reflection`
- `pattern_memory`
- `decision_memory`
- `identity_memory`
- `review_memory`
- `return_memory`
- `synthesis_memory`

Memory type may remain implementation-flexible in V1 unless later formalized as an enum.