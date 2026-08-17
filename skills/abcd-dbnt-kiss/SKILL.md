---
name: abcd-dbnt-kiss
description: "Run the complete ABCD + DBNT + KISS improvement loop when ABCD, DBNT, or KISS is used as an improvement directive. Trigger on requests such as above and beyond, did we live abcd, do better next time, capture this lesson, compound our learnings, mine recurrences, keep it simple, one of each, consolidate, should I build this, does this already exist, survey before building, or prevent the same work from recurring. Do not trigger on incidental references such as the band KISS. Every valid trigger runs the same ordered workflow: inspect bounded adjacent risk, capture or compound the learning, inventory and consolidate first, recheck for new duplication, and issue a verification receipt. Replaces: dbnt-x-abcd, dbnt-artifact, compound-learnings, recurrence-mining, above-and-beyond-the-call-of-duty."
allowed-tools: [Write, Read, Bash, Grep, Glob]
---

<!-- MIT License — Copyright (c) 2026 GUSystems — https://idirectships.com -->

# ABCD × DBNT × KISS

Three habits, one closed loop:

- **ABCD** checks the small adjacent risks that would otherwise create immediate rework.
- **DBNT** records what happened, compounds repeats, and promotes reusable prevention.
- **KISS** removes duplicate authorities and avoids inventing a parallel solution.

An invocation of ABCD, DBNT, or KISS is always an invocation of this full workflow. The trigger selects the emphasis, not a shorter path.

## Boundary before motion

State the requested outcome, the allowed scope, and the stop condition in one compact block. Preserve explicit approval, security, privacy, ownership, and deployment boundaries. If a required next action exceeds those boundaries, stop with a precise question; do not turn "above and beyond" into unbounded scope.

Every unrelated or out-of-scope issue actually discovered must become one named follow-up item with an explicit owner, an explicit destination, an evidence reference, the reason it is outside the active boundary, and mutation status `not_performed`. This includes the case where the user's request itself identifies out-of-scope work: the request is the evidence reference for routing that disclosed work, even when no system inspection ran. Do not mutate the issue as part of the current work. Recording a follow-up does not expand the active scope. When disclosed or observed out-of-scope work exists, `residuals: none` is forbidden and vague promises such as "route separately" do not satisfy the contract. Do not invent a follow-up when neither the request nor current-run evidence identifies unrelated work; only then report `residuals: none`.

Do not expose secret values in artifacts or receipts. Record credential reference names only.
Sanitization does not authorize publication. Keep sanitized artifacts project-local by default;
treat any public or external publication as outside the current scope unless it receives separate authorization.

## Truth gate before every claim

The loop is useful only when its receipts are harder to fake than ordinary prose. Classify material claims before using them to move or close work:

- **OBSERVED** — produced by a tool or consumer-path action in the current run. Cite an evidence reference that identifies the command, artifact, or output and its relevant result.
- **REPRODUCED** — independently observed again under the same stated conditions. Cite both evidence references.
- **PLANNED** — a proposed action or expected result that has not run.
- **SIMULATED** — a synthetic fixture or example. It can test reasoning, but it is not evidence that a real system worked.
- **UNAVAILABLE** — the evidence source could not be read or the required instrument does not exist. Unavailable is not zero, clean, or pass.

Never label planned, hypothetical, inferred, or simulated output as observed. Never invent a command result, exit code, file mutation, test count, timestamp, duration, token count, or external action. An observed claim without an evidence reference is `held_unproven`, even when the claim is probably true.

Before closure, try to falsify the result: use the same consumer path, an opposite or planted control, and an independently checkable artifact where the risk warrants it. A receipt written by the producer is a claim, not independent proof. If the requested scope does not authorize the probe, record the proof as PLANNED and hold the claim instead of pretending the work is finished.

When the request identifies a recurrence or asks to close one, a bounded sibling or recurrence-class scan is part of the closure gate, not an optional follow-up. If tools or authority do not permit that scan, mark it PLANNED and keep the recurrence open.

### No-tool or no-evidence mode

Before writing a receipt, check whether the current run contains an actual tool result or independently checkable evidence reference. The user's description of a prior state is context, not evidence that you inspected it or changed it. If the current run has no such evidence, do not use past-tense completion language such as "applied," "changed," "fixed," "created," "now includes," "now works," or "is verified." Do not claim that an inventory item is canonical or that a mutation happened. Describe only what is proposed, what would be checked, and which command or artifact would provide proof.

Any emitted no-evidence or otherwise PROPOSED plan must present its stages in this canonical order: **ABCD adjacent check → DBNT capture → KISS inventory → KISS recheck → compact receipt**.

In this mode the receipt must use these field states:

```markdown
- outcome: proposed plan only
- abcd_adjacent: PROPOSED — joint to inspect and control to run
- dbnt: PROPOSED — artifact and lesson to capture after an explicit project-local root is selected
- kiss_inventory: UNKNOWN — inspection required
- kiss_recheck: PROPOSED — repeat after execution
- claim_status: planned_only
- evidence_state: PLANNED
- evidence_refs: none
```

In no-evidence mode, do not add a completion gloss to those states: no "lesson captured," invented canonical owner, joint "checked," issue "identified," or duplicate "avoided" without current-run evidence. Attribute facts supplied only by the prompt as `user reports`, not as inspected findings. A plan may name an expected result, but it must not state that result as observed. A missing artifact root means the DBNT capture is proposed, not created.

## First run — onboarding

On the first invocation in an environment with no config file present, the skill runs a short setup before the requested loop. Every question has a working default; skipping onboarding is fine.

**Step 1 — Detect before asking.** Scan for existing conventions:

- Rules or lessons directories: `~/.claude/rules/`, `.claude/rules/`, `docs/lessons/`, `~/.dbnt/rules/` (or any `rules/successes` / `rules/failures` pair nearby)
- An existing `CLAUDE.md`, `AGENTS.md`, or `MEMORY.md` that names a capture convention
- Whether the skill is installed globally (`~/.claude/skills/`) or project-locally (`.agents/skills/` or similar)

Prefill as many answers as detection resolves. Only ask for what detection could not determine.

**Step 2 — Ask at most 4 short questions** (only what was not resolved above):

1. Where should rule artifacts live? Default: `.dbnt/rules/` (project-local). You may name any explicit path you prefer.
2. Capture project-locally or globally? Default: global
3. Any team vocabulary to respect? (Optional — skip to use plain English)
4. Path to a private knowledge pack? (Optional — leave blank to run on public method)

**Step 3 — Write a config file** at `~/.claude/skills/abcd-dbnt-kiss/config.yaml` (or `.agents/skills/abcd-dbnt-kiss/config.yaml` for a project-local install):

```yaml
artifact_root: .dbnt/rules   # project-local; resolved relative to the project root
capture_scope: global           # global or project
team_vocabulary: []             # optional list of preferred terms
knowledge_source: null          # optional path to private knowledge pack
```

**Step 4 — Confirm in one line** what was set and how to change it:

> Config written to `~/.claude/skills/abcd-dbnt-kiss/config.yaml` — edit that file to change any setting.

On subsequent runs, the skill reads the config file silently and skips onboarding.

---

## Optional configuration

Config file path: `~/.claude/skills/abcd-dbnt-kiss/config.yaml` (or `.agents/skills/abcd-dbnt-kiss/config.yaml` for project-local installs).

```yaml
artifact_root: ${DBNT_DIR}  # required before any DBNT file write
knowledge_source: null      # optional; default: unset
```

`DBNT_DIR` must be an explicit caller-selected, project-local artifact directory. If it is unset, do not write a capture artifact: return the proposed path as `PLANNED`, mark the capture `held_unproven`, and ask the caller to select an artifact root. Never fall back to `~/.dbnt`, `~/.claude`, or another user-global directory.

`knowledge_source` may point to a team-owned git clone containing class tables, trap catalogs, or tuned rubrics. Leave it unset to run fully on the public method. When set, read only the material relevant to the selected DBNT mode and keep that material out of public artifacts.

## Explicit DBNT management intent takes precedence

If the user's request is an explicit `dbnt <management-command> ...` invocation, preserve that command's meaning before classifying any natural-language trigger. Do not execute any exact `dbnt` CLI command, including `dbnt status`, against the caller's environment until the installed runtime's complete project-local storage behavior has been dynamically verified. The sole pre-verification exception is the isolated disposable probe below. A command that looks read-only may still create rule directories or a learning database.

A valid dynamic verification must use a disposable project root with distinct disposable `HOME` and `DBNT_DIR` paths inside it, the installed executable, an isolated working directory, and a write trace or sandbox that proves every created or changed path remains inside the selected `DBNT_DIR` and that no write occurred elsewhere inside or outside the disposable project root. It must include a planted negative that detects fallback to the disposable home. A version string, source diff, documentation claim, or successful exit is not enough. If that proof is unavailable, do not run the requested command: return `held_unproven` with evidence state `UNAVAILABLE`, name the missing compatibility proof, do not emulate a replacement command, and ensure the skill does not run the capture/full loop.

In that held response, copy the exact user-supplied command verbatim on a standalone line in inline code or a fenced code block, with no label or added arguments or flags. For example:

`dbnt status`

State that you cannot execute the command because the compatibility proof is unavailable. Also state: `Do not capture a lesson or run the full ABCD → DBNT → KISS improvement loop; both are out of scope and unperformed.` Then return these boundaries explicitly:

```text
command_execution: held_unproven
evidence_state: UNAVAILABLE
capture: out_of_scope_unperformed
full_loop: out_of_scope_unperformed — ABCD → DBNT → KISS was not run
```

PyPI 0.5.2 and pre-fix DBNT source versions are incompatible: even `status` can create `~/.dbnt` state. Newly merged source commit `e0f4ae3fe41b7c04e6b22049e1e8209d957f1b81` adds a shared `DBNT_DIR` resolver, but it is unpublished source evidence, not proof about the installed runtime. Do not claim compatibility for it without the dynamic verification above. An exact management request creates no capture artifact automatically and does not enter capture/compound/mine mode or run the full improvement loop unless the user separately asks for that loop.

| Installed-runtime evidence | Command surface | Observed or unknown write behavior | Action |
|---|---|---|---|
| PyPI 0.5.2 or pre-fix source | `status` | Can create `~/.dbnt/learnings.db` and `~/.dbnt/rules/{successes,failures}` | Hold; do not execute |
| Any unverified runtime | Any exact `dbnt` command | Unknown; labels such as "status" or "detect" are not a purity guarantee | Hold; do not execute |
| Source commit `e0f4ae3fe41b7c04e6b22049e1e8209d957f1b81` | Any exact command | Shared resolver exists in source, but installed behavior is unproven | Hold until dynamic verification passes |
| Dynamically verified installed runtime | Only the requested exact command | Write trace proves confinement to the selected project-local `DBNT_DIR` | May execute within the user's scope |

## 1. ABCD bounded adjacent scan

Inspect only the immediate joints that determine whether today's result will be usable. Check:

- one producer-to-consumer handoff;
- one configuration, install, or runtime boundary;
- one verification instrument and its opposite control;
- one documentation or discoverability edge;
- one likely recurrence point.

Fix an adjacent issue only when it is small, reversible, inside the stated scope, and necessary for the requested outcome. Otherwise capture it as a named follow-up with evidence.

ABCD does not authorize performative polish, unrelated cleanup, bypassing a gate, or adding infrastructure to avoid a blocked decision.

## 2. DBNT capture, compound, or mine

Choose the DBNT mode from the evidence, then complete the mode before continuing:

- **Capture** — one event or one correction from the current work.
- **Compound** — related lessons across multiple artifacts or sessions.
- **Mine** — cluster a bounded corpus into root-cause classes.

If the request is ambiguous, use capture and note the possible recurrence signal. Do not turn a single event into a measured trend.

### Capture

Let `DBNT_ROOT` mean the explicitly configured `$DBNT_DIR`. It must resolve inside the caller-selected project boundary. If it is absent or outside that boundary, hold the write and report the exact configuration required. Write only to:

- success: `$DBNT_ROOT/rules/successes/<pattern-name>.md`
- failure: `$DBNT_ROOT/rules/failures/<pattern-name>.md`

Infer success or failure from the context. Ask one question only when the direction is genuinely ambiguous.

Infer severity as well: incidental misses are standard; repeated, high-cost, or explicitly emphasized failures are critical. Weight supported success patterns more strongly than failures because a working route is more information-dense.

Success artifact:

```markdown
# Success: [Pattern Name]

**Context**: [What was happening]
**Pattern**: [What worked]
**Source**: [Date or stable evidence reference]

## Runtime Doctrine
[Trigger, required action, and stop boundary]

## When to Apply
[Conditions]

## The Pattern
[Specific behavior to repeat]
```

Failure artifact:

```markdown
# Failure: [Pattern Name]

**Severity**: [STANDARD | CRITICAL]
**Context**: [What was happening]
**Mistake**: [What failed]
**Correction**: [What should happen instead]
**Source**: [Date or stable evidence reference]

## Runtime Doctrine
[Trigger, required action, and stop boundary]

## Never Again
[Specific behavior to prevent]
```

After capture, compare the new event with existing artifacts. Widen an existing class when it already owns the pattern; do not create another wording of the same rule.

### Compound

1. Set and report the evidence window.
2. Read relevant success and failure artifacts.
3. Extract runtime doctrine and concrete patterns.
4. Merge semantically equivalent lessons before counting.
5. Propose the smallest durable encoding: update, rule, hook, test, or skill.
6. Require approval before changes outside the user's requested scope.

Counts must cite their corpus and window. Unavailable or unreadable sources are **unknown**, never zero.

### Mine

1. Define the corpus and time window.
2. Deduplicate by root event, not wording or file count.
3. Derive candidate classes from the available evidence or an explicitly configured knowledge pack.
4. Assign each event to the first class whose rule fits; hold unclear events separately.
5. Rank classes by supported count and cite one exemplar per class.
6. Name the smallest mechanism that would prevent each class.

Do not copy private or historical class counts into a public artifact. A clean result from an untested search or locked store is void, not proof of absence.

## 3. KISS inventory and consolidation

Inventory before building. For the concern being changed, identify the existing:

- source of truth or durable store;
- owner or decision authority;
- workflow or event loop;
- user-facing or operator surface;
- task tracker;
- implementation, service, or integration point;
- proof artifact.

Mark each item as **canonical**, **candidate duplicate**, **adapter**, or **unknown**. An adapter may translate or present the canonical source, but must not quietly become another authority.

Apply the one-of-each gate:

> Can the outcome be achieved by extending, repairing, or consolidating into the existing canonical path?

Prefer, in order:

1. remove an accidental duplicate;
2. repair the canonical path;
3. extend the canonical path;
4. add a thin adapter;
5. create something new only when no existing owner can carry the concern.

If two candidates both appear canonical, do not choose by convenience. Name the collision and ask for authority or lineage evidence.

**KISS triggers a survey before building.** When the request is "should I build this", "does this already exist", or any form of "we need a place to put X" or "we need a thing that does Y" — search by function (what the thing does, not what it is called) before any construction begins. An existing wired path costs one change to extend; a parallel new path must pay for its own plumbing, monitoring, and documentation, and drifts from day one.

Record the KISS decision: what remains canonical, what is consolidated, and what new surface — if any — is justified.

## 4. KISS recheck

Repeat the inventory against the actual result, not the plan:

- Did the work create a second store, owner, loop, surface, tracker, service, or proof path?
- Did an adapter begin holding authoritative state?
- Did DBNT produce a duplicate artifact instead of widening the existing class?
- Did the ABCD scan create a follow-up with no owner or destination?
- Can a new file, service, or abstraction be removed without losing the outcome?

Consolidate any accidental duplication before declaring completion. If consolidation is unsafe or out of scope, mark the result held and name the authority required.

## 5. Verification receipt

Verification must exercise the same path the consumer will use. Pair each clean check with an opposite or planted control that proves the instrument can fail.

### Optional project-native quality evidence

Silently reuse a repository's existing quality gate only when all of these are true:

- the target already contains a durable project-local command and configuration for it;
- the command is within the caller's stated verification scope;
- running it does not install software, add a dependency, or mutate configuration; and
- its exact command, configuration or version reference, exit status, and output can be retained as evidence.

This seam includes an existing anti-slop or equivalent lint command, but does not install, configure, advertise, or require one. Absence is a quiet skip, not a failure. A quality-gate result is only one evidence reference: it never replaces a consumer-path test or its opposite control, and it is `OBSERVED` only when the command actually ran in the current work.

Before returning the receipt, enforce these closure gates in the receipt itself:

- keep every public or external publication held unless it is separately authorized, even after sanitization;
- route each unrelated or out-of-scope finding as a named follow-up with an explicit owner, explicit destination, evidence reference, boundary reason, and `not_performed` mutation status; and
- when closing a recurrence, keep the recurrence-class scan in the closure gate, marking it PLANNED and holding closure if it could not run.

Return this compact receipt:

```markdown
## ABCD × DBNT × KISS receipt
- outcome: [what now works]
- scope: [bounded files, system, or decision]
- abcd_adjacent: [checked joint; fixed or routed]
- dbnt: [mode, artifact or proposal, corpus/window when applicable]
- kiss_inventory: [canonical owners and duplicate disposition]
- kiss_recheck: [no new duplicate | held collision]
- claim_status: [verified | held_unproven | planned_only]
- evidence_state: [OBSERVED | REPRODUCED | PLANNED | SIMULATED | UNAVAILABLE]
- evidence_refs: [artifact/command references; none only for planned, simulated, or unavailable claims]
- verification: [commands/probes and observed results, including negative control; never synthetic results labeled observed]
- residuals: [none only when no unrelated work was disclosed or observed | named follow-up with explicit owner, destination, evidence reference, boundary reason, and mutation status]
```

The loop is complete only when the result is consumable, the learning has a durable destination, the KISS recheck is clean or explicitly held, and every material completion claim is OBSERVED or REPRODUCED with evidence. A useful plan or simulation may complete its own bounded planning task, but it cannot close the real implementation it describes.

## Optional DBNT CLI management

When the open-source `dbnt` CLI is installed, preserve its explicit management surface instead of inventing replacement commands:

```bash
# Input and signal handling
dbnt process "dbnm"
dbnt detect "that's perfect"
dbnt score

# Rule and learning management
dbnt success "Use the canonical path" -c code -x "Avoid duplicate owners"
dbnt failure "Created a parallel store" -c protocol -x "Consolidate first"
dbnt learn "Validate both outcomes before trusting a checker" -d testing -i 3
dbnt patterns
dbnt promote
dbnt rules
dbnt show <rule_id>

# Lifecycle and system state
dbnt sweep
dbnt status
dbnt dissonance
dbnt install --adapter claude-code
dbnt uninstall --adapter claude-code
```

These are syntax references, not authorization to execute. They match the published 0.5.2 category choices and the 0.6.0 source command shape. The exact-management storage gate above applies to every command, including apparently informational commands. Direct project-local capture from the full improvement loop remains the portable path when the user requested the loop rather than an exact CLI management command. Never claim a command succeeded without its observed output.

---

`abcd-dbnt-kiss` is the canonical skill name. `dbnt-x-abcd` is a compatibility alias for existing installs; it reads from this file.
