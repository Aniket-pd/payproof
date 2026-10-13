# Landing-page research: six leading YC alumni

Reviewed 9 October 2026. This is the consumer/platform half of a ten-company reference study, not a claim that these are the ten largest companies under a particular valuation measure. All six official homepages were opened. Reddit's corporate site is an explicitly selected alternative to its consumer feed.

## Evidence and limits

“Observed” below distinguishes source content, public HTML/CSS declarations, and rendered screenshots. The coordinating agent captured the six pages and this researcher visually inspected every supplied image. [Local screenshots](../artifacts/yc-design-research/) are preserved with the study. Airbnb, Coinbase, and Scale provide useful rendered hero evidence; Instacart is partly loaded; Reddit has degraded typography/navigation; DoorDash remains at a security check.

Exact breakpoints, pixel spacing, and animated states remain unverified unless explicitly sourced. Screenshot descriptions are qualitative visual observations, not measured CSS tokens. Brand documentation describes the company's system; it does not prove every token is used on its homepage. Public-source CSS can reflect a particular locale, user agent, or variant. Proposed PayProof choices are our own design decisions.

## 1. Airbnb

**Page:** [airbnb.com](https://www.airbnb.com/).

**Observed structure:** Navigation distinguishes homes, experiences, and services. The main input asks for destination, dates, and guest count. Hosting is a separate audience path. Help, AirCover, safety, and accessibility provide support navigation. The text response was partial, but the final screenshot loaded the India-localized experience.

**Rendered hierarchy:** The [960×744 screenshot](../artifacts/yc-design-research/airbnb.jpg) starts with illustrated category tabs and a wide, rounded search control. Below it, five destination photos and a row of homes dominate the viewport. There is no giant promotional H1. Search is emphasized by a saturated pink-red circular button; other surfaces are white with dark sans-serif labels, fine borders, and soft search-control shadow. Photos have generous corner rounding. Small badges and favorites sit over home images.

**Token limits:** Exact font family, pink hex, spacing, and radii were not measured. Location and recommendations are contextual.

**PayProof interpretation:** Make the first action concrete, such as “Run a $20 refund.” Keep setup secondary and let the user start the job before explaining every capability.

## 2. Coinbase

**Page:** [coinbase.com](https://www.coinbase.com/). **System reference:** [Coinbase Design System colors](https://cds.coinbase.com/getting-started/colors).

**Observed structure:** A financial-future proposition leads to email entry and signup. Navigation separates individuals, businesses, institutions, and developers. Subsequent sections introduce assets, advanced trading, membership, wallet capabilities, educational material, and another signup opportunity. Image descriptions identify actual trading and wallet interfaces. The response included locale-specific currency and restrictions, so this is not evidence of universal copy.

**Hierarchy, trust, and imagery:** Product interfaces make complex features tangible; educational content supplies a slower path for uncertain visitors. The repeat CTA follows additional explanation rather than introducing a different conversion goal.

**Rendered hero:** The [1280×720 screenshot](../artifacts/yc-design-research/coinbase.jpg) uses a spacious two-column composition: oversized, regular-weight black sans-serif headline and one blue pill CTA on the left; an actual mobile product screen on a pale, substantially rounded panel on the right. Thin navigation separators and neutral utility buttons preserve emphasis. The image shows rupee values and the hero has a signup button, rather than the text response's email field: variants differ.

**Verified system tokens:** CDS separates semantic foreground, background, and line roles. Blue serves primary roles; green, red, and orange express positive, negative, and warning states. It specifies 4.5:1 text and 3:1 meaningful non-text contrast. These are documented rules. Exact homepage font, radius, spacing, and hex values were not measured.

**PayProof interpretation:** Use a real receipt/evidence preview beside a succinct claim. Keep the brand's main action color distinct from success, denial, and uncertainty. Reuse one conversion action after deeper explanation.

## 3. DoorDash

**Page:** [doordash.com](https://www.doordash.com/).

**Observed structure:** The response began with a security-check message, but exposed substantial landing-page content. There are distinct paths for delivery workers, merchants, and app users; consumer sections cover restaurant delivery, membership, grocery, convenience, and other shopping categories. Each section has an action related to its immediate promise. Location, cuisine, and chain links form a broad discovery footer.

**Hierarchy and trust:** The source supports a repeated benefit → explanation → task-specific CTA structure. The sequence connects the service to concrete jobs such as ordering dinner or groceries. It does not establish that the first returned content is the rendered hero.

**Tokens and imagery:** Hero composition, current type family, exact red values, spacing, and corner shapes were not verified. A direct HTML request returned 403. Image descriptions and content imply concrete delivery categories, but exact image crops and layout require rendered inspection.

**Rendered limit:** The [960×744 screenshot](../artifacts/yc-design-research/doordash.jpg) is a Cloudflare verification screen. Its black background and typography are not DoorDash design evidence.

**PayProof interpretation:** Give each deeper section one benefit and one visible artifact: policy evaluation, attempted action, or provider readback. Avoid a long grid of equally weighted technical features. Do not copy DoorDash's broad audience navigation into a product with one primary demo journey.

## 4. Scale AI

**Page:** [scale.com](https://scale.com/). **Brand sources:** [Typography](https://brand.scale.com/typography), [Color](https://brand.scale.com/color), [Imagery](https://brand.scale.com/imagery).

**Observed structure:** The current proposition centers on reliable AI and consequential decisions. A “Get started” action introduces enterprise applications and data offerings. Customer-logo assets and named case stories supply proof; deeper material leads toward enterprise engagement. The current source is not evidence for older purple-gradient Scale compositions.

**Rendered hero:** The [960×744 screenshot](../artifacts/yc-design-research/scale.jpg) confirms restrained monochrome styling: compact white navigation, black primary button, and a very large black hero surface with a centered, regular-weight white statement. Narrow outer gutters frame the panel, which has subtly rounded lower corners. The substantial empty upper field may include media/loading behavior; only the captured state is established.

**Verified brand typography:** Scale 2.0 documents Aeonik as its main face and Aeonik Mono for values and labels. The displayed scale is 120/88/64/40/20 for display, H1, H2, H3, and body, mostly regular weight. Display hierarchy comes from size and tracking. Headings use tight leading; digital body copy uses 150% leading. These are documented brand values, not a measurement of the homepage at one viewport.

**Verified brand palette:** Black and white carry the system. Documented accents include evergreen `#193A29`, atlas blue `#273252`, tan `#A8927C`, purple `#79648C`, and slate `#839CB2`. Guidelines favor restrained use, with color surfaces paired with black or white text. Multiple saturated fields are not the default.

**Verified imagery guidance:** Scale favors real operational contexts, people using systems, natural light, and evidence of consequence. It discourages generic abstract AI imagery. Exact homepage section padding and radii were not measured.

**PayProof interpretation:** This is the strongest reference for an evidence-centered product. Use a large, plain promise and an actual policy-to-receipt flow. Reserve monospace for hashes, IDs, and machine values. Build confidence through inspectable evidence. Scale's client logos belong to Scale; PayProof must use only its own verifiable proof.

## 5. Reddit — corporate landing-page alternative

**Page:** [redditinc.com](https://redditinc.com/), reached from `www.redditinc.com`. **Brand source:** [Reddit brand](https://redditinc.com/brand).

**Observed structure:** Company, values, news, and support navigation frames a corporate introduction. A community-centered headline is followed by product mechanics—posting, commenting, and voting—supported by illustrations, a by-the-numbers section, and newsroom material. “Visit Reddit” links to the consumer product. Metrics in the parsed page appeared as zero placeholders and should not be reused as verified numbers.

**Verified brand/source tokens:** The brand page identifies OrangeRed `#FF4500` and Reddit Sans. It describes a humanist, large-x-height typeface chosen for legibility and character differentiation. The homepage's inline CSS independently contains Reddit Sans families and `#ff4500`; it also declares 24px and 40px corner radii. Those declarations were not mapped to rendered elements, so they are not asserted as universal card or button values. Exact spacing remains unverified.

**Rendered limit:** The [960×738 screenshot](../artifacts/yc-design-research/reddit.jpg) confirms a white navigation bar, orange CTA, and orange hero field. It shows a serif heading and missing navigation/imagery despite the documented sans-serif system, so it is a degraded load. Do not use that fallback typography, incomplete layout, or empty right field as a reference design.

**PayProof interpretation:** Explain three product mechanics in ordinary language before presenting implementation detail: set a policy, run an action, inspect the result. A distinctive voice is useful; borrowing a mascot or playful tone is less suitable for a payment-control workflow.

## 6. Instacart

**Page:** [instacart.com](https://www.instacart.com/).

**Observed structure:** Grocery delivery/pickup is the opening job. Signup and an introductory delivery offer sit near local-store discovery. Category and service filters support immediate exploration. Later sections explain choosing items, communicating/tracking, and receiving delivery. Guarantee language, scale claims, FAQs, and app access address confidence and practical objections. The page selected a US locale; it is not evidence of the viewer's own location.

**Source-verified tokens:** The returned HTML declares Instacart Sans and Instacart Contrast. Its inline styles include neutral `#343538`, `#242529`, `#F6F7F8`, white, and green `#108910`. Several radii are present, including 12px, 24px, and pill-like values. The H1's source class specified 24px/28px, weight 600 and a `mobile/headline` token. That is a response-specific mobile declaration, not a desktop hero measurement. No rendered spacing was measured.

**Rendered hero:** The [960×744 screenshot](../artifacts/yc-design-research/instacart.jpg) shows search and account controls above a compact dark-green banner. A white benefit heading and bright-green pill CTA sit beside rounded grocery photography, with offer terms directly beneath the CTA. Store filters are pills. The large pale-gray region is a loading placeholder, not evidence of deliberate whitespace.

**PayProof interpretation:** Put the working product within immediate reach, then explain the process in three short steps. Address consequential objections in a compact FAQ: what is simulated, when an action is blocked, and what a provider response actually proves. Use clear product states instead of unverified customer or scale claims.

## Proposed PayProof design decisions

These are derived recommendations, not copied brand tokens or evidence of conversion effectiveness.

1. **Lead with one job:** “Give your payment agent a spending policy—and proof it followed it.” Use one primary action into the working demo, with a secondary link to the evidence explanation.
2. **Make the product the hero visual:** Render a legible policy → action → provider-result preview using PayProof's own data model. Clearly identify sample evidence and simulation. A future successful provider call can replace the sample with real evidence.
3. **Use an editorial hierarchy:** Large, concise headline; restrained subcopy; substantial section separation; compact labels only for useful metadata. Choose a licensed/system sans rather than importing proprietary brand fonts.
4. **Use color semantically:** Neutral reading surfaces, one consistent action accent, and separate success/denial/unknown states with text and icons. Color must not be the sole status signal.
5. **Progressively disclose complexity:** Landing promise, concrete preview, three mechanics, proof/limitations, final demo action. Put signatures, hash chains, MCP, and API paths inside evidence details or documentation where they help the reader decide.
6. **Use honest trust mechanisms:** Show what was evaluated, what was attempted, and what the provider returned. State that PayProof is a hackathon prototype. Never manufacture customers, transaction volume, guarantees, YC membership, or third-party endorsement.

The current evidence supports a qualitative visual study, information hierarchy, CTA strategy, documented brand systems, and selected source tokens. DoorDash remains visually blocked and Reddit's load is degraded. Captures have different widths, so they do not support pixel-matched replicas or comparative spacing measurements.
