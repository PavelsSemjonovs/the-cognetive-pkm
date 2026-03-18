# Project Guidelines

## Architecture
This repository is a Git-based Personal Knowledge Management (PKM) system, not a traditional software project. It is structured to separate belief, decision, and action to preserve epistemic integrity and support long-term learning.
Primary layers:
- `inbox/`: Raw captures, unstructured ideas, and references.
- `resources/`: Reference materials and provenance anchors.
- `beliefs/`: Stabilized models, principles, and hypotheses.
- `decisions/`: Commitments taken under uncertainty.
- `experiments/`: Logs of actions taken and measurable results.
- `synthesis/`: Integrated patterns across multiple decisions and experiments.

## Sources of truth
Use these repo-native harness docs instead of relying on ad-hoc conventions:

- Agent entrypoint: `AGENTS.md` (see `/AGENTS.md`)
- Harness table of contents: `docs/harness/index.md` (see `/docs/harness/index.md`)
- Templates: `docs/templates/` (see `/docs/templates/`)

## Git Conventions
Git is used as cognitive infrastructure to track the evolution of thought.
- **Commits**: Keep commits atomic. Write descriptive commit messages. Explicitly explain reasoning when modifying beliefs.
- **Branches**: Use branches for competing strategies, alternative models, or experimental directions. Merging represents model selection.
- **Issues**: Use issues to track open questions, contradictions, missing evidence, and structural tensions.

## Anti-Patterns
- **Mixing Layers**: Do not mix beliefs, decisions, and actions in a single document.
- **Silent Modification**: Avoid silent belief modification; always use version control to trace changes and explain why a belief changed in the commit message.
- **Note Hoarding**: Avoid collecting notes without structuring or synthesizing them.
- **Aesthetics over Clarity**: Do not optimize for visual aesthetics at the cost of cognitive clarity.
