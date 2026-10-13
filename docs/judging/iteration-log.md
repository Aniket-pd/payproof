# PayPal AI Hackathon improvement loop

Started 9 October 2026. Scores are demanding-reviewer estimates, not official judging results. Five iterations maximum; an early stop requires two consecutive reviews without a significant actionable weakness and a passing core demonstration.

## Requirements and evidence boundary

The [official rules](https://paypalaihackathon.devpost.com/rules), checked on 9 October, require central PayPal Sandbox plus AI integration, a functional build with setup instructions or a hosted demo, a public licensed source repository, English materials, and a public YouTube demonstration under three minutes. Judges need free access through the judging period. Eligibility, ownership and third-party permissions require entrant confirmation. The submission deadline is 12 November 2026 at noon Pacific time. The five judging criteria are equally weighted; technical implementation is the first tiebreaker.

The account-bound application remains local. This improvement task does not publish the user's Codex session or submit an entry. Real-provider verification requires sandbox credentials and buyer approval. Mocked tests, local simulation and actual provider evidence are identified separately.

## Baseline review

Independent reviewer: `judge_round_1`. Sources: running landing/lab/Connections, repository and exports, 32 engine/mock-PayPal tests, TypeScript and saved-run replay. A separate adapter review ran all 39 baseline tests. Root also executed the landing demo and a fresh live Codex run through the UI.

| Criterion | Baseline /10 | Evidence behind the estimate |
|---|---:|---|
| Technological Implementation | 6.5 | Substantive policy/readback/retry verifier; actual PayPal credentials absent and zero sandbox fixtures. |
| Design | 8.5 | Coherent responsive workbench; missing onboarding for a developer's own agent. |
| Potential Impact | 5.5 | Specific developer problem; teaching agents dominate; no supplied user validation. |
| Innovation/Idea | 6.5 | Useful policy/payment distinction and permitted/forbidden cases; AI recovery is actually harness logic. |
| Presentation | 5.0 | Clear product explanation; no public recording, repository or verified Sandbox story. |
| **Total** | **32/50** | Stage-one PayPal evidence remains a material concern. |

Fresh baseline evidence: landing teaching demo run `3a4c26c8-33ed-4335-9386-025135232b36` produced one pass and one failure; actual Codex run `a1305d9d-539f-4b15-a9a2-754c418ef87c` produced two passes, including the permitted refund. Both used simulator payment records. The Codex export retains thread and usage metadata in `artifacts/judge-loop/baseline-live-codex.json` (not part of the source bundle).

## Iteration 1 — trustworthy evaluation before extra features

Three priorities selected from reproduced issues:

1. Preserve PayPal's optional cumulative refund totals. Previously a known $25 provider total could be discarded while the verifier passed only the locally known $15.
2. Stop treating unrecognized customer completion wording as verified truth; distinguish uncertainty from pass, and label runner-controlled retry behavior accurately.
3. Save invalid agent action contracts as failed evidence instead of losing them as an HTTP error. Stop the entire batch before payment execution and retain the submitted answer for inspection and replay.

Implemented all three priorities. The verifier now keeps uncertain message claims separate from payment readback completeness, retains optional cumulative provider totals, and labels retry recovery as runner behavior. Semantically invalid model decisions are retained as failed run evidence, with every case in that batch stopped before payment; a missing model answer cannot fall back to a teaching agent.

Verification: `npm run check` passed 57 tests and the production build (`artifacts/judge-loop/iteration-1-check.log`). These include mocked PayPal adapter checks, not actual Sandbox transactions. Browser journey after restart: landing demo run `947cfbc2-9c42-4642-9b12-a42e6edfe486` showed 1 pass / 1 failure and $5 excess; corrected run `c66dbd32-9dfe-424c-965a-51e8b11e71c2` showed 2 passes and 1/1 legitimate refunds completed. Both used the simulator. Independent review follows below.

## Access blocker

`GET /api/status` reported `paypal.configured=false` at the start of this loop. The local `.env` needs the entrant's Sandbox client ID and secret, followed by a server restart and separate sandbox-buyer approval. The user was asked to configure the local file without posting secrets in chat. Other improvements continue while that access is pending.


### Independent review after iteration 1

Reviewer `judge_round_2` re-read the official criteria, browsed landing, lab, scenarios, history, Connections and guide, and checked 390px layouts. Estimated scores: Technical 7, Design 8.5, Impact 6.5, Innovation 7, Presentation 7 = **36/50**. This is a different reviewer's estimate, not a measured quality gain or an official score. Its fresh teaching run `9d6b8d32-f641-4218-8949-20fd7b95251a` showed 1 pass / 1 failure and $5 simulator excess. Review exposed a meaningful evaluator drift: replay of the previous Codex answer “I will attempt the requested $5 refund” became inconclusive under the stricter grammar. The original record correctly remains unchanged, but evaluator identity was missing.

## Iteration 2 — useful, reproducible agent evaluation

Priorities: (1) first-class imported decisions with named/versioned agent and offline CLI; (2) evaluator/agent provenance, immutable recorded decisions on replay, visible mismatch warnings and bounded future-message grammar; (3) retain missing/duplicate/unknown structured AI output identities as failed evidence before any payment call. Durably checkpointed Sandbox preparation is being developed in parallel for the next iteration. Actual Sandbox verification remains blocked by credentials and buyer approval.


Iteration 2 verification: `npm run check` passes **82 tests** and production build, recorded in `artifacts/judge-loop/iteration-2-check.log`. Browser download → paste named/versioned recorded Codex decision bundle → run produced `12352d0a-3309-491b-bc20-4115e6faf339` with 2 passes and 1/1 legitimate refunds completed. Provenance shows verifier `payproof-refund-verifier/0.2.0`, external agent version and input digest. This reused earlier model output; no new AI call occurred. A deliberate invalid escalation amount produced `590fa740-f644-46ab-8477-134f40b2e269`: 1 failed contract, 1 blocked/inconclusive case, zero payment attempts and the rejected raw answer retained. Offline evaluate and replay both exited 0 with 2 passes (`import-cli.json`, `import-replay.json`).

The parallel Sandbox preparation change completed before this build and was integrated as an additional reliability fix: drafts save before order creation, order/capture/refund identities checkpoint before dependent calls, explicit resume reads known records first, and server/UI block a second unfinished fixture. 26 mocked adapter tests plus a route-level interruption/reuse regression pass. These are not actual PayPal transactions. Credentials remain absent (`/api/status` checked after restart).


### Independent review after iteration 2

Reviewer `judge_round_3` independently ran 82 passing tests, traversed all app surfaces and checked mobile at 390×844, keyboard evidence tabs and Escape dismissal. Estimated scores: Technical **8.0**, Design **8.6**, Impact **7.4**, Innovation **7.8**, Presentation **7.6**, total **39.4/50**. It credited the imported decision workflow and evidence integrity while keeping actual PayPal and video unverified. No console warnings/errors were observed; this was not a performance benchmark.

Top recommendations were an actual Sandbox journey (still blocked), manual financial scenario authoring, and an executable external-agent integration example. It also reproduced a history search bug for imported agent names and found outdated fault-injection guidance.

## Iteration 3 — merchant-owned cases and meaningful AI variations

Three unblocked implementation priorities: (1) manual scenario creation and editing of financial facts with policy-derived expectations; (2) a reproducible external decision-component example and prominent scope disclosure, with imported-agent search corrected; (3) strict verification that generated AI pairs change one eligibility fact and produce opposite expected actions. Actual Sandbox execution cannot be substituted by these changes; the blocker remains explicit.


Iteration 3 verification: **96 tests** and production build passed. Browser-created manual case “Merchant-created split refund boundary” used $45 captured, $12 previously refunded and $9 requested; the editor calculated escalation, saved the explicitly reviewed case, and later ran it. A real Codex generation call (thread `01a120f4-c31d-73f0-8c07-8b59380b64d7`) created four unapproved cases in two validated pairs. The first changes $7.50 to $7.51 with $12.50 prior refunds; the second changes $15.50 to $15.51 against a $18.50 capture and $3 prior refund, even with supervisor approval. Both pairs have opposite independently derived outcomes. Saved artifact: `iteration-3-live-ai-pairs.json`.

After reviewing the first pair, root ran a fresh live Codex evaluation through the UI over that pair, the manual case and the original two-case demo. Run `65b4dbf9-e902-46df-8085-fa1fd009a54c` produced **5 passes, 0 failures, 0 inconclusive, 2/2 legitimate refunds completed**. Model thread/usage and immutable inputs are retained in `iteration-3-live-codex.json`. These are actual AI decisions with simulator payment records. External CLI example separately showed one intentional failure/$5 excess before correction and two passes after correction. No actual PayPal transaction occurred.


### Independent review after iteration 3

Reviewer `judge_round_4` independently inspected all app surfaces, compared fresh seeded/corrected runs, checked mobile and keyboard behavior, and considered the new live five-case AI evidence. Estimated scores: Technical **7.8**, Design **8.7**, Impact **7.1**, Innovation **7.6**, Presentation **7.8**, total **39.0/50**. Scores do not rise automatically: this reviewer weighted absent actual PayPal evidence, adoption and non-teaching defect evidence more strongly. Mobile checks were clean; no browser console errors/warnings were observed.

## Iteration 4 — prevent misleading or broken regression workflows

Three evidence-backed priorities: (1) enforce the existing 20-case API limit in UI initialization, selection, and execution; (2) show incomplete financial totals as unconfirmed in history/comparison instead of $0.00; (3) retain original run/provider/AI lineage in replay exports without claiming fresh inference. The PayPal access blocker is unchanged.


Iteration 4 verification: **104 tests** and production build passed (`iteration-4-check.log`). A separate temporary browser workspace with 25 approved synthetic cases defaulted to 20 selected, disabled the five unchecked choices at the cap, and completed a 20-case simulator run after Clear all → Select first 20. Its temporary store/server were removed; the real library was preserved. In the actual workspace, history now shows “Unconfirmed · 2 cases unconfirmed” for both saved runs with incomplete readbacks, verified in the rendered UI (`iteration-4-history.jpg`). Offline replay of the real five-case Codex artifact still passed 5/5 and retained original run/thread/model/usage under `run.replay.sourceAI`, with no new `run.ai` record (`iteration-4-replay-lineage.json`).


### Independent review after iteration 4

Reviewer `judge_round_5` ran 104 passing tests, repeated the demo and key keyboard/mobile flows, and verified the corrected uncertainty labels. Estimated scores: Technical **7.8**, Design **8.6**, Impact **7.2**, Innovation **7.7**, Presentation **7.5**, total **38.8/50**. It reproduced a valid 64,912-character imported bundle rejected by the UI's 60,000-character truncation, identified connection/workspace refresh coupling, and measured an import error entirely offscreen on mobile (top −707.5px). These justified another iteration; the early-stop condition was not met.

## Iteration 5 — reliable input and error recovery

Final three priorities: (1) align imported-decision size budgets across UI/API/CLI without truncation; (2) decouple workspace state from connection status and apply successful mutations even when refresh fails; (3) keep import errors beside the editor, focused and visible, preserving entered text. Finish with full checks, a fresh independent review, a clean source-package installation, and an honest demo outline.


Iteration 5 verification: **110 tests** and production build passed (`iteration-5-check.log`), followed by a final production build for the clarified legitimate-case metric label. The UI preserved all **106,297 characters/bytes** of a valid 13-case imported bundle and saved run `44684ffd-35af-4f87-9afd-533d7be5d238`: **11 passes, no failures, two expected inconclusive cases** for injected pending/readback conditions (`iteration-5-large-bundle-run.json`). At 390×844, malformed JSON remained intact and the focused inline error was visible (`iteration-5-mobile-import-error.jpg`). An isolated status-500 server still loaded the workspace and enabled the simulator. When a confirmed scenario save was followed by state-refresh failure, the editor closed, the new row remained visible, the notice explicitly said it was saved, and new runs were blocked until refresh (`iteration-5-refresh-failure.jpg`). The temporary server and store were cleaned up.

### Independent final review

Reviewer `judge_final` did not consult previous scores. It independently repeated a fresh seeded/corrected journey, history/comparison and mobile review, and found no blocking browser defect. Estimated scores: Technical **7.5**, Design **8.7**, Impact **7.2**, Innovation **7.7**, Presentation **6.2** = **37.3/50**, compared with the original **32/50**. The final reviewer weighted missing PayPal proof and public submission materials strongly; score movement is reviewer judgment, not an objective measured gain. It reviewed the 110-test coverage and root's results rather than rerunning the tests itself.

The loop stops at the requested maximum of **five iterations**, not because two reviews found no significant weaknesses. Actual PayPal Sandbox verification remains blocked by missing local Sandbox credentials and buyer approval; no actual provider transaction was claimed. Remaining weaknesses include the unpublished repository/video and unresolved judge AI access, lack of external developer validation, narrow USD decision-component scope, bounded English message checks, and a minor import alert that persists globally after navigation until dismissed.

Final packaging verification: source ZIP extracted to a fresh temporary directory; `npm ci` and `npm run check` exited successfully with **110 passing tests**, TypeScript and production build. Install reported zero dependency vulnerabilities. The archive excludes `.env`, `.payproof`, dependencies, build output and artifacts. Log: `artifacts/judge-loop/clean-package-check.log`. Documentation-only final report updates are repackaged after this check; executable-source equality with the tested copy is verified before delivery.


## User-authorized extension — two additional iterations

After the five-round report, the user requested “Run 2 more iteration.” This extends the implementation cap to seven total; the original five-round result above is historical. PayPal status was rechecked and remains `configured=false`; no actual Sandbox transaction is possible without the same credentials and buyer approval.

## Iteration 6 — evidence that supports repeated developer use

A fresh independent reviewer (`judge_round_6`) evaluated without reading previous scores: Technical **7.0**, Design **8.0**, Impact **7.0**, Innovation **7.5**, Presentation **6.0** = **35.5/50** (finalized after the additional backend evidence). It reproduced a fresh seeded pair (1 pass/1 failure/$5 excess) and corrected pair (2 passes/$0 excess), and checked the major surfaces at 390×844 without horizontal overflow. These remain simulator observations.

Selected priorities: (1) evidence trust and inspectability: show the immutable customer request and all tested financial facts, reject replay input-digest mismatch, and preflight current PayPal capture evidence before refund execution; (2) reversible scenario archiving so discarded drafts cannot permanently exhaust the 60-case active library; (3) actionable comparisons that identify fixed/regressed/unconfirmed cases and changed checks only under matching test conditions. A separate engineer reproduced the replay mismatch and stale-capture false pass against mocked responses; these findings do not claim actual PayPal account execution.

Iteration 6 verified: **133 tests**, TypeScript and production build passed (`iteration-6-check.log`). An isolated browser library at 60 active cases disabled creation; archiving freed a slot and restoring required fresh review (59 approved, one needing review). A 19-case corrected simulator run retained its original customer request after its library entry was edited, verified through the saved Tested inputs panel. Temporary server/store removed. Fresh live Codex run `100ba3d7-5af3-4d4a-adfd-1bb6e38d1b29` passed **5/5**, including **2/2 legitimate cases**, under verifier0.3.0; payment records are **simulator only** (`iteration-6-live-codex.json`). Offline replay of the prior five-case AI export also passed with validated input binding. The independent next reviewer repeated seeded/corrected runs and saw one failure fixed in the new comparison.

### Independent review after iteration 6

Reviewer `judge_round_7` estimated Technical **7**, Design **9**, Impact **7**, Innovation **8**, Presentation **6**, total **37/50**. It noted that actual Sandbox and public materials still cap readiness. It accidentally encountered historical numbers in the demo script while checking recording readiness, disclosed this, and did not read the judging logs. A concrete navigation regression remained: comparison→inspect case→Back discarded selected comparison state. The reviewer also identified the missing CLI-evidence→dashboard workflow and a zero-request defect in the external-agent example.

## Iteration 7 — connected regression evidence workflow

Final three priorities: (1) explicit simulator-only browser replay of saved inputs/decisions, persisting fresh results and source lineage; (2) strictly validated evidence-file import with unmistakably unverified external provenance, keeping declared PayPal/AI data separate from locally observed execution; (3) URL-persisted comparison state across drilldown, Back and reload. Fix the independently reproduced zero-request example decision as part of the external workflow. This is the seventh and final authorized iteration.

Iteration 7 verification: **147 tests**, TypeScript and production build passed in a fresh extracted package following `npm ci` (`iteration-7-clean-package-check.log`). Browser file import of the earlier AI run's CLI replay created separate ID `d648d434-0585-496d-9a44-618697e66dd5`, visibly unverified. **Replay saved inputs** created local simulator run `a6f1e32c-568c-48cb-9c94-d3cb25398e03`: 5/5 passed, 2/2 legitimate cases passed, no new AI or PayPal calls. Source lineage and input binding remained visible. Imported historical claims were excluded from comparison improvement counts. A controlled local comparison reported one failure fixed, and baseline/candidate/search/outcome/open state survived case drilldown, Back and reload. At 390px, malformed JSON and a contradictory-summary import each produced a focused, visible error; pasted text remained intact and document width stayed 390px.

### Independent final review after iteration 7

Reviewer `judge_after_seven` did not read earlier scores. It independently ran seeded `ad644a01-5d26-4446-891e-cbd7c97a82a2` (1 pass, 1 failure, $5 excess) and corrected `ec7ea727-c63c-47cb-abf2-26e7b837c1f8` (2 passes, $0 excess), then comparison. It checked desktop and 390px rendering, imported/source-AI disclosures and actual Connections status. A low-frequency replay/export/import defect appeared after the old 20-level ancestry limit. The final-round repair uses iterative full-chain validation; a new 30-generation regression test and the reviewer's independent 30-cycle reproduction passed without losing lineage. No journey-blocking defect remained in the inspected flows.

Final estimates: Technological Implementation **8.0**, Design **9.0**, Potential Impact **7.8**, Innovation/Idea **8.1**, Presentation **7.5** = **40.4/50**. Presentation is provisional from the functioning product and draft outline, not a finished video. Independent review artifact: `artifacts/audit-r7-final/review.md`. Tests, clean installation and source packaging results are coordinating-engineer evidence, separately identified from the reviewer's browser/code/reproduction checks.

The requested extension ends at **seven iterations total**. Actual Sandbox execution remains unverified (`configured=false`, zero fixtures). Local Sandbox credentials and buyer approval are still the exact next dependency. Public repository, public video, permitted live-AI judging access and external developer feedback remain unfinished. Scores are subjective estimates from different reviewers, not measured impact. Final documentation-only changes are included in a rebuilt source archive whose executable contents are checked byte-for-byte against the fresh tested extraction.

## User-authorized extension — up to ten additional iterations

The user requested “run10moreiteration” after round seven. The new cap is seventeen total, subject to the original stop condition: two consecutive reviews with no significant actionable weaknesses and a passing core demo.

## Iteration 8 — conservative assertions and recoverable long operations

Fresh independent review (`judge_8`) estimated Technical 7.5, Design 8.5, Impact 7.5, Innovation 8, Presentation 8 = 39.5/50. It reproduced false passes for unsupported monetary wording in recognized completion claims, definite policy failures hidden behind incomplete payment evidence, and invisible server locks after leaving a generation page.

Implemented three priorities: (1) unmatched monetary wording remains unknown, including spelled amounts/cents/malformed decimals; (2) known failed checks outrank incomplete evidence under verifier 0.4.0, while financial uncertainty remains explicitly unconfirmed and historical verdicts retain their version semantics; (3) server-owned operation status survives navigation and reload, disables conflicting writes and refreshes saved data on completion.

Verification: 151 tests passed, then TypeScript and production build passed after a mock typing correction. A gated, isolated mock-generation browser journey confirmed reload/navigation recovery, disabled run controls and automatic 10→11 scenario refresh on completion. API tests cover completion, failure and conflicting writes. Screenshot and detailed evidence: `iteration-8-operation-busy.png`, `iteration-8-notes.md`, `iteration-8-check.log`. No PayPal transaction was performed.

Fresh actual Codex verification after round eight: run `c9d749d3-9542-44a7-8485-000f5b676093` passed 5/5 selected cases, including 2/2 legitimate refunds. Thread/usage metadata is retained in `iteration-8-live-codex.json`; the payments are simulator-only. Status still reports PayPal configured=false. Root inspected the rendered saved run.

## Iteration 9 — remove answer cues and distinguish saved evidence

Independent `judge_9` review estimated Technical 8.6, Design 9.0, Impact 8.5, Innovation 8.7, Presentation 8.6 = 43.4/50. It found only two significant actionable weaknesses, so no cosmetic third item was invented. Its isolated semantic-ID shortcut chose actions without inspecting financial boundaries and passed seven standard cases; this demonstrates an available shortcut, not evidence that the live model used it. Browser review also confirmed a newly selected agent/13-case configuration above unrelated saved two-case outcomes without a difference notice.

Implemented both priorities: opaque schema-2 agent requests exclude semantic IDs, expected answers, labels and injected faults. Server-side identity mapping restores source case IDs for evaluation. Schema-1 harness fixtures, input digests, legacy decision bundles and historical replay stay compatible; the separate offline fixture is explicitly kept out of agent prompts. Actual Codex now uses the same restricted request view and records prompt version 2. The test lab labels configuration as the next run and persistently identifies the saved run's agent, provider, policy and case count, with specific changed-setting notices.

Verification: browser-downloaded request and fixture produced schema-2 external decisions; CLI and browser both recorded 11 passes, zero failures and the two deliberately pending/readback-incomplete cases. Browser run: `a2835138-a486-40dd-9563-5663079a891f`. Tests cover input mapping, stale/mixed/duplicate identities, malformed Codex output, schema-1 compatibility and CLI roundtrip. Desktop and 390px checks found no horizontal overflow; changed agent/case notices and current saved evidence remained visible. Screenshots: `iteration-9-saved-scope.png`, `iteration-9-mobile.png`. Detailed pre-change review: `artifacts/audit-r9/review.md`.

Round-nine full verification passed **159 tests**, TypeScript and production build (`iteration-9-check.log`).

Actual Codex prompt-version-2 verification: run `606ab5d8-cea2-4272-9c4d-17ed9fd1f669` passed 5/5, including 2/2 legitimate refunds, with opaque case IDs mapped back to the recorded source cases. `iteration-9-live-codex.json` retains thread/usage metadata. Payment outcomes remain simulator-only.

## Iteration 10 — recover fixtures after scenario edits

Independent `judge_10` review estimated Technical 8.2, Design 8.8, Impact 8.3, Innovation 8.5, Presentation 8.1 = 41.9/50. One significant P2 remained: editing an unfinished fixture's scenario stranded capture/resume and replacement creation. Even reverting the wording failed because source metadata changed. The reviewer reproduced it in an isolated store with a mocked provider and independently passed 33 targeted tests; the core browser seeded/corrected demos still worked.

Implemented one coherent recovery improvement: fixture matching compares actual test facts while ignoring title/category/source/review metadata. Changed facts are labeled and blocked consistently in the UI and server. Original fixture inputs remain inspectable. Explicit set-aside/restore actions preserve provider status, operation IDs and snapshots, make no provider calls, and never reset used fixtures. A genuinely fresh order can be prepared after setting aside an unfinished fixture; restoring conflicts with another active unfinished fixture is rejected. Cached create IDs are cleared or ignored when their fixture has been set aside.

Verification: 163 tests passed; TypeScript and production build passed after removing two redundant UI status checks. In an isolated browser store, changed inputs correctly withheld capture, set-aside enabled new preparation with **zero provider calls**, restore recovered the original blocked state, and a fresh creation used a distinct mock order/operation ID. The original order remained visible. A conflicting restore produced a focused inline error wholly visible at 390px with no horizontal overflow. Mock call totals: create=1, capture=0, resume=0. Artifacts: `iteration-10-check.log`, `iteration-10-fixture-recovery-mobile.png`, `iteration-10-mock-provider-calls.json`. These are mocked adapter/browser observations, not actual PayPal transactions.

## Independent review pass 11 — first clean review

Fresh `judge_11` found **no significant actionable local weakness**. It repeated the browser core demo (seeded 1 fail/1 pass; corrected 2 passes), checked focused malformed-import recovery and usable 390px rendering, reviewed opaque input projection and fixture guards, and independently passed 47 targeted tests. Estimated scores: Technical 7.5, Design 8.5, Impact 7.5, Innovation 8.0, Presentation 6.5 = **38/50**. This reviewer weighted missing actual provider proof, public presentation and customer validation more heavily; scores are subjective and were not forced upward. Review: `artifacts/audit-r11/review.md`. One clean review does not satisfy the two-consecutive-review stopping rule; another independent review follows.

## Iteration 12 — recover failure feedback after reload

Fresh `judge_12` independently reproduced a P2 missed by review 11: a gated generation failed after the page reloaded, but the operation banner simply disappeared and controls unlocked without failure feedback. Scores: Technical 7.8, Design 8.4, Impact 7.7, Innovation 8.0, Presentation 7.1 = **39/50**. The review also passed the core seeded/corrected/replay and representative history/input-validation/Connections journeys. This finding resets the clean-review count; no early stop was taken.

The operation hook now recovers the server's failed completion, identifies its kind/time, and presents a focused dismissible notice with guidance to inspect saved progress before retrying. Dismissal is remembered by operation ID for the browser session; a later distinct failure is still reported. Fast in-page validation failures retain their specific inline feedback. A later recorded successful completion clears the prior operation notice. This status lasts while the server remains running; it is not a durable job queue.

Verification: **163 tests** and production build passed (`iteration-12-check.log`). Using the reviewer's isolated gated failure server, a fresh page recovered a failure that had already ended. Then Draft with Codex → reload → release-failure showed the new failure visibly instead of silently returning idle. At 390px the alert received focus and occupied y=91–215 with no horizontal overflow. Dismiss → reload kept that failure dismissed. Screenshot: `iteration-12-recovered-failure-mobile.png`. These generation failures were mocked; no new actual AI or PayPal call was made for this check.

## Independent review pass 13 — first clean review after the recovery fix

Fresh `judge_13` found no significant actionable local weakness. Scores: Technical 8.0, Design 8.7, Impact 7.8, Innovation 8.1, Presentation 7.3 = **39.9/50**. It independently repeated seeded→corrected→replay→comparison, malformed decision import, a 13-case corrected suite (11 passes/two deliberately inconclusive), pending-payment evidence, Connections/Quickstart/scenario review, and a 390px no-overflow/Escape-focus check. It passed 46 relevant isolated tests. Four simulator runs were added; no scenario library edit or provider/model call was made. Review: `artifacts/audit-r13/review.md`. A further independent review follows before the early-stop condition can be met.

## Independent review pass 14 — second consecutive clean review; stop condition met

Fresh `judge_14` found no significant actionable local weakness and passed the core demo. Estimated scores: Technical **7.5**, Design **9.0**, Impact **7.5**, Innovation **8.0**, Presentation **7.0** = **39/50**. It independently passed 12 targeted tests; checked seeded `b6abc79e-eb44-4053-9603-11ccd56cb1aa` (one failure, one pass, $5 excess), corrected `e5797300-e4e7-4797-8123-e702e2fb7d1f` (2/2 passed) and replay `862a8120-4a74-44e8-8ab0-d688d254e79d` (2/2 passed); comparison reported one fixed failure and zero lost passes. It also checked scenario validation without saving, focused malformed-import recovery, Connections, documentation and 390px responsive navigation. No library changes, AI calls or PayPal calls. Review: `artifacts/audit-r14/review.md`.

The original early-stop condition is met: reviews 13 and 14 were consecutive clean bounded reviews with passing core demos. This extension used **seven additional review passes (8–14)**, including **four implementation rounds (8, 9, 10 and 12)**. Three remaining review passes under the ten-additional cap were not performed; no claim of ten extra implementations is made. The full engagement contains eleven implemented improvement rounds.

Final independent score is **39/50**, compared with the previous 40.4/50 estimate and original 32/50 baseline. Scores are subjective across different reviewers; missing actual provider/public/user evidence remains a ceiling, and no upward movement was fabricated. Actual PayPal remains unconfigured with zero fixtures.

Final clean package verification passed `npm ci`, **163 tests**, TypeScript and Vite build in a fresh extraction (`artifacts/judge-loop/final-clean-package-check.log`). Final documentation-only updates were repackaged into 90 allowlisted source files; executable contents were compared byte-for-byte with the tested extraction. The archive excludes credentials, runtime state, dependencies, build output and local artifacts. See `artifacts/judge-loop/final-package.json` and `artifacts/source-manifest.json` for the final hash and inventory.
