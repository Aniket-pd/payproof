# Problem evidence and intended use

PayProof is intended for the developer responsible for a PayPal refund agent's decision component. Before changing its prompt, model or decision code, that developer needs to establish which approved refund cases still work, which policy violations appear, and which payment observations remain unresolved. This is the proposed audience and workflow; no outside developer has yet validated its usefulness.

## Independent evidence for the problem

PayPal's refund integration guide describes partial refunds and recommends cumulative tracking, idempotency, logging and approval thresholds. Those are concrete engineering concerns behind PayProof's controlled cases. PayProof's $20 courtesy allowance is an illustrative merchant rule, not a PayPal requirement. [PayPal refund guide](https://developer.paypal.com/checkout/refund-payment), checked 14 October 2026 IST.

PayPal's agent-toolkit quickstart addresses developers connecting commerce operations to agent frameworks and recommends Sandbox testing, typed validation and traceability. This establishes a relevant developer workflow; it does not establish demand for PayProof or an integration between PayProof and the toolkit. PayProof currently uses PayPal REST APIs directly. [PayPal toolkit quickstart](https://developer.paypal.com/community/blog/quickstart-guide-agent-toolkit/).

The original 2024 τ-bench paper evaluates tool-using agents against business policies by checking resulting database state and repeated-trial consistency. It provides independent research context for checking outcomes as well as answers. PayProof has not run that benchmark and makes no comparison with its scores, historical models or broader conversational coverage. [Yao et al., τ-bench](https://arxiv.org/abs/2406.12045).

## The specific workflow PayProof supports

1. Approve structured merchant policy and synthetic eligible/ineligible cases.
2. Give the decision component opaque customer/order facts through the external-agent request contract.
3. Evaluate its proposed actions, using simulator payments first and separately prepared Sandbox fixtures when needed.
4. Inspect policy checks, attempted amounts, independently observed refunds and unresolved evidence. Preserve permitted refunds as well as checking excessive ones.
5. Save the agent version and export; compare compatible inputs after a change, and retain the failure for reproduction.

PayProof orchestrates the test payment operations itself. Its external-agent contract receives proposed decisions; it does not inspect an arbitrary production agent's internal conversations, tool calls or retry loop. The release artifact is evidence for the tested contract and fixtures. A production integration still needs its own authorization and enforcement.

## What has been demonstrated

| Question | Retained observation | What it establishes |
| --- | --- | --- |
| Can the checker expose a model's excessive proposal? | The first local Qwen3 0.6B response proposed $10 after $15 under the $20 allowance; simulation reported $5 excess. | Detection in one small-model synthetic batch. The other case remained inconclusive. [Exact output](../examples/recorded-local-ai/README.md). |
| Does the PayPal adapter obtain actual provider evidence? | Five controlled Sandbox cases across the seeded control, corrected controls and a fresh Codex batch have independent readbacks. | The observed standard-processing integration path. [Sandbox record](sandbox-verification.md). |
| Does refusing everything count as a successful release? | The refusal control fails the permitted case; the corrected teaching control preserves it. | The demonstration checks useful behavior as well as policy rejection. [Judge reproduction](judge-guide.md). |
| Can another person inspect the result without paid access? | Public source, offline replay and a fresh local-model path are available. | Reproducible inspection and account-free local inference, subject to documented setup. [Local AI setup](local-ai-judging.md). |

These observations do not measure avoided losses, time saved, customer adoption or production reliability. Synthetic policy excess is a test result, not money saved.

## Existing approaches and the proposed role

Broad agent benchmarks already test policy adherence. Commercial monetary controls also exist: AgentsPay describes per-transaction caps, cumulative budgets and approval rules evaluated before spending. That is the vendor's description, not an independently audited capability assessment. We have not tested AgentsPay, integrated it or established comparative performance. [AgentsPay spend controls](https://agentspay.ai/features/spend-controls).

PayProof's proposed role is a small, inspectable release-testing workflow for a PayPal refund decision component: paired cases, explicit financial uncertainty, controlled Sandbox readbacks and portable evidence. The combination is the design hypothesis. No claim is made that policy checking, agent evaluation, spending limits or payment audit logs are individually new.

## Evidence still needed

The next meaningful impact test is the prepared [outside-developer evaluation](developer-evaluation.md), using the [predefined protocol](developer-evaluation-guide.md). Record setup failures, time to a useful reproducible finding, necessary help, preserved legitimate refunds and whether the developer would use the result before a release. Report unfavorable observations too. A small usability session cannot establish time saved without a valid comparison, and stated interest is not adoption.

The published sources support the problem's relevance. They do not supply PayProof customer feedback. Potential Impact remains **7/10** and the overall internal estimate remains **40.5/50** until stronger evidence warrants a change.
