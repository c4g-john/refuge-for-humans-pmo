---
kind: risk-register
id: RFH-risk-register
project: PRJ-001-RFH
title: Refuge for Humans — Risk Register
owner: johntanner
status: approved
---

## Overview

Risks from §13 of the source BRD, which supplies a description and a
mitigation for each. Probability, impact, and owner were assigned when the
register was completed for approval.

## Risks

- **RFH-RISK-001** (threatens: RFH-BR-001): Adversarial simulation — bot operators instrument browsers to simulate behavioral signals. Probability: high. Impact: high. Owner: johntanner. Response: per-user baselines make simulation cost-prohibitive at scale; network detection catches coordinated infrastructure.
- **RFH-RISK-002** (threatens: RFH-BR-002): False-positive bias — users with atypical typing patterns (disabilities, non-native keyboards, mobile) disproportionately flagged. Probability: medium. Impact: high. Owner: johntanner. Response: per-user baseline calibration after 10 posts; manual appeal path; administrator override.
- **RFH-RISK-003** (threatens: RFH-BR-001): Signal sparsity — short posts do not generate sufficient behavioral signal for reliable scoring. Probability: high. Impact: medium. Owner: johntanner. Response: minimum character threshold enforced; content heuristics weighted more heavily for short submissions.
- **RFH-RISK-004** (threatens: RFH-BR-004): Fingerprint drift — legitimate users whose behavior changes over time flagged as suspicious. Probability: medium. Impact: medium. Owner: johntanner. Response: rolling-average fingerprint tolerates gradual drift; sharp deviation triggers a flag, not a block.
- **RFH-RISK-005** (threatens: RFH-BR-007): Regulatory exposure — behavioral signal collection is subject to privacy regulation in some jurisdictions. Probability: medium. Impact: high. Owner: johntanner. Response: no PII in the signal payload; data-minimization design; user-accessible deletion; legal review required before EU launch.
- **RFH-RISK-006** (threatens: RFH-BR-001): Degraded-mode verdicts — during backend outages the client-side score alone decides, weakening verification, and bot operators could time submissions to outage windows. Probability: low. Impact: medium. Owner: johntanner. Response: the 99.9% uptime target keeps the window rare, and per-user signal history (RFH-PR-010) lets administrators review outage-window verdicts after the fact.
