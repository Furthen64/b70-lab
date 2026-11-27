# Conductor experiments

Evaluate collaborative software engineering with a supervising cloud coding agent and a local implementation worker on the Intel Arc Pro B70.

## Architecture

- Conductor: Codex CLI, task assignment, independent review and corrective feedback.
- Worker: OpenCode CLI, Inkling 2 Mini through ArcAngel, implementation and testing.
- Human: architectural decisions, interactive application testing and final feedback.
- Communication: OpenCode CLI JSON events and explicit session continuation; no MCP bridge required.

Keep conductor experiments separate from controlled engine throughput benchmarks. Link to engine configuration IDs when verified.

## Records

Each file in `runs/` represents one delegated task. Track:

| Area | Measurements |
|---|---|
| Task | Scope, acceptance criteria, user-rated complexity (1–10); separately label estimates |
| Worker | Engine/model/version, context capacity and populated depth, input/new/generated tokens, cache reuse, prefill and generation throughput, request timings |
| Conductor | Actual model label, input/output tokens and cost when available, independent review findings |
| Collaboration | Worker session IDs, corrective iterations, human interventions, ownership of source changes |
| Outcome | Acceptance checks, verified defects and fixes, regression tests, completion and remaining limitations |
| Changes | Working-tree snapshots, file counts, additions/deletions; identify baseline |
| Observability | Visibility of worker activity, tool calls and review progress |

Use server instance ID plus request ID to identify worker requests. Preserve timestamp offsets, distinguish completed requests from in-flight requests, and do not count repeated logs twice. Derive weighted decode throughput as total generated tokens divided by the sum of per-request estimated decode durations. Keep actual request elapsed time separate.

Unknown values are null, not zero. Partial excerpts do not establish full-session totals. A model's success claim is not independent verification. A complexity score is subjective; do not confuse complexity with quality. Do not infer savings over cloud-only development without a matched baseline.

Record corrections and final outcomes as additional observations, preserving earlier measurements. Keep this public repository free of private source code, complete prompts, reasoning transcripts, credentials and large logs.

## Experiments

- [Electrow task 12 — component palette and properties](runs/electrow-task-12-2026-11-27.json): first CLI conductor/worker trial; in progress at initial recording.
