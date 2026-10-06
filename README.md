# Agent Skills

Small engineering skills that work with [Matt Pocock's skills](https://github.com/mattpocock/skills). Matt handles requirements, specifications, implementation methods, review, PR descriptions, and retrospectives. This package adds delivery coordination, three independently usable methods, simplification, and evidence-based reporting.

Skill instructions and report interfaces use English. The [offline workflow walkthrough](docs/workflow.html) explains the first version in Chinese, with examples and interactive demonstrations. Download that HTML file and open it locally; it needs no server or CDN.

This is a local first version for review. It has not been pushed to GitHub or installed into the host project yet.

## Install

After this version is published, install Matt and this package separately:

```sh
npx skills@latest add mattpocock/skills
npx skills@latest add CaiZongyuan/skills
```

Choose the intended agent and project or user scope in the installer. For PM workflows, select all six skills below so the coordinator can use the methods when needed. They can also be installed individually for bounded tasks.

Run Matt's `setup-matt-pocock-skills` for a new project that needs tracker and documentation conventions. Reuse an existing project's setup and glossary location; installing newer skills does not authorize changing them. Keep Matt's installed files unchanged and put project-specific rules in the project's own instructions.

## Use One Delivery Coordinator

Use Matt to clarify the task and, when needed, produce a spec and tickets. Once the task is explicit:

```text
$pm-development Work the approved tickets within the existing scope.
Reuse valid evidence, consult the Advisor when risk or stalled diagnosis warrants it,
and report actual integration and remaining work.
```

The PM owns scheduling, risk decisions, evidence coverage, and delivery. Developers and reviewers use the appropriate methods; a skill does not require a new agent. A normal small task may use none of the three specialist methods.

Matt's `implement-spec` remains an alternative coordinator for a whole spec. Choose either it or PM Development to schedule that execution. Matt's `pr` presents verified evidence, while `retro` uses the existing timeline and receipts to suggest improvements to the agent's environment.

## Included Skills

| Skill | Job | Reach for it when |
| --- | --- | --- |
| [pm-development](skills/pm-development/SKILL.md) | Coordinate an explicit task through implementation, independent review, validation, and actual integration. | Multiple issues, a milestone, or long-running delivery needs an owner. |
| [change-impact](skills/change-impact/SKILL.md) | Trace real consumers and prove the important fact a change's safety depends on. | Shared APIs, types, dependencies, migrations, or ownership change. |
| [check-benchmark](skills/check-benchmark/SKILL.md) | Check whether a performance claim measures correct, comparable, real work. | Reporting a speedup, regression, or measured choice between options. |
| [verification-guide](skills/verification-guide/SKILL.md) | Reuse and prove a project's existing launch, drive, evidence, and cleanup instructions. | A new agent repeatedly has to rediscover how to verify the app. |
| [development-timeline](skills/development-timeline/SKILL.md) | Record stages and generate current status and offline delivery reports from shared inputs. | Delivery, rework, waits, a pause, or a retrospective needs evidence. |
| [reduce-complexity](skills/reduce-complexity/SKILL.md) | Simplify a bounded change, or survey an integrated epic for maintenance opportunities. | Behavior works and the change is approaching final validation and review. |

The methods can also be used directly:

```text
$change-impact Check this task's event-field change and its real consumers.
$check-benchmark Does this 200 ms to 120 ms report establish an improvement?
$verification-guide Reuse existing project docs and prove one representative verification path.
```

The PM delegates an applicable method to the existing Developer or Reviewer and reuses its result. It does not run all three for every issue, create another tracker, or repeat equivalent evidence.

## Advisor

The Advisor is an independent, read-only consultation role used at major decisions, repeated failures without new evidence, or conflicting review findings. The PM provides the narrow question, contract, alternatives, and original evidence, then evaluates the response. It is not a separate installed skill or a completion gate.

Use the host's available subagent capability and model configuration. A different model family is optional and requires actual provider support; this package does not install Cursor's Advisor plugin or configure external credentials. The [Advisor reference](skills/pm-development/references/advisor.md) owns the consultation protocol.

## Portable Tools

The helpers require Node.js 18 or later and no npm dependencies. CI observation also requires an authenticated `gh` CLI. They do not modify issues, trigger CI, or merge changes.

The [CI observer](skills/pm-development/references/ci-observer.md) reads an explicit repository and PR. It saves source/head/run/attempt observations and returns short notifications only when facts change. Observation failures stay distinct from the last known CI facts; it does not decide which checks are required or whether the task is complete.

The [report composer](skills/development-timeline/references/composition.md) reads the PM's declared scope and decisions, journals, and optional observer output. It projects one model into `current.md` and offline HTML. The source inputs remain authoritative and unchanged. CI success never sets the task's completion state.

Save run-specific receipts and outputs under the host project's task directory, such as `.scratch/<task>/`. Keep generic methods and scripts in this skill package. Product CI wiring and business runner changes belong in the product's own implementation work.

Run helper tests from this repository:

```sh
node --test skills/pm-development/tests/*.test.mjs skills/development-timeline/tests/*.test.mjs
```

## Method Sources

The specialist methods and consultation protocol draw on [pstack](https://github.com/cursor/plugins/tree/df581122cde17e6e27686b5a448bde23e4ad4318/pstack) and [Advisor](https://github.com/cursor/plugins/tree/df581122cde17e6e27686b5a448bde23e4ad4318/advisor). Their Cursor-specific routing, model names, and hooks are not copied into this package. Existing design exploration and two-axis review use Matt's methods rather than adding duplicate skills.

All skills follow the user's scope and the host's `AGENTS.md`, accepted decisions, verification policy, and actual available capabilities. They preserve independent review, required final-head CI where configured, actual integration checks, and resource ownership. Reports explain delivery; they do not add a merge gate.
