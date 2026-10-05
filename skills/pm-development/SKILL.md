---
name: pm-development
description: Coordinate multi-issue or long-running agent development, scheduling verification, independent review, and integration by risk, with delivery timelines and improvement reports.
---

# PM Development

The project manager (PM) owns scope, scheduling, risk decisions, and delivery verification; independent Developers own implementation. Follow the runtime configuration and host repository's rules, specifications, accepted decisions, and authorization. Reuse approved requirements and experiences without asking for the same approval again.

This workflow needs independent implementers and reviewers. Check available capabilities before dispatch; record a capacity limitation when they are unavailable, continue useful preparation, and distinguish that work from independent implementation or review.

## Establish Scope

- For web work, default to desktop delivery unless the user or approved task includes mobile. Preserve existing commitments and apply the latest explicit scope correction, recording which earlier criteria it supersedes.
- Before dispatch, reconcile parent and child acceptance criteria, accepted experience, and latest corrections. Identify key failure states and boundaries. Resolve contradictions through existing decisions or a concrete user decision when required.
- Read the tracker, actual blockers, agents, and Git state. Claim ready implementation issues without an owner. Use one owner, branch, and worktree per issue, with an explicit baseline, public verification entrypoints, and deliverable. Give the Developer the approved artifacts, authorization, and evidence locations.

## Schedule Fairly

- Treat source implementation, heavy execution, and review as separate capacities. Schedule by actual overlap in responsibilities and contracts and by available slots; lightweight preparation may continue during serialized builds.
- Isolate databases, migration identifiers, accounts, ports, build directories, and evidence as well as worktrees. Assign an integration owner for coordinated registration or generation changes. Path overlap alone does not require serializing an entire issue.
- Reuse non-author review roles by phase. An author may finish an active turn once the candidate is frozen or waiting for CI. Record readiness, last progress, and next stage; preserve an issue's continuation plan when borrowing its implementer.
- Give maintenance, diagnosis, and review a phase goal and exit condition. Hold heavy resource locks during execution and cleanup, release them promptly, and let independent issues proceed while diagnosis is reconsidered.

## Implement, Verify, and Review

When entering verification, review, or difficult diagnosis, read [delivery and rework control](references/delivery.md). Reuse already loaded rules and valid evidence.

1. Developers follow the host implementation process through observable public behavior, with short feedback and test-driven development where applicable. WIP commits and authorized Draft PRs preserve progress; they do not establish completion or authorize merging. Return repairs to the original Developer when available.
2. Seek early review for an actionable slice or consequential design. A formal review checks acceptance and related boundaries together. Each finding needs a location, falsifiable basis, and acceptance condition; batch compatible repairs.
3. Follow the host's reviewer policy. When it does not specify a count, use one non-author Reviewer with separate Standards and Spec passes, recording the reduced context independence. Prefer two independent reviewers for permissions, transactions or migrations, recovery or idempotency, complex budget algorithms, broad shared contracts, or milestone integration. Rebalance capacity first; record actual coverage and remaining risk if still limited. An explicit two-reviewer requirement remains binding.
4. Complete bounded simplification, then validate the stable candidate. Agreed CI may own final full-suite coverage; valid focused local evidence can be reused. After repairs or baseline changes, inspect the semantic delta and refresh affected verification and review coverage.
5. Before merging, verify the complete candidate, simplification, applicable independent review, and required CI on the final head. Read back the actual merge before updating the tracker. Pending integration remains unfinished.

## Consult and Diagnose

Consult the configured Advisor or an independent read-only agent for repeated rework without new evidence, architectural trade-offs, or conflicting review findings. Provide the minimum question, contracts, counterexample, and alternatives. Evaluate the recommendation and record the decision; the PM retains scope and judgment responsibility. If the channel is unavailable, record the limitation and continue decisions supported by existing evidence.

Accept a cause-equivalent reproduction when the public failure and observations distinguish the same defect. Match an exact number only when it distinguishes competing causes. Evidence sufficient for an instrumentation repair need not wait for exhaustive upstream investigation. At the diagnostic budget, reconsider the probe, consult, or report the remaining blocker; preserve acceptance assertions and thresholds.

## Record, Deliver, and Improve

- Keep the current checkpoint small: authorization and scope, issue and role mappings, revisions, resource owners, recent results, and next steps. Reference separate history and logs. On recovery, reconcile the tracker, Git, agents, and evidence, then resume the original implementer. Confirm writes have stopped before transferring work.
- At the start, use [development-timeline](../development-timeline/SKILL.md) when available to record dispatch, stage boundaries, waits, role changes, key verification, review rework, and integration. Reuse existing runner records. When installed alone, use a lightweight local journal and delivery report with the same facts; another skill is optional.
- At delivery, task end, pause, or handoff, update the report with completed and pending work, evidence, blockers, rework causes, and practical improvements. With the timeline helper, generate offline HTML. Report generation adds no merge gate; preserve unknown intervals and use existing evidence.
- Verify approved real user journeys and the usable application address. Review and survey simplification across the entire milestone baseline to integrated revision, including current consumers. The last issue's diff is insufficient. Optional cleanup remains a proposal.
- Report actual results and limitations, including partial delivery, pauses, and blockers. Completion follows the authorized delivery goal and tracker evidence, rather than local code or successful test counts. Redact credentials and follow existing authorization for publication and release.
