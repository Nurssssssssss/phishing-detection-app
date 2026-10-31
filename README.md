# Explainable Multilingual Fraud Risk Assessment — Thesis Project

**Official topic proposed for approval:** Development of a Multilingual Mobile Application for Explainable Fraud Risk Assessment in Text Messages

**Русское название:** Разработка многоязычного мобильного приложения для объяснимой оценки риска мошенничества в текстовых сообщениях

**Status:** Thesis topic revision submitted for supervisor review (31 October 2026). This repository currently contains design, research and pre-implementation materials; **a finished mobile application or validated detection model is not yet available**.

## Research focus and differentiation
Instead of only detecting phishing, the project will **assess message fraud risk and present understandable, evidence-linked warning indicators**. It targets **Kazakh and Russian** text messages and relevant Kazakhstan scenarios. The research includes language-specific model evaluation and assessment of explanation accuracy/usability.

The new title has **not** yet been approved by AITU. Its distinctness from any unknown duplicate topic must be checked by the supervisor.

## Team
- **Nurbolat Seilkhanov** — Flutter/Android, UX, results/explanations interface, documentation and project coordination; temporary support for backend documentation.
- **Dulat Amangeldi** — NLP/ML, datasets, baseline, cross-language evaluation and explanation verification.
- **Erasyl Zhagypar** — FastAPI backend, validation, integration, security and deployment.
- **Supervisor:** Turarova Marzhan Kabdykalievna.
- **Programme / group:** Software Engineering / SE-2413.

## Mandatory MVP (planned)
1. User manually enters or pastes suspicious message text.
2. Flutter sends a validated request over HTTPS to `POST /api/v1/analyze`.
3. FastAPI invokes the NLP/ML risk assessment and an indicator extraction method.
4. The app displays a cautious risk category and **indicators actually supported by the analysis**.
5. The app handles input/network errors and states that the result is advisory.

**Excluded from mandatory MVP:** automatic reading/interception of SMS or chat messages, required iOS release, guaranteed detection, unapproved storage of private texts, and mandatory on-device inference.

## Candidate stack (not yet fully implemented)
Flutter/Dart (Android first) → FastAPI/Python → NLP/ML (TF-IDF + Logistic Regression / Linear SVM baseline; optional multilingual advanced model). Server-side message storage is not required by default.

## Project resources
- [GitHub repository](https://github.com/Nurssssssssss/phishing-detection-app)
- [Pull Requests](https://github.com/Nurssssssssss/phishing-detection-app/pulls)
- [YouTrack PDA](https://aitu-se2413-phishing-2026.youtrack.cloud/projects/PDA)
- [Documentation](docs/)
- [Diagrams](diagrams/)
- [Proposed topic revision and change log](docs/topic-change-2026-10-31.md)
- [Updated thesis work plan](docs/thesis-work-plan-2026-10-31.md)
- [Project proposal](docs/project-proposal.md)
- [Requirements](docs/requirements.md)
- [Architecture](docs/architecture.md)
- [Dataset research](docs/dataset-research.md)
- [Technology comparison](docs/technology-comparison.md)
- [Evaluation plan](docs/verification_and_evaluation_plan.md)
- [Literature review](docs/final_literature_review.md)
- [Supervisor feedback](docs/supervisor-feedback.md)

**UX prototype:** draft images under [prototype/](prototype/); a verified Figma link has not been provided.

## Current evidence and known limitations
Research drafts and architecture diagrams exist, but the dataset-research sheet has no approved final dataset. Survey percentages in `validation_of_relevance.md` require original anonymized responses/methodology for independent verification. Some literature claims require source-level checking before final thesis submission.

**Pull request #5** (additional data-flow diagram) was still open when this revision was prepared; its files must not be described as present in `main` until merged.

## Privacy and ethics
Never commit raw personal messages, OTP codes, keys or secrets. Do not persist message bodies or log them by default. Risk levels are estimates and must not be presented as guarantees that a message is safe or malicious.
