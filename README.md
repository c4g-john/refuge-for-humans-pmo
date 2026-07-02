# Refuge for Humans — PMO

[![pmo docs](https://img.shields.io/endpoint?url=https%3A%2F%2Fc4g-john.github.io%2Frefuge-for-humans-pmo%2Fbadge.json)](https://c4g-john.github.io/refuge-for-humans-pmo/)

The Refuge for Humans project run as
[PMO as Code](https://c4g-john.github.io/pmo-as-code/): the document spine under
`documents/PRJ-001-RFH/`, gated by [docassert](https://github.com/c4g-john/docassert)
on every pull request, converted faithfully from `Refuge for Humans BRD.docx`
(v1.0, March 2026).

**Faithful over passing:** where the source BRD has gaps, the audit reports
them. Everything is `status: draft`, so (as of docassert 0.7.0) the gaps are
**advisory** — drafts merge; flipping a document to `proposed` turns its
completeness gate on. The to-do list:

- **Charter** — the source names no **budget** and no **target date**; sponsor
  is the company, not a person. Milestones are missing entirely.
- **Risk register** — all five risks lack **probability, impact, and owner**
  (the source gives only descriptions + mitigations).
- **Coverage** — 6 of 10 product requirements have **no acceptance criterion**
  yet (see `docassert status --project PRJ-001-RFH`).

Fix them in PRs; the gate re-checks automatically.

```bash
pipx install docassert
docassert validate documents/**/*.md
docassert status --project PRJ-001-RFH
```

**Live dashboard:** https://c4g-john.github.io/refuge-for-humans-pmo/ —
rebuilt on every push to `main`. `STATUS.md` is the committed snapshot.
