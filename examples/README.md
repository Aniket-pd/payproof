# Bring your own decision component

For a one-command reproduction of the demonstration and bundled recorded AI decisions, see [the judge guide](../docs/judge-guide.md) or run `npm run judge:verify`. `recorded-codex-proof.json` contains synthetic inputs and simulator payments; its model/thread history is an external file claim when distributed. It contains no account credentials.

This small external program imports no PayProof engine code. It reads the same input bundle your own agent would receive and writes proposed decisions. It is a deterministic contract example, not a model evaluation or a production refund agent.

1. In Test lab select only the cumulative-over and cumulative-exact cases, keep **Simulator** selected, and choose **Your agent**. Use the default $20 policy for the outcomes below.
2. Choose **Download agent request** and save it as `payproof-agent-request.json` in the project directory. Expand **Decision format and evaluation scope**, choose **Download evaluation fixture**, and save that separate file as `payproof-evaluation-fixture.json`. Do not change the policy or selected cases between these downloads.
3. Run the example twice against the same agent request. Evaluate each decision file using the evaluation fixture:

```sh
node examples/external-agent.mjs payproof-agent-request.json --ignore-prior > before.json
node examples/external-agent.mjs payproof-agent-request.json > after.json
npm run evaluate -- payproof-evaluation-fixture.json before.json --out before-evidence.json
npm run evaluate -- payproof-evaluation-fixture.json after.json --out after-evidence.json
```

The first evaluation should fail for the default $20 policy ($15 already refunded plus a new $10). The second should pass both cases, including the permitted $5 refund. `evaluate` returns exit 1 for a failure; run the next command separately if your shell stops on errors. Different policies or selected cases can produce different results.

The schema-2 request contains only the agent-facing facts and opaque case IDs. The schema-1 evaluation fixture retains evaluator-only identities and fault settings. Give only the request to the decision component; keep the fixture for the evaluator. Passing the request directly to `evaluate` produces `Unsupported agent input schemaVersion`. These filenames are distinct intentionally.

Paste either decision JSON into Your agent in the browser to save and compare those runs. Replace the decision function with a call to your actual agent and identify its real prompt/code version. Keep the exact input digest and one decision per case.

PayProof owns payment execution and retry behavior in this flow. It checks the decision contract against simulated or PayPal Sandbox records; it does not observe your agent's internal tools. Never include credentials, personal customer records or fabricated payment receipts in the bundle.
