# Architecture and API Contract (draft)

## Components
- **User / Flutter UI:** manual message input, status indicator, explanations, retry states.
- **FastAPI backend:** input validation, transport security, model invocation, structured response, sanitized diagnostics.
- **NLP model:** outputs predicted risk category and model-specific evidence/indicators.
- **Storage (optional):** no persistence of raw message text in the default design.

See editable source files in `../diagrams/` (Mermaid).

## Flow
1. User inputs suspicious message.
2. App sends HTTPS `POST /api/v1/analyze`.
3. API validates payload, rejects empty/oversized content.
4. API invokes model and maps its output to a documented response.
5. UI displays cautious result; errors are handled without exposing message content.

## Provisional API example (synthetic text only)

`POST /api/v1/analyze`
```json
{"text":"Your package is waiting. Check this suspicious link: example.invalid"}
```
Illustrative response shape (NOT real inference):
```json
{"risk_level":"high","confidence":null,"indicators":["Contains a suspicious link"],"disclaimer":"This is an estimate, not proof of fraud."}
```
Validation error: HTTP 422 or a documented 4xx error object; system error: sanitized 5xx error response. Exact values and schema subject to review.

## Security
- No tokens / private messages in Git commits, issue tracker, logs or tests.
- Input length limits, basic rate controls, HTTPS in deployments.
- Avoid retaining raw text without a legitimate requirement and user consent.
- Minimize explanations that overclaim model interpretability.

## Open design points
Hosting choice, authentication/rate limits, optional storage and explainability method require research and team approval.


## Architecture Diagrams

The proposed system architecture is represented by three diagrams:

1. System Context Diagram — shows the interaction between the Android user and the Phishing Detection System.
2. Use Case Diagram — describes the main user interactions, including message input, analysis requests, result viewing, and error handling.
3. Component Diagram — illustrates communication between the Flutter mobile application, FastAPI backend, and NLP/ML classifier.

Editable Mermaid source files and exported SVG diagrams are available in the `diagrams/` directory.

| Diagram | Editable source | Viewable diagram |
|---|---|---|
| System Context | [system-context.mmd](../diagrams/system-context.mmd) | [system-context.svg](../diagrams/system-context.svg) |
| Use Case | [use-case.mmd](../diagrams/use-case.mmd) | [use-case.svg](../diagrams/use-case.svg) |
| Component | [component.mmd](../diagrams/component.mmd) | [component.svg](../diagrams/component.svg) |

## Architecture Responsibilities

- Nurbolat Seilkhanov: Flutter mobile application, user interface, API integration, and temporary backend documentation support.
- Dulat Amangeldi: NLP/ML model design, classification approach, model evaluation, and prediction output.
- Erasyl Zhagypar: Backend architecture, API design, input validation, data handling, and integration.

The architecture is preliminary and subject to supervisor review.
