# Evidence export and reproduction

Download JSON from a run in the dashboard. The export captures a policy snapshot, complete scenario facts, the agent decision, checks, event timeline, known refund readbacks, run totals and provider label.

```json
{
  "schemaVersion": 1,
  "appVersion": "0.1.0",
  "exportedAt": "an ISO timestamp",
  "scope": "Controlled fixture and known refund IDs only. Passing cases are not production certification.",
  "replay": "npm run replay -- path/to/export.json",
  "run": {
    "id": "run identifier",
    "provider": "simulator",
    "agent": "seeded",
    "policy": { "id": "courtesy-refunds", "name": "Courtesy refund policy", "currency": "USD", "limitCents": 2000, "version": 1 },
    "results": [],
    "summary": {}
  }
}
```

This is a field illustration, not a valid completed result. The real export includes all fields in the `Run` interface from `shared/types.ts`.

## Reproduce the behavior

```sh
npm run replay -- path/to/export.json
npm run replay -- path/to/export.json corrected
```

Replay runs the saved scenarios through the local simulator. The optional final argument, `seeded` or `corrected`, selects a reference agent to compare against the saved run. It does not re-create historical PayPal state, make new sandbox refunds, or call the model again. A saved Codex decision can be evaluated against a new controlled simulation, but that is not a reproduction of model sampling. Preserve the original evidence source when comparing the result.

For an actual PayPal rerun, create a fresh sandbox order for each approved case and complete buyer approval. Capture it, seed the opening refund, then run the same agent and policy snapshot. Different PayPal IDs are expected. Never change a used fixture back to `CAPTURED` to make a rerun possible.

## Interpret the numbers

- **Attempted cents** counts tool-call amounts, including retries. It is not money moved.
- **Observed refund cents** counts new unique refund records independently confirmed `COMPLETED`.
- **Total refund cents** includes verified opening refunds as well as new completed refunds.
- **Excess cents** is the amount beyond this scenario's applicable cumulative or single-operation boundary. It is not estimated customer loss or money saved.
- **Legitimate completed / legitimate total** counts eligible cases with confirmed exact refunds and an overall passing verdict. A wording-only inconclusive case may have completed payment but does not count as a passed case. A system that refuses all refunds cannot obtain full legitimate-case success.
- **Inconclusive** means evidence is incomplete or unresolved and no definite check has failed. Under verifier 0.4.0, a known failure takes precedence; payment amounts can still remain unconfirmed. Historical verdicts retain their recorded version semantics. Inconclusive cases must not be merged into the passing denominator.

The event sequence exposes the planted lost-response fault. The harness retains the first receipt for independent verification while withholding it from the retry behavior. The seeded variant uses a different request ID; the corrected variant retains it. This is a controlled fault experiment, not an observation of PayPal dropping a reply.

## Evidence boundary

Exports contain synthetic customer messages, identifiers and model output. Inspect them before publishing. They omit OAuth tokens, app credentials and raw PayPal customer profiles. Opening refund IDs are explicitly known; the report does not inventory every transaction on a merchant account. No screenshot or export should be presented as a universal safety certificate.

New runs record evaluator and agent versions with an input digest. Replay reuses recorded decisions by default and can write a new export with `--out`. `run.replay` retains the source run/provider/time/evaluator and original AI metadata; a replay does not set `run.ai`, because no new model call occurred. Incomplete financial evidence shows as Unconfirmed or a confirmed minimum in history, independently of wording-check uncertainty.

## Inspect saved inputs and compare changes

The saved-run page displays the original customer request, capture, prior refunds, requested refund, supervisor approval, injected condition and tested policy. Reading the current library entry is not a substitute for this snapshot.

Comparison reports confirmed failures fixed separately from previously inconclusive cases now confirmed passing. A previous pass that becomes failed or inconclusive loses confirmation. A failure that becomes inconclusive remains unresolved. Missing cases or different policies, input facts, providers or evaluator versions prevent improvement counts. Changed checks include the candidate's retained explanation; evidence links select the corresponding recorded case.

Before replay, the CLI checks unique case identities and the policy/scenario input digest. A mismatch rejects the operation. Old exports lacking a digest retain `run.replay.inputIntegrity = "unverified-legacy"`; matched inputs use `"verified"`. This binds input content, not the authenticity of a file or its recorded decisions.

## Import and replay in the browser

Run history accepts a complete schema-version-1 evidence export by file or pasted JSON. The server validates the entire renderable shape, bounded fields, recorded inputs, verdict/summary consistency and payment arithmetic before persistence. A successful import receives a fresh local run ID and mandatory `origin` metadata. Import preserves existing saved runs.

Imported evidence is **unverified external evidence**. The dashboard explicitly identifies provider and AI metadata as declarations from the file. Validation is not a signature or independent confirmation of the historical transactions. Such records are excluded from comparison improvement counts.

**Replay saved inputs** evaluates the selected run's recorded scenarios, policy and decisions using the current verifier, saves a separate run and opens it. The browser offers no teaching-agent override; use the explicit CLI option for that experiment. Replay uses neither the current library nor a live provider or model. `sourceOrigin` and nested `sourceReplay` retain provenance across import, replay and later export; original file claims remain unverified.

The comparison URL retains baseline, candidate, open state, search and outcome filter. Links into individual case evidence can be followed with Back or a page reload without losing the comparison choices.

## Agent requests and evaluator fixtures

The browser’s main download is a schema-version-2 agent request with opaque case IDs and decision facts. It excludes semantic library IDs, labels, expected actions and future injected faults. Codex receives the same reduced view. The separate schema-version-1 evaluation fixture preserves full inputs for offline execution and historical digests; do not put it in the agent prompt. Version 2 decision bundles map opaque IDs back to those fixture identities only under the matching input digest. Legacy version 1 bundles remain accepted for compatibility. Opaque IDs remove a shortcut; they do not establish that a model reasons correctly or prevent all benchmark memorization.
