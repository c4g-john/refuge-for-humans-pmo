---
kind: brd
id: RFH-brd
project: PRJ-001-RFH
title: Refuge for Humans — Business Requirements
owner: johntanner
status: draft
---

## Purpose

AI-generated content has reached a quality threshold where it is largely
indistinguishable from human writing to casual readers, moderation algorithms,
and most detection tools — which analyse the output after the fact, not the act
of writing. Refuge for Humans protects authentic human expression by verifying
human authorship through passive behavioral biometrics and content heuristics,
blocking or flagging posts that fail verification before publication. The
platform compounds in accuracy with use through per-user fingerprints and
cross-account pattern analysis.

## Business Requirements

- **RFH-BR-001**: The business shall block AI-generated posts before publication at a rate above 95% at steady state.
- **RFH-BR-002**: The business shall keep false positives below 2% of genuine human posts.
- **RFH-BR-003**: The business shall establish behavioral biometrics as the primary human-verification layer, weighted at 60% of the composite score.
- **RFH-BR-004**: The business shall build per-user fingerprints that outperform generic threshold scoring by at least 30% after 10 posts.
- **RFH-BR-005**: The business shall identify coordinated bot networks of 5 or more accounts within 48 hours of activation.
- **RFH-BR-006**: The business shall hold verification friction below 1% of users contacting support about verification issues.
- **RFH-BR-007**: The business shall build a compounding behavioral and content signal corpus as a durable data asset.

## Out of Scope

Out of scope for Version 1.0: server-side AI content detection using external
APIs or LLM classifiers; image, video, or audio post verification; real-time
human agent review of suspect posts; the third-party verification API (planned
for v2.0); a mobile native SDK for signal collection; and integration with
external identity verification services.
