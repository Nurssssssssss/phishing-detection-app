# Section: Validation of Relevance and User Requirements Analysis

## 1. Validation of Relevance

Analysis of the domain shows a steady increase in social engineering attacks, phishing, and fraudulent links in text messages (smishing). Mobile devices are becoming the primary target for attackers, while traditional security tools (standard carrier spam filters and basic mobile antiviruses) often fail to provide timely detection of new phishing resources.

To confirm the relevance of the thesis topic and objectively justify the functional requirements for the proposed mobile application, a user research study was conducted via an online survey among potential target users.

Survey Demographics:
* **Age Category:** 71.4% of respondents are aged 18–24; 28.6% are under 18.
* **Primary Mobile OS:** 85.7% run iOS, while 14.3% run Android.

## 2. Analysis of Survey Results

### Threat Exposure and User Vulnerability

* **Attack Frequency:** **83.3%** of respondents regularly receive suspicious messages (16.7% daily or several times a week; 33.3% 1–2 times a month; 33.3% very rarely). Only 16.7% reported never noticing such messages.

* **Phishing Exposure Experience:** **83.3%** of respondents have experienced interacting with scam links:
  * **33.3%** personally clicked a link or lost money.
  * **50.0%** clicked a link but realized it was a scam in time.
  * Only **16.7%** have never fallen for online scams.

### Types of Scam Messages Encountered

* **66.7%** of respondents encountered **links to fake websites** (giveaways, discounts, fake prizes).
* **33.3%** encountered **fake account suspension or parcel delivery notifications**.

### Detection Criteria Used by Users

* **100%** of respondents rely on analyzing **unfamiliar or misspelled web links (URLs)** when identifying fraudulent messages.
* **50.0%** look for an **urgent call to action or a sense of panic** (social engineering indicators).
* **16.7%** check suspicious phone numbers/emails, typos, or cross-check information through official customer service channels.

### Current Usage of Security Tools

* **50.0%** rely on built-in carrier or messaging app protection settings.
* **33.3%** use mobile antivirus software.
* **16.7%** use built-in caller ID / spam blocker apps (e.g., Truecaller, Getcontact).

These metrics demonstrate that existing native and third-party solutions are insufficient, highlighting a clear user demand for a dedicated text and link analysis tool.

## 3. Evidence-Based Requirements: Facts vs. Hypotheses

Based on the research findings, all input requirements for the mobile application were classified into **confirmed facts** and **working hypotheses**.

### 3.1 Confirmed Results (Facts & Evidence)

1. **Core Feature Need:** URL analysis and detection is the highest-priority feature, as 100% of respondents identify scams by links, and 66.7% actively encounter malicious website links.

2. **Prioritized Features:**
   * **Automatic scanning of incoming SMS** for phishing links — **50.0%**.
   * **Real-time warnings when opening unsafe websites** — **50.0%**.
   * On-demand link/text checking (copy-and-paste testing) — **33.3%**.
   * Knowledge base and tips on current scam tactics — **33.3%**.
   * One-tap reporting to submit scam numbers/links — **33.3%**.

3. **Security and Data Privacy:** **83.3%** of users are willing to grant SMS reading permissions **only under strict privacy conditions**:
   * **50.0%** require that **all processing happens locally on the device** (no cloud uploads).
   * **33.3%** demand explicit privacy guarantees.

4. **Monetization Model:** **83.3%** of respondents preferred a **Freemium model** (free basic features with an optional premium subscription for advanced tools).

### 3.2 Working Hypotheses (To Be Tested During MVP Development)

1. **On-Device ML/NLP Hypothesis:** Deploying a lightweight machine learning model (e.g., ONNX / CoreML) directly on the mobile device will achieve a response time of < 200 ms without significantly degrading battery life or violating user privacy.

2. **iOS UX Hypothesis:** Due to iOS system limitations regarding background SMS interception for third-party messengers, integrating an intuitive "Share Extension" workflow and widget will maintain high user retention among iOS users (who represent 85.7% of the survey sample).