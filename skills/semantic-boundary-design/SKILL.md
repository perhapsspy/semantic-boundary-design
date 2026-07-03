---
name: semantic-boundary-design
description: Use when a feature, migration, integration, port, or refactor crosses UI, route, client state, command, API, storage, realtime, adapter, or presentation layers and semantic decisions may drift across convenient callers. Apply before or during work involving identity aliases, lifecycle/status, permissions/capabilities, route/query grammar, command payloads, result/event projection, freshness/fallback/revision behavior, compatibility adapters, or multiple representations of the same user/domain meaning.
---

# Semantic Boundary Design

## Purpose

Prevent semantic drift across representation boundaries.

When the same meaning passes through raw data, user intent, events, records, routes, commands, API payloads, realtime patches, and presentation models, assign one owner for each semantic decision. Many layers may observe, pass, or render data; only one layer should decide what a domain meaning is.

## Use / Do Not Use

Use this skill to steer capability-wide design before local code shaping when:

- a change crosses several layers or representations
- equivalent meanings have aliases, fallbacks, derived labels, statuses, permissions, or lifecycle rules
- callers are starting to parse, normalize, translate, or infer meaning for convenience
- compatibility, migration, or integration code risks preserving product policy outside the owner
- tests are asserting helper internals instead of behavior contracts at owner boundaries

Do not use this skill for:

- tiny local edits with no semantic boundary movement
- read-only discovery of current source owners; use `source-owner-audit` first or alongside this skill
- local primary-flow cleanup after owners are already clear; use `structure-first`
- async interaction freshness alone; use `interactive-state-flow`
- deciding whether a broad change is justified; use `justified-change`

## Adjacent Skills

- `source-owner-audit` identifies current source owners from evidence. It does not assign new semantic owners or authorize edits.
- `structure-first` shapes the current unit's readable flow, atoms, and contract tests after semantic owners are known.
- `interactive-state-flow` specializes in route, async, realtime, stale, pending, and presentation freshness ownership.
- `justified-change` keeps implementation scope proportional and verifiable. It does not decide where a semantic rule belongs.

## Operating Flow

1. Name the capability in user or domain terms.
2. List representation crossings: source record, read model, UI draft, user intent, route/query state, client command input, API/remote payload, command result, event/realtime patch, presentation model, compatibility adapter.
3. Identify semantic decisions: identity/alias, lifecycle/status, permission/capability, command grammar, route/navigation grammar, freshness/conflict/revision/pending/fallback, projection/presentation, compatibility.
4. Assign one owner per decision. Prefer the smallest durable owner that has enough context and authority to decide the meaning.
5. Define caller boundaries: callers may pass, select, invoke, display, or render; callers must not interpret, normalize, re-decide, or preserve policy unless they own that decision.
6. Refactor only the scope justified by the current task. Do not repair every nearby drift smell unless it blocks the owner boundary or verification.
7. Add guards or tests that fail if semantic decisions leak into callers.
8. Hand off local code shaping, async freshness, read-only owner discovery, or scope control to the adjacent skill that owns that concern.

## Owner Selection Rules

- Schema or field aliases -> record/contract owner.
- User intent shape -> UI surface or command input owner.
- Final command payload -> session/command owner.
- API request parsing -> application route owner, not a framework route wrapper.
- Route or query grammar -> navigation owner.
- Permission or capability -> policy owner.
- Labels and actions -> surface/view-model owner.
- Result envelope, patch, or resync semantics -> application/realtime result owner.
- Stale, pending, fallback, conflict, or revision acceptance -> freshness-owning route, session, or screen owner.
- Compatibility behavior -> adapter translates between shapes; it does not own policy unless explicitly assigned.

## Drift Smells

- `x || y || z` fallback chains outside the record/contract owner.
- Duplicated lifecycle or status checks.
- UI code building final command payloads directly from records.
- Route components parsing or building shared query grammar.
- API route wrappers reading business request fields.
- Realtime or event handlers re-deciding lifecycle, permission, or product policy.
- Duplicated revision, conflict, pending, fallback, or freshness keys.
- Adapters preserving product policy instead of translating to the owner.
- Tests asserting helper internals instead of owner-boundary behavior.

## Required Guards

Choose the smallest guard that protects the owner boundary:

- Contract tests for alias normalization, command payload shape, route/query grammar, or result envelopes.
- Boundary tests showing callers pass/render/invoke without reinterpreting meaning.
- Negative cases for stale, fallback, permission, lifecycle, or compatibility behavior when those decisions are owner-owned.
- Type or schema constraints that make duplicate interpretations harder to express.
- Regression tests for the user-visible behavior that depends on the semantic decision.

Avoid tests that only freeze a helper's current implementation. The useful assertion is that meaning is decided once, by the owner, and callers cannot silently choose another meaning.

## Output Contract

When this skill is useful for a plan, review, or implementation note, keep the output compact:

- `Capability:` user/domain capability being shaped
- `Representation Crossings:` relevant data or control forms
- `Semantic Decisions:` decisions that could drift
- `Owner Ledger:` `decision -> owner -> reason`
- `Caller Boundaries:` what callers may do and must not do
- `Drift Smells:` observed or likely leaks
- `Required Guards:` tests, schemas, or checks needed
- `Handoffs:` other skills or follow-up owners

## Final Gates

- Is the capability named in user/domain terms?
- Are all relevant representation crossings visible?
- Does each semantic decision have exactly one owner?
- Can callers observe, pass, render, or invoke without deciding meaning?
- Are adapters limited to translation unless explicitly assigned policy ownership?
- Are fallback, freshness, lifecycle, permission, and compatibility decisions owned where they can be verified?
- Is the refactor scope limited to what the current task justifies?
- Do guards verify behavior contracts at owner boundaries rather than helper internals?
- Are needed handoffs to adjacent skills explicit?
