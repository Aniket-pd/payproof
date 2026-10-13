# Submission preparation

This is a draft checklist, not a submitted entry. Recheck the [official rules](https://paypalaihackathon.devpost.com/rules) before submission; checked on 13 October 2026. The currently published deadline is **12 November 2026 at noon Pacific** (13 November, 01:30 IST). See [sourced research](judging/2026-10-13-research.md) for rules, judge backgrounds and related winners.

## Official requirements to satisfy

- [x] Build a working application combining PayPal Sandbox with AI; actual two-case Codex + Sandbox run observed (see `sandbox-verification.md`).
- [x] Public source with MIT license, setup instructions and necessary assets: [Aniket-pd/payproof](https://github.com/Aniket-pd/payproof); anonymous cloning verified.
- [x] Complete local setup instructions are publicly available in the README and judge guide. Fresh Ubuntu CI passes; no hosted live-AI demo is claimed.
- [x] English functionality/tools description is available in this public source. The Devpost form itself remains unsubmitted.
- [ ] Upload a publicly visible YouTube demonstration under three minutes showing the application working.
- [x] Provide free local judging access: [Ollama + Qwen3 setup](local-ai-judging.md), fresh decisions and dashboard import, with no API key or paid account. Runtime/model download and local compute are required; no hosted service is claimed.
- [ ] Confirm eligibility, ownership, third-party licenses and the final deadline against the rules.

The five criteria—implementation, design, impact, innovation and presentation—are equally weighted. Sponsor tools are optional; claim a sponsor category only for a real integration. [Official rules](https://paypalaihackathon.devpost.com/rules)

## PayProof readiness

- [x] MIT license included locally.
- [x] Local setup and mode-specific instructions written.
- [x] Seeded faults and evidence boundaries disclosed.
- [x] Actual PayPal Sandbox path verified with five fresh approved captures, three teaching-control cases and a two-case Codex batch; exact exports retained.
- [x] Local Codex integration smoke-tested with ChatGPT sign-in, without an API key.
- [x] Save genuine AI-generated candidates and an exported AI run for the final demonstration (local simulator payment evidence; see `verification.md`).
- [x] One-action comparison of over-refund, blanket refusal and correct behavior on the same inputs, with saved case/export links.
- [x] Fresh Codex comparison and persisted request recovery verified; the two-case call passed 2/2, including 1/1 legitimate case, with simulator payments.
- [x] Fixed 20-case genuine Codex challenge and complete offline replay: 18 pass, 0 fail, 2 inconclusive; 10/12 legitimate cases passed. Synthetic single-batch scope is documented in `ai-challenge.md`.
- [x] Interrupted Sandbox execution evidence survives a forced process stop with mocked providers; actual PayPal execution remains a separate gate.
- [x] Portable synthetic AI export and one-command judge reproduction: `npm run judge:verify`; see `judge-guide.md` for provenance limits.
- [x] Source package: clean install, automated suite, TypeScript and production build verified; see `verification.md` for the final test count and evidence.
- [ ] Customer or developer feedback collected; replace any hypothetical impact claim with evidence. The [participant worksheet](developer-evaluation.md) and [predefined evaluation guide](developer-evaluation-guide.md) are prepared; no sessions have been completed.
- [x] Public repository created; all 181 anonymously cloned files match the reviewed allowlist. Credentials and private runtime artifacts are excluded.
- [x] Read-only, pinned CI passed on GitHub's Ubuntu runner: 182 tests, TypeScript/build, both offline reports, packaging and presentation checks. [Initial successful run](https://github.com/Aniket-pd/payproof/actions/runs/38460136404).
- [x] Editable local 2:39 demonstration updated with app captures, recorded AI evidence, captions and separately labeled actual Sandbox results. See `presentation/README.md`.
- [ ] Final actual-Sandbox demonstration published publicly on YouTube and checked in a signed-out browser.
- [x] Fresh local AI available for reviewers through the published `judge:local` command and setup guide, without sharing subscription credentials.
- [ ] Devpost form completed and explicitly submitted by the entrant.

The simulator is available without an account. The published [local-model path](local-ai-judging.md) also generates fresh AI decisions without an account or API key, then brings its evidence into the dashboard. It requires Ollama, a model download and local compute. The direct Codex buttons still use an authorized local Codex account. PayPal Sandbox needs a free test app and buyer approval. Anonymous access to all 194 files of the revised source and [188-test CI](https://github.com/Aniket-pd/payproof/actions/runs/38463647640) are verified.

## Draft description

**PayProof Refunds** is a local release-testing workbench for developers building refund agents. An agent can stay below the original purchase amount while violating a merchant's smaller cumulative-refund allowance. A repeated request can also use a new operation identity and produce an unintended second refund.

PayProof pairs eligible and ineligible scenarios, runs a documented teaching agent, a corrected reference, a live Codex decision component, or named/versioned external decisions, and checks the result against structured merchant policy. The PayPal adapter creates sandbox orders, captures approved payments, seeds controlled prior refunds and independently reads known refund IDs. The report distinguishes attempts, confirmed completion and unresolved evidence. AI can propose additional scenarios for human review.

The opening comparison makes a critical distinction visible: a solution that refuses every customer also fails. A reviewer can reproduce the controls and re-evaluate bundled recorded AI decisions with one local command, without account access. A fresh inference is separately labeled and recorded. The opening comparison uses simulator payments. A separate observed Sandbox experiment reproduced the seeded $5 excess, passed both corrected controls, and passed a fresh two-case Codex batch with independent refund readbacks. Exact exports are included; replay does not authenticate their historical provider claims.

The initial scope is USD courtesy refunds and controlled fixtures. Seeded defects demonstrate test sensitivity; they are not claims about model failure rates or PayPal vulnerabilities. Results do not certify production safety. The next validation step is to test the workflow with developers integrating their own refund agents and measure time to a useful reproducible failure.

**Build disclosure:** Codex assisted development. Optional runtime AI uses the official OpenAI Codex SDK and local CLI authentication. PayPal integration uses Orders v2 and Payments v2 REST APIs; the interface uses React, TypeScript and Vite, with a Node/Express local server. No sponsor tool integration is claimed unless listed in the README.

An additional local judging path uses Ollama with Qwen3 0.6B and requires no account or API key. Its first retained two-case response produced a $5 simulated policy excess and an inconclusive customer-message check. The result demonstrates detection on one small-model synthetic batch; it is not a benchmark or a production failure rate. The recorded Codex + actual PayPal Sandbox experiment remains separate.

Repository URL: [https://github.com/Aniket-pd/payproof](https://github.com/Aniket-pd/payproof). The judge-access instructions are [publicly available](https://github.com/Aniket-pd/payproof/blob/main/docs/local-ai-judging.md). Before submitting the entry, add the public video URL and an honest account of what was built during the hackathon. Keep unverified outcomes conditional.
