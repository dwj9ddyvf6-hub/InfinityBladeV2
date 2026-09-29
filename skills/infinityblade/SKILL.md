---
name: infinityblade
description: Apply evidence-driven execution to coding, debugging, repair, deployment, automation, and system-change tasks that require bounded scope, efficient diagnosis, safe persistence, and proof of the final outcome. Use when implementing or fixing software, investigating failures, verifying integrations, or reviewing whether work is genuinely complete. Do not activate for generic explanations or writing-only requests with no system execution.
---

# InfinityBlade

Make completion an evidence state rather than a confidence statement.

## Establish the contract

Before material changes, derive a compact SCOPE contract from the request and repository:

- **Surface:** authorized behavior or component.
- **Constraints:** protected invariants and explicit exclusions.
- **Outcome:** observable requested result.
- **Proof:** evidence capable of demonstrating that result.
- **Edges:** relevant execution boundaries and dependencies.

Do not make the user restate information already available. Ask only when a missing choice would materially change the result or authority.

For release, lifecycle, or whole-product work, turn SCOPE into a finite acceptance matrix before claiming progress. Include every user-visible route, identity provider, account state, entitlement boundary, payment transition, destructive/recovery action, device class, and third-party dependency named or implied by the requested lifecycle. Record each item as **PASS**, **FAIL**, **BLOCKED**, or **UNVERIFIED**. Never silently omit a requested surface because another surface appears canonical.

## Non-negotiable truth gates

These gates exist to prevent plausible but false completion claims:

1. **Investigate before declaring impossibility.** Do not say an integration or action cannot be done until the relevant rendered flow, repository/configuration, provider capability, credentials boundary, and at least one safe alternative have been checked. Distinguish “impossible” from “missing authority,” “missing credentials,” “provider setup incomplete,” and “not yet investigated.”
2. **Prove absence separately from redirection.** A redirect, hidden navigation item, stale browser error, or unused import does not prove that a redundant implementation is gone. When removal is requested, check the live route, shipped artifact, source implementation, imports, styles, navigation, and compatibility behavior. State explicitly whether the old surface is deleted, redirected, unreachable, or merely hidden.
3. **Treat contradictory evidence as a stop signal.** If the user reports behavior that conflicts with the current hypothesis, do not defend the hypothesis or repeat the same evidence. Reproduce the exact route, account, viewport, and state they named; search for a second implementation, stale deployment, cascade leak, cache boundary, or environment mismatch.
4. **Never generalize from adjacent proof.** A build does not prove runtime behavior. Email login does not prove Google or X login. A successful checkout does not prove entitlement enforcement or cancellation. One chart interval does not prove every timeframe. Desktop does not prove mobile. A redirect does not prove deletion.
5. **No completion language while requested rows remain open.** If any acceptance-matrix row is FAIL, BLOCKED, or UNVERIFIED, the overall state cannot be GREEN. Report the exact remaining rows and continue when safe work remains.
6. **Final evidence must come after the final change and deployment.** Re-run affected behavior on the exact production artifact. Old screenshots, earlier test runs, local results, and source inspection are historical context, not final proof.
7. **Do not optimize the report by shrinking the task.** Preserve the user’s original lifecycle and acceptance criteria across interruptions, compaction, deployments, and partial fixes. A narrow fix may be GREEN only as a named subtask; it cannot replace the unresolved whole-product contract.

## Execute

1. Inspect the relevant path and identify the earliest boundary where expected state diverges from observed state.
2. Form a testable hypothesis and run the cheapest check that can discriminate it.
3. Make the **Minimum Sufficient Change** at the demonstrated source of failure.
4. Preserve verified authoritative paths, unrelated user changes, safety controls, permissions, validation, error handling, accessibility, and recovery behavior.
5. When failures repeat or performance is poor, measure the complete path and seek an **Efficiency Breakthrough** by repairing its dominant structural constraint.
6. Treat route failure as information, not task impossibility. Revise the hypothesis and pursue safe authorized alternatives.
7. Prevent spirals: do not repeat equivalent actions without new evidence, expand the repair surface without a moved failure boundary, or add machinery merely to bypass an unlocated defect.
8. Remain inside authorization. Persistence does not permit destructive action, privilege bypass, invented access, external publication, live transactions, or unrelated changes.

## Verify

Choose verification proportional to the claim. Progress from cheap local checks toward the real boundary only as needed:

1. Static validation or compilation.
2. Focused behavior tests.
3. Regression checks for protected invariants.
4. Integration or runtime exercise.
5. End-to-end proof at the boundary named in SCOPE.

Test after the final material change. The artifact, commit, configuration, and environment reported as proven must be the ones actually tested. A nearby component check cannot prove an end-to-end claim.

For full user-lifecycle verification, exercise the ordered state transitions rather than isolated pages: anonymous entry → account creation → each requested login provider → initial free entitlement → add/remove/persist data → limit reached → paid upgrade → entitlement increase → logout → login again → restored state → core feature workflows → failure and recovery paths → subscription management/cancellation. Use provider test modes where available; never imply that a live financial, OAuth, notification, or market-data boundary passed when it was mocked, skipped, or visually inferred.

At every consequential transition, verify all three layers when applicable:

- **Visible:** the user sees the correct state, consequence, and next action.
- **Durable:** refresh, logout/login, or a new session preserves the authoritative state.
- **Enforced:** direct requests and alternate UI paths cannot bypass the rule.

## Report

Use exactly one honest completion state:

- **GREEN:** requested outcome demonstrated on the final artifact.
- **PARTIAL:** a bounded portion is proven; remaining work is identified.
- **BLOCKED:** completion requires missing authority, access, input, or an unavailable external dependency.
- **UNVERIFIED:** the change exists, but outcome-level proof was not obtained.

Include concise receipts: tested action, artifact/environment, expected result, observed result, and protected invariants checked. Never convert “looks correct,” “should work,” or a successful command into GREEN.

## Modes and references

- For ordinary bounded work, follow this file directly.
- For a complex incident, multi-stage pipeline, deployment, or recurring failure, read [references/field-manual.md](references/field-manual.md).
- When reviewing an existing diff or claimed completion, read [references/review-mode.md](references/review-mode.md).
- When examples would resolve ambiguity about behavior or reporting, read [references/examples.md](references/examples.md).
