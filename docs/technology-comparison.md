# Technology Comparison — provisional analysis

**Requirement:** >=3 key decisions, each with 2–3 substantiated alternatives. Below are preliminary engineering hypotheses; benchmark evidence and references must be added before calling choices final.

## Decision A: Mobile framework
| Option | Advantages | Drawbacks / validation needed |
|---|---|---|
| Flutter (candidate) | Single Dart UI stack; Android first, possible cross-platform reuse | Flutter/Dart expertise and plugin constraints need evaluation |
| React Native | Familiar JS/TS ecosystem | Native module and runtime requirements need evaluation |
| Native Kotlin | Direct access to Android APIs | Separate implementation needed for iOS |

**Provisional choice:** Flutter, subject to UX requirements and Android limitations.

## Decision B: API framework
| Option | Advantages | Drawbacks / validation needed |
|---|---|---|
| FastAPI (candidate) | Python integration with NLP code and request schemas | Deployment and security configuration still needed |
| Django REST Framework | Built-in ecosystem for persistence/admin | Possibly more setup for a small inference API |
| Node.js/Express | JavaScript backend ecosystem | Python model needs separate service or bridge |

**Provisional choice:** FastAPI, pending integration evaluation.

## Decision C: Inference method
| Option | Advantages | Drawbacks / validation needed |
|---|---|---|
| TF-IDF + Logistic Regression | Simple, fast, interpretable baseline | Limited contextual language understanding |
| TF-IDF + linear SVM | Effective classical text classifier candidate | Calibration/explanations require care |
| Multilingual transformer | Potential for contextual modeling | Greater data/compute demands; actual language performance unknown |

**Final selection:** TODO — Dulat, after scientific review and dataset analysis.

## Decision D (optional): Storage strategy
| Option | Advantages | Drawbacks / validation needed |
|---|---|---|
| No persistent raw text by default (preferred) | Reduces sensitive data exposure | Less historic analytics |
| PostgreSQL metadata only | Can retain non-sensitive event metadata | Security/retention policy necessary |
| SQLite metadata only | Easy prototype setup | Unsuitable for some multi-user deployments |

**Decision:** Minimize stored data; exact design awaits the requirements and privacy review.

## Selection criteria and references
TODO: cite benchmarks, documentation, platform policy and project-specific constraints; record who approved each choice.
