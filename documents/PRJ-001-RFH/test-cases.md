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
