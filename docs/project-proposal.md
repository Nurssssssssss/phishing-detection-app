# Project Proposal — Phishing Detection App

**Program / group:** Software Engineering / SE-2413  
**Team:** Nurbolat Seilkhanov; Dulat Amangeldi (team update pending supervisor approval)  
**Supervisor:** Turarova Marzhan Kabdykalievna (per project plan)  
**Stage:** proposal draft, 22 October 2026

## 1. Problem statement
Suspicious text messages that impersonate banks, government services and logistics services are a risk for mobile users in Kazakhstan. Recipients may have difficulty noticing scam indicators, especially when messages are written in local languages and mimic familiar institutions. **The scale of the problem and the users' needs must be validated with real sources and interviews.**

## 2. Target users
Android smartphone users in Kazakhstan who receive messages in Russian or Kazakh and wish to check potentially suspicious text before taking action. Secondary audience: nontechnical users who benefit from clear, accessible explanations.

## 3. Goal
Design and subsequently build an Android-first mobile application that evaluates the risk of manually submitted messages using NLP/ML and shows an understandable, cautious explanation.

## 4. Objectives
1. Validate user needs through 3–5 discussions.
2. Study scientific methods and existing solutions.
3. Compare technical approaches and select a justified stack.
4. Specify testable functional and nonfunctional requirements.
5. Design system context, use cases and component architecture.
6. Prototype the main UI screens.
7. Define measurable validation criteria, baselines and test procedures.
8. Implement and evaluate the solution in subsequent development phases.

## 5. In-scope MVP
- Manual text entry / paste.
- Input validation and API submission.
- Risk assessment by a model (implementation planned).
- Risk explanation based on available evidence/indicators.
- Handling unsuccessful or unavailable analysis.

## 6. Out of scope for required MVP
- Automatic reading of SMS, notifications or private chats.
- Interception of personal messages without explicit user action.
- Guaranteed fraud detection or replacement for official verification.
- Required iOS release.

## 7. Preliminary architecture
Flutter/Dart client -> Python/FastAPI API -> NLP classifier -> risk response. These are **candidates**, not finalized choices; see technology comparison.

## 8. Expected deliverables
Proposal; evidence from interviews; literature review; comparison tables; requirements; editable diagrams; linked UX prototype; testing/evaluation plan; GitHub repository; YouTrack tracking and documented supervisor feedback.

## 9. Success criteria (proposed, pending agreement)
- Demonstrate end-to-end manual message assessment in later MVP.
- Report Precision, Recall and F1-score on held-out labeled samples, separately by language when feasible.
- Check functional requirements using reproducible test cases.
- Report failure cases, latency and limitations rather than claiming guaranteed accuracy.

## 10. Risks and mitigations
- Insufficient quality Kazakh dataset -> investigate coverage; document limitations; avoid unsupported performance promises.
- Sensitive message contents -> avoid raw-message storage by default; sanitize logs; use synthetic test cases.
- Model false negatives / false positives -> clear disclaimer and evaluation against baseline.
- Limited time / team capacity -> manual-input-only MVP and staged implementation.

## 11. Open approvals
Confirm team membership, supervisor, MVP scope, data legality, selected stack, metrics, meeting feedback.
