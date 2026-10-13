# Submission preparation

This is a draft checklist, not a submitted entry. Recheck the [official rules](https://paypalaihackathon.devpost.com/rules) before submission; checked on 13 October 2026. The currently published deadline is **12 November 2026 at noon Pacific** (13 November, 01:30 IST). See [sourced research](judging/2026-10-13-research.md) for rules, judge backgrounds and related winners.

## Official requirements to satisfy

- [ ] Build a working application combining PayPal Sandbox with AI; PayPal must be central.
- [ ] Publish a public source repository with its open-source license, setup instructions and necessary assets.
- [ ] Provide a functional hosted demo or complete instructions for running the project.
- [ ] Supply an English project description explaining functionality and tools.
- [ ] Upload a publicly visible YouTube demonstration under three minutes showing the application working.
- [ ] Provide free judging access and explain any required special access.
- [ ] Confirm eligibility, ownership, third-party licenses and the final deadline against the rules.

The five criteria—implementation, design, impact, innovation and presentation—are equally weighted. Sponsor tools are optional; claim a sponsor category only for a real integration. [Official rules](https://paypalaihackathon.devpost.com/rules)

## PayProof readiness

- [x] MIT license included locally.
- [x] Local setup and mode-specific instructions written.
- [x] Seeded faults and evidence boundaries disclosed.
- [ ] Actual PayPal Sandbox path verified with approved buyer and exported readback evidence.
- [x] Local Codex integration smoke-tested with ChatGPT sign-in, without an API key.
- [x] Save genuine AI-generated candidates and an exported AI run for the final demonstration (local simulator payment evidence; see `verification.md`).
- [x] One-action comparison of over-refund, blanket refusal and correct behavior on the same inputs, with saved case/export links.
- [x] Fresh Codex comparison and persisted request recovery verified; the two-case call passed 2/2, including 1/1 legitimate case, with simulator payments.
- [x] Fixed 20-case genuine Codex challenge and complete offline replay: 18 pass, 0 fail, 2 inconclusive; 10/12 legitimate cases passed. Synthetic single-batch scope is documented in `ai-challenge.md`.
- [x] Interrupted Sandbox execution evidence survives a forced process stop with mocked providers; actual PayPal execution remains a separate gate.
- [x] Portable synthetic AI export and one-command judge reproduction: `npm run judge:verify`; see `judge-guide.md` for provenance limits.
- [x] Source package: clean install, automated suite, TypeScript and production build verified; see `verification.md` for the final test count and evidence.
- [ ] Customer or developer feedback collected; replace any hypothetical impact claim with evidence.
- [ ] Public repository created and checked for secrets and generated account artifacts.
- [x] Isolated public-source candidate and read-only, pinned CI prepared; clean installation and all workflow commands verified locally. Publication and remote CI remain pending.
- [x] Editable local 2:38 demonstration rehearsal prepared with app captures, recorded real-AI evidence, captions and explicit Sandbox/mock disclosures. See `presentation/README.md`.
- [ ] Final actual-Sandbox demonstration published publicly on YouTube and checked in a signed-out browser.
- [ ] Reviewer access arranged for optional live AI without publishing a subscription token or exposing the local authenticated server.
- [ ] Devpost form completed and explicitly submitted by the entrant.

The simulator is available without an account. Full interactive AI uses an authorized local Codex account; the final entry must explain reviewer access to that functionality. PayPal Sandbox needs a test app and buyer approval. Do not present those dependencies as already solved by a working simulator.

## Draft description

**PayProof Refunds** is a local release-testing workbench for developers building refund agents. An agent can stay below the original purchase amount while violating a merchant's smaller cumulative-refund allowance. A repeated request can also use a new operation identity and produce an unintended second refund.

PayProof pairs eligible and ineligible scenarios, runs a documented teaching agent, a corrected reference, a live Codex decision component, or named/versioned external decisions, and checks the result against structured merchant policy. The PayPal adapter creates sandbox orders, captures approved payments, seeds controlled prior refunds and independently reads known refund IDs. The report distinguishes attempts, confirmed completion and unresolved evidence. AI can propose additional scenarios for human review.

The opening comparison makes a critical distinction visible: a solution that refuses every customer also fails. A reviewer can reproduce the controls and re-evaluate bundled recorded AI decisions with one local command, without account access. A fresh inference is separately labeled and recorded. The current demonstration uses simulator payments; the actual PayPal account flow remains unverified.

The initial scope is USD courtesy refunds and controlled fixtures. Seeded defects demonstrate test sensitivity; they are not claims about model failure rates or PayPal vulnerabilities. Results do not certify production safety. The next validation step is to test the workflow with developers integrating their own refund agents and measure time to a useful reproducible failure.

**Build disclosure:** Codex assisted development. Optional runtime AI uses the official OpenAI Codex SDK and local CLI authentication. PayPal integration uses Orders v2 and Payments v2 REST APIs; the interface uses React, TypeScript and Vite, with a Node/Express local server. No sponsor tool integration is claimed unless listed in the README.

Before publishing, replace future/conditional language with verified observations where evidence exists. Add the actual repository URL, public video URL, final build instructions, and an honest account of what was built during the hackathon.
