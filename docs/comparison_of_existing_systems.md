# Comparison of Existing Systems and Approaches

**Programme:** Software Engineering, SE-2413  
**Project:** Development of a Mobile Application for Detecting Phishing and Fraudulent Messages  
**Work package:** System Analysis & Architecture  
**Review date:** 23 October 2026

## 1. Introduction and Rationale

To design an effective mobile application for detecting phishing and fraudulent messages (smishing) in Kazakh and Russian, it is essential to evaluate existing technological paradigms and architectural approaches. Direct, production-ready packaged applications specifically tailored for Kazakh-Russian bilingual smishing detection are limited in public open-source literature. Therefore, this section evaluates 4 major architectural and methodological approaches identified in recent academic research (2020–2026) as comparative proxies.

The evaluated systems span traditional telecom filtering to modern machine learning and transformer-based architectures.

## 2. Evaluation Criteria

To establish a rigorous, standardized comparison, **7 key criteria** are established:

1. **Inference Location (Architecture):** Where message processing and classification occur (locally on the mobile device vs. remote server/cloud).
2. **Language Adaptability:** Level of multilingual support, handling of morphological richness in Slavic (Russian) and Turkic (Kazakh) languages.
3. **Classification Granularity:** Ability to categorize messages (e.g., binary Ham vs. Spam, or multi-class Legitimate vs. Spam vs. Targeted Smishing/Phishing).
4. **Adversarial and Evasion Robustness:** Resilience against text obfuscation, spelling variations, homoglyphs, and link masking techniques.
5. **Class Imbalance Handling:** Explicit utilization of mitigation techniques (e.g., SMOTE, GAN-based augmentation) to handle rare fraud classes.
6. **Privacy-Awareness:** Protection of user data minimization, avoidance of unnecessary raw message transmission or logging.
7. **Latency and Resource Footprint:** Processing speed per message (in milliseconds) and hardware footprint suitability for mobile deployment.

---

## 3. Comparative Matrix of Systems

| Evaluation Criteria | 1. Traditional Telecom & Cloud Filters | 2. Classical Machine Learning (TF-IDF + SVM/Ensemble) | 3. Two-Stage Hybrid Mobile Classifiers (TextCNN + Structure) | 4. Multilingual Transformers & LLM Approaches |
| :--- | :--- | :--- | :--- | :--- |
| **1. Inference Location** | Cloud / Telecom Operator Server | Local device or backend server | Local on mobile device (On-device) | Cloud-based or Hybrid API |
| **2. Language Adaptability** | Basic keyword/regex matching | Dependent on vocabulary coverage | Requires morphological tokenization support | High, via cross-lingual pre-trained embeddings |
| **3. Granularity** | Binary (Spam / Safe) | Binary or simple multi-class | Multi-class (Safe / Spam / Smishing) | High, supports reasoning via prompting |
| **4. Evasion Robustness** | Low (easily bypassed via symbol changes) | Moderate (vulnerable to lexical drift) | High (due to structural/stylistic feature analysis) | High to synonyms, moderate to spelling noise |
| **5. Imbalance Handling** | Rarely documented (relies on blacklists) | Requires manual balancing (e.g., SMOTE) | Addressed via architectural design / weighting | Handled via large pre-trained representations |
| **6. Privacy-Awareness** | Low (raw texts transmitted to third-party servers) | Moderate (depends on implementation) | High (all evaluation handled locally on-device) | Low/Moderate (privacy risks sending texts to cloud LLMs) |
| **7. Latency & Resources** | Low network latency, dependent on connectivity | Extremely fast (single-digit milliseconds) | Optimized for mobile constraints (~30 ms) | High memory footprint and inference latency |

---

## 4. In-Depth Analysis of Comparative Systems

### 4.1 Traditional Telecom and Cloud Filters
Cloud-based blacklists and operator-level filters are widely deployed for mass spam filtering. While they offer low latency under stable network conditions, they suffer from severe limitations: low resilience against modern evasion tactics (such as character substitution and zero-day scam templates) and complete compromise of user data privacy as message contents are sent to centralized servers.

### 4.2 Classical Machine Learning Models (TF-IDF + Linear Models / Ensembles)
Classifiers utilizing term frequency-inverse document frequency (TF-IDF) combined with Logistic Regression, Support Vector Machines (SVM), or Random Forests provide a robust, interpretable, and lightweight baseline (Xu et al., 2025; Birthriya et al., 2026). However, they are bounded by vocabulary size and struggle significantly with out-of-vocabulary terms, concept drift, and dynamic phrasing alterations.

### 4.3 Two-Stage Hybrid Mobile Architectures
Recent literature highlights optimized multi-stage frameworks (e.g., initial structural/heuristic filtering followed by a lightweight TextCNN or deep network for ambiguous texts) tailored for mobile edge deployment (Shahbazov, 2026). These systems achieve an optimal balance for mobile applications, maintaining low inference time (~30 ms per message) and high on-device privacy by preventing raw text exposure.

### 4.4 Multilingual Transformers and Large Language Models (LLMs)
State-of-the-art transformer encoders and generative LLMs (such as BERT, RoBERTa, and instruction-tuned models) provide unmatched semantic comprehension and cross-lingual transfer capabilities (Filali et al., 2026; Hur et al., 2026). Despite their high classification accuracy, their large model sizes, high memory consumption, processing latency, and reliance on external API calls make them challenging for direct, offline, resource-constrained mobile execution without raising user privacy concerns.

## 5. Conclusion and Implications for the Project

The comparative analysis demonstrates that no single pre-existing paradigm perfectly satisfies all project constraints. While cloud transformers provide high semantic accuracy, they violate on-device privacy requirements and introduce latency. Conversely, classical models lack deep contextual adaptation for multi-language nuances.

For the proposed mobile application targeting Kazakh and Russian, a **privacy-aware hybrid strategy** is justified: utilizing a lightweight, interpretable baseline (such as TF-IDF with linear classifiers) or a compact on-device architecture, complemented by rigorous handling of class imbalance and strict risk-assessment communication rather than absolute guarantees.

## 6. References

* Birthriya, S. K., Ahlawat, P., & Jain, A. K. (2026). Machine learning-based smishing detection using fuzzy logic and TF-IDF feature engineering. *Franklin Open*, *14*, Article 100506. https://doi.org/10.1016/j.fraope.2026.100506
* Filali, A., Shorfuzzaman, M., Abdellaoui Alaoui, E., et al. (2026). Cross-lingual SMS spam detection using GAN-based augmentation for imbalanced datasets. *Scientific Reports*, *16*, Article 7128. https://doi.org/10.1038/s41598-026-37769-4
* Hur, M., Seo, S., Hwang, J., & Min, M. (2026). Are large language models effective for detecting spam messages? *International Journal of Information Security*, *25*, Article 127. https://doi.org/10.1007/s10207-026-01283-5
* Shahbazov, V. (2026). Development of a lightweight two-stage hybrid classifier for privacy-preserving on-device multi-class SMS threat detection. *EUREKA: Physics and Engineering*, (5), 194–209. https://doi.org/10.21303/2461-4262.2026.004397
* Xu, H., Qadir, A., & Sadiq, S. (2025). Malicious SMS detection using ensemble learning and SMOTE to improve mobile cybersecurity. *Computers & Security*, *154*, Article 104443. https://doi.org/10.1016/j.cose.2025.104443