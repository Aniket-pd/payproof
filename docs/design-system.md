# PayProof design system

Version 1 · October 9, 2026

This is PayProof's own implementation specification, informed by ten selected leading YC alumni. The selection is a reference sample, **not an objective valuation-based top ten**, and does not imply that PayProof is affiliated with YC or any reference company. We studied current public page content, selected official design documentation, and rendered captures for all ten references. Stripe, Dropbox, GitLab, Replit, Airbnb, Coinbase, and Scale provide useful rendered page evidence. Instacart is partly loaded, Reddit has a degraded load, and DoorDash's capture shows a security check; those limitations constrain the conclusions below. No complete proprietary design system was extracted or reproduced.

Research: [Stripe, Dropbox, GitLab, Replit](design-research-b2b.md) · [Airbnb, Coinbase, DoorDash, Scale AI, Reddit, Instacart](design-research-consumer.md).

## Product and visual direction

PayProof helps a developer understand whether a refund agent followed a merchant-approved policy and whether payment state supports its claimed outcome. The landing page should establish that job immediately, demonstrate the problem, and lead into the working lab. A compact product demonstration is more useful here than a generic AI illustration.

The visual language combines warm paper, strong ink, one burnt-orange action accent, readable sans typography, and restrained product framing. Broad spacing separates arguments; fine rules organize related evidence. The dashboard remains a work surface. The landing page is an explanation and entry point, with its own hierarchy.

## Ten-company decision map

| Reference | Evidence studied | Transfer to PayProof |
|---|---|---|
| [Stripe](https://stripe.com/) | Current content and desktop capture; [historical engineering essay](https://stripe.com/blog/connect-front-end-experience) | Align the page coherently; progress from outcome to concrete capabilities and technical proof. Keep one primary conversion path. |
| [Dropbox](https://www.dropbox.com/) | Current content/capture; official [framework](https://brand.dropbox.com/framework), [type](https://brand.dropbox.com/typography), [color](https://brand.dropbox.com/color), [motion](https://brand.dropbox.com/motion) | Warm canvas, clear split hero, one large legible product specimen, an obvious next action, purposeful feedback. |
| [GitLab](https://about.gitlab.com/) | Current content/capture; [brand typography](https://design.gitlab.com/brand-design/typography/) and [color](https://design.gitlab.com/brand-design/color/) | Strong display hierarchy; explain trust through context, controls, and traceability. Reserve mono type for machine values. |
| [Replit](https://replit.com/) | Current content/capture; [historical RUI token essay](https://replit.com/blog/rui-tokens) | Let the hero expose a product action; offer example cases; define a small, named token vocabulary. |
| [Airbnb](https://www.airbnb.com/) | Partial text response plus a reliable India-localized capture: category tabs, prominent search, and photo-led listings | Make the task concrete and sequence the user's inputs. Keep advanced setup secondary. |
| [Coinbase](https://www.coinbase.com/) | Live content and a reliable split-hero capture with a real mobile interface; official [CDS colors](https://cds.coinbase.com/getting-started/colors) | Separate brand action color from financial/status semantics; show understandable product evidence and answer practical concerns. |
| [DoorDash](https://www.doordash.com/) | Substantial source content; rendered capture blocked by a security check, so no homepage styling conclusions | Give each section one benefit, one supporting artifact, and one appropriate action. Avoid a feature inventory of equal-weight boxes. |
| [Scale AI](https://scale.com/) | Live content and a reliable monochrome hero capture; official [type](https://brand.scale.com/typography), [color](https://brand.scale.com/color), [imagery](https://brand.scale.com/imagery) | A plain, consequential promise; a restrained palette; operational evidence instead of generic AI decoration. |
| [Reddit corporate](https://redditinc.com/) | Corporate-page alternative; public source and [brand guidance](https://redditinc.com/brand); degraded capture supports only limited color observations | Explain the core mechanics in three ordinary-language steps before introducing technical depth. |
| [Instacart](https://www.instacart.com/) | Live content, response-specific public source, and a partly loaded capture: search, green benefit banner, and grocery photography; midpage placeholder is not a spacing reference | Immediate product access, a short process explanation, and FAQs addressing practical objections. |

These are design interpretations, not claims that a pattern caused those companies' commercial success. Public brand documentation is distinct from current homepage styling. Screenshot-based dimensions are approximate; source declarations are not universal responsive values.

## Tokens

These are PayProof values, not copied or inferred reference-company tokens. The implementation lives in [landing.css](../src/landing.css), with bundled font imports and the shared mono family in [styles.css](../src/styles.css). The table uses descriptive names; only the six `--lp-*` colors are landing CSS custom properties. Dimensions and typography are component rules.

| Token | Value | Role |
|---|---|---|
| `--lp-paper` | `#f8f7f3` | Main landing canvas |
| `surface` | `#ffffff` | Product specimens and elevated controls |
| `--lp-ink` | `#202720` | Headlines, body, critical values |
| `--lp-muted` | `#60675f` | Supporting copy and useful metadata |
| `--lp-line` | `#dedfd6` | 1px rules and component boundaries |
| `--lp-accent` | `#bd492b` | Primary action, selected emphasis |
| `--lp-dark` | `#202820` | Evidence section / closing contrast |
| `font-body` | DM Sans, bundled with Fontsource | Headings, prose, controls |
| `font-data` | DM Mono, bundled with Fontsource | Amounts where alignment matters, IDs, labels |
| `content-width` | 1160px maximum | Shared page alignment |
| `page-gutter` | 48px per side by default; 32px at ≤1100px, 22px at ≤800px, 20px at ≤600px, 16px at ≤374px | Responsive outer margins, subject to the content maximum |
| `section-spacing` | 103px block padding by default; 76px at ≤800px; 65px at ≤600px | Main section rhythm; hero and evidence have their own spacing |
| `hero-type` | `clamp(54px, 6.1vw, 80px)` by default; approximately 78px at 1280px; 84px at ≥1400px | Desktop outcome-led headline |
| `hero-type-responsive` | 68px at ≤1100px; 55px at ≤800px; 50px at ≤600px; 44px at ≤374px | Explicit viewport overrides |
| `section-type` | 50px by default; 44px at ≤1100px; 36px at ≤800px; 39px at ≤600px | Main H2 scale; evidence and closing headings have separate rules |
| `body-type` | 16px base; hero copy 17px by default, 18px at ≥1400px, 16px at ≤1100px, 14px at ≤800px, 16px at ≤600px, 15px at ≤374px | Component-specific explanatory copy |
| `button-height` | 50px minimum for `.lp-button` | Primary demo controls; compact navigation and illustration controls differ |
| `button-radius` | 7px | Restrained action styling |
| `product-radius` | 13px proof card and closing panel; 10px trace and feature cards | Related frames with component-specific rounding |
| `hover-duration` | 120ms | Color/border feedback |
| `state-duration` | 220ms | Illustrative graphic/state changes |

The hero uses weight 550 and 1.01 line height by default; main H2s use weight 500 and 1.08 line height. The desktop hero has two columns with a 60px gap, changing to one column at ≤600px. Its copy is capped at 438px by default and 450px on mobile. Spacing is tailored to each component rather than enforced as an exact 8px scale. Later, narrower breakpoint rules override earlier ones; mobile type should not be inferred by linear interpolation.

Use natural line wrapping. Status uses text and icons as well as color. Essential labels must remain legible, and hover must not be the only way to reveal an action. Reduced-motion preferences remove nonessential animation. Contrast and keyboard behavior require their own verification; matching these tokens alone does not establish accessibility conformance.

## Page architecture

- `/`: public-facing explanation and interactive demonstration.
- `/app`: existing working test lab, scenarios, run history, and integrations.
- Shared identity and semantic status language connect the two; landing-page styling must not leak into dense evidence tables.

### Landing sequence

1. **Header:** identity, short section links, entry to the working lab.
2. **Hero:** one refund-testing promise, concise supporting copy, primary working-demo action, secondary explanation link. The adjacent cumulative-refund specimen is large enough to read.
3. **Interactive illustration:** switch between seeded/corrected behavior and a $5/$10 request against a $20 cumulative cap with $15 already refunded. Display the arithmetic and expected action. Always label this as illustrative; toggling it does not call PayPal or create a recorded run.
4. **Three-step mechanism:** define and approve the expectation; challenge the agent; verify independent payment state. Show how the steps connect.
5. **Evidence:** feature explanations accompanied by product evidence and a clearly labeled illustrative trace. Expose the difference between a decision, an attempted action, and an observed result.
6. **FAQ:** simulation versus sandbox, the meaning of inconclusive evidence, what a tested suite can establish, and how to begin.
7. **Final CTA:** repeat the same real-demo/lab entry, with a concise description of what will happen.

### Working CTA contract

The primary live demo calls the isolated `/api/demo` route using demo defaults. It preserves the user's existing policy, scenario approvals, and recorded work, and opens actual returned results in the lab. Loading, error, and completion states reflect the real request. Do not fabricate success or mutate the user's policy to manufacture a favorable result. A simulator-backed demo must remain visibly labeled Simulator; only actual sandbox evidence earns a PayPal Sandbox label.

## Content and evidence rules

- Use PayProof's own functionality, reproducible cases, and actual returned evidence as proof.
- Do not invent customer logos, endorsements, adoption figures, savings, transaction volume, or affiliation with the reference companies or YC.
- Clearly distinguish illustrative values, simulator records, and actual sandbox records.
- Show incomplete readbacks as unconfirmed. A pending or missing result is not a verified zero refund.
- Describe tested scope rather than universal certification. Preserve the difference between failed, passed, and inconclusive.
- Keep API paths, credentials, implementation details, and traces in the app/documentation where useful. The landing explanation should focus on the user's job.

## Acceptance checks

At desktop and mobile widths, confirm that the headline, CTA, illustrative labels, amounts, and policy boundary are readable without horizontal scrolling. Exercise both agent switches and both request amounts. Confirm the live demo opens genuine results and leaves prior workspace state intact. Check keyboard navigation, focus visibility, disabled/loading/error states, section links, app return navigation, and reduced motion. Verify text contrast against each surface, especially muted metadata and status colors. These are acceptance checks, not a claim of a completed WCAG audit. Keep all reference captures clearly presented as research artifacts, not PayProof customers or integrations; retain the loading, degraded-render, and security-check qualifications.

## Application design system

The working application uses the same warm palette with a denser reading hierarchy. [Shared styles](../src/styles.css) define the shell, controls, forms, status labels, and dialog foundation; feature styles own the evidence, scenarios, history, connections, and documentation layouts. The following describes the current implementation, not verification results.

### Shared values

| Role | Implemented value |
|---|---|
| Canvas / panel | `--bg: #f8f7f3`; `--paper: #fff` |
| Text / supporting text / rules | `--ink: #202720`; `--muted: #60675f`; `--line: #dedfd6` |
| Action / hover / action wash | `--accent: #bd492b`; `--accent-dark: #a43c22`; `--accent-wash: #fbefe8` |
| Positive / negative / caution | `--green: #326548`; `--red: #aa3e2c`; `--amber: #85601e` |
| Semantic washes | `--green-wash: #edf5ee`; `--red-wash: #fceee9`; `--amber-wash: #fbf4e4` |
| Reading type | DM Sans; application base 14px / 1.55; DM Mono for code and machine values |
| Page heading | 36px, weight 550, 1.13 leading, −1.5px tracking; 32px at ≤960px |
| Shared panel | White, 1px rule, `--radius: 12px` |
| Standard controls | `.button` minimum height 44px, 7px radius; form controls minimum height 44px, 7px radius |
| Shared motion | 140ms color, background, border, and shadow transitions |

These are foundations, not universal component measurements. For example, shared compact buttons default to 36px, while feature controls can override their height. Shared H2/H3 defaults are 19px/17px; feature headings set their own scale. Status chips also define their own foreground, border, and background colors. The application's `--paper` means a white panel; the landing page's `--lp-paper` means its warm canvas.

### Page architecture

[App.tsx](../src/App.tsx) stores the selected page in the `view` query parameter and supports browser history.

- **`/app?view=lab`:** Agent, evidence source, scenario selection, and policy setup lead into recorded run evidence. A saved result can be opened with an additional `run` parameter. The [evidence component](../src/components/RunEvidence.tsx) separates case outcomes, the proposed decision, checks, events, and payment records.
- **`/app?view=scenarios`:** A searchable case library leads to the review dialog. Facts, expected behavior, and approval are presented together; generated drafts require review.
- **`/app?view=runs`:** Search and outcome filters organize recorded runs. Evidence-row buttons and downloads have separate targets. Baseline/candidate comparison preserves snapshot differences and missing-case states.
- **`/app?view=connections`:** Connection cards explain readiness and next steps. PayPal credentials remain distinct from a verified provider result. The sandbox workbench presents creation, buyer approval, capture, and fixture use in order.
- **`/app?view=docs`:** Quickstart provides section anchors, copyable commands, and navigation into the working screens. `/api/docs` remains the secondary full README reference.

### Responsive layout and interaction

The desktop sidebar is 228px wide, reducing to 210px at ≤1230px and 190px at ≤960px. At ≤760px it becomes a 280px overlay drawer and the content loses its sidebar offset. The main region has a 1500px maximum width and default padding of 36px 38px 30px; narrow layouts reduce horizontal padding to 18px at ≤560px and 14px at ≤360px. The top bar changes from 76px to 66px at ≤760px. Lab setup becomes one column at ≤960px. Feature layouts independently stack comparisons, review fields, fixtures, and guide navigation; long identifiers wrap or truncate with full values available through the relevant evidence or copy control.

Shared buttons, links, and summaries define a 3px focus outline with a 4px offset; feature scopes can use their own 2px accent outlines. Form focus changes the border and adds a 3px tinted ring. Navigation closes the drawer, updates the URL, scrolls to the top, and focuses the main region. The [shared dialog hook](../src/components/ui.tsx) manages initial focus, visible focusable elements, Tab cycling, Escape, scroll locking, and return focus.

Loading labels and spinners describe active operations. Disabled actions retain explanatory next steps; errors remain visible instead of becoming fabricated success. Status text distinguishes passed, failed, and inconclusive evidence, and provider labels distinguish Simulator from PayPal Sandbox. Reduced-motion rules shorten shared animation and transition durations to `.01ms` and disable smooth scrolling; feature styles remove nonessential transitions.
