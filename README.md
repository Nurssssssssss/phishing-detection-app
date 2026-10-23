# Phishing Detection App

**Status:** Planning / Pre-defense preparation (October 2026)

Mobile application concept for identifying phishing and fraudulent text messages for users in Kazakhstan. The MVP allows users to manually paste text and receive an explanatory risk assessment. **The project is not a finished application.**

## Problem
Fraudulent messages may imitate banks, eGov/1414, or delivery companies. Users need help recognizing suspicious signs. The solution is advisory and cannot guarantee that any message is safe or malicious.

## Team and responsibilities
- Nurbolat Seilkhanov — Mobile/Flutter, UX, API/backend planning, architecture, GitHub and YouTrack coordination (temporarily covering backend responsibilities).
- Dulat Amangeldi — AI/ML, literature review, dataset research and evaluation.
- Team composition and reassignment: **pending supervisor confirmation**.
- Supervisor listed in the planning document: Turarova Marzhan Kabdykalievna.

## MVP scope
1. User manually inputs/pastes a text message.
2. Android Flutter app sends a request to the backend.
3. Backend validates input and invokes a detection model.
4. App displays risk category and available reasons, with a disclaimer.
5. App handles network and input errors.

**Outside required MVP:** automatic collection of SMS/notifications, full device monitoring, access to user accounts, or claims of guaranteed detection.

## Candidate technologies (pending comparative review)
- Client: Flutter/Dart, Android first.
- API: Python/FastAPI.
- Model: Python, scikit-learn NLP baseline; alternatives to be compared.
- Storage: minimal; avoid retaining message content by default.

## Project links
- YouTrack: **TODO: insert actual link**
- Figma prototype: **TODO: insert actual link**
- Supervisor feedback: [docs/supervisor-feedback.md](docs/supervisor-feedback.md)

## Documentation
- [Proposal](docs/project-proposal.md)
- [User research](docs/user-research.md)
- [Literature review](docs/literature-review.md)
- [Dataset research](docs/dataset-research.md)
- [Competitor analysis](docs/competitor-analysis.md)
- [Technology comparison](docs/technology-comparison.md)
- [Requirements](docs/requirements.md)
- [Architecture](docs/architecture.md)
- [Test plan](docs/test-plan.md)
- [Supervisor feedback](docs/supervisor-feedback.md)

## Diagrams and prototype
- Editable Mermaid sources in `diagrams/`: context, use cases, components.
- Export readable PNG/SVG versions before submission (TODO).
- UX wireframe plan in `prototype/README.md`; actual Figma link required (TODO).

## Current status / remaining work
This repository contains **initial planning drafts**, not verified completed research. Required tasks: 3–5 genuine user discussions, >=12 genuine sources including >=8 scientific publications, evidence-backed comparison of 3–5 real systems against 6–10 criteria, decision comparisons, UX prototype, finalized acceptance tests, supervisor review, populated YouTrack and authentic gradual Git history.

## Run and test
No executable MVP yet. Setup and testing commands will be added once code exists.

## Privacy and ethics
Do not upload real messages, OTP codes, passwords, private datasets or secrets. Use synthetic examples. Research participants must be informed about the use of their feedback and their responses should be anonymized.


## Project Management

**YouTrack:** https://aitu-se2413-phishing-2026.youtrack.cloud/projects/PDA

**GitHub:** https://github.com/Nurssssssssss/phishing-detection-app

**Current stage:** Pre-defense preparation

**Deadline:** October 24, 2026