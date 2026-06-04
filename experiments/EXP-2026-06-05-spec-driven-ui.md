# EXP-2026-06-05 — Spec-Driven UI Development

## Metadata

- Status: complete
- Created: 2026-06-05
- Updated: 2026-06-05
- Owner: Pavels Semjonovs

## Hypothesis

- Hypothesis: Providing a strict design contract (`DESIGN.md`) before prompting an AI to generate UI code will produce more consistent, structured output than an unstructured "build me a dashboard" prompt.
- Rationale: Unstructured prompts allow the AI to fill gaps with generic defaults (e.g. default Streamlit blue, no layout rules, no backend wiring). A spec forces the AI to justify every decision against a constraint.

## Links

- Decision tested: Use Streamlit as UI framework (lightweight, native Python, no build step)
- Beliefs stressed: AI-generated UI requires a design contract to avoid "div soup" / generic outputs

## Setup

- Environment: Python 3.8+, Streamlit, existing `db_core.py` and `audit_module/`
- Tools: Claude (Anthropic), GitHub
- Baseline: Existing Tkinter desktop GUI (`gui_app.py`) as reference for expected functionality

## Procedure

1. Wrote `docs/DESIGN.md` defining framework, color palette, typography, component rules, and backend connection requirements.
2. Provided `DESIGN.md` as context to the AI agent along with `db_core.py` and `audit_module/audit_observer.py`.
3. Prompted AI: *"Generate a Streamlit web interface for the Prison Management System following the constraints in DESIGN.md. The UI must connect to PrisonRepo for all CRUD operations and must fire PrisonEventPublisher.notify() for every prisoner and guard add/delete action."*
4. Reviewed generated `ui_app.py` against the design contract.
5. Updated `ROADMAP_MVP.md` to mark Stage 5 complete.

## Measures

- Primary: Did the AI follow the color palette and component rules from DESIGN.md?
- Secondary: How many prompts were needed to get a working backend connection?
- Secondary: Is the Observer pattern correctly wired in the UI?

## Results

- Observations:
  - The AI followed the framework choice (Streamlit) and component rules precisely — `st.form()` wrappers, `st.dataframe()` for tables, `st.success/error/warning()` for messages, `st.sidebar.radio()` for navigation.
  - Color palette was applied via a custom CSS block injected with `st.markdown()`. The sidebar correctly uses `#1B4F72` as specified.
  - The Observer pattern was correctly wired: every `add_prisoner`, `delete_prisoner`, `add_guard`, `delete_guard` action calls `publisher.notify()` immediately after the database operation.
  - Backend connection was achieved in **1 prompt** — no follow-up corrections needed on the wiring logic.
  - The Dashboard section uses `st.metric()` as specified, displaying live counts for prisons, prisoners, capacity, and guards.

- Unexpected signals:
  - Streamlit's `st.cache_resource` was used to initialise the `PrisonRepo` and `PrisonEventPublisher` singletons — this was a sensible addition not explicitly specified in DESIGN.md, preventing re-initialisation on every page interaction.
  - The "auto-assign prison" option in the prisoner form was preserved from the original Tkinter UI, which was a good carry-over not explicitly requested.

## Deviations from plan

- What changed: No deviations. The AI did not hallucinate generic Streamlit blue styles ("the Tailwind Blue problem") because the color palette was specified as hex codes, not descriptive names.
- Why: Specific hex codes leave no room for interpretation. Vague instructions like "use a professional color scheme" would likely have produced generic defaults.

## Interpretation

- What this suggests: The DESIGN.md contract was effective. Providing explicit hex codes, named component rules, and a backend connection table eliminated the most common failure modes of AI-generated UI (wrong colors, missing backend wiring, inconsistent component choices).
- Belief updates: Spec-Driven Development meaningfully reduces prompt iterations for UI generation. The gap between "vibe coding" and structured output is primarily a problem of missing constraints, not AI capability.
- What remains uncertain: How well this approach scales to more complex UIs with dynamic state, animations, or multi-user scenarios.

## Next steps

- Follow-up experiment: Test the same DESIGN.md approach with a React + Tailwind frontend to compare output quality across frameworks.
- Decision update: Add DESIGN.md as a required document in AGENTS.md for any future UI work.

## Sources

- Spec-Driven Development concept — course material, TSI Software Engineering course, 2026
