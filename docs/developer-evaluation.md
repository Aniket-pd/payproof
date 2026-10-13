# Try PayProof as a developer

This is a 15-minute product evaluation after installation, not a quiz. We want to learn whether the workflow is useful and where it fails. Finding no value, getting stuck, or disagreeing with a result is useful feedback. No AI or PayPal account is needed for these tasks; use the Simulator throughout.

Please use synthetic examples only. A participant code is enough; omit employer, customer and account details. Share your notes privately with the person who invited you. Nothing in this worksheet sends a response automatically.

## Before starting

Use a fresh folder containing the PayProof source package. Requirements: Node.js 22 or later, npm, and macOS or Linux. Windows has not been verified. From the `payproof` folder run:

```sh
npm ci
npm run dev
```

Open [the local app](http://127.0.0.1:4318). If installation fails, keep the error text and mark setup incomplete; do not spend more than 10 minutes troubleshooting for this session. Installation time is recorded separately from task time. The app saves local test runs in this fresh folder. Do not enter credentials or start fresh AI/Sandbox operations for this evaluation.

Before exploring, note how you currently test an automated refund or similar policy decision. If you do not work on that type of system, say so. What is the hardest part of that workflow? “Not a problem I have” is a valid response.

## Tasks

Start a timer at the beginning of each task. You may use the shipped README and documentation. Record any help from another person separately. Stop when you finish, get stuck, or reach the time limit; incomplete tasks still count as observations.

1. **Inspect a release decision — 4 minutes.** From the landing page, run the two-case comparison. Which result would you investigate before release, and why? Is a result with no refunded money sufficient to call the agent successful? Point to the case or evidence that supports your answer.
2. **Trace the evidence — 3 minutes.** Open a case and inspect its saved inputs and payment records. Describe what was proposed, what was observed, and whether those payments came from the Simulator or actual PayPal. Export the evidence. Describe one thing this file cannot prove. Reload the case and check whether you can still reach the same evidence.
3. **Evaluate a separate decision component — 6 minutes.** Follow [the external-agent walkthrough](../examples/README.md) using the two cumulative-refund cases and default policy in this fresh workspace. Produce the before and after evidence exports. Explain the differing exit statuses and whether the passing version still performs the permitted refund. If you cannot finish, record the exact command or UI step where you stopped.

Use the remaining two minutes for the questions below. Do not run optional live AI, PayPal checkout, or additional scenarios to improve a result. A complete response does not require all tasks to pass.

## Response to copy and fill in

```text
Participant code:
Date and source ZIP SHA-256 or Git commit, if known:
Relevant experience (optional; e.g. API development, payments, agent testing):
Relationship to project (outside developer / contributor / entrant / other):
OS, Node and npm versions:
Current workflow and hardest part, before trying PayProof:

Setup: completed / incomplete
Setup minutes:
Setup error or help needed:

Task 1: completed / partial / stopped
Elapsed seconds:
Case/result I would investigate and evidence:
Is refunding nothing sufficient? Why?
Documentation used and any human assistance:

Task 2: completed / partial / stopped
Elapsed seconds:
Proposed action, observed result and payment source:
Evidence file or run/case identifier:
What this file cannot prove:
Reload result:
Documentation used and any human assistance:

Task 3: completed / partial / stopped
Elapsed seconds:
Before/after exit statuses and evidence filenames:
What changed, including the permitted refund:
Where I got stuck, if applicable:
Documentation used and any human assistance:

Would this fit a real task in your workflow? Give a concrete example or say no:
What existing approach would you use instead, and why?
What would prevent you from trying your own agent here?
Most confusing or untrustworthy part:
One change that would make this more useful:
Any other feedback, including a reason not to use it:
May an anonymized quote be used in the submission? yes / no
If yes, exact quote you permit (leave blank otherwise):
```

Do not include credentials or real customer records in notes or exported files. A response is feedback on this prototype; it is not an endorsement or a claim of production suitability.
