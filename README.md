# PayProof Refunds

**A release check for AI refund agents.** Compare the agent's decision with approved merchant policy and independently read payment records. Keep the legitimate refunds working while catching the tested policy and retry failures.

PayProof is a local developer application built for the PayPal AI Hackathon. It includes a working simulator, optional live AI through the official Codex SDK, and a PayPal Sandbox adapter. **Actual Sandbox execution was verified on 14 October IST:** the seeded defect produced $5 policy excess, both corrected controls passed, and a fresh two-case Codex run passed with independent PayPal readbacks. See the [verification record](docs/sandbox-verification.md) and [recorded exports](examples/recorded-paypal/README.md). Simulator replay remains explicitly separate from these historical provider observations.

The styled Quickstart is available at [http://127.0.0.1:4318/app?view=docs](http://127.0.0.1:4318/app?view=docs) while the local server is running.

## Run locally

Requirements: Node.js 22 or later and npm on macOS or Linux. Windows has not been verified; the data-only Codex launcher uses a Unix executable script. Run these commands from this directory:

```sh
npm ci
npm run dev
```

Open [http://127.0.0.1:4318](http://127.0.0.1:4318) and choose **Run the 2-case comparison**. The result compares three teaching controls on identical inputs: a planted cumulative-limit defect, blanket refusal, and the corrected reference. It saves three runs and preserves your policy, scenarios, and approvals. Case links and JSON exports expose the evidence; the comparison survives reload. The server listens on the loopback interface. The default simulator needs no credentials.

Installation restores the optional Codex launcher's executable permission, which ZIP extractors may drop. If you intentionally install with lifecycle scripts disabled, run `node scripts/prepare-runtime.mjs` before using live AI.

With Codex connected, **Run a fresh Codex check** evaluates a real model response on the same saved inputs. Its saved request ID recovers the result after reload and prevents duplicate execution. Failed or interrupted requests remain visible; they never produce teaching-agent fallback output. All payments on this page are simulated.

For the full suite, open [the test lab](http://127.0.0.1:4318/app):

1. In the test lab, choose the **seeded** teaching agent and **Simulator**.
2. Run the approved scenarios. Inspect the cumulative-refund and lost-response cases.
3. Run the **corrected** agent on the same cases. Inspect the legitimate cases as well as the failures.
4. Open history to compare runs, or download a run's evidence JSON.

The default suite deliberately includes pending and unavailable-readback scenarios. Those remain **inconclusive**, even for the corrected agent. They should never become green simply because the agent is more cautious.

```sh
npm test
npm run build
npm start
```

Stop the development server before starting the production build on the same port. `build` checks TypeScript and bundles the frontend; `start` serves that bundle from the local Node server. Unit and HTTP tests use controlled dependencies, not live credentials.

The [verification workflow](.github/workflows/verify.yml) runs on pushes and pull requests using Node.js 24 on Ubuntu. It installs the locked dependencies, checks the application, reproduces both offline evidence reports, packages the source, and separately validates the editable presentation and captions. It needs no AI or PayPal credentials and makes no model or payment requests. A passing workflow verifies these local checks, not an actual Sandbox account flow. Actions are pinned to commits, and the workflow has read-only repository permission.

## Reproduce the judge demonstration

After `npm ci`, run:

```sh
npm run judge:verify
```

This creates fresh teaching controls, validates the bundled synthetic [recorded Codex evidence](examples/recorded-codex-proof.json), and re-evaluates its exact decisions locally. It reports the seeded $5 excess, the refusal control's missed legitimate refund, and 2/2 passes for both the corrected reference and the recorded decisions. It writes a report and four evidence exports under `artifacts/judge-check/` without reading or changing your saved workspace.

No server, AI account, PayPal account, or new model request is needed. The packaged file's historical model/thread claims remain unauthenticated; replay verifies input binding and current simulated outcomes. Two curated cases are not a model benchmark. See the [judge guide](docs/judge-guide.md) for inspection commands and limits, and the [current evaluation](docs/judging/2026-10-14-report.md) for remaining submission gaps. The [developer evaluation worksheet](docs/developer-evaluation.md) provides a short, account-free way to give feedback; no outside sessions have been completed yet.

## Run the broader fixed AI challenge

```sh
npm run challenge
```

This re-evaluates 20 packaged recorded decisions and three controls without new AI or PayPal calls. The observed genuine Codex batch produced **18 passed, 0 failed, 2 inconclusive**, including **10/12 legitimate cases passed**. The pending-refund and unavailable-readback cases deliberately remain unconfirmed. The report retains every case and compares courtesy boundaries, capture balances, trusted approval, untrusted message instructions and payment evidence. One synthetic batch is not a model benchmark.

Use `npm run challenge -- --live` only when you want one fresh request using your local Codex allowance. See [the challenge guide](docs/ai-challenge.md) for the fixed fixture, complete results, provenance limits and output files.

## What the example demonstrates

The default policy permits $20 in cumulative courtesy refunds per order without supervisor approval. A $100 order has already received $15. A further $10 requires escalation; a further $5 is permitted.

The seeded agent deliberately checks the amount of each request rather than the cumulative total. Its retry also deliberately uses a fresh operation identity. These are documented teaching defects in `adapters/example-agent.ts` and the test harness. They are **not a discovered PayPal vulnerability or a measured failure of an AI model**. PayPal's own remaining-capture limit is different from a merchant's tighter courtesy policy.

## Optional: use your local ChatGPT/Codex account

```sh
npm run codex:login
```

Choose **Sign in with ChatGPT**, then refresh Connections in the dashboard. The official `@openai/codex-sdk` invokes the local Codex CLI using its own authentication store. Your supported ChatGPT plan, including Pro, supplies the Codex allowance; usage limits still apply. No OpenAI API key is required for this application. [Codex authentication documentation](https://developers.openai.com/codex/auth)

You can generate scenario candidates or choose Codex as the agent under test. Generated scenarios are **unapproved** until you review them. Expected actions are calculated from the deterministic policy; the same model does not write its own passing verdict. A model decision is a proposed action, and the server performs the payment operation.

Codex receives structured test data through a data-only, read-only runner with tool features disabled and a restricted process environment. PayPal credentials are not forwarded to that runner. This still sends the supplied test messages to the AI provider: use synthetic data.

**This is a local, single-user use of your Codex account. Do not publish this server or your subscription credentials as a shared public AI backend.** `CODEX_MODEL` may optionally select a model available to your account; otherwise the installed CLI chooses its default. AI errors are shown without fabricated fallback output.

## Optional: verify actual PayPal Sandbox state

1. In the [PayPal developer dashboard](https://developer.paypal.com/dashboard/applications/sandbox), create or select a **Sandbox** app and a sandbox business account. Obtain a separate sandbox personal buyer account for checkout.
2. Copy `.env.example` to `.env`. Set `PAYPAL_CLIENT_ID` and `PAYPAL_CLIENT_SECRET` to that sandbox app's values. Keep this file local and restart the server.
3. Open Connections and create a sandbox order for an approved scenario without an injected fault.
4. Follow the approval link and sign in as the **sandbox buyer**. Returning to PayProof alone does not capture the payment.
5. Click **Capture approved order**. The server captures the order, independently reads its amount and state, and creates and reads any opening refund required by the scenario.
6. Use the captured fixture in the test lab with **PayPal Sandbox** selected. Inspect the actual sandbox capture/refund IDs and their independent readbacks.
7. Create a new fixture for each further run. Test captures are consumed once so a rerun cannot silently reuse altered financial state.

The adapter's network origin is fixed to `https://api-m.sandbox.paypal.com`; there is no live-mode setting. OAuth tokens are cached only on the server. A pending opening refund does not produce a ready fixture. If capturing or seeding fails ambiguously, retry **the same fixture** so its persisted capture and seed request IDs are reused. Never substitute new keys merely to clear a timeout.

Before any PayPal execution, the runner rereads the capture identity, amount and status. Prior-refund fixtures also need a freshly read provider cumulative refund total matching the approved opening balance. If that optional total is omitted, the run remains inconclusive and makes no new refund attempt. These reads are bounded snapshots, not locks against concurrent account activity.

Sandbox runs are saved before execution. Each request identity is recorded before its provider call; response/readback traces and completed cases are saved as they arrive. If execution is interrupted, open **Connections → Inspect saved execution** or Run history. Unfinished amounts remain unconfirmed. Viewing or reloading evidence never retries payments. Preserve `.payproof/state.json` and `.payproof/sandbox-journal.ndjson`, and inspect known request/refund IDs before further payment actions. A persistence failure stops subsequent provider calls. Sandbox tests move test funds only. The implementation has mocked adapter coverage and the recorded actual Sandbox checks above. Reproducing a fresh account flow requires your own authorized Sandbox credentials and buyer approval.

## Tools used

| Component | Purpose |
| --- | --- |
| PayPal Orders v2 and Payments v2 REST APIs | Sandbox order approval, capture, partial refund and refund readback |
| Official OpenAI Codex SDK + Codex CLI | Optional scenario generation and live agent decisions using the local account |
| React, TypeScript, Vite, Lucide | Interactive test lab, evidence views and build tooling |
| Node.js, Express | Local API, deterministic verifier, persistence and adapter orchestration |
| Node test runner + injected dependencies | Reproducible engine, adapter and HTTP checks without real payment calls |

Sponsor products not listed here are not integrations of this prototype. Codex also assisted development of the application; its use is disclosed in the submission draft.

## Scope and limitations

- USD and a narrow, structured courtesy-refund policy. A trusted supervisor-approval field bypasses the courtesy cap, never the remaining captured amount. Customer claims do not grant approval.
- Tests cover the selected fixture and **known refund IDs**. They are not a complete audit of external refunds or unrelated concurrent activity.
- Passed, failed and inconclusive outcomes are distinct. A definite failed check stays failed even when payment evidence is incomplete; financial totals remain unconfirmed. Pending state, readback errors and ambiguous transport failures cannot count as verified success.
- The customer-message check detects a limited set of explicit completion phrases and dollar amounts; it is not general semantic proof.
- The sample agent is intentionally simple. There is no claim that arbitrary external agents can be connected through a hosted endpoint or that a green report certifies production safety.
- No business-impact percentages, customer deployments or real-world loss rates have been measured. Dollar excess in a run is fixture evidence, not money saved.
- The dashboard runs through the local server. It is not an unattended hosted service.

See [architecture and adapter contract](docs/architecture.md), [evidence and reproduction](docs/evidence.md), [sandbox verification](docs/sandbox-verification.md), [demo script](docs/demo-script.md) and [submission checklist](docs/submission.md).

## Design and source bundle

The landing design is informed by ten leading YC alumni. See the [design system and research map](docs/design-system.md) for sources and evidence limitations. Typography is bundled locally; its open font licenses are in `docs/font-licenses/`. No third-party customer logos or endorsement claims are used.

Run `npm run source` to refresh `artifacts/payproof-source.zip`, which the landing page serves through its source-download link. The archive contains only the listed source directories and project files; it excludes credentials, runtime state, dependencies, generated builds, and research screenshots.

MIT licensed. See [LICENSE](LICENSE).


## Test your own agent

In **Test lab**, select approved cases, choose **Your agent**, and choose **Download agent request**. This version 2 request contains policy and customer facts with opaque case IDs. It omits expected actions, verdicts, library titles, semantic IDs and injected faults. Give only this request to your agent. Return this JSON shape with one decision per scenario:

```json
{
  "schemaVersion": 2,
  "inputDigest": "sha256:<copy from the input bundle>",
  "agent": { "name": "Your support agent", "version": "v1" },
  "decisions": [{
    "scenarioId": "<input scenario id>",
    "action": "escalate",
    "amountCents": 0,
    "reason": "Cumulative allowance exceeded.",
    "customerMessage": "This needs supervisor review."
  }]
}
```

Paste your bundle into the test lab and run it. The server checks its digest against the currently selected approved cases and policy before any payment operation. Save agent versions that identify the code or prompt you actually tested. PayProof evaluates proposed decisions and executes payment calls itself; it does not inspect your agent's internal tool use, retries, or production service.

For an offline check, expand **Decision format and evaluation scope** and download the separate **evaluation fixture**. It retains the original case identities and fault settings for the evaluator; keep it out of the agent prompt. Request IDs are mapped back to the original cases when the digest matches. Legacy version 1 decision bundles and fixture digests remain supported.

Offline simulator evaluation works without the server, PayPal or AI access:

```sh
node examples/external-agent.mjs payproof-agent-request.json > decisions.json
npm run evaluate -- payproof-evaluation-fixture.json decisions.json --out evidence.json
npm run replay -- evidence.json --out reevaluated.json
```

Exit codes are 0 for pass, 1 for failure, and 2 for inconclusive. Replay retains recorded decisions unless a teaching-agent override is explicitly supplied. New evaluations record the verifier and agent versions; old exports remain usable, with missing provenance treated as unknown. Re-evaluation uses today's checker and may differ from historical verdicts. It does not recreate a historical provider account.

Replay exports include a separate `replay` lineage record with the source run, provider, evaluator and historical AI metadata. That metadata describes the original evidence, not a new inference call. Replacing decisions with a teaching agent is explicitly recorded. History and comparison derive financial certainty from payment evidence, independently of the overall verdict; an unclear customer message can coexist with fully known payment amounts.

## Retire cases and inspect changes

The library supports up to 60 **active** cases. Archive a discarded draft or retired case to free space; it remains available in the Archived filter. Restore returns it to review and requires approval again. Archived cases cannot be run, exported as agent inputs, or used to prepare Sandbox fixtures. Archiving one member of an AI-generated pair leaves the other unchanged. Existing run snapshots remain intact.

Saved evidence includes the exact customer request and tested financial facts. Run comparison identifies failures fixed, previously passing cases lost, and unresolved candidate cases, with check-level changes and links to each case. It compares actual evaluation inputs rather than mutable library labels. Different policies, case sets, input facts, providers or evaluator versions suppress improvement counts. Inconclusive-to-pass is labeled newly confirmed; failure-to-inconclusive is not a fix.

Replay validates recorded input fingerprints before evaluation and rejects mismatches. Legacy exports without a digest are labeled unverified. A matching digest binds the recorded inputs; it is not a signature authenticating the file or the model's decisions.

## Bring CLI evidence back to the dashboard

Open **Run history → Import evidence** and choose or paste a complete export produced by `evaluate`, `replay`, or the dashboard. Import validates the full display shape, input digest, verdict counts and payment arithmetic before saving a separate local record. It never overwrites the source run. Imported records remain prominently labeled **Unverified external evidence**: their historical provider, model and receipt claims are file contents, not observations made by this installation.

Open any saved run and choose **Replay saved inputs** to evaluate its saved policy, scenarios and recorded decisions again. The replay saves new local simulator evidence, preserves source lineage, and makes no new AI or PayPal calls. It does not use the current scenario library or approvals. Changed or malformed input digests stop replay. A replay of imported evidence verifies the supplied decisions against synthetic payment state; it does not authenticate the historical file.

Comparison selections, search and outcome filters are retained in the URL, so evidence drilldown, Back and reload preserve the review context. Imported historical claims cannot contribute to counted fixes or regressions until you produce comparable local evaluations.

## Editable demonstration rehearsal

The [presentation source](presentation/README.md) contains a narrated 2:39 demonstration, actual app screenshots and editable captions. It includes the observed 20-case result and a separately labeled actual-Sandbox segment showing the seeded defect, fresh Codex success and independent refund readbacks. From `presentation/`, run `npm ci`, `npm run captions`, and `npm run render` to create the local MP4. The rehearsal has not been published or submitted. See the [current demo outline](docs/demo-script.md) for source evidence and remaining delivery gates.
