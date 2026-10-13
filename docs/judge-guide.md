# Reproduce PayProof's central claim

PayProof checks whether a proposed refund respects merchant policy while preserving permitted refunds. A $100 purchase has already received $15 against a $20 courtesy allowance. A new $10 needs escalation; a new $5 is permitted. The demonstration deliberately uses this small pair so the decision and payment evidence can be inspected directly.

## Fresh source package

Use Node.js 22 or later and npm on macOS or Linux. Clone [the public repository](https://github.com/Aniket-pd/payproof), then enter the `payproof` directory (or extract a source ZIP and enter its folder):

```sh
git clone https://github.com/Aniket-pd/payproof.git
cd payproof
```

```sh
npm ci
npm run judge:verify
```

The verification command needs no running server, credentials or account. It does not read or alter `.payproof/state.json`. Installation downloads dependencies; the verification itself uses local simulator execution only. A test runs the command with network connections and child processes blocked.

Expected results:

| Evaluated decisions | Cases passed | Legitimate cases passed | Synthetic policy excess |
| --- | --- | --- | --- |
| Seeded cumulative-limit defect | 1/2 | 1/1 | $5.00 |
| Escalate every request | 1/2 | 0/1 | $0.00 |
| Corrected teaching reference | 2/2 | 1/1 | $0.00 |
| Reused recorded Codex decisions | 2/2 | 1/1 | $0.00 |

The command exits 0 only when this complete comparison holds, and 1 for invalid evidence or an unmet check. Expected failures in the negative controls are part of the verifier demonstration. The command prints an output directory containing `report.json`, `seeded.json`, `refusal.json`, `corrected.json`, and `recorded-replay.json`. Each export includes the scenario snapshots, decisions, checks, refund records and provenance. To choose a destination:

```sh
npm run judge:verify -- --out artifacts/my-review
```

Input modification without updating the recorded digest stops evaluation. `--recorded path/to/evidence.json` accepts another original Codex export only if it validates and uses the exact same two demonstration inputs. It does not turn arbitrary historical claims into authenticated evidence.

## What the AI artifact establishes

`examples/recorded-codex-proof.json` is a synthetic two-case export captured during the local browser session on 13 October 2026. Original run: `df7e6c3f-a89a-4a51-b21a-166f0ed150ea`; thread: `01a13584-af4f-73d0-bb66-ec8dedeb2d3a`. The official Codex CLI/SDK was version 0.162.0, using the CLI default model; the exact model revision was not resolved. Locally, that genuine call took 17.514 seconds and produced two passing decisions under simulator evaluation.

In a downloaded source package, those historical facts are **file claims**. The checker validates the whole evidence document, marks it imported, and preserves that origin through replay. It independently executes the recorded decisions under the current simulator and verifier. It does not call the model, authenticate its authorship, reproduce PayPal account state, or establish a model success rate. The digest binds the inputs; it is not a digital signature over the result.

For fresh inference, run `npm run dev`, open the landing page, run the comparison, connect an authorized local Codex account, then choose **Run a fresh Codex check**. The model receives opaque case identities and no expected answers or injected fault labels. The verifier determines the outcome separately. A reload recovers the persisted request; failure is displayed without fabricated fallback. Optional inference consumes the account's Codex allowance.

## Inspect beyond the two-case demonstration

```sh
npm run check
npm run dev
```

In Test lab, run the broader approved suite. Pending payments and missing readbacks deliberately stay inconclusive. Inspect saved input facts, timelines and refund records; compare only compatible runs. Import any generated export via Run history, observe its **Unverified external evidence** label, then choose **Replay saved inputs** to produce a local simulator observation. The external-agent example in `examples/README.md` shows how to submit a named/versioned decision component.

## Remaining submission gates

Actual PayPal Sandbox execution was observed on five fresh captures, including one two-case Codex batch. See [the verification record](sandbox-verification.md) and [exact exports](../examples/recorded-paypal/README.md). Optional fresh verification uses your own authorized account and buyer approval. Offline replay does not authenticate the historical provider claims.

The public source and anonymous cloning are verified. [The initial Ubuntu CI run](https://github.com/Aniket-pd/payproof/actions/runs/38460136404) passed all 182 tests, build, offline evidence checks, packaging and presentation checks. The final public YouTube video under three minutes, free live-AI judging access, entrant eligibility, and Devpost submission remain separate checklist items. External developer feedback and measured business impact are still missing. See [submission preparation](submission.md), [the 2:38.5 script](demo-script.md), and [the current review](judging/2026-10-14-report.md). A [developer evaluation worksheet](developer-evaluation.md) is ready for outside participants; no responses have been collected.
