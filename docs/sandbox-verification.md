# PayPal Sandbox verification record

**Observed 14 October 2026 IST (13 October UTC).** Five fresh $100 Sandbox orders were approved by an existing personal test buyer, captured, and prepared with a $15 opening refund. These are actual Sandbox API observations with test funds and synthetic customer requests. They establish this controlled standard-processing flow, not production safety or arbitrary account-wide refund inventory.

- [x] Selected the existing Sandbox business app and a separate personal buyer.
- [x] Stored app credentials only in excluded local `.env` (0600); restarted the local server.
- [x] Created, approved and captured five separate orders; amount/currency matched the cases.
- [x] Independently read each $15 opening refund as `COMPLETED`.
- [x] Seeded $15 + $10 case: PayPal completed $10; PayProof failed it at $25 total and $5 policy excess.
- [x] Fresh corrected $15 + $10 case: no new refund attempted; passed with $15 total.
- [x] Fresh corrected $15 + $5 case: $5 completed; passed at exactly $20 total.
- [x] Fresh Codex batch on two more captures: both cases passed, including the legitimate $5 refund.
- [x] Retained exact exports, provider IDs, request identities, independent readbacks and snapshots.
- [x] Confirmed attempted and observed completed amounts remain distinct in each report.
- [x] Simulator pending/readback-failure coverage and mocked crash recovery retain their separate labels; neither is claimed as a live-provider fault experiment.

All five results have complete readbacks. PayPal supplied `seller_payable_breakdown.total_refunded_amount` in this observed flow. The seeded opening refund's final readback changed from $15 to $25 after the additional refund. This does not establish every account's behavior or protect against concurrent external activity; missing/conflicting totals remain inconclusive.

| Agent / case | Capture ID | Independently read completed refund IDs | Result |
| --- | --- | --- | --- |
| seeded / cumulative-over | `8AE283481L340613P` | `1LN787893V334952A` ($15), `4CX10379EL141335C` ($10) | fail; $10 attempted, $25 total |
| corrected / cumulative-over | `1VJ20957ET941040R` | `40M83349MH0817333` ($15) | pass; $0 attempted, $15 total |
| corrected / cumulative-exact | `7XE55057EF407883J` | `34H79473W1511353E` ($15), `7R79696977941700T` ($5) | pass; $5 attempted, $20 total |
| codex / cumulative-over | `8P2698015B754423U` | `49N54630VN5942933` ($15) | pass; $0 attempted, $15 total |
| codex / cumulative-exact | `05S70396HG965393B` | `2YF51657GE5358405` ($15), `4X3161116K305551F` ($5) | pass; $5 attempted, $20 total |

The [four original exports](../examples/recorded-paypal/README.md) retain their `paypal` provider label. The Codex run is `1db60e11-e7a7-47ab-bd17-698f47e662b0`, thread `01a136b7-e468-7312-845b-063ae953d93b`, default CLI 0.162.0 model (exact revision unknown). It was one fresh two-case batch; no rerun was made to improve its result.

Offline replay validated all four exports and reproduced the decisions, verdicts and amounts while changing the evidence provider to Simulator. **Replay does not authenticate historical PayPal or AI claims.** A consumer importing a file sees unverified external provenance. For an independent live check, use fresh captures in your own authorized Sandbox account; reusing the recorded captures is disallowed.

The original policy, 27 library cases and 57 saved runs were preserved. This session added four runs and five finalized fixtures. Local verification artifacts are in `artifacts/improvement-2026-10-14/`. Credentials, buyer details, OAuth tokens and account state are excluded from the source package.

If a future operation times out, preserve its request ID and consult the local journal and provider readback before deciding whether to retry. The forced-process-stop recovery test remains a separate mocked-provider test.

## Edited scenarios and fixtures set aside locally

A fixture keeps its original test inputs. Cosmetic title/category/source changes do not invalidate the fixture. Changes to the request, payment facts, supervisor approval or injected fault do: Connections explains the mismatch and withholds capture/resume/test actions. Expand **Original fixture inputs** to inspect the saved facts.

To use changed inputs, choose **Set aside fixture**, then prepare a fresh order. Setting aside is a reversible local bookkeeping action: it preserves the provider status, IDs and original snapshot, and makes no PayPal call. It does not cancel an order, refund a capture or resolve an unknown provider outcome. Inspect retained provider records before creating a separate order. **Restore fixture** restores only its workspace availability; it does not reset a used capture or issue another provider request, and another active unfinished fixture must be resolved or set aside first.
