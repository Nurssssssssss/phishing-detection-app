# Initial Requirements Specification (draft)

Acceptance criteria are **proposed**, to be validated with users and supervisor. Priorities: Must / Should / Could.

## Functional requirements
| ID | Priority | Requirement | Verifiable acceptance criterion |
|---|---|---|---|
| FR-01 | Must | Manually enter/paste message | Given non-empty supported text, user can request analysis |
| FR-02 | Must | Reject invalid input | Empty input cannot be submitted; user sees useful message |
| FR-03 | Must | Request backend analysis | Client sends defined JSON schema to API and handles response |
| FR-04 | Must | Display result | UI shows category and explanation from valid response |
| FR-05 | Must | Handle failure | Network errors and server errors produce understandable retry guidance |
| FR-06 | Should | State model uncertainty | UI avoids labeling uncertain messages as definitely safe |
| FR-07 | Could | History | Only if user approves and privacy requirements are met |
| FR-08 | Could | Automatic notification analysis | Separate later research; not mandatory MVP |

## Nonfunctional requirements
| ID | Priority | Requirement | Verifiable acceptance criterion |
|---|---|---|---|
| NFR-01 | Must | Minimize sensitive data exposure | Message contents and OTP codes are excluded from logs and repository |
| NFR-02 | Must | Secure network transport | App uses HTTPS for deployed API calls |
| NFR-03 | Must | Explain limitations | UI explains that predictions may be incorrect |
| NFR-04 | Must | Supported Android environment | Tested on documented device/OS or emulator configuration (spec TBD) |
| NFR-05 | Should | Response latency | Record p50/p95 time under reproducible test conditions; threshold TBD |
| NFR-06 | Should | Russian/Kazakh handling | Language-specific evaluation recorded; no untested coverage claims |
| NFR-07 | Should | Accessible UI | Text and status understandable without relying solely on color |

## Pending decisions
Maximum message length, Android version, score calibration, desired quality thresholds, latency thresholds, API hosting, and dataset rights require justification and sign-off.
