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
