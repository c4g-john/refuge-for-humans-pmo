---
kind: frnfr
id: RFH-frnfr
project: PRJ-001-RFH
title: Refuge for Humans — Functional & Non-Functional Requirements
owner: johntanner
status: approved
---

## Overview

Detailed functional requirements for signal collection and fingerprint
management, and the non-functional requirements from §10 of the source BRD.
All behavioral signals are collected client-side; no post content is
transmitted to the verification layer.

## Functional Requirements

- **RFH-FR-001** (traces: RFH-PR-011): The client shall collect keystroke signals (inter-key intervals, per-key dwell, WPM curve over rolling windows, backspace count and clustering, burst–pause rhythm with gaps over 300ms flagged as pauses and over 1,500ms as thinking pauses, first-keypress delay).
- **RFH-FR-002** (traces: RFH-PR-011): The client shall collect mouse and pointer signals (cursor-path linearity per segment, click coordinate distribution, hover behavior, scroll depth/velocity, and scroll event count).
- **RFH-FR-003** (traces: RFH-PR-011): The client shall collect session and focus signals (focus/blur events with durations, total time on page before submit, interaction-sequence entropy, and device/input method for normalization).
- **RFH-FR-004** (traces: RFH-PR-011): The client shall collect text-evolution signals (character-count snapshots every 3 seconds, paste-event count and pasted-character ratio, nonlinear-editing depth and frequency).
- **RFH-FR-005** (traces: RFH-PR-005): The client shall compute the content-heuristic score from the submitted text without transmitting content to any external service (AI-phrase density, sentence-length uniformity, contraction frequency, lexical diversity, passive-voice density, AI-typical sentence openers, first-person specificity, hedging density, emotional vocabulary).
- **RFH-FR-006** (traces: RFH-PR-005): The submission payload shall carry the fields of §8.1 of the source BRD (session/user/prompt identifiers, timestamps, the signal arrays, the three scores, flags, verdict, and the behavioral fingerprint hash).
- **RFH-FR-007** (traces: RFH-PR-008): The fingerprint store shall maintain the per-user rolling aggregates of §8.2 (typing speed and dwell means/variances, burst-gap and correction rates, content-style aggregates, rolling composite mean and variance, and network cluster id).

## Non-Functional Requirements

- **RFH-NFR-001** (traces: RFH-PR-012): Client-side scoring shall complete within 100ms of submission.
- **RFH-NFR-002** (traces: RFH-PR-012): Signal collection shall add no perceptible latency, with a JavaScript execution budget under 5ms per event.
- **RFH-NFR-003** (traces: RFH-PR-013): The verification service shall target 99.9% uptime, and in degraded mode (backend unavailable) the client-side score alone shall determine the verdict.
- **RFH-NFR-004** (traces: RFH-PR-014): The signal ingestion pipeline shall handle a burst load of 10,000 concurrent submissions without degradation.
- **RFH-NFR-005** (traces: RFH-PR-015): Signal payloads shall be signed client-side and the signature validated by the backend before processing.
- **RFH-NFR-006** (traces: RFH-PR-018): Full signal collection shall work on current Chrome, Firefox, Safari, and Edge, with graceful degradation of mouse signals on mobile browsers.
- **RFH-NFR-007** (traces: RFH-PR-016): The verification layer shall not penalize users with motor disabilities or atypical input patterns; per-user baseline calibration shall mitigate population-level bias.
- **RFH-NFR-009** (traces: RFH-PR-006): The backend response that determines the verdict, including fingerprint retrieval, shall complete within 2 seconds of submission so the verdict deadline holds.
- **RFH-NFR-008** (traces: RFH-PR-017): Raw signal payloads shall be retained for 90 days and aggregated fingerprints for the account's life; users may request deletion (removing raw payloads and resetting the fingerprint); signal data shall be encrypted at rest and in transit and never shared with third parties or used for advertising.
