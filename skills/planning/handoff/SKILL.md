---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up. Use when the user asks for a handoff, session summary, continuation brief, or next-agent context.
argument-hint: "What will the next session be used for?"
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save to the temporary directory of the user's OS - not the current workspace.

Use a user-specified destination when provided; otherwise choose a unique temporary filename and return its absolute path. Preserve the active objective, latest steering, accepted decisions, remaining tasks, and the next executable step. Include modified paths and their ownership, validation commands with results, exact blockers, and authorization already granted or still needed. Distinguish observed results from assumptions so the next agent does not repeat completed work or mistake a proposed action for approval.

Include a "suggested skills" section in the document, which suggests skills that the agent should invoke. If `codebase-map-understand.md` exists and the continuation needs codebase understanding, include the exact codebase map query to run and any map leads already verified.

Verify the saved file exists and that referenced artifacts resolve. Temporary handoffs are not durable storage; name this limitation if the next session may run on another machine.

Do not duplicate content already captured in other artifacts (PRDs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.

## Shared contract

Follow [the shared skill contract](../../shared/COMMON-CONTRACT.md) for repo study, dirty-worktree hygiene, verification evidence, safe handoffs, and safety defaults.
