# Demonstration rehearsal — 2 minutes 38 seconds

**Current status: local review artifact, updated 13 October 2026. Actual PayPal Sandbox execution is not verified.** The public repository, public YouTube video, free live-AI judging access and external developer feedback remain unfinished.

The editable [Remotion source](../presentation/README.md) contains eight separately editable scenes, captured app screens, generated stock narration and source-relative captions. The authored timeline is **4,739 frames at 30 fps: 157.967 seconds**, below the [official three-minute limit](https://paypalaihackathon.devpost.com/rules). It is an edited demonstration of saved evidence, not a continuous recording of a new AI request or PayPal transaction. Narration uses the stock Leslie voice through Runway; attribution is in [NOTICE](../presentation/NOTICE.md).

| Time | Visual evidence | Main point |
| --- | --- | --- |
| 0:00–0:14 | Cumulative arithmetic: $15 already refunded + $10 requested = $25 against a $20 allowance. | A small new refund can still violate the merchant's cumulative policy. |
| 0:14–0:37 | Captured three-control proof page, highlighting each result. | The seeded control over-refunds; blanket refusal misses the valid customer; the corrected reference preserves the permitted $5 refund. Payments are simulated. |
| 0:37–0:54 | Captured saved inputs and independent outcome checks. | Follow the saved decision to the money; a tool response alone does not establish completion. |
| 0:54–1:14 | Recorded Codex result and saved model/thread metadata. | Real model decisions receive opaque identities and no expected answers. Deterministic code evaluates them; exact model revision remains unknown. |
| 1:14–1:35 | The observed 20-case report: 18 passed, 0 failed, 2 inconclusive; 10/12 legitimate passed. | One fixed synthetic batch, with pending/unavailable payment evidence still inconclusive. It is not a reliability benchmark. |
| 1:35–1:57 | Current Connections setup status, then an explicitly labeled mocked crash-recovery screenshot. | Actual PayPal account execution remains unverified. The separate mock test retained request identity and uncertainty without repeating a payment after restart. |
| 1:57–2:16 | `npm run judge:verify` and `npm run challenge` commands. | Replay evaluates recorded decisions locally without a fresh model/provider call. Imported historical claims stay unverified. |
| 2:16–2:38 | External decision import workflow, controlled USD scope, and closing claim. | Catch the tested failure, preserve the valid refund, and make the evidence inspectable. Actual Sandbox execution and developer feedback are next. |

The exact supplied narration is in `presentation/narration.json`. `npm run captions` from that directory validates timing and exports a companion SRT. Scene source contains inline caption arrays that remain editable in Studio. Editing the scene captions also requires updating the matching JSON before regenerating the companion SRT.

## Gate for the final PayPal segment

Actual Sandbox execution is **unverified now**. Follow [Sandbox verification](sandbox-verification.md), retain provider exports, and confirm each fixture is fresh and matches its scenario. Do not substitute simulator or mocked receipts. Once verified, replace the 1:35–1:57 segment with the actual order→buyer approval→capture→refund→independent readback evidence, then revise the closing and recheck total duration.

## Evidence used

- Teaching comparison: baseline `e969ad26-df09-4816-80af-695cd85b6c63`, refusal `55615e3b-0ed4-4189-8e79-9f2d8da18a62`, corrected `6de51d9e-151c-4a7a-87bd-72f2075db005`. Seeded: 1/2, $5 excess. Refusal: 1/2, 0/1 legitimate. Corrected: 2/2, 1/1 legitimate, $0 excess.
- Genuine two-case Codex candidate: `df7e6c3f-a89a-4a51-b21a-166f0ed150ea`, recorded 13 October 2026: **2/2 passed; 1/1 legitimate; $0 excess**, with simulator payments. The 17.514-second request survived a browser reload. CLI/SDK 0.162.0; exact default-model revision unknown. Export: `examples/recorded-codex-proof.json`.
- Genuine fixed 20-case Codex candidate: `c7f34d7c-e278-449b-a7fc-e9199125706d`: **18 pass / 0 fail / 2 inconclusive**, 10/12 legitimate passed. One observed batch, no prompt tuning or rerun to improve the result. Full scope: [challenge guide](ai-challenge.md). Original export: `examples/recorded-codex-challenge.json`; video report: `presentation/public/challenge-report.json`.
- Mocked recovery: isolated run `dfbfe0a1-1336-4aa5-94cd-cfffb97756aa`, retained after a forced server stop following exactly one mocked refund response. Zero provider calls occurred after restart while browsing. The captured report remains inconclusive and is visibly labeled mocked in the film.
- Automated checks, browser observations and source-package verification: [verification](verification.md). Counts are engineering evidence, not guarantees. Seeded faults are teaching examples, not PayPal vulnerabilities or model failure rates. Synthetic excess is not measured money saved.

Publishing the licensed repository, uploading the public YouTube video, arranging free judging access and submitting Devpost remain separate unfinished actions. This rehearsal performs none of them.
