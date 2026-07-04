# Refuge for Humans — PMO

[![pmo docs](https://img.shields.io/endpoint?url=https%3A%2F%2Fc4g-john.github.io%2Frefuge-for-humans-pmo%2Fbadge.json)](https://c4g-john.github.io/refuge-for-humans-pmo/)

The Refuge for Humans project run as
[PMO as Code](https://c4g-john.github.io/pmo-as-code/): the document spine under
`documents/PRJ-001-RFH/`, gated by [docassert](https://github.com/c4g-john/docassert)
on every pull request, converted faithfully from `Refuge for Humans BRD.docx`
(v1.0, March 2026).

**Faithful over passing.** At import, nothing was invented to make checks
green — the audit reported the source document's real gaps instead: a charter
with no budget, target date, or milestones; five risks with no probability,
impact, or owner; six of ten product requirements without an acceptance
criterion. Every one of those gaps was then closed the only way this repo
allows: through pull requests that the gate re-checked. Today the register is
complete, every business requirement traces through requirements, acceptance
criteria, and test cases, and the documents are approved — any new gap shows
up on the dashboard, not in this README.

Delivery runs from the documents: the docassert bridge scaffolds Features and
Stories into [refuge-for-humans-app](https://github.com/c4g-john/refuge-for-humans-app)
from the approved user stories, and polices scope against them.

```bash
pipx install docassert
docassert validate documents/**/*.md
docassert status --project PRJ-001-RFH
```

**Live dashboard:** https://c4g-john.github.io/refuge-for-humans-pmo/ —
rebuilt on every push to `main`. `STATUS.md` is the committed snapshot.
