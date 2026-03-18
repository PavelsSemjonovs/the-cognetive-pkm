# Document Standards

## Metadata

Canonical artifacts (belief/decision/experiment/synthesis/resource) use a `## Metadata` section near the top with:

- Status (required)
- Created (required, `YYYY-MM-DD`)
- Updated (optional)
- Review cadence (optional)
- Owner (optional)

Raw clippings in `inbox/` may use YAML front matter (already common for captures).

## Linking

- Use Markdown relative links: `[label](../path/to/file.md)`.
- Prefer linking to *canonical artifacts* (resources/beliefs/decisions/experiments/synthesis) rather than to inbox captures.
- When you supersede a record, link both directions:
  - old → new (“Superseded by …”)
  - new → old (“Supersedes …”)

## Citations / sources

When a claim depends on an external source, add a `## Sources` section with bullet entries. Prefer primary sources.

Recommended source bullet format:

- Title — Author/Org — Published date — URL — Accessed `YYYY-MM-DD`

If no stable URL exists, cite enough information to re-find the source (book/paper identifiers).

## Naming conventions (new files)

- Beliefs: `beliefs/<slug>.md`
- Decisions: `decisions/DEC-YYYY-MM-DD-<slug>.md`
- Experiments: `experiments/EXP-YYYY-MM-DD-<slug>.md`
- Synthesis: `synthesis/SYN-YYYY-MM-DD-<slug>.md`
- Resources: `resources/<slug>.md`

Use lowercase slugs with hyphens.

## Status vocabulary (recommended)

- `draft` — incomplete; may be messy
- `hypothesis` — plausible but untested
- `tested` — evaluated against evidence/experiments
- `stable` — unlikely to change without strong evidence
- `deprecated` — retained for history, not used as a live constraint
- `superseded` — replaced by a newer record (decisions/experiments)

## Revision history (beliefs)

Beliefs should include a `## Revision history` section with dated entries:

- `YYYY-MM-DD` — what changed and why (link to evidence/experiment if applicable)

