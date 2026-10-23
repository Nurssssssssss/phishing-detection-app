# Technology Comparison — Phishing Detection App

**Project:** Phishing Detection App  
**Program / Group:** Software Engineering / SE-2413  
**Team:** Nurbolat Seilkhanov, Dulat Amangeldi, Erasyl Zhagypar  
**YouTrack:** PDA-6  
**Date:** 23 October 2026  
**Status:** Preliminary technology selection — pending supervisor approval

## 1. Purpose

This document compares technology alternatives for the proposed mobile phishing detection system.

The comparison considers development complexity, integration requirements, maintainability, security, performance considerations, and suitability for the project MVP.

Four technical decisions are analyzed:
1. Mobile application framework.
2. Backend API framework.
3. NLP/ML classification approach.
4. Data storage strategy.

The decisions are preliminary. No project-specific benchmarks have been conducted at this stage.

## 2. Decision A — Mobile Application Framework

**Evaluation criteria:** Android support, development effort, interface flexibility, cross-platform potential, native API integration, and maintenance.

| Technology | Advantages | Limitations |
|---|---|---|
| Flutter / Dart | Single UI codebase, rich widget ecosystem, Android and potential iOS support | Requires Dart knowledge; platform-specific integrations may require native code |
| React Native | JavaScript/TypeScript ecosystem, reusable components, cross-platform development | Native integrations and dependencies require compatibility checks |
| Native Android / Kotlin | Direct Android API access, strong Android platform integration | Separate implementation required for an independently developed iOS app |

### Preliminary Selection: Flutter

Flutter is proposed because the mandatory MVP focuses on an Android application with a relatively small number of custom screens.

Flutter supports a single codebase for multiple platforms and offers integration with Android-specific functionality when required.

Because automatic SMS and notification analysis are outside the mandatory MVP, advanced platform-specific access is not immediately necessary.

**Decision:** Flutter / Dart is the preferred mobile development technology, subject to final approval.

**References:**
- https://docs.flutter.dev/platform-integration
- https://flutter.dev/
- https://kotlinlang.org/docs/android-overview.html

## 3. Decision B — Backend API Framework

**Evaluation criteria:** Python ML integration, validation, API documentation, complexity, security configuration, and maintainability.

| Technology | Advantages | Limitations |
|---|---|---|
| FastAPI / Python | Python-based, request validation through Pydantic, OpenAPI documentation, direct integration with Python ML code | Deployment, security, and operational settings still require configuration |
| Django REST Framework / Python | Mature Django ecosystem, authentication and database-related tooling | May introduce unnecessary components for a small inference-only API |
| Express.js / Node.js | JavaScript ecosystem, lightweight HTTP API development | Integration with Python ML inference may require another process or service |

### Preliminary Selection: FastAPI

FastAPI is preferred because the planned NLP model will be developed in Python.

Using Python for both the API and inference components may simplify integration and reduce the need for a separate cross-language service.

FastAPI also provides request validation and generated API documentation.

These features are useful for implementing and documenting `POST /api/v1/analyze`.

**Decision:** Python / FastAPI is the preferred Backend technology.

**References:**
- https://fastapi.tiangolo.com/features/
- https://www.django-rest-framework.org/
- https://expressjs.com/

## 4. Decision C — NLP/ML Classification Approach

**Evaluation criteria:** Classification performance, inference cost, training requirements, Russian/Kazakh language coverage, interpretability, and dataset availability.

| Approach | Advantages | Limitations |
|---|---|---|
| TF-IDF + Logistic Regression | Simple baseline, relatively low computational requirements, feature-based interpretation | Limited ability to represent context and word order |
| TF-IDF + Linear SVM | Established classical text classification approach, suitable for sparse features | Probability calibration and interpretation require additional consideration |
| Multilingual Transformer | Contextual text representations and potential multilingual transfer | Higher computational requirements; actual Kazakh/Russian performance must be tested |

### Preliminary Selection Strategy

The project will initially investigate TF-IDF with classical classification algorithms as baseline approaches.

A multilingual Transformer model will be considered as a possible advanced alternative.

The final model must be selected based on actual dataset availability and evaluation results.

The evaluation will consider:
- Precision.
- Recall.
- F1-score.
- Confusion matrix.
- False positives and false negatives.
- Language-specific results where sufficient test data is available.
- Inference time under documented conditions.

No model is currently claimed to be superior for this project.

**Decision:** Pending Dulat's dataset analysis and scientific literature review.

**References:**
- https://scikit-learn.org/stable/modules/feature_extraction.html
- https://scikit-learn.org/stable/supervised_learning.html
- https://huggingface.co/docs/transformers/index

## 5. Decision D — Data Storage Strategy

**Evaluation criteria:** Privacy, implementation effort, data retention, operational complexity, and MVP requirements.

| Approach | Advantages | Limitations |
|---|---|---|
| No persistent message storage | Reduces sensitive data retention, simple initial architecture | No persistent server-side message history |
| SQLite | Lightweight, straightforward local database setup | Requires retention and access policies; scalability depends on deployment requirements |
| PostgreSQL | Suitable for structured, multi-user persistent data | Additional deployment and database administration requirements |

### Preliminary Selection: No Persistent Raw Message Storage

The MVP will not require server-side persistence of submitted message contents.

The analysis API is planned to process the submitted text and return the result without retaining the raw message in normal operation.

If metadata storage is introduced later, the team must first define what information is collected, why it is necessary, and how it is protected.

**Decision:** No persistent raw message storage by default.

**References:**
- https://www.sqlite.org/docs.html
- https://www.postgresql.org/docs/

## 6. Summary of Preliminary Decisions

| Component | Preferred Solution | Status |
|---|---|---|
| Mobile application | Flutter / Dart | Preliminary selection |
| Backend API | Python / FastAPI | Preliminary selection |
| ML baseline | TF-IDF + classical classifier | To be evaluated |
| Advanced ML | Multilingual Transformer | To be investigated |
| Message storage | No persistent raw text by default | Preliminary selection |

## 7. Project-Specific Rationale

The proposed architecture is:

**Flutter Application → FastAPI Backend → NLP/ML Classifier → Risk Assessment**

This separation allows the mobile interface, API, and ML component to be developed and tested independently.

The approach is suitable for the planned team responsibilities:

- Nurbolat: Flutter and UX/UI.
- Dulat: AI/ML model and evaluation.
- Erasyl: Backend architecture and API.

Nurbolat temporarily assists with Backend documentation while Erasyl is unavailable.

## 8. Validation and Remaining Work

Before confirming the final technology stack, the team must:

1. Validate the available Russian and Kazakh datasets.
2. Perform model comparisons using consistent evaluation conditions.
3. Confirm API integration requirements.
4. Verify Android compatibility.
5. Define acceptable latency and privacy requirements.
6. Obtain feedback from the scientific supervisor.

**Conclusion:** Flutter, FastAPI, and Python-based NLP form a feasible preliminary architecture for the planned MVP. The ML algorithm and final engineering decisions require further empirical validation and supervisor approval.