# Developer evaluation: facilitator record

**Prepared before data collection on 14 October 2026 IST. No sessions have been completed.** Use [the participant worksheet](developer-evaluation.md). The purpose is to collect evidence about developer usefulness and reviewability, the weakest part of the current assessment. This guide is not participant feedback.

## Recruitment and procedure

Invite three developers who did not build PayProof; aim for at least one with payments or refund-system experience. This is a small purposive sample, not representative market research. Record relevant experience and project relationship. Entrant/contributor feedback can improve the product but must be reported separately from outside observations. No invitations have been sent; sending requires the user's explicit instruction identifying recipients or an authorized channel.

Provide the participant worksheet and the reviewed source ZIP. The app works locally and the required tasks use simulator payments with no account access. Give the facilitator answer key only after tasks are finished. Participants may consult all shipped documentation; this evaluates a documented workflow, not unaided policy reasoning. Do not coach a participant to the desired answer. Record every hint and the point at which it occurred.

Record the exact source SHA-256 or Git commit before each session. Keep raw responses and supporting synthetic exports in `artifacts/developer-feedback/`, which is excluded from the source package and ignored by Git. Do not put participant responses under `docs/`, because that directory is packaged for release. Use pseudonyms and obtain separate permission for any quotation. Retain original responses and label later interpretations; do not rewrite a negative answer as a positive one.

## Predefined observations

For each task, record completion status, elapsed seconds, documentation consulted, facilitator assistance, the participant's explanation and a supporting evidence identifier. Start timing when its prompt is presented and stop at completion or its stated limit. Exclude installation time from task timings and report it separately. Retain failed installs, incomplete tasks and refusals; do not silently replace those participants. If a technical interruption requires a later session, preserve both attempts and identify them as the same participant.

| Task | Observable completion rule | What a partial result means |
| --- | --- | --- |
| Setup | Fresh installation and local app open within the 10-minute troubleshooting cap | Installation or launch barrier; include it in the cohort denominator |
| 1: release decision | Identifies the seeded cumulative-limit failure and explains why blanket refusal loses the legitimate refund, pointing to evidence within 4 minutes | Records what was understood; do not assign full completion for repeating a green/red label |
| 2: evidence trace | Correctly identifies Simulator as the payment source, distinguishes a proposed action from observed execution, exports evidence, identifies a provenance/scope limit, and returns to the same case after reload within 3 minutes | Missing any element is partial; record source confusion explicitly |
| 3: external decisions | Produces both local simulator evidence files with unchanged inputs, explains the before failure and after pass, and verifies the permitted refund remains within 6 minutes | If commands run but explanation/evidence is missing, retain the files and mark partial |

For the exact default pair, the facilitator key is: $15 already refunded against a $20 courtesy allowance; another $10 creates $5 excess and must escalate, while another $5 is permitted. The seeded external example ignores prior refunds, so its evaluation exits 1. The corrected example exits 0, rejects the excess, and retains the $5 refund. These are deterministic examples, not fresh AI calls. Refusal of everything is insufficient. Exported evidence can be replayed under a simulator but cannot authenticate the historical model/provider claims or certify production safety.

## Decision rules recorded before recruitment

Treat this first round as encouraging only if at least two of three outside developers complete all three tasks within their limits without facilitator hints, no participant mistakes simulator evidence for actual PayPal execution after inspecting it, and at least two describe a concrete relevant workflow plus a reason they would try the tool. Documentation use is allowed and reported. A missing or unattempted task is not a pass. These are product-development thresholds, not a validated usability scale or an automatic Impact score of 8.

If setup or a task fails, address the most consequential observed barrier and test it with new participants on a new version. Keep the earlier round and results; do not merge observations across versions into a cleaner success rate. A returning participant has learned the workflow and must be labeled as a repeat participant.

## Report template

Copy this into the private artifact directory and fill it only after collecting real responses:

```text
Round/version and source hash:
Dates:
Recruited / attempted / completed counts:
Outside developers / contributors / entrants:
Relevant experience and recruitment limitations:
Setup completed count / attempted count:
Task 1 completed count / attempted count; times; assistance:
Task 2 completed count / attempted count; times; assistance:
Task 3 completed count / attempted count; times; assistance:
All tasks completed without hints count / attempted count:
Any evidence-source confusion (include exact observations):
Concrete workflow fit count and supporting observations:
Negative feedback and incomplete attempts:
Permitted anonymized quotes with raw-response references:
Predefined thresholds met / unmet / incomplete and why:
Most consequential problem and next change:
Limitations and claims this evidence does not support:
```

Report counts and individual times for this small sample. Task time does not establish time saved: there is no randomized comparison with the participant's current tool. Do not translate synthetic policy excess into losses prevented, a participant's stated interest into adoption, or a successful task into production reliability. Rejudge the five criteria conservatively after inspecting the raw evidence. Until then, Impact stays **7/10** and the overall estimate stays **40.5/50**.
