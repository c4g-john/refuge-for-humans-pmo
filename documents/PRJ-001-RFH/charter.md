---
kind: charter
project: PRJ-001-RFH
id: RFH-charter
title: Refuge for Humans — Project Charter
sponsor: John Tanner
budget:
  amount: 1200
  currency: USD
dates:
  created: 2026-03-01   # "March 2026" per the source document
  target: 2026-08-31
status: approved
---

## Objective

Build the platform where authentic human expression is structurally protected,
not just moderated: verify human authorship passively and continuously via
behavioral biometrics (60% of the composite score) and content heuristics
(40%), blocking or flagging AI-generated posts before publication, with
per-user fingerprints that make detection more accurate with use.

## Success Criteria

- More than 95% of AI-generated posts blocked before publication at steady state.
- Fewer than 2% of genuine human posts incorrectly flagged.
- Per-user baseline scoring outperforms generic threshold scoring by 30% or more after 10 posts.
- Coordinated bot clusters of 5 or more accounts identified within 48 hours of activation.
- Fewer than 1% of users contact support regarding verification-related issues.

## Scope

In scope: behavioral signal collection (keystroke, mouse, session/focus, text
evolution), content heuristics, scoring and verdicts, fingerprint-relative and
network-level detection, the writing interface, and administration tooling.
Out of scope for v1.0: server-side AI detection via external APIs or LLM
classifiers; image, video, or audio verification; real-time human review of
suspect posts; the third-party verification API; a mobile native SDK; external
identity-verification integrations.

## Milestones

- TODO: the source document defines no delivery milestones — add at least an
  MVP date and a launch date.

## Risks

- Bot operators instrument browsers to simulate behavioral signals. Owner: TODO. Mitigation: per-user baselines make simulation cost-prohibitive at scale; network detection catches coordinated infrastructure.
- Users with atypical typing patterns are disproportionately flagged. Owner: TODO. Mitigation: per-user baseline calibration after 10 posts; manual appeal path; administrator override.

## Approval

Draft — pending review per the source document. TODO: name the accountable
sponsor and approvers; the source lists only "C4G Enterprises Inc." and
"Status: Draft — For Review".
