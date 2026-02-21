# Project Guidelines

## Architecture
This repository is a Git-based Personal Knowledge Management (PKM) system, not a traditional software project. It is structured to separate belief, decision, and action to preserve epistemic integrity and support long-term learning.
- `inbox/`: Raw captures, unstructured ideas, and references.
- `beliefs/`: Stabilized models, principles, and hypotheses.
- `decisions/`: Commitments taken under uncertainty.
- `experiments/`: Logs of actions taken and their measurable results.
- `synthesis/`: Integrated patterns across multiple decisions and experiments.
- `resources/`: References and external materials.

## Project Conventions
When creating or updating documents, adhere to the specific structure required for each cognitive layer:
- **Beliefs** (`beliefs/`): Must include a clear statement, assumptions, supporting evidence, counterarguments, status (hypothesis/tested/stable/deprecated), and revision history.
- **Decisions** (`decisions/`): Must capture the decision question, context snapshot, alternatives considered, reasoning, expected outcomes, and reconsideration conditions.
- **Experiments** (`experiments/`): Must include actions performed, measurable results, deviations from expectation, and unexpected signals.
- **Synthesis** (`synthesis/`): Must answer what was learned, which beliefs survived stress, and which assumptions failed.

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
