# PayPal Sandbox verification record

This checklist is intentionally unchecked. Mocked adapter tests verify request construction and defensive handling, but do not establish successful access to a real PayPal Sandbox account. Only mark an item after completing it and retaining the corresponding evidence.

- [ ] Create or select a sandbox business app and a separate sandbox personal buyer.
- [ ] Put the sandbox app ID and secret in the local `.env`; restart the server.
- [ ] Create an order from Connections and approve it as the sandbox buyer.
- [ ] Capture the approved order; verify its currency and amount match the selected scenario.
- [ ] For a prior-refund case, confirm the opening refund is independently read as `COMPLETED`.
- [ ] Run the $15 + $10 cumulative-policy case with the seeded teaching agent and inspect the new sandbox refund ID.
- [ ] On a fresh fixture, run the same case with the corrected agent and verify no new refund is issued.
- [ ] On another fresh fixture, run the $15 + $5 legitimate case and verify the additional $5 is completed.
- [ ] Export each run, retain its provider label, and compare the policy snapshots and case inputs.
- [ ] Confirm attempted cents and completed cents are distinguishable in the report.
- [ ] Test the stopped/pending/readback states in the simulator and keep their labels visible.

Suggested local record:

| Check | Date | Fixture/order ID | Capture ID | Refund IDs | Result / notes |
| --- | --- | --- | --- | --- | --- |
| Sandbox buyer approval and capture | Not run | — | — | — | Credentials required |
| Opening refund readback | Not run | — | — | — | Credentials required |
| Seeded cumulative-policy case | Not run | — | — | — | Credentials required |
| Corrected cumulative-policy case | Not run | — | — | — | Fresh fixture required |
| Legitimate matched case | Not run | — | — | — | Fresh fixture required |

Use IDs and status records in this table; never include credentials, personal buyer details or OAuth tokens. If an operation times out, preserve its existing request ID and consult the local sandbox journal and PayPal readback before deciding whether to retry.

## Edited scenarios and fixtures set aside locally

A fixture keeps its original test inputs. Cosmetic title/category/source changes do not invalidate the fixture. Changes to the request, payment facts, supervisor approval or injected fault do: Connections explains the mismatch and withholds capture/resume/test actions. Expand **Original fixture inputs** to inspect the saved facts.

To use changed inputs, choose **Set aside fixture**, then prepare a fresh order. Setting aside is a reversible local bookkeeping action: it preserves the provider status, IDs and original snapshot, and makes no PayPal call. It does not cancel an order, refund a capture or resolve an unknown provider outcome. Inspect retained provider records before creating a separate order. **Restore fixture** restores only its workspace availability; it does not reset a used capture or issue another provider request, and another active unfinished fixture must be resolved or set aside first.
