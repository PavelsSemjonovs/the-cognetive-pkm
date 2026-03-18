# Engineering Harness for a Cognitive Git-Based PKM

## Metadata

- Status: Draft
- Created: 2026-03-18
- Owner: Repository maintainer
- Scope: How humans and agents create and maintain knowledge artifacts in this repo

## 1) Definition: “harness” in a knowledge repo

In this repository, the engineering harness is the set of repo-encoded constraints, templates, maps, and feedback loops that make work:

- epistemically rigorous (academic-quality claims, provenance, counterarguments)
- structurally legible (correct layer placement, consistent format)
- navigable over time (indexes, links, stable naming)
- agent-executable (templates + clear routing, minimal ambiguity)

This is not a build/toolchain harness. It is an **epistemic harness**.

## 2) Why `AGENTS.md` must stay short

Agents have limited context budgets. A monolithic rulebook crowds out the task and relevant artifacts.

Therefore:

- `AGENTS.md` is the routing layer (map / table of contents).
- `docs/harness/` is the system of record (standards, protocols, rubrics).
- The cognitive layers are the artifacts (beliefs/decisions/experiments/synthesis/resources).

## 3) Repository map (cognitive layers)

- `inbox/`: raw captures (unprocessed)
- `resources/`: sources and reference summaries (provenance anchors)
- `beliefs/`: structured claims and models (with evidence + counterarguments)
- `decisions/`: commitments under uncertainty (records; supersede, don’t rewrite)
- `experiments/`: actions + measured outcomes (records; reproducibility where possible)
- `synthesis/`: integrated learning across time (meta-level updates)

Canonical harness docs live in:

- `docs/harness/index.md` (table of contents)
- `docs/harness/document-standards.md`
- `docs/harness/workflows.md`
- `docs/harness/quality-rubric.md`
- `docs/harness/templates.md`

## 4) Epistemic invariants (non-negotiable)

1) Layer purity: do not mix belief/decision/experiment in one document.
2) Provenance: non-trivial factual claims should cite sources (prefer primary sources).
3) Explicit uncertainty: separate what is known, inferred, and speculative.
4) Counterarguments: significant beliefs include credible counterpoints.
5) Traceability: decisions link to beliefs; experiments link to decisions; synthesis links to all.
6) No silent history edits:
   - decisions/experiments are records → supersede with a new file and cross-link
   - beliefs may evolve → update revision history and note what changed

## 5) Document standards (summary)

Canonical docs use:

- `## Metadata` (Created, Status, Review cadence, Sources if applicable)
- stable section headers per doc type (see templates)
- Markdown relative links
- a “Revision history” section for beliefs (and optionally synthesis)

See: `docs/harness/document-standards.md`.

## 6) Workflows (summary)

### Inbox → processed knowledge

- Capture in `inbox/` (minimal friction).
- When processing:
  1) create/update a `resources/` entry for the source (provenance)
  2) extract claims into `beliefs/` (if they change your model)
  3) if you commit to action under uncertainty → `decisions/`
  4) if you take action and can measure outcome → `experiments/`
  5) periodically integrate into `synthesis/`

### Superseding records (decisions/experiments)

If a decision changes:

- create a new decision record
- mark the old one as “Superseded by …” and link both ways
- do not rewrite the original reasoning as if it was always known

See: `docs/harness/workflows.md`.

## 7) Quality rubric (summary)

Each artifact must meet a minimum bar before it’s considered “stable”:

- clarity of claim/question
- explicit assumptions
- evidence quality + citations
- counterarguments / failure modes
- measurable expectations (for decisions/experiments)
- correct linking into the graph

See: `docs/harness/quality-rubric.md`.

## 8) How agents should operate here (runbook)

When asked to add/update knowledge:

1) Classify the task into one layer (belief/decision/experiment/synthesis/resource/inbox).
2) Search for existing relevant artifacts; prefer updating/linking over duplicating.
3) Use the correct template from `docs/templates/`.
4) Add citations and counterarguments proportional to claim strength.
5) Add links to connect the artifact into the graph.
6) Update the relevant `*/index.md` page.

## 9) Maintenance (“garbage collection”)

On a cadence:

- weekly: inbox triage + index updates
- monthly: belief review (stale, unsupported, missing counterarguments)
- quarterly: synthesis (what changed, what held, what failed)

The goal is low-entropy, high-traceability knowledge over years.

