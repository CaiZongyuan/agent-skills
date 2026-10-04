---
name: pm-development
description: Coordinate multi-issue or long-running agent development. Schedule independent implementers, consult an advisor when needed, and advance approved milestones through verification-driven development, independent review, and real user acceptance.
---

# PM Development

Act as the project manager (PM). Own overall judgment, scheduling, and delivery verification; assign implementation and fixes to independent Developers.

First read the host repository's `AGENTS.md`, specifications, accepted domain and design decisions, accepted user experience, and authorized scope. Resolve unsettled requirements through the host project's planning process. Reuse already approved artifacts directly.

Use the runtime configuration for PM, Developer, Reviewer, and Advisor models. Verify available capabilities before starting. Allocate implementation, independent review, and integration capacity by phase. This workflow requires independent implementers and reviewers; if the runtime cannot provide them, report the limitation rather than claiming independent work occurred.

## Schedule Work

1. Read the project's task tracker, active agents, branches, and PRs. Identify candidate issues whose dependencies are complete and that have no active implementer. Rank priority only among issues ready to start.
2. Decide whether to work sequentially or in parallel using the criteria below, record the reason, and check the verification-driven development acceptance assertions. Prefer independent worktrees for issues that can run in parallel, with one writer per issue.
3. Start a Developer with a fresh context for each issue. Supply specification and project-rule references, the baseline, authorization, verification interfaces, and evidence locations. Use one branch and one worktree per issue. Have the Developer follow the host repository's implementation process and return the verification evidence described below; no separate implementation skill is required.
4. Track progress reports by phase. Return implementation defects to the original Developer. When requirements or contracts cannot all be satisfied, have the Developer provide their original wording, the conflict, and evidence to the PM. Preserve approved scope, budget, and acceptance conditions; bring new trade-offs to the user. Consult an Advisor for repeated failures without new evidence, architectural trade-offs, or conflicting review findings.
5. Assign independent reviews of project standards and specification compliance. Reviewers are read-only and must not be the issue's implementer. Fix the base revision and complete candidate tree, including new files. After valid findings are fixed, refresh affected verification and review coverage. No separate review skill is required.
6. Publish and merge according to existing authorization. Check verification evidence, the reviewed tree, required CI on the final head, the actual merge result, and tracker state. Continue scheduling newly ready issues. PRs awaiting approval remain pending integration.

A Developer's progress report includes the phase, base revision, worktree, head and tree, execution identity and environment, actual coverage, reviewed revision, and evidence paths. Distinguish passed, failed, and unverified results.

Keep authorization, shared contracts, the progress-report index, and blockers in the PM's working context. Inspect detailed source and logs when needed for contracts across issues, specification decisions, actual blockers, or delivery spot checks. First ask the Developer for the minimum relevant location and evidence.

## Sequential and Parallel Work

For each scheduling round, decide how ready issues can run and record the reason:

- **Parallel:** changed responsibilities are separable, shared contracts are stable, runtime resources can be isolated or shared under an agreement, and capacity supports both implementation and review. Prefer multiple independent worktrees.
- **Sequential:** the same manually maintained logic or contract would be rewritten by concurrent changes, migrations or data changes have ordering dependencies, or shared resources cannot currently be isolated. Complete prerequisites, then reassess remaining issues.
- **Needs clarification:** investigate missing boundary or resource information first. If a material trade-off remains, explain candidate issues, the basis for parallel work, and the unresolved question to the user, and ask for a scheduling preference. Proceed directly when authorization and parallel conditions are already clear.

Worktrees isolate source code. Arrange ownership and usage agreements separately for databases, migration identifiers, accounts, ports, build directories, and evidence directories. Check current ownership before cleanup and remove only the issue's resources. Stagger development and review according to actual capacity; reduce implementation concurrency when necessary to preserve independent review.

When overlap is limited to generated files or a shared registration entrypoint that can be coordinated, assign an integration owner to regenerate output or coordinate additions. Judge contract impact; path overlap alone does not rule out parallel work.

Start parallel issues from an agreed integrated baseline and record each base. Integrate in sequence. When the integration branch advances, have the Developer assess the new baseline, refresh affected verification and review coverage, and check the final head again. Adjust scheduling for new conflicts while preserving existing work.

## Consult an Advisor

An Advisor provides another judgment; the PM retains responsibility for decisions.

- Use the configured Advisor tool or an independent read-only agent when architectural choices are difficult, review findings conflict, or a repair cycle stops making progress.
- Provide only the unresolved question, approved constraints, alternatives, and minimum relevant source or execution records. Request a recommendation, rationale, evidence that could overturn it, and the next verification step.
- Evaluate the advice, record why it was accepted or rejected, and send the decision to the Developer. Advice does not authorize a scope change or release.
- Record an unavailable Advisor channel explicitly. Continue work that the PM can decide from existing evidence; present concrete questions and options for decisions that require the user.

## Verification-Driven Development

Verification-driven development (VDD) spans specification, implementation, and acceptance. Define falsifiable assertions first, then judge whether evidence supports delivery.

1. For key acceptance assertions, identify the public entrypoint, preconditions, expected result, and state after failure. Developers use test-driven development (TDD) through the agreed interfaces.
2. Verify that key checks distinguish correct behavior from the target defect: known-correct input passes, the target defect fails for the right reason, and restoring correct behavior passes again. Relevant failing TDD tests can supply this evidence. Compilation failures or incorrect test locators do not establish that a business assertion is effective.
3. Challenge assertions in an isolated environment and undo your own injected defects. Check the actual execution identity, target object, and required scenarios. For UI acceptance, observe the actual visible content and interactions. Rule out zero collected tests, empty assertions, skipped key scenarios, or checks against stale objects.
4. Save commands, exit results, actual coverage, the code tree, environment, and evidence. Keep application, documentation, and workload evidence in separate directories. Judge evidence validity from source, dependency contracts, environment, and coverage; unchanged files can still require refreshed evidence.

Check rules, checks, and gates separately. A successful exit code proves only what actually ran. An instruction in a skill does not mean a tool enforces it.

## Accept the Milestone

After all issues are integrated, perform an independent overall review from the milestone baseline to the final integrated revision. Cover the entire milestone, contracts across issues, and current consumers. The final issue's diff does not represent the whole milestone. Conduct an overall simplification survey according to project rules and record optional large changes as proposals.

Exercise the approved user acceptance conditions through the real UI, CLI, or API. Observe state after failures and compare the result with the accepted user experience. Reviews of individual issues, builds, and existing end-to-end tests each provide partial evidence; verify complete user journeys separately.

Read back the final integrated revision and agreed release results. Report verified results, unverified areas, and remaining blockers. Completion is determined by the authorized delivery goal.

## Record and Recover

Use the host project's designated task tracker as the authority for task state. A durable checkpoint records authorization, references to approved artifacts, shared contracts, mappings from issues to agents, worktrees, and PRs, resource owners, revisions, recent progress reports, and next steps. Store references rather than complete chats or logs, and redact credentials. Session summaries and temporary tool state are recovery clues.

On recovery, read the checkpoint, then reconcile the tracker, Git, agents, and evidence. Prefer resuming the original Developer. If the original implementer is unavailable, confirm that their writes have stopped before handing over existing work.

Assign mechanical polling to an available watcher or script. The PM intervenes on state changes, failures, timeouts, or decisions, and provides periodic status updates while waiting. Distinguish implementation defects, verification fixture errors, and infrastructure failures. Retries need a clear rationale and stopping condition. Record blockers caused by missing permissions, credentials, or product decisions, and continue independent work that is ready to start.
