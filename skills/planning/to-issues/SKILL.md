---
name: to-issues
description: Break plans, specs, or PRDs into independently grabbable tracker issues. Use when converting plans into tickets or implementation slices.
---

# To Issues

Break a plan into independently-grabbable issues using vertical slices (tracer bullets).

The issue tracker and triage label vocabulary should have been provided by repo docs or project instructions. If missing, inspect `AGENTS.md`, `CONTEXT.md`, docs/ADR files, and available issue tracker metadata; ask one focused setup question only if the tracker or labels remain ambiguous.

## Process

### 1. Gather context

Work from whatever is already in the conversation context. If the user passes an issue reference (issue number, URL, or path) as an argument, fetch it from the issue tracker and read its full body and comments.

### 2. Explore the codebase (optional)

If you have not already explored the codebase, inspect `git status --short --branch`, repo instructions, `README.md`, `CONTEXT.md`/`CONTEXT-MAP.md`, `docs/adr/`, relevant manifests/tests, `codebase-map-understand.md` when present. For broad plans, consult the codebase map for module/caller/data-flow leads and verify named files before slicing. Issue titles and descriptions should use the project's domain glossary vocabulary and respect ADRs in the area you're touching.

### 3. Draft vertical slices

Break the plan into **tracer bullet** issues. Each issue is a thin vertical slice that cuts through ALL integration layers end-to-end, NOT a horizontal slice of one layer.

Slices may be 'HITL' or 'AFK'. HITL slices require human interaction, such as an unresolved architectural decision. AFK slices have enough information for autonomous implementation; the label does not authorize merging, deployment, or other external actions. Prefer AFK when the evidence supports it.

<vertical-slice-rules>
- Each slice delivers a narrow but COMPLETE path through every layer (schema, API, UI, tests)
- A completed slice is demoable or verifiable on its own
- Prefer many thin slices over few thick ones
</vertical-slice-rules>

### 4. Check the breakdown

Present the proposed breakdown as a numbered list. For each slice, show:

- **Title**: short descriptive name
- **Type**: HITL / AFK
- **Blocked by**: which other slices (if any) must complete first
- **User stories covered**: which user stories this addresses (if the source material has them)

Check granularity, dependency order, story coverage, and HITL/AFK classification against the source plan. Reuse an approved breakdown. Ask only about decisions that change scope or dependencies; a complete request to create these issues already authorizes the requested publication. For a draft-only request, return the issue bodies and stop there.

### 5. Publish the issues to the issue tracker

For each approved slice, publish a new issue to the issue tracker. Use the issue body template below. These issues are considered ready for AFK agents, so publish them with the correct triage label unless instructed otherwise.

Publish issues in dependency order (blockers first) so you can reference real issue identifiers in the "Blocked by" field.

Before creating an issue, check for an existing issue covering that slice. On partial failure, retain confirmed issue URLs and resume only the missing creations; verify remote state before retrying a request whose outcome is uncertain. Report created, reused, and still-pending slices.

<issue-template>
## Parent

A reference to the parent issue on the issue tracker (if the source was an existing issue, otherwise omit this section).

## What to build

A concise description of this vertical slice. Describe the end-to-end behavior, not layer-by-layer implementation.

Avoid specific file paths or code snippets — they go stale fast. Exception: if a prototype produced a snippet that encodes a decision more precisely than prose can (state machine, reducer, schema, type shape), inline it here and note briefly that it came from a prototype. Trim to the decision-rich parts — not a working demo, just the important bits.

## Acceptance criteria

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## Blocked by

- A reference to the blocking ticket (if any)

Or "None - can start immediately" if no blockers.

</issue-template>

Do NOT close or modify any parent issue.

## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for repo study, dirty-worktree hygiene, verification evidence, safe handoffs, and safety defaults.
