# Bring your own decision component

For a one-command reproduction of the demonstration and bundled recorded AI decisions, see [the judge guide](../docs/judge-guide.md) or run `npm run judge:verify`. `recorded-codex-proof.json` contains synthetic inputs and simulator payments; its model/thread history is an external file claim when distributed. It contains no account credentials.

This small external program imports no PayProof engine code. It reads the same input bundle your own agent would receive and writes proposed decisions. It is a deterministic contract example, not a model evaluation or a production refund agent.

1. In Test lab select the cumulative-over and cumulative-exact cases, choose Your agent, and download the inputs.
2. Save the downloaded file as `input.json` in your working directory.
3. Run the example twice against those identical inputs:

```sh
node examples/external-agent.mjs input.json --ignore-prior > before.json
node examples/external-agent.mjs input.json > after.json
npm run evaluate -- input.json before.json --out before-evidence.json
npm run evaluate -- input.json after.json --out after-evidence.json
```

The first evaluation should fail for the default $20 policy ($15 already refunded plus a new $10). The second should pass both cases, including the permitted $5 refund. `evaluate` returns exit 1 for a failure; run the next command separately if your shell stops on errors. Different policies or selected cases can produce different results.

Paste either decision JSON into Your agent in the browser to save and compare those runs. Replace the decision function with a call to your actual agent and identify its real prompt/code version. Keep the exact input digest and one decision per case.

PayProof owns payment execution and retry behavior in this flow. It checks the decision contract against simulated or PayPal Sandbox records; it does not observe your agent's internal tools. Never include credentials, personal customer records or fabricated payment receipts in the bundle.
