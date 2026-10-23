# Software Requirements Specification (SRS)

**Project:** Phishing Detection App  
**Program / Group:** Software Engineering / SE-2413  
**Team:** Nurbolat Seilkhanov, Dulat Amangeldi, Erasyl Zhagypar  
**Status:** Initial requirements specification  
**Date:** 23 October 2026  
**Related YouTrack Issue:** PDA-7

---

## 1. Introduction

### 1.1 Purpose

The purpose of this document is to define the functional and non-functional requirements for a mobile application that helps users identify potentially phishing or fraudulent text messages using Natural Language Processing (NLP) and Machine Learning (ML).

The document defines the expected system behavior, priorities, constraints, and acceptance criteria.

### 1.2 Target Users

The primary target users are Android smartphone users in Kazakhstan who receive suspicious messages in Russian or Kazakh.

Secondary users include individuals with limited technical knowledge who need simple and understandable security warnings.

### 1.3 Project Scope

The initial Minimum Viable Product (MVP) will allow users to manually enter or paste suspicious messages, submit them for analysis, and receive a risk assessment.

Automatic access to SMS messages, private chats, and Android notifications is excluded from the mandatory MVP.

---

## 2. Functional Requirements

Functional requirements describe what the application must do.

| ID | Requirement | Priority | Acceptance Criteria |
|---|---|---|---|
| FR-01 | The application shall allow users to manually enter text messages. | Must | Users can type text into the input field. |
| FR-02 | The application shall allow users to paste copied messages. | Must | Pasted text appears correctly in the input field. |
| FR-03 | The application shall validate message input before submission. | Must | Empty input is rejected with an understandable error message. |
| FR-04 | The application shall allow users to submit messages for analysis. | Must | Valid text is sent to the Backend API. |
| FR-05 | The Backend API shall accept text analysis requests. | Must | A valid request receives a correctly structured response. |
| FR-06 | The system shall analyze message text using an NLP/ML classifier. | Must | A supported input produces a model classification result. |
| FR-07 | The application shall display the estimated risk level. | Must | The result screen shows the returned risk category. |
| FR-08 | The application shall display an understandable explanation of available suspicious indicators. | Must | The result includes an explanation supported by the implemented analysis method. |
| FR-09 | The application shall handle server or network failures. | Must | Users receive an understandable error message when analysis is unavailable. |
| FR-10 | The application shall display a loading state during analysis. | Should | A loading indicator appears while awaiting the API response. |
| FR-11 | The system should support Russian-language message analysis. | Must | Russian test messages can be processed and evaluated. |
| FR-12 | The system should support Kazakh-language message analysis. | Must | Kazakh test messages can be processed and evaluated; limitations are reported. |
| FR-13 | The application should provide guidance about the limitations of automated detection. | Should | Users can view information explaining that the analysis is not a guarantee of safety. |
| FR-14 | The application may provide a local history of previous assessments. | Could | Users can view previous results if this functionality is implemented. |

---

## 3. Non-Functional Requirements

Non-functional requirements describe how the system should operate.

| ID | Requirement | Priority | Acceptance Criteria |
|---|---|---|---|
| NFR-01 | The application shall target Android devices. | Must | The application can be built and tested on a supported Android device or emulator. |
| NFR-02 | Communication between the mobile application and a deployed API shall use HTTPS. | Must | Network requests to the deployed service use TLS. |
| NFR-03 | The system shall avoid storing raw message contents by default. | Must | Normal analysis requests do not persist raw submitted messages. |
| NFR-04 | The system shall avoid exposing sensitive data in logs. | Must | Test logs do not contain submitted message bodies or sensitive tokens. |
| NFR-05 | The interface shall be understandable to non-technical users. | Must | Main user tasks can be completed during usability testing without technical instructions. |
| NFR-06 | The Backend shall validate incoming requests. | Must | Invalid requests are rejected with documented errors. |
| NFR-07 | The system shall support reproducible ML evaluation. | Must | Dataset split, model configuration, and evaluation procedure are documented. |
| NFR-08 | The system shall report ML performance limitations. | Must | Evaluation documentation includes relevant errors and limitations. |
| NFR-09 | The application should provide a responsive interface. | Should | The interface remains usable while awaiting server responses. |
| NFR-10 | The system should record response-time measurements under defined test conditions. | Should | The test report contains measured latency and test conditions. |

Performance targets and specific usability thresholds will be agreed upon with the supervisor during later development.

---

## 4. Requirements Prioritization

The MoSCoW method is used to classify requirements.

**Must Have:** Essential requirements for the initial MVP, such as manual input, validation, NLP analysis, risk results, basic security, and error handling.

**Should Have:** Important requirements that improve user experience, such as loading indicators and additional explanations.

**Could Have:** Optional improvements, including local analysis history.

**Won't Have in the Initial MVP:** Automatic SMS interception, background notification scanning, and mandatory iOS support.

---

## 5. Main User Scenarios

### UC-01: Analyze a Suspicious Message

**Actor:** Mobile application user.

**Preconditions:** The application is available, and the analysis service is reachable.

**Main Flow:**
1. The user opens the application.
2. The user enters or pastes a suspicious message.
3. The user selects the analysis action.
4. The application validates the input.
5. The application sends the message to the API.
6. The Backend submits the text to the ML component.
7. The analysis result is returned.
8. The application displays the risk assessment and available explanation.

**Postconditions:** The user sees the estimated risk and relevant warning information.

### UC-02: Invalid Message Input

1. The user submits an empty message.
2. The application detects invalid input.
3. The application displays an explanatory validation message.
4. No analysis request is submitted.

### UC-03: Analysis Service Unavailable

1. The user submits a valid message.
2. The Backend or network becomes unavailable.
3. The application handles the failed request.
4. The user receives an understandable error message.

---

## 6. System Constraints

- Android is the priority platform.
- Flutter/Dart is the preliminary mobile technology.
- Python/FastAPI is the preliminary Backend technology.
- Python and NLP/ML libraries will be considered for message classification.
- Russian and Kazakh are the target analysis languages.
- Model performance depends on dataset quality and availability.
- Sensitive information must not be included in repository files or test logs.
- The system cannot guarantee that every fraudulent message will be detected.

The final technology stack will be justified in the Technology Comparison document.

---

## 7. Acceptance and Verification Strategy

Functional requirements will be verified using manual or automated test cases.

Backend requirements will be evaluated using API validation and integration tests.

ML requirements will be evaluated using labeled test datasets and metrics such as Precision, Recall, and F1-score.

Non-functional requirements will be assessed through security checks, usability testing, documentation review, and response-time measurements.

All implemented requirements should be traceable to corresponding test cases.

---

## 8. Responsibility Distribution

**Nurbolat Seilkhanov**
- Mobile functional requirements
- UX and usability requirements
- Message input and result presentation
- User scenarios

**Dulat Amangeldi**
- ML classification requirements
- Dataset and evaluation requirements
- Russian and Kazakh language analysis requirements

**Erasyl Zhagypar**
- Backend API requirements
- Validation and security requirements
- Integration and data handling requirements

Nurbolat temporarily supports Backend documentation while Erasyl is unavailable. The project team continues to consist of three members.

---

## 9. Current Status and Open Decisions

This document defines the preliminary requirements for the Phishing Detection App.

The following decisions require further validation or supervisor approval:

- Final technical stack
- Dataset selection and language coverage
- ML performance thresholds
- API response-time target
- Optional message history functionality
- Detailed privacy and data retention policy

**Status:** Draft prepared for the first pre-defense checkpoint. Implementation and acceptance testing will take place during subsequent development phases.