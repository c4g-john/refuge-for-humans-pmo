---
kind: test-cases
id: RFH-test-cases
project: PRJ-001-RFH
title: Refuge for Humans — Test Cases
owner: johntanner
status: draft
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
