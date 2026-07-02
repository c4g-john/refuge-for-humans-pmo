# Refuge for Humans — PMO

**Confidential — private repo.** The Refuge for Humans project run as
[PMO as Code](https://c4g-john.github.io/pmo-as-code/): the document spine under
`documents/PRJ-001-RFH/`, gated by [docassert](https://github.com/c4g-john/docassert)
on every pull request, converted faithfully from `Refuge for Humans BRD.docx`
(v1.0, March 2026).

**Faithful over passing:** where the source BRD has gaps, the documents fail the
audit *on purpose*. Current blocking findings to resolve:

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

The status dashboard workflow is present but gated off (`DOCASSERT_PAGES`
variable) — GitHub Pages on a private repo depends on the account plan.
`STATUS.md` is the committed snapshot meanwhile.
