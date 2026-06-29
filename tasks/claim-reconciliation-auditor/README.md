# terminal-bench/claim-reconciliation-auditor
# Claim Reconciliation Auditor

Original Terminal-Bench 3 task for healthcare-style claim reconciliation using CSV and JSONL inputs.

## Validation Results

Static checks:

* `check-task-fields.sh`: PASS
* `check-instruction-suffix.sh`: PASS
* `check-canary.sh`: PASS

Oracle validation:

* Command: `uv run harbor run -p .\tasks --include-task-name claim-reconciliation-auditor --agent oracle --yes`
* Result: PASS
* Reward: 1.0
* Exceptions: 0

NOP validation:

* Command: `uv run harbor run -p .\tasks --include-task-name claim-reconciliation-auditor --agent nop --yes`
* Result: PASS
* Reward: 0.0
* Exceptions: 0

Codex standard trials:

* Trial 1: reward 0.0, exceptions 0
* Trial 2: reward 0.0, exceptions 0
* Trial 3: reward 0.0, exceptions 0

Claude Code trials:

* Not completed due to Claude Code authentication/subscription/API setup limitation.

Adversarial `/cheat` trials:

* Not completed before submission.

## Failure Analysis

Codex failed all three standard trials with reward 0.0. The task appears difficult because the agent must correctly combine duplicate detection, temporal coverage status, authorization windows, manual correction overrides, deterministic sorting, exact schema requirements, and checksum generation. Partial solutions that classify some claims correctly still fail because the verifier checks exact record contents, summary counts, evidence strings, sorted order, and checksum consistency.
