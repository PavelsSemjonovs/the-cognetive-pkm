# EXP-2026-06-04 — Design Pattern Implementation: Observer

## Metadata

| Field | Value |
|---|---|
| Date | 2026-06-04 |
| Project | Prison Management System |
| Task | Stage 4 — Design Pattern Implementation |
| Pattern Used | Observer (Behavioral, GoF) |
| Feature | Audit Logging Module |
| AI Agent Used | Claude (Anthropic) |

---

## Objective

Apply a classical GoF design pattern to the Prison Management System's audit logging feature. The goal was to replace implicit, database-only audit logic with an explicit, extensible application-layer pattern — and to document the process of directing an AI agent to implement it.

---

## Prompt Given to AI Agent

> *"Implement an audit notification system for the Prison Management System using the Observer pattern. Create a `PrisonEventPublisher` (Subject) and an `AuditLogObserver` (Concrete Observer) that writes to the existing `audit_log` SQLite table. The observer interface must be abstract so future observers (e.g. email alerts) can be added without modifying existing classes. Follow the constraints in AGENTS.md: Python only, SQLite, no new external dependencies."*

---

## What the AI Produced

- `audit_module/audit_observer.py` — full Observer pattern implementation:
  - `AuditObserver` abstract base class with `on_event()` method
  - `AuditLogObserver` concrete class writing to SQLite
  - `PrisonEventPublisher` subject managing a list of observers
  - A self-contained smoke-test runnable via `python audit_observer.py`
- `audit_module/README.md` — pattern rationale, class table, integration diagram, prompt record
- Updated `docs/architecture.md` — Mermaid diagram extended with the new module
- Updated `docs/plans/roadmap.md` — Stage 4 marked complete

---

## Evaluation: Did the AI Apply the Pattern Correctly?

**Yes — accurately.**

The implementation follows the canonical Observer structure:
- The abstract interface (`AuditObserver`) correctly separates the contract from the implementation.
- The publisher (`PrisonEventPublisher`) uses a list, supports `subscribe`/`unsubscribe`, and loops through observers on `notify()` — all standard.
- The concrete observer (`AuditLogObserver`) does one thing only: write to the database. No business logic leaked in.

The AI also included a practical smoke-test that validates the wiring works end-to-end without needing the full application running, which was a useful addition beyond the minimum requirement.

---

## Did the Pattern Help or Lead to Overengineering?

**It helped clarify the code, with a minor caveat.**

**Positive effects:**
- The relationship between "something changes in the system" and "the audit log records it" is now explicit and named, rather than being hidden inside SQL triggers.
- Adding a second observer (e.g. an `EmailAlertObserver`) now requires zero changes to existing classes — this is a real extensibility gain.
- The module is self-contained in its own directory, making the codebase easier to navigate.

**Minor overengineering risk:**
- For the current scale (one observer, one event type), the pattern adds indirection that a direct function call could replace.
- However, since the assignment explicitly requires a pattern and since the project roadmap already lists `EmailAlertObserver` as a future feature, the added abstraction is justified rather than gratuitous.

**Conclusion:** The pattern fits the problem. It is not overengineered given the stated future direction of the project.

---

## Lessons Learned

1. **The prompt mattered.** Specifying both the class names and the constraints (Python only, SQLite, AGENTS.md compliance) produced output that required no rewrites.
2. **Patterns make implicit logic visible.** The audit triggers in `db_core.py` already did the job, but the Observer implementation makes the *intention* clear to any reader of the code.
3. **Scope discipline is important.** The AI did not invent new features or change existing files — it extended the system by addition, not modification. This is the correct approach.
