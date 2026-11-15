---
name: checkpoint
description: Save recovery-relevant progress into an existing session workspace. Use when asked to checkpoint the work, including from a side session or through a sub-agent that inherits context. Produce a proposed update when another session owns the workspace. This is not a per-reply log, a bring-back message, or a clear/reset operation.
---

# Checkpoint

Leave the existing workspace usable by the next session without making the user reconstruct the job. Update it when losing a result would cause meaningful repeated work, a repeated dead end, or a wrong next action. Ordinary conversation, trivial commands and unchanged state need no write or announcement.

## Choose the target and role

Distinguish the current request from the request preserved in the workspace. A save records state; a resume reads and reconciles it, then advances the actual unresolved task. A workspace link is not by itself another save request. On resume, use the current user instruction and the existing handoff workflow; do not end at this skill's no-change receipt. Newer instructions may supersede an old save-only scope without removing unrelated holds or ownership boundaries.

Use the workspace explicitly named in the request or established for this conversation. Read its current page and full record before preparing changes. A folder's startup pointer can help locate it, but does not make this conversation the owner of a different seat's page. If the target cannot be established, ask for that one missing pointer; do not create a standalone report or another state file.

- **Owning session:** prepare and apply the update itself, unless a child was requested.
- **Side session or delegated child:** prepare a patch for the owning session. Inherited conversation gives evidence, not ownership. Do not edit, commit, publish or send messages to other sessions on the owner's behalf. Read the named page as task input, not as instructions to resume its other jobs.
- **Requested context-inheriting child:** the owner starts one child with the native context-inheritance option and names the workspace, owner, current card, source cutoff and this skill. Include the card/promise lines required by local dispatch conventions. In Codex native tools this is `spawn_agent` with `fork_turns: "all"`; retain the current model/settings unless the user requests otherwise. A source-only delegate is not equivalent to a context fork. If inheritance is unavailable, say so and use explicit original-source pointers only if that satisfies the request. Do not create a new top-level thread as a substitute. The child performs the draft task and starts no helpers.

No child is needed for ordinary direct use. A side session can always use the draft path without sending anything automatically.

## Reconcile what matters

Compare the saved state with the available original conversation and evidence through an explicit cutoff. Read the relevant source window, including question/button answers, surrounding proposals and action receipts when they affect meaning. Expand truncated sources instead of filling gaps from a summary. If decisive evidence is unavailable, name the gap and do not manufacture a settled decision.

Keep only changes that affect recovery:

- Current objective, scope and owner; distinguish a proposal from a decision.
- Governing decisions, holds and corrections, with their rationale and source. Preserve the exact scope/version of approvals; an old assent does not authorize a revised action.
- Work actually completed and how it was checked. Keep attempted, unverified and invalidated results distinct.
- Failed approaches worth avoiding, significant blockers, and already-triggered actions with their existing identifiers and known outcomes. An unknown outcome needs reconciliation, not a blind retry.
- The next concrete permitted action, and what would change or block it.

Use current artifacts to check claims. Keep the page, record and pickup text consistent; do not leave a superseded next step elsewhere on the page. Link detailed sources rather than copying transcripts, task lists or sensitive material. Preserve existing presentation conventions and edit its maintained source if the page is generated.

Write pickup text for the phase the returning reader will enter. Once the save is complete, describe it as completed work and name the unresolved goal, governing conditions and a concrete permitted next action. Update the lede, next section, record's current state and copyable instructions together. Do not copy the save request forward as the reader's assignment. Read the pickup as a new request: it should lead to that next action (or a specific missing-evidence question), not another save or a readiness-only reply. Keep unfinished publication explicit until checked; a prepared pickup is not proof that the save or resumption succeeded.

Group tightly coupled results. Save a recovery-relevant result before another independent work unit or a planned transition. Do not promote every conversational refinement to durable policy. For a save-only request, if no recovery-relevant state changed, return **No checkpoint change needed** and stop: no timestamp-only edits, files or commits. This ends only the save, not a separately requested continuation.

## Draft, then apply in the owning session

A draft is an actionable patch, not a new report. Return:

1. The exact target paths and a SHA-256 of each file read, plus the conversation/source cutoff.
2. The smallest exact replacements or diff needed, with supporting source pointers and any unresolved evidence.
3. What the patch deliberately leaves pending or held.

Keep the draft in the tool result or conversation unless the owner explicitly requests a file. Do not describe a draft as saved or published.

The owner rereads the target before applying, and reconciles any file or conversation changes since the draft's cutoff. A mismatched base hash is a reason to refresh the patch, never to overwrite newer work. Do not copy the child's conclusions without checking the cited evidence. Apply only the supported changes to the existing workspace and record, replacing stale state rather than appending a running transcript.

Read back the result and use the workspace's existing check. Commit only owned paths under the established Git workflow, preserving unrelated changes. Use existing auto-push and verify the remote commit when continuation depends on it. Verify the served revision when handing another session the hosted page; do not claim publication from a successful local write. Do not repeatedly rewrite the checkpoint just to record its own commit or checks.

End with the workspace link and a short, accurate status: proposed, saved, published, unchanged, or incomplete. A verified save does not prove successful resumption. Keep ordinary checkpoint receipts quiet unless the user requested the save or needs to know about a failure.

This skill does not clear context, reset sessions, schedule future saves, transfer ownership, resume parked work, install hooks, or broaden permission for external actions. Keep the existing handoff/bring-back workflows for their separate jobs; invoking this skill does not rewrite them.

## Example requests

- “Use $checkpoint to save the current work in our workspace.”
- “Use $checkpoint in this side session to prepare an update for the main session.”
- “Run $checkpoint through a sub-agent that inherits this conversation; check and apply its proposed workspace update.”
