---
kind: user-story
id: RFH-user-story
project: PRJ-001-RFH
title: Refuge for Humans — User Stories
owner: johntanner
status: approved
---

## Overview

Stories decompose the product requirements into implementable slices, using
the roles the BRD names (writers and administrators, plus the trust operators
who run the verification layer). A requirement whose work splits into distinct
slices carries several stories; each story traces to its product requirement.
Acceptance criteria live with the PRD and are verified by the test cases.

## User Stories

- **RFH-US-001** (traces: RFH-PR-001): As a writer, I want a daily prompt presented before the textarea unlocks so that I start from a real writing intention.
- **RFH-US-002** (traces: RFH-PR-002): As a trust operator, I want signal collection to begin at page load so that verification covers the whole session rather than only the typing.
- **RFH-US-003** (traces: RFH-PR-003): As a writer, I want my human-confidence score visible and updating at least every 500ms so that verification stays transparent while I write.
- **RFH-US-004** (traces: RFH-PR-004): As a writer, I want the submit button to unlock once my draft reaches the minimum length so that the length rule is visible instead of surprising.
- **RFH-US-005** (traces: RFH-PR-005): As a trust operator, I want the composite assembled client-side at 60% behavioral and 40% content, with the signal payload sent on submission, so that post content never leaves the client for scoring.
- **RFH-US-006** (traces: RFH-PR-006): As a writer, I want a verdict that publishes at 70 or above, holds 40 to 69 as suspect with a plain-language explanation, and blocks below 40, so that the decision is understandable.
- **RFH-US-007** (traces: RFH-PR-007): As a returning writer with 10 or more posts, I want scoring relative to my own baseline so that my natural style is judged against me instead of a generic threshold.
- **RFH-US-008** (traces: RFH-PR-008): As a trust operator, I want fingerprints updated only from verified-human submissions, excluding suspect verdicts pending review, so that the baseline stays trustworthy.
- **RFH-US-009** (traces: RFH-PR-009): As a trust operator, I want network fingerprint comparison to run asynchronously within 60 seconds of each submission so that coordinated-account detection never slows publishing.
- **RFH-US-010** (traces: RFH-PR-010): As an administrator, I want per-user signal history with fingerprint and verdict views so that I can see exactly why the system decided what it did.
- **RFH-US-011** (traces: RFH-PR-002): As a trust operator, I want mouse, scroll, and focus activity from before the first keystroke captured into the session payload so that pre-typing behavior contributes to the score.
- **RFH-US-012** (traces: RFH-PR-003): As a writer, I want individual signal indicators visible while I write so that I can see which signals my score rests on.
- **RFH-US-013** (traces: RFH-PR-004): As a writer, I want pasting to raise a visible, non-blocking notice so that I know pasted text is weighed differently without losing my flow.
- **RFH-US-014** (traces: RFH-PR-005): As a trust operator, I want behavioral signals scored client-side so that the 60% behavioral component is available in real time while the user writes.
- **RFH-US-015** (traces: RFH-PR-005): As a trust operator, I want content heuristics scored client-side so that the 40% content component is computed without the text leaving the browser.
- **RFH-US-016** (traces: RFH-PR-006): As a trust operator, I want the backend to return a verdict within 2 seconds of submission so that publishing decisions keep pace with posting.
- **RFH-US-017** (traces: RFH-PR-008): As a trust operator, I want accounts flagged when a composite score drops more than 20 points below their rolling mean so that account takeovers and handoffs surface quickly.
- **RFH-US-018** (traces: RFH-PR-009): As an administrator, I want clusters of 5 or more similar accounts flagged into my investigation queue so that a coordinated network surfaces as one case.
- **RFH-US-019** (traces: RFH-PR-010): As an administrator, I want manual verdict override with every action recorded in an audit log carrying timestamp and operator ID so that corrections are possible and accountable.
- **RFH-US-020** (traces: RFH-PR-010): As an administrator, I want a network cluster view so that I can investigate related accounts together.
- **RFH-US-021** (traces: RFH-PR-010): As an administrator, I want a daily metrics dashboard showing post volume, bot block rate, suspect rate, and false-positive reports so that I can see whether verification is working.
