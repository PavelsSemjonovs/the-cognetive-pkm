# MVP Roadmap — Cognitive Git-Based PKM (3 Months)

## Metadata

- Status: Draft
- Created: 2026-03-18
- Timebox: 12 weeks (3 months)
- Primary surface: GitHub + local editor
- Source of truth: This roadmap + [docs/harness/index.md](harness/index.md)

## 1) Vision (what “MVP success” means)

Deliver a Git-native personal knowledge system that:

- preserves epistemic integrity (claims, evidence, uncertainty, counterarguments)
- separates belief vs decision vs action (experiment) vs synthesis
- makes belief evolution and outcomes traceable over time
- is legible to humans and agents via templates, indexes, and clear standards
- stays low-entropy through lightweight “garbage collection” and integrity checks

## 2) MVP Scope (in / out)

### In scope

- End-to-end lifecycle:
  - capture in [`inbox/`](../inbox/)
  - provenance anchors in [`resources/`](../resources/)
  - canonical artifacts: [`beliefs/`](../beliefs/), [`decisions/`](../decisions/), [`experiments/`](../experiments/), [`synthesis/`](../synthesis/)
- Standards and templates:
  - `## Metadata` section standard (see [Document Standards](harness/document-standards.md))
  - Markdown relative links
  - naming conventions per harness (see [Document Standards](harness/document-standards.md))
- Navigation:
  - per-layer indexes (`*/index.md`) updated when new artifacts are added
- MVP seed pack:
  - at least 1 real example artifact per layer
  - at least 1 “closed loop” thread: belief → decision → experiment → synthesis
- Lightweight enforcement:
  - simple local scripts to check metadata/required sections and broken links
  - optional GitHub Action to run checks on PRs

### Out of scope (explicit non-goals)

- A web app, database, or bespoke UI
- Full bibliographic system (Zotero integration, CSL rendering, etc.)
- Perfect ontology/taxonomy from day one
- Heavy CI gating that blocks progress on minor doc issues

## 3) Operating Principles (project-specific)

- Layer purity: don’t mix beliefs/decisions/experiments/synthesis in one file.
- Provenance-first: non-trivial factual claims cite sources (prefer primary sources).
- No silent history edits:
  - decisions/experiments are records → supersede, don’t rewrite
  - beliefs may evolve → revision history required
- Keep the graph connected: link artifacts and update the relevant index.
- Default formatting choices:
  - links: Markdown relative
  - metadata: `## Metadata` section headers

See:

- Harness TOC: [docs/harness/index.md](harness/index.md)
- Quality rubric: [docs/harness/quality-rubric.md](harness/quality-rubric.md)
- Templates: [docs/templates/](templates/)

## 4) MVP Success Metrics (practical OKRs)

**O1: Usable knowledge lifecycle**

- KR1: One closed loop exists (belief → decision → experiment → synthesis) with correct links and index entries.
- KR2: Creating a new artifact from template + indexing takes <10 minutes.

**O2: Academic rigor baseline**

- KR1: Each canonical artifact type has at least one example meeting the minimum bar in [docs/harness/quality-rubric.md](harness/quality-rubric.md).
- KR2: At least 10 resource entries exist for the MVP seed topics, each with extracted claims.

**O3: Low-entropy maintenance**

- KR1: Inbox can be triaged weekly with a documented process ([docs/harness/workflows.md](harness/workflows.md)).
- KR2: Integrity checks exist (local scripts) and detect broken links + missing metadata.

## 5) Workstreams (epics)

1) **Lifecycle & governance**
   - inbox processing cadence, superseding rules, review schedule
2) **Provenance & academic rigor**
   - resource summaries, citation discipline, counterarguments, uncertainty labeling
3) **Navigation & discoverability**
   - indexes, linking conventions, cross-layer traceability
4) **Tooling & enforcement**
   - metadata/link checks; optional CI
5) **Seed content & onboarding**
   - examples + “how to use this repo” quickstart experience

## 6) Timeline (12 weeks; dates are exact)

Assume start on Monday **2026-03-23** and finish Sunday **2026-06-14**.

### Sprint 1 (2026-03-23 → 2026-04-05): Define MVP + seed structure

Deliverables

- Confirm and finalize the MVP seed topic(s) (1–3 themes max).
- Create seed pack plan: what artifacts will exist by MVP end (counts + link structure).
- Ensure [docs/index.md](index.md) links to all core harness docs and this roadmap.

Acceptance

- A maintainer (future-you) can explain “where does this go?” for any new note in <30 seconds.

### Sprint 2 (2026-04-06 → 2026-04-19): Provenance anchors (resources) + first beliefs

Deliverables

- Create 5–10 `resources/<slug>.md` entries for seed topics.
- Create at least 2 beliefs (`beliefs/<slug>.md`) backed by those resources.

Acceptance

- Each new belief includes: statement, assumptions, evidence, counterarguments, status rationale, revision history.

### Sprint 3 (2026-04-20 → 2026-05-03): Decisions + experiments (closing the loop)

Deliverables

- Create at least 2 decisions using `decisions/DEC-YYYY-MM-DD-<slug>.md`.
- Create at least 2 experiments using `experiments/EXP-YYYY-MM-DD-<slug>.md`.
- Ensure decisions link to beliefs; experiments link to decisions + beliefs.

Acceptance

- At least 1 decision has explicit measurable outcomes + reconsideration triggers.
- At least 1 experiment has measures + results + interpretation.

### Sprint 4 (2026-05-04 → 2026-05-17): Synthesis + belief updates

Deliverables

- Create at least 1 synthesis document `synthesis/SYN-YYYY-MM-DD-<slug>.md`.
- Perform at least 1 belief update with a proper revision history entry pointing to evidence/experiment.

Acceptance

- Synthesis explicitly lists inputs and outputs (belief updates, decision guidance, open questions).

### Sprint 5 (2026-05-18 → 2026-05-31): Integrity tooling (lightweight enforcement)

Deliverables

- Add local scripts (no external deps preferred) to check:
  - missing `## Metadata` in canonical artifacts
  - missing required headings per template (minimum set)
  - broken relative links to repo files
- (Optional) Add a GitHub Action to run checks on PRs.

Acceptance

- Running checks locally produces actionable failures and a clean pass on main.

### Sprint 6 (2026-06-01 → 2026-06-14): Onboarding + release readiness

Deliverables

- Add a short “Quickstart” section to [`README.md`](../README.md) (or a dedicated doc in `docs/`) pointing to:
  - the lifecycle
  - templates
  - indexes
  - quality rubric
- Ensure each `*/index.md` has up-to-date entries for MVP artifacts.

Release criteria (MVP)

- One closed loop thread exists and is easy to navigate.
- Seed pack meets the rubric minimum bar.
- Integrity checks exist and run clean on the repo.

## 7) Definition of Done (industry-style, adapted)

A roadmap item is “Done” only when:

- The artifact exists in the correct layer.
- Required sections (per template) are present.
- Links connect it into the knowledge graph.
- Index updated.
- If applicable: sources cited and uncertainty/counterarguments included.
- If applicable: superseding is used instead of rewriting history.

## 8) Risks & mitigations

- **Scope creep (taxonomy, tooling, UI):** keep MVP surface GitHub-native; enforce out-of-scope list.
- **Entropy (inbox backlog):** weekly triage ritual; cap inbox size; promote or archive.
- **False rigor (long docs, low signal):** rubric focuses on minimum bar + clarity; prefer short, well-cited claims.
- **Broken navigation:** link checks + index discipline; avoid duplicating sources of truth.

## 9) Governance & cadence

- Weekly (30–60 min): inbox triage + index updates + next-week plan.
- Monthly (60–90 min): belief review (stale, unsupported, missing counterarguments).
- Quarterly (90–120 min): synthesis of major themes; update core beliefs and decision heuristics.

## 10) Appendix: Key repo docs

- Concept: [docs/CONCEPT.md](CONCEPT.md)
- Harness concept: [docs/ENGINEERING_HARNESS.md](ENGINEERING_HARNESS.md)
- Harness TOC: [docs/harness/index.md](harness/index.md)
- Templates: [docs/templates/](templates/)
- Quality rubric: [docs/harness/quality-rubric.md](harness/quality-rubric.md)

## 11) Optional: issue tracking setup (no new tooling required)

If you track execution in GitHub Issues, use milestones (or labels) that mirror the timeline:

- `MVP Sprint 1` … `MVP Sprint 6`

Each roadmap deliverable becomes an issue with:

- links to produced artifacts (PRs or files)
- explicit acceptance criteria copied from this document

