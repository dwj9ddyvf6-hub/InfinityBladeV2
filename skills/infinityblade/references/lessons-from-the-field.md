# Lessons from the field: turning repeated failures into doctrine

This guide supplements the core InfinityBlade skill. It distills recurring failure patterns from real agent work across software changes, research pipelines, generated artifacts, browser workflows, publishing, and backups. Examples are generalized: account details, proprietary data, private conversations, credentials, and machine-specific session state do not belong in a shareable playbook.

The central lesson is simple: **when a failure repeats, improve the system’s memory and proof—not merely the next prompt.** Convert each incident into a precise invariant, a discriminating check, and a durable place where the next agent will find it.

## Failure patterns and durable countermeasures

### 1. A plausible artifact can still be the wrong artifact

**Failure pattern:** A chart, build, document, or model output looks reasonable, but came from a different renderer, branch, configuration, data cutoff, or release than the workflow requires. Names such as latest, final, and corrected do not establish lineage.

**Countermeasure:** Record the authoritative repository/ref, commit or release, entry point, configuration, input identity, and expected output form before producing anything. Hash critical inputs and outputs when byte identity matters. Compare at least one known-good example from the same path. Keep research/intermediate artifacts distinct from user-facing deliverables and prove the final artifact came through the intended path.

### 2. Similar labels can hide different semantics

**Failure pattern:** An agent confuses signals, timeframes, environments, accounts, or similarly named entities. A result can be numerically valid yet answer a different question.

**Countermeasure:** Resolve names to an authoritative source definition. Carry identity, date, unit, timeframe, and version beside every row. Test known positive and negative cases; assert coverage and uniqueness; do not substitute a nearby name or infer identity from visual proximity. Keep labels derived from the same versioned source as the behavior they describe.

### 3. A success message is not durable state

**Failure pattern:** A command exits successfully, a toast appears, a queue count changes, or an editor briefly looks correct, while the destination has not saved the intended object—or has saved only part of it.

**Countermeasure:** Define the success boundary before acting. After each consequential mutation, wait for the interface or service to settle, read back the exact durable row, refresh when appropriate, and reconcile source against destination. Distinguish draft, queued, published, delivered, and remotely synchronized states. Historical screenshots and earlier receipts prove only their timestamped state.

### 4. Rich UI objects can be damaged by text-only edits

**Failure pattern:** Replacing visible text in a media-bearing card, document, or form leaves stale blocks, duplicates, or detached attachments even though the editor looks plausible.

**Countermeasure:** Use the product’s supported semantic editing path and preserve the structured object. Do not use raw contenteditable replacement, select-all, or other text-only shortcuts on rich objects unless the product guarantees attachment preservation. If a safe edit path is unavailable, stop and rebuild from the authoritative structured source. Re-read the saved object and its media after every edit.

### 5. Batch work magnifies small identity errors

**Failure pattern:** Missing rows, duplicates, wrong pairings, stale text, or changes to unrelated items accumulate because the agent relies on nearby names, a queue preview, or an assumed starting state.

**Countermeasure:** Freeze a manifest before mutation. Give each target a stable identity and idempotency key; include the exact input and output references and the expected final state. Reconcile existing records first. Preserve non-targets. Stop the batch on the first failed row, record expected versus observed state, repair one item at a time, and rerun the complete manifest gate. Never hide a failed published item by deleting or reposting it without specific authorization.

### 6. Repeated user corrections are evidence, not friction

**Failure pattern:** The agent repeats the same explanation or action after the user has identified a concrete contradiction. The work grows noisier while the original defect remains.

**Countermeasure:** Treat a specific correction as a falsification test. State what prior assumption it disproves, reproduce the exact route, identity, artifact, and state the user named, and inspect for a second implementation, stale cache, wrong version, or environment mismatch. Change the hypothesis before acting again. Do not ask for a decision the user has already made; ask only when a material choice or authority is genuinely missing.

### 7. Tool failure and security boundaries are different things

**Failure pattern:** A UI automation route fails and the agent concludes the task is impossible—or tries an unsupported browser, hidden control, broader desktop takeover, or security workaround.

**Countermeasure:** Classify the failure: implementation, wrong hypothesis, transport, provider capability, missing dependency, account state, or permission boundary. Use the requested app and narrowest supported surface. Check tool documentation and exact live state before switching routes. Treat the installed tool, its cached package, its source manifest, and effective configuration as potentially different states; compare them and test the original user-facing route, because a config parser passing does not prove the requested workflow resumes. When a browser permission or authentication step belongs to the user, explain the precise manual step and stop at that boundary; never bypass the control or handle one-time authentication codes on the user’s behalf.

### 8. Generated analysis and prose can drift apart

**Failure pattern:** The calculation is correct but the explanation misstates direction, thresholds, units, geometry, horizon, or source. Templates may omit a meaningful condition or produce repetitive filler. Current-event claims may be invented to make every item look complete.

**Countermeasure:** Treat each sentence as a claim with a source. Validate narrative fields independently against the canonical measurements and definitions, including change-versus-level semantics and configured thresholds. Check coverage, grammar, uniqueness, and identity across the full batch. For factual updates, use verifiable sources; include only relevant confirmed developments, and omit the line rather than inventing or padding when nothing qualifies. Variation in wording must never weaken factual consistency.

### 9. A local copy is not proof of cloud backup

**Failure pattern:** Files exist in a sync folder but uploads remain pending, locked files were skipped, the cloud listing is incomplete, or a “complete” status file is stale. Removing the local source too early can turn a partial copy into data loss.

**Countermeasure:** Measure free-space headroom and active jobs before a large copy. Use resumable incremental passes and bounded status reporting. Preserve source data while transfer is pending. Verify the remote destination independently with file counts, sizes, checksums, or the provider’s authoritative sync state; check locked-file exceptions explicitly. Only reclaim or offload the source after the remote copy is confirmed.

### 10. Knowledge in chat does not reliably survive a handoff

**Failure pattern:** A later run chooses the wrong version, repeats browser setup failures, or cannot reproduce the work because the procedure lived only in conversation or local machine state.

**Countermeasure:** Put the durable operating contract beside the project: version-pinned runbook, exact entry points, manifests, hashes where important, required permissions, safe recovery actions, known failure modes, verification gates, and a dated receipt. Test the handoff from a fresh checkout or machine when portability is claimed. Keep secrets, cookies, browser profiles, authentication state, and unnecessary raw conversation dumps out of shareable repositories; archive only what is needed and safe to preserve.

## The incident-to-doctrine loop

Use this loop whenever the same class of failure returns, or whenever a workflow spans multiple tools or durable states:

1. **Capture the contract:** requested outcome, authorized scope, protected state, identity, version, environment, and the observable success boundary.
2. **Record the contradiction:** exact expected state, exact observed state, and the artifact or transition where they first diverged.
3. **Find the first failed boundary:** trace upstream from the symptom; do not patch a downstream display if the source or transport is wrong.
4. **Choose a discriminating check:** each attempt must test a hypothesis and reduce uncertainty. Do not repeat an equivalent action without new evidence.
5. **Repair the invariant:** make the smallest structural change that prevents the failure class, not just the one example.
6. **Add a regression guard:** a test, manifest assertion, checksum, UI read-back, or operational gate that would have caught the original failure.
7. **Replay the original path:** after the last change, rerun the same route, identity, input shape, and environment at the boundary the claim names.
8. **Persist the lesson:** update the shared runbook or skill, preserve a concise receipt, and carry unresolved states forward without upgrading them to PASS.

If no action can be named that will either solve the problem or distinguish competing explanations, pause and re-scope before touching more state.

## Compact incident receipt

~~~text
Outcome and authorized scope:
Protected state:
Authoritative inputs / version / hashes:
Target identities and idempotency key (if batched):
Expected state:
Observed state:
First failed boundary:
Hypothesis and discriminating check:
Root cause:
Minimum repair and regression guard:
Final artifact / environment / commit:
Post-change proof and preserved invariants:
Status: PASS | FAIL | REPAIRED | BLOCKED | NOT TESTED
Remaining uncertainty:
Portable lesson added at:
~~~

## One-line rule

**Do not trust resemblance, intent, or success copy: bind the right identity to the right source, change state through a supported route, read it back at the real boundary, and save the proof where the next agent can use it.**
