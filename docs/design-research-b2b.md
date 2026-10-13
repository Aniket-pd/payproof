# Landing-page research: Stripe, Dropbox, GitLab, Replit

Inspected October 9, 2026. These are four selected leading YC alumni from the wider ten-company study, **not a valuation ranking**.

## Method and evidence boundaries

- Opened all four current official homepages with the web reader and studied their live document content, navigation, conversion actions, product examples, and story sequence.
- Consulted official public brand/design documentation where available. Brand guidelines describe intended rules; they do not prove every rule is applied on the current homepage.
- This subagent's direct CUA attempt was unavailable, but the root agent successfully captured all four current landing pages. I then visually inspected the four saved 1280×720 screenshots under `artifacts/yc-design-research/`. No existing PayProof browser tab was manipulated by this subagent. Visual observations below refer to those captures; webpage document content supplies the longer story sequence.
- Screenshots: [Stripe](../artifacts/yc-design-research/stripe.jpg), [Dropbox](../artifacts/yc-design-research/dropbox.jpg), [GitLab](../artifacts/yc-design-research/gitlab.jpg), [Replit](../artifacts/yc-design-research/replit.jpg). Stripe's browser visit redirected to its India homepage, while the web-reader content came from its global homepage. Their conversion language differs; that is localization, not an assumed universal CTA.
- No complete proprietary design system is claimed. Exact values below are either explicitly published brand values or clearly labeled PayProof proposals. Historical design essays are labeled with their date and used for principles, not as proof of the current page.

## 1. Stripe

**Current content observed.** The first message promises revenue growth through financial infrastructure; the next sentence defines its scope. Self-serve signup is prominent, with sales as a separate route. The narrative expands through business-model capabilities, operational scale, named customer examples, startup/platform use cases, developer integration choices, and a closing conversion area. Examples describe product outcomes and implementation contexts, not only generic feature labels. [Current homepage](https://stripe.com/)

**Rendered first screen observed.** The India variant uses a broad, left-aligned multiline sans statement: dark first sentence, muted continuation, roughly 42–44px at this viewport. Content begins about 135px from the left. A saturated flowing-ribbon visual crosses the upper-right area. Fine outer grid lines and a bordered customer-logo rail structure the canvas. The primary hero invitation button is compact, filled violet, about 48px tall, with nearly square corners; sales is also visible in navigation. [Inspected capture](../artifacts/yc-design-research/stripe.jpg)

**Why the structure works — interpretation.** The first screen answers the commercial question; subsequent sections progressively support technical and purchasing decisions. Product representations and specific customer outcomes carry the proof burden. Different buyer sophistication levels have separate paths rather than one ambiguous CTA.

**Documented design principle.** A 2017 first-party engineering essay explains a story-first approach to product landing pages and a flexible CSS Grid implementation instead of fragile decorative positioning. This is historical evidence of method, not a measurement of the 2026 homepage. [Stripe design/engineering essay](https://stripe.com/blog/connect-front-end-experience)

**For PayProof.** Lead with the business outcome—finding refund mistakes before deployment—then show the actual decision/evidence distinction. Use a single primary “Open test lab” action and a lower-emphasis “See how it works” anchor. Organize three proof modules around policy correctness, duplicate protection, and verified payment state. The technical integration story belongs after the first concrete example.

**Limits:** approximate dimensions are screenshot estimates, not computed CSS. Exact typeface and motion timing were not measured. This research corroborates a current ribbon treatment; copying it would still be the wrong way to give PayProof its own identity.

## 2. Dropbox

**Current content observed.** The page begins with a plain-language promise about reducing work and a free-trial action. A desktop/mobile product image follows. Its content moves through social proof, AI integration, finding content, keeping it organized, sharing, security, industries, and learning resources. The main conversion action repeats across the workflow sections. [Current homepage](https://www.dropbox.com/)

**Rendered first screen observed.** A white navigation bar sits above a warm cream hero. The left half contains a two-line, bold sans headline around 40px, supporting copy around 21px, and a large rounded blue CTA. The right half is dominated by a readable desktop interface with a phone overlapping its foreground. Product frames have restrained rounding and soft shadow. Generous empty space separates navigation, headline, and product. The hero is not divided into many cards. [Inspected capture](../artifacts/yc-design-research/dropbox.jpg)

**Published identity, not inferred pixels.** Dropbox's official palette groups colors into core, accent, and gray roles. Its core includes Blue `#0061FE`, Coconut `#F7F5F2`, and Graphite `#1E1919`. Typography guidance describes a custom DB Sharp Grotesk family with variable headline treatment. We should learn the role separation and type hierarchy, not borrow a proprietary font. [Color guidance](https://brand.dropbox.com/color) · [Typography guidance](https://brand.dropbox.com/typography)

**Documented strategy.** The framework emphasizes human warmth, clarity, an obvious next action, and small moments of delight. Motion guidance recommends purposeful movement, immediate feedback, and explanation rather than excessive spectacle. Those are published principles; live homepage animation was not observed. [Framework](https://brand.dropbox.com/framework) · [Motion](https://brand.dropbox.com/motion)

**For PayProof.** Preserve warm paper/ink surfaces, but make body copy genuinely readable. Tell the flow through verbs: define policy → challenge agent → inspect evidence. Use one large, legible product example rather than many small ornamental panels. Keep the next action visible after the explanation. A short counterexample animation can teach cumulative refunds; it should be manually replayable and respect reduced motion.

**Limits:** typography scale and spacing are visual estimates. Exact computed radius and below-fold carousel behavior were not measured.

## 3. GitLab

**Current content observed.** The page positions speed and control together in agentic engineering. A free trial is the primary entry. Three capability groups cover AI orchestration, platform consolidation, and built-in security. A numbered sequence then explains shared context, governance, and auditability. Industry outcomes, attributed customer stories, current product news, and final CTAs follow. It includes a product image described as an agent session with its activity feed. [Current homepage](https://about.gitlab.com/)

**Rendered first screen observed.** Dark charcoal-purple, a subtle dot texture, and fine vertical rules support an exceptionally large, bold, two-line white headline—approximately 84px. Its left edge aligns with short supporting copy and a broad rectangular CTA. The CTA contains restrained warm-to-purple color, while the header trial button is white. A narrow announcement band appears above navigation. Large type, alignment, and whitespace carry the page; decorative cards do not. [Inspected capture](../artifacts/yc-design-research/gitlab.jpg)

**Published typography.** GitLab Sans is the primary family, with Inter as a fallback. Brand guidance defaults to left-aligned, sentence-case, solid-colored copy. It distinguishes compact headline leading from more open body leading and reserves mono type for secondary labels, snippets, and data. This is a useful hierarchy principle, not a reason to turn PayProof's whole page into terminal typography. [Brand typography](https://design.gitlab.com/brand-design/typography/)

**Published color.** Charcoal `#171321` and white carry most copy and CTA roles; accent colors have specific functions. The documentation explicitly stresses readable contrast, including 4.5:1 for regular text. Its purple/orange palette belongs to GitLab; PayProof should keep its own restrained accent. [Brand color](https://design.gitlab.com/brand-design/color/)

**For PayProof.** Explain trust through mechanisms: a human-approved expectation, an agent decision, and independently observed transaction state. Numbered steps and an actual trace can communicate this better than an abstract “AI safety” illustration. Separate reassuring promises from inspectable evidence. Avoid unsupported compliance or certification claims.

**Limits:** transitions and below-fold geometry were not rendered in this pass. Pajamas distinguishes brand guidance from product UI guidance; inspecting the homepage is not equivalent to learning the entire system. [Pajamas overview](https://design.gitlab.com/)

## 4. Replit

**Current content observed.** The homepage begins with an invitation to build, then exposes product creation choices and example prompts near that entry. The narrative progresses into product capabilities, infrastructure/integrations/security, attributed user stories, plans, and another start action. The action itself teaches what the product does before a long feature explanation. [Current homepage](https://replit.com/)

**Rendered first screen observed.** A warm neutral canvas holds a centered sans headline around 60px after substantial whitespace. Under a short subline sits the actual wide prompt interface: pale surface, thin warm border, softly rounded corners, understated submit control. Small creation-type buttons and starter examples reduce the blank-page problem. The orange brand color is concentrated in the wordmark and navigation CTA. The product interaction is the hero visual, with no giant stock illustration. [Inspected capture](../artifacts/yc-design-research/replit.jpg)

**Published design-system approach.** Replit's RUI essay describes tokens composed into utilities, components, patterns, and guidance. It advocates meaningful role names for foreground/background/outline values and a limited, distinct token set. The essay was published in 2021 and updated in 2023; its example values should not be presented as current homepage tokens. [RUI token essay](https://replit.com/blog/rui-tokens)

**Published brand reasoning.** A 2024 rebrand essay connects visual choices to the product's human/technical story, rejecting generic AI imagery and building a consistent language from pixels and characters. The principle is relevant; its custom letterforms should not be copied. [First-party rebrand essay](https://replit.com/blog/rebranding-replit-inspiration-to-action)

**For PayProof.** Put a small real action beside the promise: choose an illustrative case or enter the test lab with the seeded agent. Three example chips—cumulative limit, replayed request, uncertain readback—are useful entry points. Distinguish a deterministic landing-page explanation from a real run. Reserve “run completed” results for actual API evidence.

**Limits:** exact font/color values, motion, and interaction behavior were not measured. The linked brand-kit page returned almost no readable content, so no current pixel tokens were extracted from it.

## Recommended synthesis for PayProof

The common structure is **clear outcome → immediate action → concrete product proof → mechanism → credible evidence → repeat action**. The useful lesson is the order and clarity, not combining four companies' decorative styles.

### Proposed page sequence

1. **Compact header:** wordmark, How it works, Evidence, FAQ; one entry to the real app.
2. **Hero:** one specific refund-agent promise, concise supporting copy, primary test-lab action, secondary explanation anchor. Adjacent product evidence uses real interface components or a clearly marked illustrative example.
3. **Concrete counterexample:** a known prior refund plus a small new request crosses the merchant limit. Let the reader inspect policy, decision, and resulting money state.
4. **Three mechanisms:** human-approved expectations, adversarial/replay scenarios, independent provider-state checks. Explain each in one short section with evidence, not uniform decorative feature cards.
5. **Before/after comparison:** show actual seeded/corrected run snapshots only when available; otherwise show an explicit illustrative example. Keep uncertainty visible.
6. **Integration boundary:** Codex and PayPal sandbox labels; describe exactly what is connected and what the simulator proves. No customer logo wall or invented savings metrics.
7. **Questions + final action:** what gets tested, what “inconclusive” means, and how to open the local test lab.

### Proposed starting tokens — our design choices, not extracted company values

| Role | PayProof proposal | Purpose |
|---|---|---|
| Page/paper | Warm near-white, around `#FAF9F5` | Calm canvas with restrained section contrast |
| Strong ink | Around `#202522` | High-contrast copy and critical values |
| Secondary ink | Around `#68716A`, contrast checked | Supporting copy without washed-out labels |
| Primary accent | Warm burnt orange, around `#CF6030` | Primary action and a few meaningful marks |
| Borders | Around `#E2E5DB`, 1px | Structure with minimal visual weight |
| Display scale | About 56–76px desktop / 38–48px mobile | Strong landing-page hierarchy, short line length |
| Body/UI scale | 16–18px marketing copy; 13–15px controls | Comfortable reading, not tiny dashboard labels |
| Content width | About 1120–1200px | Product proof remains readable at common desktop widths |
| Section rhythm | 80–120px desktop / 48–72px mobile | Give each claim room; avoid arbitrary empty height |
| Component space | 8px base with 16/24/32px group spacing | Predictable composition |
| Corners | 8–14px product frames, restrained CTA radius | Friendly but credible financial tool |
| Motion | Short state transitions; optional explanatory sequence | Show cause and effect; no essential autoplay |

Validate these choices in the actual responsive rendering. In particular, keep metadata readable, use labels as well as color for status, make the product example large enough to inspect, and preserve the simulator/sandbox distinction.

## Verification boundaries

All four first screens have now been visually inspected using root-captured current screenshots. Each screenshot is a single frame, so this report does not infer animation duration, easing, or hover behavior. Sizes inferred from pixels are approximate. Longer story structure is verified from the live webpage document; additional viewport captures would be needed to assess the complete below-fold layout and mobile composition. No full proprietary design system is claimed.
