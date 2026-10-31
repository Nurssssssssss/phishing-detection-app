# Updated Thesis Work Plan — 31 October 2026

**Topic:** Development of a Multilingual Mobile Application for Explainable Fraud Risk Assessment in Text Messages  
**RU:** Разработка многоязычного мобильного приложения для объяснимой оценки риска мошенничества в текстовых сообщениях  
**Students:** Nurbolat Seilkhanov · Dulat Amangeldi · Erasyl Zhagypar  
**Supervisor:** Turarova Marzhan Kabdykalievna  
**Group:** SE-2413  
**Status:** Draft proposed milestones; official university dates are not yet confirmed.

## Continuity with initial plan (13–24 Oct 2026)
Retain the original scope: manual check of text messages, Flutter/Android, FastAPI/Python, NLP/ML baseline, Russian and Kazakh, privacy by default, GitHub/YouTrack and the three team roles. Historical milestone completion must be verified from actual artifacts and logs rather than inferred from old due dates.

## Scope and innovation
The project is an explainable risk-assessment tool, not merely a binary spam/phishing detector. The system will display a cautious risk category and signs supported by observed features. Evaluate model performance by language and check explanation relevance/clarity.

## Roles
| Owner | Workstream | Acceptance evidence |
|---|---|---|
| Nurbolat | Flutter UI, UX, API integration, coordination and thesis documents | Working input/result/error flows, explanations UI, linked commits/screenshots |
| Dulat | Literature, data, NLP/ML baseline, explainability and multilingual testing | Dataset card, reproducible scripts, RU/KZ metrics, explanation verification |
| Erasyl | FastAPI, contract, validation, security, deployment and integration | API endpoints, tests, logging review, deployed or local reproducible demonstration |

## Proposed checkpoints
| Period | Work package | Verifiable deliverable |
|---|---|---|
| 31 Oct–3 Nov 2026 | Re-submit topic; align scope, README, requirements and architecture | Supervisor decision + revision PR |
| 4–15 Nov 2026 | Reconcile requirements and UX; audit datasets and licences | SRS, UI mockups, Data Card, language-test plan |
| 16–30 Nov 2026 | Baseline training and evaluation | Reproducible TF-IDF + classifier with held-out metrics |
| 1–20 Dec 2026 | FastAPI endpoint, Flutter main flow | End-to-end synthetic-message demo |
| 21 Dec–20 Jan 2027 | Robust integration, errors, basic privacy/usability | Integrated and tested MVP |
| 21 Jan–28 Feb 2027 | Model comparison, RU/KZ evaluation and explanations | Evaluation log, error analysis and evidence-linked explanations |
| 1–31 Mar 2027 | Functional/integration/UX testing and thesis drafting | Test report, stabilized MVP, thesis draft |
| 1–30 Apr 2027 | Final dissertation documentation, slides, demo | Defense package and rehearsal |

## Evaluation requirements
- Data: source/licence, deduplication, privacy, train/validation/test isolation, no pre-split augmentation.
- Classification: precision, recall, class-wise F1, macro-F1, confusion matrix, error categories, measured RU/KZ breakdown.
- Explanations: only emit indicators actually observed by the system; include clear disclaimer; investigate incorrect/misleading reasons with user tests.
- Service and UI: API contract, invalid data/network failure, request latency under defined test conditions, accessible UI.
- No raw message storage/logging by default. Never add OTPs or personal messages to Git.
- Do not promise numerical scores until the benchmark and supervisor criteria exist.

## Open issues for supervisor
1. Confirmation of revised thesis title and non-duplication.
2. Mandatory languages and available labels for Kazakh/Russian.
3. Explainability method and quality criteria.
4. Formal dates for milestones, pre-defense and defense.
5. Approved sources, implementation/deployment choices and responsibilities.

**Note:** This Markdown plan accompanies the longer Russian Word work plan prepared on 31 October 2026; future dates are proposals, not official institutional deadlines.
