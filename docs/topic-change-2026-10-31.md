# Thesis topic clarification — 31 October 2026

**Status: PROPOSED, pending official acceptance**

**Old topic (RU):** Разработка приложения для обнаружения фишинговых и мошеннических сообщений.

**New topic (EN):** Development of a Multilingual Mobile Application for Explainable Fraud Risk Assessment in Text Messages

**New topic (RU):** Разработка многоязычного мобильного приложения для объяснимой оценки риска мошенничества в текстовых сообщениях

## Reason
AITU's topic system reported: "Тема дублируется, рекомендуется пересмотреть задачу" and another similarity warning on 31 October 2026. We do not know the exact other thesis, so do not assert that a new name alone guarantees uniqueness.

## Revised task
The deliverable is an Android-first mobile text-message risk assessment application using Kazakh/Russian NLP/ML and **explainable user warnings**. A result contains a cautious risk category plus concrete indicators grounded in what the pipeline extracted, not an invented post-hoc explanation.

## What is unchanged
- Manual entry/paste MVP and no automatic SMS interception.
- Flutter / Android, FastAPI / Python, baseline NLP/ML evaluation.
- Kazakh and Russian as target analysis languages.
- Privacy by default: no persistent raw text.
- Existing three-person roles, GitHub/YouTrack organization, initial architecture.

## What is clarified
- Title, objective and comparison with other projects.
- Explicit requirement to verify explanation fidelity and user comprehension.
- Per-language metrics and language coverage limitations.
- Conceptual output fields: `risk_level`, `language`, `indicators`, `explanation`, `disclaimer` (subject to contract review).
- Measured end-to-end latency for server inference instead of unsupported mobile/offline speed claims.

## Approval checklist
- [ ] Scientific supervisor confirms title in English and Russian.
- [ ] AITU verifies no relevant duplication with another accepted topic.
- [ ] Team agrees on risk categories and truthful indicator method.
- [ ] ML datasets, per-language testing and reporting criteria agreed.
- [ ] Delivery schedule aligned with actual institutional deadlines.

## Review notes
Existing `docs/validation_of_relevance.md` reports a user survey with 85.7% iOS respondents. This does not justify changing the mandatory Android-first MVP without supervisor direction. Evidence, sample size and methodology must be attached for final academic claims.

Existing `docs/verification_and_evaluation_plan.md` referred to on-device `≤30ms` and performance gains as if they were agreed objectives; those are not supported for the current Flutter→FastAPI MVP without benchmarks. Treat as optional research hypotheses, not achievements.

PR #5 on the data-flow diagram was open on the review date and must be merged/reviewed independently.
