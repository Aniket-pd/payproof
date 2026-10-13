# PayProof evaluation — 13 October 2026

PayProof now has a clearer, reproducible opening demonstration and a directly observable live-AI path. Its strongest moment is the side-by-side proof that both over-refunding and blanket refusal fail, while a valid refund remains usable. The current implementation is a polished local prototype with a substantial verifier. **First-place readiness is not yet established:** actual PayPal Sandbox evidence and external user validation remain missing.

This assessment uses the [five equally weighted official criteria](https://paypalaihackathon.devpost.com/rules) on an internal ten-point scale. It was made by the implementing agent, not an independent panel; the numbers are estimates, not official scores or a winning probability. The [research report](2026-10-13-research.md) documents all 13 current judges, sourced professional work, explicitly inferred design implications, and related PayPal winners. No previous edition of this exact event was verified.

## Goal and milestones

The ultimate target is a submission capable of competing for first place, operationalized as at least 8/10 on every criterion plus actual PayPal/AI evidence and complete public delivery. Six defined iterations are complete so far; iteration 7's tested public-source candidate is prepared and awaits publication approval. The ongoing goal remains active, and the broader readiness target remains unmet.

| Milestone | Evidence and status |
| --- | --- |
| Official research and baseline | Complete: rules, current roster, relevant primary-source work and related winners; inspected source and rendered experience before editing; 163 baseline tests passed. |
| Innovation made visible | Complete: three approaches evaluated on identical inputs, including a refusal negative control that misses the permitted refund. |
| Functionality and first impression | Complete locally: one action opens saved evidence above the desktop fold; direct case/JSON links, stable URL, mobile layout, and preserved policy/library/approvals. Human comprehension within 30 seconds has not been measured. |
| Observable AI | Complete locally: the two-case call passed 2/2; a fixed 20-case challenge produced 18 passes, no failures and two deliberately inconclusive payment cases, with recorded model/thread metadata and complete offline replay. Simulator payments only. |
| Reliability | Complete for these changes: durable request IDs, no duplicate inference for the same ID, pending/completed/failed/interrupted recovery, no fabricated fallback, invalid decisions making no refund attempt. Browser reload tested through success and injected failure. Interrupted Sandbox reports and request IDs survive a forced process stop with mocked providers. |
| Portable technical review | Complete: bundled synthetic AI export, full import validation, provenance-preserving replay, one-command reproduction, altered-input rejection, and offline execution regression. |
| Presentation preparation | Complete locally: an editable, narrated 2:38 MP4 with timed captions, actual app captures, recorded AI evidence and disclosed integration limits. Full decoding and browser playback passed. Public video and repository remain unpublished. |
| Public-source preparation | Complete locally: an isolated 169-file candidate with pinned, read-only CI and both offline evidence commands, verified from a clean installation. A reproduced ZIP launcher-permission defect is repaired by installation and covered by regression. Publication approval, remote CI and public access checks remain pending. |
| PayPal proof | Unmet: adapter and mocked checks exist, but a real Sandbox order→approval→capture→refund→readback export has not been observed. |
| Impact validation | Unmet: no external developer study, adoption, measured time savings or loss prevention. |

## Before and after

| Criterion | Before /10 | After /10 | Evidence-based assessment |
| --- | ---: | ---: | --- |
| Technological Implementation | 7.5 | 7.5 | Stronger AI recovery and portable verification; actual PayPal execution still caps confidence. |
| Design | 8.5 | 9.0 | The key result is immediate, the comparison is readable, and mobile errors recover with focus. |
| Potential Impact | 7.0 | 7.0 | A credible developer problem and practical artifact; benefits remain unmeasured outside this project. |
| Innovation/Idea | 8.0 | 8.0 | Independent policy/payment checking while preserving useful refunds is differentiated; scope remains narrow. |
| Presentation | 7.0 | 8.5 | Compact three-control story, recorded AI evidence and a verified 2:38 rehearsal with editable source and captions. Final actual-Sandbox segment and public video remain missing. |
| **Total** | **38.0/50** | **40.0/50** | Improvement is concentrated in demonstrability and usability; missing evidence is not scored as complete. |

Iteration totals were 39.0, 39.5, 39.5, 39.5, 39.5 and 40.0. Broader AI coverage, reproducibility and interrupted-execution recovery strengthen the evidence without closing the PayPal and impact gaps. The internal ≥8-everywhere threshold remains unmet in Implementation and Impact. [Detailed goals, acceptance criteria and measurements](2026-10-13-progress.md).

## What was observed

With a $20 cumulative courtesy limit, $15 already refunded, and a $100 purchase:

| Evaluated approach | Passed | Legitimate passed | Synthetic policy excess |
| --- | --- | --- | --- |
| Seeded per-request check | 1/2 | 1/1 | $5 |
| Blanket refusal | 1/2 | 0/1 | $0 |
| Corrected reference | 2/2 | 1/1 | $0 |
| Genuine recorded Codex decisions | 2/2 | 1/1 | $0 |

The Codex run is `df7e6c3f-a89a-4a51-b21a-166f0ed150ea`, using CLI/SDK 0.162.0 and its default model (exact revision unknown). This small curated pair demonstrates the workflow; it does not establish model reliability or money saved. The shipped artifact's historical model claims remain unauthenticated on another machine; replay independently checks supplied decisions against simulated state.

`npm run check` passes **182 tests**, TypeScript and a production build. `npm run judge:verify` reproduces the table without a server or account. A regression runs it with network and subprocess access blocked; another alters the saved message and confirms rejection. Existing HTTP checks cover loopback/same-origin controls, input isolation and state preservation. Zero known runtime dependency vulnerabilities were reported, without a claim of full security assurance.

At iteration 3, the 102-file source ZIP passed a fresh `npm ci`, complete check and judge reproduction in a separate directory with no saved workspace state. Final documentation-only notes were repackaged after that check, with executable sources compared byte-for-byte to the tested copy. Deliverable: `artifacts/payproof-source.zip`; reproducible logs and inventory: `artifacts/improvement-2026-10-13/`.

At 1280×720 the comparison banner and three cards fit the initial view; at 390×844 the result ends around y536 with no horizontal overflow. A real model request survived reload. An isolated injected model failure also survived reload, focused its visible mobile alert and preserved the prior comparison. Screenshots and logs: `artifacts/improvement-2026-10-13/`. See [verification](../verification.md) for exact scope.

## Judge's remaining objections, in priority order

1. **PayPal is required and central, but actual account execution is unverified.** Complete one fresh approved fixture through capture, refund and independent readback; retain provider evidence and demonstrate the distinction between merchant policy and provider acceptance. This is the highest-impact next milestone.
2. **Who has used it, and what improved?** Have at least three developers connect a decision component using the guide. Measure setup time, time to an interpretable failure and whether the replay helps reproduce a fix. Report the observations and failures honestly; three users would be exploratory evidence, not market validation.
3. **Can judges access the complete submission?** Publish the licensed source, provide free permissible access and setup for optional live AI, record the working <3-minute video, and verify links signed out. A local source ZIP and verified rehearsal prepare this step but do not fulfill it.
4. **How far do the guarantees extend?** The policy is USD courtesy refunds, financial observations cover controlled fixtures and known refund IDs, and completion-language checks are bounded. PayProof owns test execution/retries and does not inspect arbitrary agents' internal tool use. Keep these limits visible.

The memorable claim should remain concrete: **catch the tested over-refund, reject blanket refusal as a fix, preserve the permitted refund, and let a reviewer inspect and reproduce the evidence.** Further cosmetic features currently have less value than closing the PayPal and user-evidence gaps.

## Ongoing goal checkpoint after iteration 4

The user resumed the continuous goal after the three-iteration checkpoint above. Interrupted Sandbox execution now retains a stable report, request identities, responses and completed cases. A forced process stop with a mocked provider recovered the same inconclusive case and produced zero provider calls after restart while browsing. Full validation: **178 tests**, TypeScript and production build pass. See [the progress log](2026-10-13-progress.md) for scope and artifacts. Scores remain **39.5/50** because actual PayPal execution, external user validation, and public delivery remain unverified. This is a checkpoint in an active goal, not completion of the ultimate target.

## Ongoing goal checkpoint after iteration 5

The [fixed 20-case challenge](../ai-challenge.md) was defined before inference, sent without evaluator labels, and evaluated once through Codex. It returned **18 pass / 0 fail / 2 inconclusive**, matching the corrected control; **10/12** legitimate cases passed. The two payment-evidence faults stay inconclusive. All 20 decisions, messages, checks and events are retained, bundled and replayed offline. The exact default-model revision is unknown, and one synthetic batch does not establish a general reliability rate. Full validation: **181 tests**, TypeScript and production build pass. Scores remain **39.5/50** and the goal remains active.

## Ongoing goal checkpoint after iteration 6

The local rehearsal is complete: **157.973 seconds, 1920×1080, 30 fps, H.264/AAC**, with generated stock narration and 73 caption pages. All frames decode and browser playback succeeds. Eight scene timelines, actual app captures, source audio, captions and attribution are packaged. The video explicitly distinguishes teaching controls, recorded AI, simulated payments, a mocked crash-recovery test and the unverified actual PayPal flow. The presentation estimate increases to **8.5**, giving **40.0/50** overall; this is still an internal estimate by the implementing agent.

A fresh 166-file source extraction passed installation, all 181 application tests, TypeScript, build, the two-case judge command and the 20-case offline challenge. Presentation installation, lint and caption validation also passed. Deliverables: `artifacts/payproof-demo-2026-10-13.mp4`, companion SRT, `artifacts/payproof-source.zip`, and [editable video source](../../presentation/README.md). See `artifacts/improvement-2026-10-13/video-verification.json` for media checks. The goal remains active. Actual Sandbox account access is the immediate dependency; external developer observations and public delivery remain required.

## Ongoing goal checkpoint during iteration 7

The source archive now includes the [verification workflow](../../.github/workflows/verify.yml) and a fresh-install launcher repair, bringing it to 169 files. The extracted candidate passed a fresh install, all 182 tests, build, both offline reports, packaging, and the presentation checks. Final inspection caught a real issue missed by offline evaluation: ZIP extraction discarded the executable permission required by the Codex SDK. Installation now restores it, a regression reproduces both failure and recovery, and the candidate records the executable Git file mode. No new inference was needed for this process-launch check.

An isolated local repository is prepared for `Aniket-pd/payproof`; publication requires approval. Neither remote CI nor public access has been observed yet. This closes local release preparation without changing the **40.0/50** estimate or the active goal's outstanding requirements.
