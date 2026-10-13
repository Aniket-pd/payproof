# Final independent review — 10 October 2026

**The latest extension ended after seven additional review passes (8–14), including four rounds of implemented fixes.** Two consecutive independent reviews (13 and 14) found no significant actionable local weaknesses, and both repeated the core demo successfully. This meets the user's early-stop rule; the remaining three passes under the ten-pass cap were not performed. Eleven implementation rounds were completed across the full engagement.

PayProof is a stronger local developer prototype. Actual PayPal Sandbox execution, public submission materials and external user validation remain unfinished. The stopping decision applies to actionable local defects within the authorized work; it does not mean the submission is complete or the product is defect-free.

The assessment uses the five equally weighted [official PayPal AI Hackathon criteria](https://paypalaihackathon.devpost.com/rules). Scores are subjective estimates from different independent reviewers, not objective measurements or predictions of selection. The latest score is 39.0/50; it was not forced upward to match the earlier estimate.

## Before and after

| Criterion | Original baseline | Before this extension (after seven rounds) | Latest independent review | Evidence and remaining ceiling |
| --- | ---: | ---: | ---: | --- |
| Technological Implementation | 6.5 | 8.0 | 7.5 | Stricter claim checking, opaque agent inputs, fixture recovery and visible operation outcomes. Real Codex execution verified; actual Sandbox account execution remains unverified. |
| Design | 8.5 | 9.0 | 9.0 | Saved/current input boundaries, recoverable unfinished fixtures, reload-safe operation feedback and inspected desktop/mobile flows. |
| Potential Impact | 5.5 | 7.8 | 7.5 | Concrete developer workflow for reproducing refund errors and comparing changes. No external developer feedback or measured business benefit. |
| Innovation/Idea | 6.5 | 8.1 | 8.0 | Combines policy boundaries, independently observed payment outcomes and reusable regression evidence. Evaluates decisions; the harness controls payment execution and retries. |
| Presentation | 5.0 | 7.5 | 7.0 | Functioning failure→fix→replay narrative and a 2:45 outline. Provisional product/draft assessment; no finished public video. |
| **Total /50** | **32.0** | **40.4** | **39.0** | See the review evidence and limitations below. |

Review 13 independently estimated 39.9/50. Full score history is retained in the [iteration log](iteration-log.md); differences between reviewers were not smoothed away.

## Completed improvements in this extension

### Round 8: conservative verdicts and recoverable operations

- Unsupported monetary wording such as spelled amounts, cents and malformed decimals cannot silently receive a passing customer-claim check. Verifier 0.4.0 preserves a definite failed check even when payment evidence is incomplete, while money totals remain unconfirmed. Historical imported verdicts retain their recorded version semantics.
- Server-owned operation status stays visible through navigation and reload, disables conflicting writes and refreshes saved data after completion. API checks cover success, failure and conflicting mutations. A gated browser test verified completion recovery.

### Round 9: fair agent inputs and clear saved evidence

- Agent-facing schema-2 requests use opaque case IDs and exclude answer-bearing labels, expected actions and injected faults. The harness maps decisions back to original case identities. Legacy fixtures and bundles remain compatible. A shortcut using only old semantic IDs was reproduced before this change; there is no claim that the live model used that shortcut.
- Saved results identify their recorded agent, provider, policy and cases, and explain differences from the next-run configuration. Current form choices no longer appear to describe an unrelated historical result.
- Browser and CLI external-agent evaluation passed 11 cases with two intentionally unconfirmed cases. A fresh actual Codex call using the restricted request passed five selected cases.

### Round 10: unfinished fixture recovery

- Fixture matching compares actual financial and customer-request facts rather than editorial metadata. Changed inputs are explicitly blocked and the original snapshot remains inspectable.
- Local set-aside/restore actions preserve provider identifiers and recorded state. They make no provider calls and allow fresh preparation without pretending to cancel an old provider order. Conflicting restore is rejected with focused, visible feedback. Used fixtures cannot be reset.

### Round 12: failure feedback after reload

- A failed long operation now produces a focused, dismissible notification after reload or first arrival. Dismissal is remembered by operation ID for the browser session. The message directs users to inspect saved progress before retrying.
- A gated mock generation verified failure recovery and dismissal at 390px. Operation state survives browser reload while the server runs; it is not a durable job queue across server restarts.

Review passes 11, 13 and 14 did not manufacture extra improvements. Review 11 initially found no issue, but review 12 reproduced missing failure feedback and reset the clean-review count. Reviews 13 and 14 then supplied the two consecutive clean reviews required to stop.

## Verification evidence

| Observed result | Evidence | What it proves |
| --- | --- | --- |
| Final independent seeded demo: 1 pass, 1 failure, $5 excess; corrected: 2/2 passed | `b6abc79e-eb44-4053-9603-11ccd56cb1aa` → `e5797300-e4e7-4797-8123-e702e2fb7d1f` | Detects the deliberately planted policy defect while preserving the legitimate refund. Simulator only. |
| Fresh actual Codex prompt-version-2 run: 5/5 passed, including 2/2 legitimate cases | `606ab5d8-cea2-4272-9c4d-17ed9fd1f669`; `artifacts/judge-loop/iteration-9-live-codex.json` | Real AI decisions using opaque case IDs, with retained thread/usage metadata. Payments are synthetic; this is not a model benchmark. |
| Corrected full approved suite: 11 passes, zero failures, two deliberately inconclusive cases | Review 13 run `d8d65eda-dc7b-4452-a2ad-18e8650a1157` | Pending/readback-failure injections cannot falsely pass. Simulator only. |
| Fresh package installation and complete checks | `artifacts/judge-loop/final-clean-package-check.log` | `npm ci`, 163 tests, TypeScript and production build all passed in a fresh extracted directory. |
| Source archive validation | `artifacts/judge-loop/final-package.json`, `artifacts/source-manifest.json` | 90 allowlisted files; credentials, runtime state, dependencies, build output and local evidence excluded. Final executable files match the clean tested copy byte-for-byte. |
| Operation, scope and fixture recovery | `iteration-8-operation-busy.png`, `iteration-9-saved-scope.png`, `iteration-10-fixture-recovery-mobile.png`, `iteration-12-recovered-failure-mobile.png` in `artifacts/judge-loop/` | Rendered completion/failure recovery, saved-input boundaries and mocked fixture recovery, including 390px error/focus checks. |
| Final independent reviews | `artifacts/audit-r13/review.md`, `artifacts/audit-r14/review.md` | Separate reviewers found no significant actionable local defects in bounded reviews and repeated the core journey. |

Review 14 independently passed 12 targeted tests, repeated corrected replay (2/2), verified comparison reported one fixed failure and zero lost passes, and checked focused malformed-import recovery, editor validation and mobile navigation. It made no actual AI/PayPal calls and preserved the scenario library. Its score was 39/50. Review 13 independently passed 46 targeted tests; the coordinating engineer separately performed the full clean-package check.

Local screenshots, exports and logs are intentionally excluded from the source archive. Mocked PayPal tests prove bounded adapter behavior, not successful actual account integration. The CLI default model's exact revision was not resolved. Browser checks are not a comprehensive accessibility audit or a performance benchmark. Complete evidence and earlier rounds are in [verification](../verification.md).

## Remaining weaknesses and exact next actions

1. **Actual Sandbox execution remains blocked.** Local status reports `paypal.configured=false`, with zero actual fixtures. Add local Sandbox credentials, restart, complete separate Sandbox buyer approval, then capture, execute and retain independent refund readbacks. Follow [Sandbox verification](../sandbox-verification.md). Simulator receipts and mocked tests do not fill this gap.
2. **Public delivery is unfinished.** Publish the licensed source repository and a public YouTube demonstration strictly under three minutes, then verify access and finish the submission checklist. The ZIP and script are preparation, not a submitted entry.
3. **Live-AI judging access is unresolved.** Arrange permitted reproducible access without publishing subscription credentials or exposing the authenticated local server.
4. **User benefit is unmeasured.** Observe developers using the external-decision/import/replay workflow and gather feedback before claiming adoption, avoided losses or time saved.
5. **Scope remains bounded.** USD courtesy refunds, known fixture refund IDs, bounded English claim checking, and harness-owned payment/retry execution. Passing cases do not certify production safety or an external agent's complete orchestration.

## Demo outline — 2:45

- **0:00–0:35:** Introduce the cumulative-refund problem; show the seeded failure and legitimate companion.
- **0:35–1:12:** Correct the decision, compare results and show the external-agent input contract.
- **1:12–1:37:** Show the genuine paired AI generation and recorded live Codex evidence, with simulator payments clearly labeled.
- **1:37–2:02:** Show actual PayPal Sandbox evidence only after completing verification. For the current rehearsal, disclose setup-needed status and the exact blocker.
- **2:02–2:45:** Import/replay saved evidence, show an unconfirmed case and export the reproduction.

The [full recording script](../demo-script.md) includes narration and the conditional PayPal segment. The [submission checklist](../submission.md) remains open.
