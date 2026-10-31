# Project Proposal — Explainable Multilingual Fraud Risk Assessment

**Proposed official English topic:** Development of a Multilingual Mobile Application for Explainable Fraud Risk Assessment in Text Messages

**Proposed Russian topic:** Разработка многоязычного мобильного приложения для объяснимой оценки риска мошенничества в текстовых сообщениях

**Programme / group:** Software Engineering / SE-2413  
**Team:** Nurbolat Seilkhanov (Mobile / Flutter), Dulat Amangeldi (AI/ML), Erasyl Zhagypar (Backend)  
**Supervisor:** Turarova Marzhan Kabdykalievna  
**Revision:** 31 October 2026; pending university/supervisor approval. The initial proposal was prepared on 22 October.

## 1. Problem statement
Mobile users receive legitimate and potentially fraudulent text messages that may imitate banks, government services or delivery providers. Generic binary phishing detection is not always an adequate user-facing outcome: users also need a cautious assessment of potential risk and concrete, understandable warning signs. In Kazakhstan, evaluating Russian and Kazakh texts separately is especially relevant. The prevalence of scams and user needs require verifiable sources and appropriately documented user research.

## 2. Aim and scope
Design, implement and evaluate an Android-first mobile application that accepts manually entered Kazakh or Russian text messages, produces an NLP/ML-assisted fraud risk assessment, and provides understandable indicators supporting the warning.

**Research focus:** (i) multilingual performance; (ii) mapping observable text indicators to understandable explanations; (iii) evaluation of model errors and explanation validity. This is a revised task definition, **not an assertion that no similar thesis exists**.

## 3. Objectives
1. Review scientific literature, existing systems and verified user needs.
2. Audit licensed datasets, language coverage, labels, deduplication and privacy.
3. Establish TF-IDF + Logistic Regression / Linear SVM baselines.
4. Explore a multilingual alternative only if data and resources permit.
5. Specify evidence-linked indicators (e.g., suspicious URL patterns, pressure wording, request for a verification code) and test whether the explanation reflects actual extracted signals.
6. Build Flutter UX, FastAPI integration, validation and user-friendly error handling.
7. Measure precision, recall, macro-F1, false positives/negatives, RU/KZ performance, real response latency, and explanation usefulness.
8. Deliver a reproducible demonstration, documentation and defense.

## 4. Users
Android smartphone users in Kazakhstan who want to check a suspicious message before acting. Users who prefer a clear risk explanation rather than an opaque label are an intended audience.

## 5. In-scope MVP
- Manual text entry/paste, input validation, analysis request.
- Predicted risk category with careful advisory language.
- Real extracted indicators with short human-readable explanation; never fabricate rationale.
- Handling service timeout, network and input errors.
- Russian/Kazakh text handling with separately reported empirical limits.
- Default avoidance of persistent raw-message storage.

## 6. Excluded from mandatory MVP
- Automatic reading of SMS/notifications/private chats.
- Required iOS app or on-device / offline inference.
- Automatic blocking, message interception, account access.
- Guaranteed scam identification or unsupported model certainty claims.

## 7. Preliminary architecture
Flutter / Android → HTTPS `POST /api/v1/analyze` → FastAPI → NLP classifier and indicator extraction → response with risk level and explanation. Candidate components are subject to engineering and supervisor review.

## 8. Planned evaluation
Held-out, leakage-controlled labelled dataset; class-wise precision/recall/F1 and macro-F1; confusion matrices; RU, KZ and code-switched test sets where supported. Explanation checks: indicator-to-source alignment, comprehensibility and cautiousness. App and backend: contract tests, error paths, latency, logs and basic usability. Metrics and thresholds must be agreed after examining actual data.

## 9. Risks
Limited Kazakh examples; invalid cross-language generalizations; poorly supported explanations; class imbalance; sensitive content; false positives/negatives; delays; possible overlapping thesis topics.

## 10. Status / next decisions
The implementation, performance claims and supervisor approval are **pending**. Confirm official new title, uniqueness, data sources, planned evaluation thresholds, future deadlines, UX prototype and API contract. Task tracking is in YouTrack (PDA), code history in GitHub.
