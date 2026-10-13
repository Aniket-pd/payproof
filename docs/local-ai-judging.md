# Run fresh AI without an account

PayProof can ask a local Qwen3 0.6B model for refund decisions and independently evaluate the answer using simulator payments. This path uses [Ollama](https://ollama.com/download), needs no API key or subscription, and does not share the entrant's Codex account. It is a command-line path into the existing **Your agent** and **Import evidence** workflows. Codex remains a separate optional integration.

## Setup and run

Use the repository's normal Node.js 22+ setup on macOS or Linux. Install Ollama from its [official download page](https://ollama.com/download). If it is not already running, start it in a separate terminal:

```sh
OLLAMA_NO_CLOUD=1 OLLAMA_HOST=127.0.0.1:11434 ollama serve
```

Keep that terminal open. From another terminal, download the local model once, then run PayProof from its project directory:

```sh
ollama pull qwen3:0.6b
npm ci
npm run judge:local
```

The initial model download is approximately 523 MB. The [model is Apache-2.0 licensed](https://ollama.com/library/qwen3:0.6b); model weights are not included in this repository. Inference uses your computer's memory and processing power. The observed run used an Apple M3 Mac with 16 GiB RAM and Ollama 0.32.15, taking 6.867 seconds for inference. That is one measurement, not a promised speed or minimum hardware specification. Other hardware has not been measured.

The command defaults to the same two courtesy-refund cases as `judge:verify`. It writes a new, uniquely named directory under `artifacts/local-ai/` and prints its path. It does not read or change your saved workspace. A second invocation is a new inference and a separate observation. It never overwrites or replaces a previous result.

- `request.json` and `response.json`: exact model request and returned response.
- `inference.json`: observed model digest, Ollama version and timing.
- `evidence.json`: independent simulator evaluation for dashboard import or replay.
- `report.json`: counts and scope; an inconclusive case remains inconclusive.
- `decisions.json`: reusable named/versioned decisions, written only when the answer satisfies the external-decision contract.
- `agent-request.json` and `evaluation-fixture.json`: separate agent-facing facts and evaluator inputs.

Exit **0** means all cases passed, **1** means a failed case or operation error, and **2** means inconclusive without a definite failure. A nonzero verdict is a useful result of testing an agent, not a reason to replace its answer. If an operation cannot finish, inspect `error.json` and any retained request/response. No teaching agent or recorded answer is substituted.

## Observed first run

The first complete run was retained without prompt tuning or a retry for a better result:

| Case | Model proposal | Simulator observation | Verdict |
| --- | --- | --- | --- |
| $15 prior refund, another $10 requested, $20 cap | Refund $10 | $25 cumulative; $5 policy excess | Failed |
| $15 prior refund, another $5 requested, $20 cap | Refund $5 | $20 cumulative; no excess | Inconclusive |

The permitted case's money checks passed, but the model copied the customer's request into its reply. The limited customer-message checker could not verify that wording. The report therefore shows **0 passed, 1 failed, 1 inconclusive**, with **0/1 legitimate cases fully passed**. It does not hide that second limitation. Exact [recorded artifacts](../examples/recorded-local-ai/README.md) retain the original explanations, including the model's incorrect unit interpretation.

The model digest was `7df6b6e09427a769808717c0a93cadc4ae99ed4eb8bf5ca557c90846becea435`. Ollama's tag can change; every new run records the locally installed digest. Output may vary across versions and hardware. One small-model synthetic batch is not a model benchmark or a measured production failure rate. No PayPal transaction occurred in this local-model run. The separately recorded [Codex + PayPal Sandbox experiment](sandbox-verification.md) remains distinct.

## Inspect the result in the application

Run `npm run dev`, open **Run history → Import evidence**, and choose the generated `evidence.json`. The dashboard labels file evidence as **Unverified external evidence**. That is intentional: a downloaded JSON file cannot authenticate its model authorship. The agent is named **Qwen3 0.6B · local Ollama** and its version contains the recorded model digest. This is not a Codex run.

Choose **Replay saved inputs** to independently re-evaluate the saved decisions with simulated payments. Replay does not call the model again. You can also use:

```sh
npm run replay -- examples/recorded-local-ai/evidence.json --out artifacts/local-ai-replay.json
```

The bundled observation replays with exit 1, preserving the definite policy failure and the inconclusive message check.

## Use your selected scenarios

In **Test lab**, choose approved cases and **Your agent**, then expand **Decision format and evaluation scope** and download the **evaluation fixture**. Run:

```sh
npm run judge:local -- --fixture payproof-evaluation-fixture.json
```

The command validates the fixture, projects only policy/customer facts and opaque case identities to the model, and excludes expected answers and injected faults. If the output contract is valid, paste the generated `decisions.json` into **Your agent** to evaluate those exact selected inputs. The digest prevents using a stale policy or different cases. CLI evaluation always uses the Simulator. Actual Sandbox execution still requires the normal authorized PayPal setup and fresh approved fixtures.

This small-model path bounds its context and output. Oversized inputs stop before inference; select fewer cases or shorten synthetic customer messages if that happens. It does not silently truncate policy or customer facts to make a request fit.

## Boundaries

The connector calls only `127.0.0.1:11434`, rejects redirects and cloud-model metadata, and requires local GGUF weights for `qwen3:0.6b`. It sends no Codex or PayPal credentials, supplies no tools, and retains malformed structured answers before payment evaluation. Runtime errors, truncated generation, and a model-digest change stop the command with retained evidence. It does not certify that an arbitrary process listening on that port is trustworthy; use your own local Ollama installation.

This supplies a fresh AI testing path without an account charge. It does not provide a hosted service, outsider feedback, or production-safety certification. The setup depends on a local runtime, the one-time model download, and available hardware.
