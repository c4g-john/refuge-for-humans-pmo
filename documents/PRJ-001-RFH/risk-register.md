---
kind: risk-register
id: RFH-risk-register
project: PRJ-001-RFH
title: Refuge for Humans — Risk Register
owner: johntanner
status: draft
---

## Overview

Risks from §13 of the source BRD. The source supplies a description and a
mitigation for each risk but no probability, impact, or owner — the audit will
(correctly) flag every entry until those are assigned.

## Risks

- **RFH-RISK-001** (threatens: RFH-BR-001): Adversarial simulation — bot operators instrument browsers to simulate behavioral signals. Response: per-user baselines make simulation cost-prohibitive at scale; network detection catches coordinated infrastructure.
- **RFH-RISK-002** (threatens: RFH-BR-002): False-positive bias — users with atypical typing patterns (disabilities, non-native keyboards, mobile) disproportionately flagged. Response: per-user baseline calibration after 10 posts; manual appeal path; administrator override.
- **RFH-RISK-003** (threatens: RFH-BR-001): Signal sparsity — short posts do not generate sufficient behavioral signal for reliable scoring. Response: minimum character threshold enforced; content heuristics weighted more heavily for short submissions.
- **RFH-RISK-004** (threatens: RFH-BR-004): Fingerprint drift — legitimate users whose behavior changes over time flagged as suspicious. Response: rolling-average fingerprint tolerates gradual drift; sharp deviation triggers a flag, not a block.
- **RFH-RISK-005** (threatens: RFH-BR-007): Regulatory exposure — behavioral signal collection is subject to privacy regulation in some jurisdictions. Response: no PII in the signal payload; data-minimization design; user-accessible deletion; legal review required before EU launch.
