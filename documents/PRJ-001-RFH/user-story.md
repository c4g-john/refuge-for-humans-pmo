---
kind: user-story
id: RFH-user-story
project: PRJ-001-RFH
title: Refuge for Humans — User Stories
owner: johntanner
status: proposed
---

## Overview

One story per product requirement, derived from the PRD and the roles the BRD
names (writers and administrators, plus the trust operators who run the
verification layer). Each story traces to its product requirement; acceptance
criteria live with the PRD and are verified by the test cases.

## User Stories

- **RFH-US-001** (traces: RFH-PR-001): As a writer, I want a daily prompt presented before the textarea unlocks so that I start from a real writing intention.
- **RFH-US-002** (traces: RFH-PR-002): As a trust operator, I want signal collection to begin at page load so that verification covers the whole session rather than only the typing.
- **RFH-US-003** (traces: RFH-PR-003): As a writer, I want my human-confidence score visible and updating at least every 500ms so that verification stays transparent while I write.
- **RFH-US-004** (traces: RFH-PR-004): As a writer, I want the submit button to unlock at the minimum length and paste events to raise a visible, non-blocking notice so that the rules are clear without interrupting me.
- **RFH-US-005** (traces: RFH-PR-005): As a trust operator, I want the composite score computed client-side at 60% behavioral and 40% content, with the signal payload sent on submission, so that post content never leaves the client for scoring.
- **RFH-US-006** (traces: RFH-PR-006): As a writer, I want a verdict within 2 seconds that publishes at 70 or above, holds 40 to 69 as suspect with a plain-language explanation, and blocks below 40, so that submission feels immediate and understandable.
- **RFH-US-007** (traces: RFH-PR-007): As a returning writer with 10 or more posts, I want scoring relative to my own baseline so that my natural style is judged against me instead of a generic threshold.
- **RFH-US-008** (traces: RFH-PR-008): As a trust operator, I want fingerprints updated only from verified-human submissions and accounts flagged when a score drops more than 20 points below their rolling mean, so that the baseline stays trustworthy.
- **RFH-US-009** (traces: RFH-PR-009): As a trust operator, I want asynchronous network fingerprint comparison within 60 seconds that flags clusters of 5 or more similar accounts, so that coordinated accounts surface without slowing submissions.
- **RFH-US-010** (traces: RFH-PR-010): As an administrator, I want per-user signal history, verdict override, a network cluster view, an audit log, and a daily metrics dashboard so that I can investigate and correct the system's decisions.
