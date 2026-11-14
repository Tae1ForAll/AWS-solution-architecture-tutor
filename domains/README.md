# Exam Domains – AWS Certified Solutions Architect – Associate (SAA-C03)

> **Source:** `resources/exam-guide/solutions-architect-associate-03.pdf`
> (SAA-C03 exam guide, version 1.1, published October 29, 2026). Verified 2026-11-12.

## Exam Facts (from the guide)

| Item | Value |
|------|-------|
| Questions | 50 scored + 15 unscored (unscored are not identified) = 65 |
| Question types | Multiple choice (1 of 4) · Multiple response (2+ of 5+) |
| Guessing | Unanswered = wrong; no penalty for guessing |
| Scoring | Scaled 100–1,000 · **pass = 720** · compensatory (pass overall, not per domain) |
| Target candidate | ≥ 1 year hands-on experience designing AWS solutions |
| Framework | Solutions are judged against the AWS Well-Architected Framework |

> Time limit and price are **not** in the guide — check the AWS Certification website.

## Domains

| # | Domain | Weight | ≈ scored Qs* | Folder |
|---|--------|--------|--------------|--------|
| 1 | Design Secure Architectures | 30% | ~15 | `1-design-secure-architectures/` |
| 2 | Design Resilient Architectures | 26% | ~13 | `2-design-resilient-architectures/` |
| 3 | Design High-Performing Architectures | 24% | ~12 | `3-design-high-performing-architectures/` |
| 4 | Design Cost-Optimized Architectures | 20% | ~10 | `4-design-cost-optimized-architectures/` |

\* My own estimate (weight × 50 scored questions), not stated in the guide.

Each domain folder contains:

- `README.md` – task statements (from the guide) and learning sections (my organisation)
- `lessons/` – one Markdown file per lesson taught (`NN-topic-name.md`)

Service scope (in / out) is summarised in `resources/exam-guide/scope-summary.md`.

Suggested order: 1 → 2 → 3 → 4 (security and resilience concepts are
reused heavily in the later domains).
