# Verification and Evaluation Plan

**Programme:** Software Engineering, SE-2413  
**Project:** Development of a Mobile Application for Detecting Phishing and Fraudulent Messages  
**Work package:** Verification, Testing & Evaluation  
**Review date:** 23 October 2026

## 1. Testing Plan

The verification strategy spans multiple levels of system testing to ensure robust performance under real-world conditions:

1. **Unit Testing:** 
   - Validates text preprocessing modules (normalization, URL masking, phone number extraction) and tokenizer stability for Cyrillic and Turkic specific characters ($ә, ғ, қ, ң, ө, ұ, ү, һ, і$).
2. **Integration Testing:** 
   - Tests communication pipelines between the Flutter mobile client and the classification backend.
3. **Hold-out Evaluation:** 
   - Assesses performance on a strictly isolated test set excluded from all training, hyperparameter tuning, and balancing procedures.
4. **Adversarial / Robustness Testing:** 
   - Measures model resilience against deliberate evasion techniques identified in literature: intentional spelling variations, homoglyph substitution, punctuation noise, and obfuscated URLs.
5. **Cross-Language Testing:** 
   - Evaluates generalization across Russian, Kazakh, and code-switched message samples.

## 2. Result Metrics

Due to severe class imbalance in fraud detection datasets (where legitimate messages vastly outnumber fraudulent ones), standard accuracy is insufficient. The evaluation relies on the following metrics:

1. **Precision (Phishing Class):** 
   - Minimizes false positives to prevent blocking legitimate user alerts and important notifications.
2. **Recall (Phishing Class):** 
   - Minimizes false negatives to ensure critical security threats and scam messages are not missed.
3. **F1-score & Macro-F1:** 
   - Evaluates overall balance across multi-class categories (legitimate, spam, smishing).
4. **Inference Latency:** 
   - Target execution speed of $\le 30\text{ ms}$ per message, ensuring responsiveness suitable for mobile edge deployment.
5. **Resource Footprint:** 
   - Memory consumption and CPU overhead during on-device or edge processing.

## 3. Measurement Conditions

To ensure objectivity and reproducibility, measurements are conducted under strict conditions:

* **Fixed Datasets:** Experiments run on standardized, partitioned evaluation sets with pre-defined distributions.
* **Leakage Prevention:** Oversampling or augmentation techniques (e.g., SMOTE) are applied **exclusively** to training folds post-split, ensuring the test set remains untouched.
* **Hardware Benchmarking:** Latency metrics are recorded on reference mobile devices, while algorithmic metrics are evaluated in a controlled Python environment with fixed library versions.

## 4. Baseline Solution for Comparison

* **Baseline Model:** TF-IDF feature extraction combined with **Logistic Regression** or **Linear SVM**.
* **Justification:** Serves as a standard, lightweight, highly reproducible baseline derived from comparative literature. More complex architectures (such as deep neural networks or transformers) must demonstrate statistically significant improvements in Macro-F1 and adversarial resilience over this baseline to justify their complexity.

## 5. Demonstration of Project Goal Achievement

The primary objective—delivering a secure, effective mobile risk-assessment application for Kazakh and Russian messages—will be validated through the following outcomes:

1. **Performance Superiority:** Outperforming the baseline model by at least 5–10% in Macro-F1 and phishing Recall on the test dataset.
2. **Robustness Verification:** Sustaining high recall ($\ge 85\%$) under adversarial text distortion and evasion attempts.
3. **Mobile Readiness:** Confirming real-time local execution ($\le 30\text{ ms}$) and strict on-device privacy compliance (minimizing raw text transmission).
4. **Safe Communication:** Delivering transparent risk assessments with clear trigger explanations rather than absolute safety guarantees.

## 6. References

* Birthriya, S. K., Ahlawat, P., & Jain, A. K. (2026). Machine learning-based smishing detection using fuzzy logic and TF-IDF feature engineering. *Franklin Open*, *14*, Article 100506. https://doi.org/10.1016/j.fraope.2026.100506
* Filali, A., Shorfuzzaman, M., Abdellaoui Alaoui, E., et al. (2026). Cross-lingual SMS spam detection using GAN-based augmentation for imbalanced datasets. *Scientific Reports*, *16*, Article 7128. https://doi.org/10.1038/s41598-026-37769-4
* Shahbazov, V. (2026). Development of a lightweight two-stage hybrid classifier for privacy-preserving on-device multi-class SMS threat detection. *EUREKA: Physics and Engineering*, (5), 194–209. https://doi.org/10.21303/2461-4262.2026.004397
* Xu, H., Qadir, A., & Sadiq, S. (2025). Malicious SMS detection using ensemble learning and SMOTE to improve mobile cybersecurity. *Computers & Security*, *154*, Article 104443. https://doi.org/10.1016/j.cose.2025.104443