# Workflows

This repository is designed to make belief evolution, decisions, and outcomes traceable over time.

## Workflow A: Capture → Process

### 1) Capture (inbox)

Goal: fast capture with minimal friction.

- Add raw notes, links, clippings to `inbox/`.
- Do not treat inbox content as “true” or “stable”.

### 2) Promote provenance (resources)

If the capture depends on an external source:

- Create or update a `resources/<slug>.md` entry.
- Summarize the source and extract the key claims you might later promote to beliefs.

### 3) Promote to beliefs

If a capture changes your model of the world:

- Create `beliefs/<slug>.md` using the belief template.
- Make assumptions explicit and add counterarguments.
- Add links back to resources and forward to any dependent decisions/experiments.

### 4) Promote to decisions

If you commit to a course of action under uncertainty:

- Create a decision record in `decisions/` using the decision template.
- Link to the beliefs that justify it.
- Define expected outcomes and reconsideration triggers.

### 5) Run experiments (outcomes)

If you take action and can measure outcomes:

- Create an experiment record in `experiments/` using the experiment template.
- Link to the decision it tests and the beliefs it stresses.
- Record deviations from plan, results, and interpretation.

### 6) Synthesize

On a cadence, integrate what changed:

- Create synthesis documents in `synthesis/`.
- Update beliefs (with revision history entries) when evidence meaningfully changes them.

## Workflow B: Changing your mind (without rewriting history)

### Decisions and experiments are records

When a decision changes, do **not** rewrite the old file. Instead:

1) Create a new decision record.
2) In the old record’s `## Status` (or metadata), note: `Superseded by [new](./DEC-...).`
3) In the new record, note: `Supersedes [old](./DEC-...).`

Same pattern for experiments.

### Beliefs evolve, but must show their work

When a belief changes:

- Update the belief.
- Add an entry to `## Revision history` with the reason and link to the evidence.

## Index maintenance (required)

When adding a new canonical artifact, update the relevant index:

- `beliefs/index.md`
- `decisions/index.md`
- `experiments/index.md`
- `synthesis/index.md`
- `resources/index.md`

