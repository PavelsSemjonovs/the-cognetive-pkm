# AGENTS.md — Cognitive PKM Engineering Harness (Map)

This repository is a Git-based Personal Knowledge Management (PKM) system with strong academic/epistemic rigor.
It is **not** an application codebase. Your job is to create and maintain **epistemically sound knowledge artifacts**.

## Non‑negotiable invariants

1) **Do not mix layers** in a single document:
- Beliefs = what is true (claims/models)
- Decisions = commitments under uncertainty
- Experiments = actions + measurable outcomes
- Synthesis = integrated learning across time

2) **Provenance over vibes**:
- Non-trivial factual claims should cite sources (prefer primary sources).
- Distinguish **known / inferred / speculative**.

3) **No silent history edits**:
- `decisions/` and `experiments/` are records: **supersede, don’t rewrite**.
- `beliefs/` may evolve, but must include an explicit **Revision history**.

4) **Keep the graph connected**:
- Add links between related artifacts (belief → decision → experiment → synthesis).
- Update the relevant `*/index.md` when you add a new artifact.

## Where to put things (cognitive layers)

- Capture (raw): `inbox/`
- Sources/provenance: `resources/`
- Beliefs (claims/models): `beliefs/`
- Decisions (commitments): `decisions/`
- Experiments (outcomes): `experiments/`
- Synthesis (integration): `synthesis/`

## System of record (read these first)

- Docs map: [docs/index.md](docs/index.md)
- Harness index: [docs/harness/index.md](docs/harness/index.md)
- Document standards: [docs/harness/document-standards.md](docs/harness/document-standards.md)
- Workflows: [docs/harness/workflows.md](docs/harness/workflows.md)
- Quality rubric: [docs/harness/quality-rubric.md](docs/harness/quality-rubric.md)
- Templates catalog: [docs/harness/templates.md](docs/harness/templates.md)
- Templates: [docs/templates/](docs/templates/)
- Concept foundation: [docs/CONCEPT.md](docs/CONCEPT.md)
- Harness concept: [docs/ENGINEERING_HARNESS.md](docs/ENGINEERING_HARNESS.md)

## Canonical formatting choices (locked)

- **Internal links:** Markdown relative links (GitHub-native).
- **Metadata:** use a `## Metadata` section (YAML front matter is allowed only for raw clippings in `inbox/`).

## Naming conventions (new files)

- Beliefs: `beliefs/<slug>.md`
- Decisions: `decisions/DEC-YYYY-MM-DD-<slug>.md`
- Experiments: `experiments/EXP-YYYY-MM-DD-<slug>.md`
- Synthesis: `synthesis/SYN-YYYY-MM-DD-<slug>.md`
- Resources: `resources/<slug>.md`

Dates use ISO format. Use lowercase slugs with hyphens.

## How to execute a knowledge task (default agent workflow)

1) **Classify** the request into exactly one primary layer (belief/decision/experiment/synthesis/resource/inbox).
2) **Search first** for existing relevant artifacts; prefer linking or updating over duplicating.
3) **Start from a template** in `docs/templates/`.
4) **Meet the minimum bar** in `docs/harness/quality-rubric.md`.
5) **Link and index**: add graph links and update the relevant `*/index.md`.

## Escalate when uncertain

If any of these are ambiguous, ask before creating content:
- Which layer the artifact belongs to
- Whether a claim should be promoted from “hypothesis” to “stable”
- Whether a change is a belief update vs a new belief
- What counts as success/outcome for an experiment
