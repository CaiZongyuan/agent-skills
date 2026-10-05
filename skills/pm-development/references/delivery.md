# Delivery and Rework Control

Use these decision criteria within the host repository's workflow. The user's explicit scope, runtime constraints, and host rules take precedence. No separate implementation, testing, review, or diagnosis skill is required.

## Select Verification by Risk and Change

Before implementation, identify key invariants and relevant boundaries, such as precision, ties, budgets, or retention. Test-driven implementation can proceed one behavior at a time after this design check.

- During editing, use focused public behavior, type, and static checks. Run the complete gate on a stable candidate in the responsible environment, which may be CI.
- Use falsifiable acceptance assertions and verify that important checks distinguish correct behavior from the target defect. An existing TDD red/green can provide this evidence when it fails for the right reason. Add a counterexample when the oracle changes or a key risk lacks coverage.
- When a complete gate already includes an affected suite, cite its coverage rather than immediately repeating it.
- Judge evidence reuse by the complete revision, contracts, dependencies, environment, and actual coverage. Inspect semantic changes when the integration baseline advances. A changed commit identifier alone does not invalidate every check; unchanged files alone do not prove validity.
- Required final-head CI remains mandatory. Zero collected tests, skipped scenarios, broken locators, or compilation failures do not establish the target business behavior.
- Classify commands by actual resource use. Documentation or contract checks may invoke a compiler and need the heavy execution queue. Use existing commands rather than inventing unimplemented fast modes.

## Verify UI and Browser Behavior

Apply the approved viewport and journey scope. Desktop web is the default only when mobile has not been included. Preserve existing unrelated test responsibilities without creating new mobile delivery obligations.

Before reserving real execution resources, check discovery, actual identity, target state, component actions, and rendering prerequisites. Wait on a business or geometry predicate for dynamic UI rather than a fixed sleep or stale rectangle.

Cover new critical paths with the real business journey. Use focused scenarios for layout, copy, or selector changes. Reuse unaffected identity, backend, and documentation evidence according to their valid inputs.

Judge visibility by what a user can see and operate. A canvas, a visible DOM element, or a colored cropped screenshot alone cannot prove panels leave the content exposed. Record relevant screenshots and external geometry or hit testing. Give failed scenarios unique evidence paths and redact sensitive fields.

## Review and Repair

Review consequential design and specification risks while changes are cheap. Formal review pins the base and complete candidate, including new files and necessary consumers. Use a commit or explicit tree comparison that includes uncommitted work.

Follow the host review policy and any explicit reviewer count. Otherwise, one non-author may report Standards and Spec separately; two independent contexts are preferable for high-risk or milestone work when available. Reuse unchanged coverage and review roles. Record capacity limits, actual independence, and remaining risk.

After repairs, check related boundaries and refresh affected verification and review in a batch. Repeated rounds without new evidence or with the same class of defect warrant a short design check or Advisor consultation. A retry limit is a stopping condition, never an automatic pass.

Separate optional smells, formatting preferences, and large refactor proposals from located contract defects or actual risks. Optional cleanup does not block delivery by itself.

## Diagnose with Sufficient Evidence

Preserve the public entrypoint, original failing assertion, and observations that distinguish causes. Exact numeric matching is needed only when it separates competing causes.

Each retry should answer an unresolved question and change a justified condition. Repeated green runs with identical inputs cannot establish a correct performance oracle. Preserve budgets, thresholds, and data semantics; diagnostic guards must allow the original acceptance assertion to be observed.

When evidence is sufficient for a bounded repair, record why remaining probes add no useful distinction. At the diagnostic budget, summarize knowns and unknowns and reconsider or consult. Record missing permissions or external state as the relevant blocker. Release compute resources and continue independent ready work.

## Keep Execution and Records Bounded

A finite execution phase can include target red, minimal green, related verification, and cleanup. Hold resource locks only during actual execution and cleanup. Allow enough time for startup, execution, and cleanup before creating resources.

Use the host's isolation fixtures and ownership ledger. Reconcile global resources at phase start, abnormal recovery, and completion; reconcile owned resources and consumers for normal retries. Remove only resources whose ownership and stopped consumers are verified. Preserve persistent and shared development services and provide interruption cleanup according to the host policy.

Progress reports retain commands, exits, revisions, environment, actual coverage, review version, and evidence paths. The PM acts on changes, failures, and real decisions rather than copying complete logs. Record stages in a lightweight journal and keep the current checkpoint short. Unknown intervals remain unknown instead of being attributed to waiting or CPU time.
