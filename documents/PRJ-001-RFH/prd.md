---
kind: prd
id: RFH-prd
project: PRJ-001-RFH
title: Refuge for Humans — Product Requirements
owner: johntanner
status: approved
---

## Overview

The product verifies human authorship invisibly during writing: signals are
collected client-side from page load, scored in real time, and combined into a
composite human-confidence score (60% behavioral, 40% content) that yields a
verdict on submission. Fingerprint-relative scoring takes over after 10 posts;
network-level comparison runs asynchronously. The experience feels like a
thoughtful writing space, not a security checkpoint.

## Product Requirements

- **RFH-PR-001** (traces: RFH-BR-003): The platform shall present a daily prompt before the writing textarea is active.
- **RFH-PR-002** (traces: RFH-BR-003): Signal collection shall begin at page load, before the user has typed anything.
- **RFH-PR-003** (traces: RFH-BR-006): The human confidence score shall be displayed in real time, updating at minimum every 500ms, with individual signal indicators visible during writing.
- **RFH-PR-004** (traces: RFH-BR-001): The submit button shall be disabled until a configurable minimum character threshold (default 20) is reached, so that every submission carries enough behavioral signal for a reliable verdict, and paste events shall trigger a visible, non-blocking notification so pasted text is weighed by the content heuristics.
- **RFH-PR-005** (traces: RFH-BR-003): The composite score shall be calculated as 60% behavioral plus 40% content, both computed client-side, with the signal payload transmitted to the backend on submission regardless of score.
- **RFH-PR-006** (traces: RFH-BR-001): A verdict shall be returned within 2 seconds of submission: 70+ publishes, 40–69 is held as suspect with a plain-language explanation, below 40 is blocked with a plain-language explanation.
- **RFH-PR-007** (traces: RFH-BR-004): For users with 10 or more prior posts, the backend shall apply fingerprint-relative scoring, weighting sudden deviations from the user's baseline heavily regardless of absolute score.
- **RFH-PR-008** (traces: RFH-BR-004): The fingerprint shall update after each verified-human submission, exclude suspect-verdict submissions pending review, and flag accounts whose composite score drops more than 20 points below their rolling mean.
- **RFH-PR-009** (traces: RFH-BR-005): Network fingerprint comparison shall run asynchronously within 60 seconds of each submission, flagging clusters of 5 or more accounts with above-threshold similarity into the administrator investigation queue without affecting submission latency.
- **RFH-PR-010** (traces: RFH-BR-002, RFH-BR-005): Administrators shall have per-user signal history, fingerprint and verdict views, manual verdict override, a network cluster view, an audit log of administrative actions with timestamp and operator ID, and a daily metrics dashboard (post volume, bot block rate, suspect rate, false-positive reports).
- **RFH-PR-011** (traces: RFH-BR-003): The platform shall collect behavioral signals in four classes as inputs to the behavioral score: keystroke dynamics, mouse and pointer behavior, session and focus context, and text evolution.
- **RFH-PR-012** (traces: RFH-BR-006): Verification shall stay imperceptible while writing and instant at submission: signal collection shall keep a JavaScript execution budget under 5ms per event, and client-side scoring shall complete within 100ms of submission.
- **RFH-PR-013** (traces: RFH-BR-006): The verification service shall target 99.9% uptime, and when the backend is unavailable the client-side score alone shall determine the verdict so that publishing never stalls.
- **RFH-PR-014** (traces: RFH-BR-007): The signal ingestion pipeline shall sustain burst loads of 10,000 concurrent submissions without degradation.
- **RFH-PR-015** (traces: RFH-BR-001): Signal payloads shall be tamper-evident: signed client-side and validated by the backend before processing.
- **RFH-PR-016** (traces: RFH-BR-002): Verification shall not penalize users with motor disabilities or atypical input patterns; per-user baseline calibration shall keep false positives within the business threshold across user populations.
- **RFH-PR-017** (traces: RFH-BR-007): Signal data shall be privacy-bounded: raw payloads retained for 90 days, fingerprints for the life of the account, user-requested deletion honored (removing raw payloads and resetting the fingerprint), encryption at rest and in transit, and no third-party sharing or advertising use.
- **RFH-PR-018** (traces: RFH-BR-003): Full signal collection shall work on current Chrome, Firefox, Safari, and Edge, with graceful degradation of mouse signals on mobile browsers.

## Acceptance Criteria

- **RFH-AC-001** (verifies: RFH-PR-006): Given a submission with a composite score of 70 or above, when the verdict is returned, then the post proceeds to publication.
- **RFH-AC-002** (verifies: RFH-PR-006): Given a submission scoring below 40, when the verdict is returned, then publication is blocked and the user sees a plain-language explanation.
- **RFH-AC-003** (verifies: RFH-PR-006): Given any submission, when the payload reaches the backend, then the verdict is returned to the client within 2 seconds.
- **RFH-AC-004** (verifies: RFH-PR-003): Given a user writing in the textarea, when 500ms elapse, then the displayed human-confidence score has refreshed.
- **RFH-AC-005** (verifies: RFH-PR-007): Given a user with 10 or more prior posts, when a new post scores within generic thresholds but deviates sharply from the user's baseline, then the deviation dominates the verdict.
- **RFH-AC-006** (verifies: RFH-PR-009): Given 5 or more accounts sharing above-threshold fingerprint similarity, when the asynchronous comparison runs, then the cluster appears in the administrator investigation queue within 60 seconds of the last submission.
- **RFH-AC-007** (verifies: RFH-PR-001): Given a user opens the writing page, when the daily prompt has not yet been presented, then the writing textarea is inactive.
- **RFH-AC-008** (verifies: RFH-PR-002): Given a user loads the writing page, when the first keystroke occurs, then the collected signal timeline already contains events from before that keystroke.
- **RFH-AC-009** (verifies: RFH-PR-004): Given a draft below the configured minimum length (default 20 characters), when the user reaches the threshold, then the submit button changes from disabled to enabled.
- **RFH-AC-010** (verifies: RFH-PR-004): Given a user pastes text into the textarea, when the paste event fires, then a visible, non-blocking notification appears and typing is not interrupted.
- **RFH-AC-011** (verifies: RFH-PR-005): Given a submission with any composite score, when the client submits, then the signal payload is transmitted to the backend and the composite equals 60% behavioral plus 40% content.
- **RFH-AC-012** (verifies: RFH-PR-008): Given a suspect-verdict submission pending review, when fingerprints update, then that submission is excluded from the user's fingerprint.
- **RFH-AC-013** (verifies: RFH-PR-008): Given an account whose new composite score is more than 20 points below its rolling mean, when scoring completes, then the account is flagged.
- **RFH-AC-014** (verifies: RFH-PR-010): Given an administrator viewing a user, when the record opens, then signal history, fingerprint, and verdict views are available and a manual verdict override can be applied.
- **RFH-AC-015** (verifies: RFH-PR-010): Given any administrative action, when it completes, then the audit log holds an entry with timestamp and operator ID.
- **RFH-AC-016** (verifies: RFH-PR-010): Given the daily metrics dashboard, when an administrator opens it, then post volume, bot block rate, suspect rate, and false-positive reports are shown.
- **RFH-AC-017** (verifies: RFH-PR-011): Given a completed writing session, when the submission payload is inspected, then it carries signals from all four classes: keystroke dynamics, pointer behavior, session and focus context, and text evolution.
- **RFH-AC-018** (verifies: RFH-PR-012): Given collection active during writing, when any signal handler executes, then it completes within 5ms; and when client-side scoring runs at submission, then it completes within 100ms.
- **RFH-AC-019** (verifies: RFH-PR-013): Given the backend is unreachable, when a user submits, then the client-side score alone determines the verdict and publishing proceeds without error.
- **RFH-AC-020** (verifies: RFH-PR-014): Given a burst of 10,000 concurrent submissions, when the ingestion pipeline processes them, then none are dropped and processing latency does not degrade.
- **RFH-AC-021** (verifies: RFH-PR-015): Given a signal payload altered after signing, when the backend validates the signature, then the payload is rejected before processing.
- **RFH-AC-022** (verifies: RFH-PR-016): Given sessions with atypical input patterns (assistive input, dictation cadence, non-native keyboards) scored against an established per-user baseline, when verdicts are compared with typical-input controls, then they do not differ systematically.
- **RFH-AC-023** (verifies: RFH-PR-017): Given a user's deletion request, when it completes, then raw signal payloads are removed and the fingerprint is reset; and given stored signal data, when audited, then it is encrypted at rest.
- **RFH-AC-024** (verifies: RFH-PR-018): Given current Chrome, Firefox, Safari, and Edge, when a writing session runs on each, then all four signal classes are collected; and given a mobile browser without pointer signals, when a session runs, then collection degrades gracefully and the remaining classes are captured.
