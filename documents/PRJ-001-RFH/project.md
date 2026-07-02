---
kind: project
id: PRJ-001-RFH
code: RFH
name: Refuge for Humans
sponsor: C4G Enterprises Inc.
status: proposed
profile: lean-startup
---

## Overview

Refuge for Humans is a social posting platform that protects authentic human
expression by verifying human authorship through passive behavioral biometrics
(how a user interacts with the page while writing) and content heuristics
(linguistic patterns). Verification is invisible until it matters: posts that
fail are blocked or flagged before publication, and the platform grows more
accurate with use as per-user fingerprints and cross-account analysis compound.

<!-- TODO: sponsor is currently the company; name the accountable individual. -->

## Scope

In scope: client-side behavioral-signal collection, content heuristics,
real-time scoring and verdicts, per-user fingerprinting, network-level bot
detection, and the writing and administration interfaces. Out of scope for
v1.0: server-side LLM classifiers, non-text post verification, real-time human
review of suspect posts, the third-party verification API (v2.0), a mobile
native SDK, and external identity-verification integrations.
