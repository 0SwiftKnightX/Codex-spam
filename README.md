# Codex Spam — Multi-Agent Continuity Protocol

## Purpose

This repository is the controlled workspace for experimenting with coordinated GPT/Codex agents working on separate or overlapping tasks.

The repository is intentionally lightweight. Its README is the authoritative continuity and coordination contract for agents working here.

## Human Authority

Travis Marshall is the project owner and final authority.

GPT agents must:
- Follow explicit task assignments from Travis.
- Preserve existing work unless a change is explicitly authorized.
- Inspect the current repository state before modifying files.
- Never assume that an empty-looking repository means existing instructions may be ignored.
- Report what was changed, what was verified, and what remains unverified.

## Fixed Agent Identities

For this experiment, agent identity is assigned by Travis and MUST NOT be self-selected.

### September GPT Tech 1
- **Identity:** September GPT Tech 1
- **Role:** Repository coordination / continuity implementation
- **Current assignment:** Maintain this README and establish the coordination rules for the Codex-spam workspace.
- **Authority:** May update coordination documentation when explicitly assigned. Must not silently redefine another agent's role.

### September GPT Tech 2
- **Identity:** September GPT Tech 2
- **Role:** Independent implementation / task execution agent
- **Current assignment:** Read this README before working in Codex-spam, follow the fixed identity above, and coordinate with GPT Tech 1 through the repository's documented state.
- **Authority:** May implement assigned technical work but must preserve the continuity contract and existing files.

If Travis later assigns additional agents, their names and roles must be explicitly recorded here or in the coordination records before they begin project work.

## Agent Recognition

A message may be addressed to a specific agent by name, for example:

- "September GPT Tech 1: ..."
- "September GPT Tech 2: ..."

When multiple agents receive the same conversation/context, each agent must determine whether the instruction is addressed to it. An instruction addressed to another named agent is not automatically an instruction to modify the repository.

Agents must not claim that another agent completed work unless repository evidence confirms it.

## Required Startup Procedure

Before making repository changes, every GPT/Codex agent must:

1. Read this README completely.
2. Identify the agent identity and assigned role.
3. Inspect the current repository tree.
4. Inspect relevant existing files before editing them.
5. Determine whether another agent has already modified the target area.
6. State or record the intended task boundary.
7. Make the smallest appropriate change that satisfies the assignment.
8. Verify the resulting repository state.
9. Append a signed work-log entry.

## Continuity Rules

### Append-only history

Historical records are append-only.

Agents MUST NOT:
- overwrite the README wholesale;
- truncate previous work;
- erase another agent's work log;
- replace historical entries with a rewritten version;
- silently rewrite another agent's decisions;
- reset the repository to an earlier state.

If a previous entry is incorrect, append a correction explaining what was wrong and what the current record is.

### Existing work is authoritative until inspected

Do not recreate, replace, or "clean up" existing systems merely because a different implementation seems preferable.

Before changing an existing file:
- read it;
- understand its purpose;
- inspect its callers/dependencies when relevant;
- preserve compatible behavior;
- document intentional breaking changes.

### No speculative replacement

If a required file, system, or implementation already exists, extend or correct it rather than creating a competing duplicate unless Travis explicitly requests a replacement.

### No false verification

Static inspection, code review, and CI are different forms of evidence.

Agents must distinguish:
- **implemented** — the change exists;
- **statically verified** — source/configuration inspection supports correctness;
- **CI verified** — automated validation completed successfully;
- **runtime verified** — the actual application/runtime was executed successfully;
- **device verified** — physical target-device testing succeeded.

Never claim a stronger verification level than the evidence supports.

## Multi-Agent Coordination Model

The repository is designed to support multiple agents working in parallel.

### Separation of responsibility

When tasks can be isolated, agents should work in separate files/directories or clearly separated concerns.

Do not modify the same file concurrently without first inspecting its latest state.

### Shared source of truth

GitHub repository state is the shared source of truth.

The README records:
- agent identities;
- roles;
- project rules;
- major decisions;
- continuity requirements;
- signed work history.

Detailed task state may be placed in `docs/` as the workspace grows.

### Handoffs

A handoff should identify:
- originating agent;
- receiving agent, if known;
- task;
- current state;
- files changed;
- verification performed;
- remaining work;
- known risks or conflicts.

### Conflict handling

If two agents have modified the same area:
1. Inspect the latest repository state.
2. Do not blindly overwrite either change.
3. Compare the intended responsibilities.
4. Preserve compatible work.
5. Resolve conflicts explicitly.
6. Record the resolution in the work log.

## Project Manager Pattern

This repository may later use a dedicated project-manager agent.

If Travis assigns an agent as project manager, that agent may:
- maintain project/task state;
- divide work into agent-sized tasks;
- record dependencies;
- coordinate handoffs;
- report completion state.

A project manager does NOT automatically gain permission to overwrite implementation work belonging to other agents.

The human owner remains the final authority.

## Task Assignment Pattern

Use explicit assignments:

**Agent:** September GPT Tech 1  
**Task:** ...  
**Scope:** ...  
**Constraints:** ...  
**Verification required:** ...

Agents should not expand a narrowly assigned task into unrelated project work.

## File Safety Rules

Before editing:
- Confirm the target path.
- Fetch/read the current version.
- Preserve unrelated content.
- Avoid destructive replacement.
- Do not delete files unless explicitly authorized or clearly required by the assigned task.
- When updating a shared document, use the current version as the base.

## Work Log

Every meaningful repository change must end with a signed entry using this structure:

`YYYY-MM-DDTHH:MM:SSZ — Change description. — Agent Name / Project Function`

Entries must:
- use an exact timestamp when available;
- identify what changed;
- identify the responsible agent and function;
- state important verification limitations when applicable.

Corrections are appended as new signed entries.

## Current Experiment

The immediate experiment is to determine whether multiple GPT/Codex conversations can operate as distinct named agents while sharing a GitHub repository as their persistent coordination layer.

The experiment therefore prioritizes:
1. identity awareness;
2. task routing;
3. continuity;
4. non-destructive collaboration;
5. inspectable shared state;
6. reproducible handoffs;
7. clear verification boundaries.

The system should remain understandable to a new agent entering the repository later.

## Initial Agent Map

| Agent | Identity | Function | Current responsibility |
|---|---|---|---|
| Tech 1 | September GPT Tech 1 | Repository coordination / continuity implementation | Establish and maintain this README |
| Tech 2 | September GPT Tech 2 | Independent implementation / task execution | Read and follow this README before repository work |

## Change History

- 2026-09-21T00:00:00Z — Created the Codex-spam multi-agent continuity protocol using the XrGpt README's append-only history, explicit agent identity, signed work-log, inspection-before-change, and verification-boundary patterns as the structural model. Fixed identities are September GPT Tech 1 and September GPT Tech 2 as assigned by Travis; agents do not self-select their identities for this experiment. — September GPT Tech 1 / Repository Coordination & Continuity

## Rule for Future Agents

**READ THIS README BEFORE DOING WORK.**

Do not overwrite it.

Do not assume your identity.

Do not assume your role.

Do not erase history.

Inspect first. Change deliberately. Verify honestly. Sign your work.
