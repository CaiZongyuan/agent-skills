# Agent Skills

Standalone skills for simplifying software changes, coordinating development across issues or milestones, and recording delivery timelines.

Skill instructions and default report interfaces use English.

## Install

```sh
npx skills add CaiZongyuan/agent-skills
```

## Included Skills

- [reduce-complexity](skills/reduce-complexity/SKILL.md): simplify completed issue or pull request changes while preserving behavior, or survey an integrated epic for opportunities to reduce maintenance.
- [pm-development](skills/pm-development/SKILL.md): coordinate independent implementers, independent review, verification, integration, and milestone acceptance.
- [development-timeline](skills/development-timeline/SKILL.md): record stage changes and evidence, then generate an offline HTML report of delivery, waits, rework, and improvements.

All skills follow the host repository's `AGENTS.md`, specifications, accepted decisions, and the user's authorized scope. Their procedures are self-contained; they do not require another skill or a particular project structure. PM Development can use Development Timeline when both are installed, or the host's existing journal and report when installed alone.

Development Timeline's recording and rendering helpers require Node.js 18 or later and no npm dependencies. The generated HTML opens directly in a browser without a server or CDN. See its [data contract](skills/development-timeline/references/data-contract.md) for report and event formats.

Run the helper regression tests from this repository:

```sh
node --test skills/development-timeline/tests/*.test.mjs
```
