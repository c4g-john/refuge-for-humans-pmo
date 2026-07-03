---
kind: test-cases
id: RFH-test-cases
project: PRJ-001-RFH
title: Refuge for Humans — Test Cases
owner: johntanner
status: approved
---

## Overview

Test cases derived from the acceptance criteria (the source BRD defines no
test cases of its own; these exercise its stated thresholds and SLAs).

## Test Cases

- **RFH-TC-001** (tests: RFH-AC-001): Steps: submit a post whose composite score is 70 or above. Expected: the post is published with a human verdict.
- **RFH-TC-002** (tests: RFH-AC-002): Steps: submit a post whose composite score is below 40. Expected: publication is blocked and a plain-language explanation is shown.
- **RFH-TC-003** (tests: RFH-AC-003): Steps: submit a post and measure time from submission to verdict. Expected: the verdict arrives within 2 seconds.
- **RFH-TC-004** (tests: RFH-AC-004): Steps: type continuously for 10 seconds while sampling the on-screen score. Expected: the score refreshes at least every 500ms.
- **RFH-TC-005** (tests: RFH-AC-005): Steps: for an account with 10+ verified posts, replay a submission whose absolute score passes generic thresholds but deviates more than 20 points from the account's rolling mean. Expected: the deviation dominates and the submission is flagged.
- **RFH-TC-006** (tests: RFH-AC-006): Steps: create 5 accounts submitting with substantially identical behavioral fingerprints. Expected: the cluster is flagged into the administrator investigation queue within 60 seconds of the last submission.
- **RFH-TC-007** (tests: RFH-AC-007): Steps: open the writing page and attempt to type before the daily prompt renders. Expected: the textarea rejects input until the prompt is displayed.
- **RFH-TC-008** (tests: RFH-AC-008): Steps: load the page, move the mouse and scroll, then type one character and inspect the signal timeline. Expected: events earlier than the first keystroke are present.
- **RFH-TC-009** (tests: RFH-AC-009): Steps: type 19 characters, observe the submit button, then type a 20th. Expected: the button is disabled at 19 characters and enabled at 20.
- **RFH-TC-010** (tests: RFH-AC-010): Steps: paste a sentence into the textarea. Expected: a visible, non-blocking notification appears and the textarea keeps accepting input.
- **RFH-TC-011** (tests: RFH-AC-011): Steps: submit one post scoring above the publish threshold and one below the block threshold, capturing each outbound payload. Expected: both payloads are transmitted and each composite equals 60% behavioral plus 40% content within rounding.
- **RFH-TC-012** (tests: RFH-AC-012): Steps: force a suspect verdict, leave it pending review, submit a later verified post, and compare fingerprints before and after. Expected: the suspect submission contributed nothing to the fingerprint.
- **RFH-TC-013** (tests: RFH-AC-013): Steps: for an account with an established rolling mean, replay a session scoring more than 20 points below it. Expected: the account is flagged.
- **RFH-TC-014** (tests: RFH-AC-014): Steps: as an administrator, open a user record and apply a manual verdict override. Expected: signal history, fingerprint, and verdict views render, and the override takes effect.
- **RFH-TC-015** (tests: RFH-AC-015): Steps: perform an administrative override, then read the audit log. Expected: the entry carries the action, a timestamp, and the operator ID.
- **RFH-TC-016** (tests: RFH-AC-016): Steps: open the daily metrics dashboard. Expected: post volume, bot block rate, suspect rate, and false-positive reports are displayed.
- **RFH-TC-017** (tests: RFH-AC-017): Steps: write and submit a post, then inspect the captured payload. Expected: keystroke, pointer, session/focus, and text-evolution signal arrays are all present and populated.
- **RFH-TC-018** (tests: RFH-AC-018): Steps: profile signal handlers during a 60-second writing session, then measure client scoring time at submission. Expected: every handler stays under 5ms and scoring completes within 100ms.
- **RFH-TC-019** (tests: RFH-AC-019): Steps: block backend connectivity, write, and submit. Expected: a verdict is produced from the client-side score alone and the post publishes or blocks accordingly, with no error surfaced.
- **RFH-TC-020** (tests: RFH-AC-020): Steps: replay a recorded burst of 10,000 concurrent submissions against the ingestion pipeline. Expected: zero dropped payloads and no latency degradation beyond baseline.
- **RFH-TC-021** (tests: RFH-AC-021): Steps: capture a signed payload, mutate one signal value, and resubmit. Expected: the backend rejects the payload before processing.
- **RFH-TC-022** (tests: RFH-AC-022): Steps: score recorded atypical-input sessions (assistive input, dictation cadence, non-native keyboards) against established baselines alongside typical-input controls. Expected: verdict distributions do not differ systematically.
- **RFH-TC-023** (tests: RFH-AC-023): Steps: file a deletion request for a test account, then audit storage. Expected: raw payloads are gone, the fingerprint is reset, and remaining data is encrypted at rest.
- **RFH-TC-024** (tests: RFH-AC-024): Steps: run an instrumented writing session on current Chrome, Firefox, Safari, Edge, and one mobile browser. Expected: all four signal classes captured on each desktop browser; on mobile, missing mouse signals raise no errors and the other classes are present.
