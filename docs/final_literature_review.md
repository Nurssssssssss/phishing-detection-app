# Literature Review: Detecting Phishing and Fraudulent Messages

**Programme:** Software Engineering, SE-2413  
**Project:** Development of a Mobile Application for Detecting Phishing and Fraudulent Messages  
**Work package:** AI / Machine Learning  
**Review date:** 23 October 2026

## 1. Aim and scope

This review examines research on SMS spam and phishing detection (smishing), including classical machine learning, Transformer-based methods, multilingual classification, dataset quality, evasion, class imbalance, and privacy-aware deployment. The project aims to help users assess suspicious messages in Kazakh and Russian. The central research concern is that performance on English-only benchmark data cannot be assumed to transfer to those languages or to local scam patterns.

The project should describe its output as a **risk assessment**, not a guarantee that a message is safe or fraudulent.

## 2. Search and selection approach

The initial search focused on publisher pages, peer-reviewed venues, the ACL Anthology, the UCI Machine Learning Repository, and arXiv for directly relevant work. Recent research from 2021–2026 was prioritized, while foundational work was retained where it explains an established method or benchmark.

The selection criteria were: (1) relevance to SMS spam, smishing, or fraud detection; (2) a clearly described method, dataset, evaluation, or deployment consideration; and (3) usefulness for the planned Kazakh/Russian mobile application.

## 3. Analytical table of sources

| # | Source / type | Problem and data | Method / contribution | Findings reported by the source | Critical assessment and relevance |
|---:|---|---|---|---|---|
| 1 | Al Saidat et al. (2024), survey, *Procedia Computer Science* | Reviews SMS spam and smishing detection research. | Surveys rule-based, ML, NLP, and deep-learning approaches. | The authors identify the combination of ML and NLP, including CNN/RNN methods, as an important direction. | Useful for mapping the field, but a survey’s overall conclusions do not prove that any one model will work on Kazakh/Russian data. |
| 2 | Salman et al. (2024), *IEEE Access* | Examines SMS spam evolution and evasion strategies using a dataset of 67,018 messages (2012–2023). | Compares shallow ML, deep neural methods, and anti-spam services using semantic and syntactic features. | The authors report that the tested methods and services were susceptible to evasion strategies. | Directly motivates robustness tests: altered wording, spelling variation, obfuscated links, and messages from a later time period. |
| 3 | Xu et al. (2025), *Computers & Security* | Classifies malicious and legitimate SMS and addresses class imbalance and false positives. | Combines SVM and Random Forest; compares TF and TF-IDF features and uses SMOTE. | The publisher abstract reports 99.58% accuracy for the ensemble using TF-IDF on a balanced dataset. | A useful comparison for ensemble and TF-IDF baselines. Oversampling must occur only inside the training data after splitting to prevent leakage. |
| 4 | Martínez-Mendoza et al. (2026), *Engineering Applications of Artificial Intelligence* | Introduces MIMICS-3500, a dataset of 3,500 English smishing examples with multi-class taxonomies. | Combines multiple sources, clustering-assisted category discovery, manual labelling, and inter-annotator agreement. | The abstract reports RoBERTa F1-scores of 86.94% for seven classes and 82.43% for thirteen classes. | Shows the value of multi-class threat labels. The dataset is English-only, so it cannot establish Kazakh/Russian performance. |
| 5 | Birthriya et al. (2026), *Franklin Open* | Studies classification of SMS using 5,574 messages from SMS Spam Collection plus 545 smishing examples. | Combines TF-IDF with fuzzy representations of structural and stylistic features. | Reports up to 99.10% accuracy, 99.30% precision, and 94% recall. | A relevant lightweight baseline/hybrid design, though high performance on a mixed benchmark does not guarantee real-world generalization. |
| 6 | Filali et al. (2026), *Scientific Reports* | Examines class imbalance and cross-lingual SMS spam detection using monolingual and multilingual datasets. | Compares traditional ML, LSTM/Bi-LSTM, multiple embeddings, and augmentation methods (GANs, SMOTE). | Reports F1 of 97.61% for BERT+Bi-LSTM+GAN on monolingual and 94.44% on multilingual data. | Relevant to multilingual evaluation and imbalance, but synthetic augmentation should never contaminate the test set. |
| 7 | Amaral Cejas et al. (2026), ACL Anthology | Studies HAM/SPAM/SMISHING classification across several languages under telecom-scale constraints. | Evaluates four multilingual embedding models and fine-tunes domain-adapted representations. | The authors report improved classification after domain adaptation across several languages. | Highly relevant to multilingual design, but the dataset is partly proprietary and language-specific metrics require verification. |
| 8 | Hur et al. (2026), *International Journal of Information Security* | Evaluates LLMs for SMS spam detection on English and Korean datasets under concept drift. | Compares traditional ML, deep learning, Transformer encoders, and LLMs using prompt strategies. | Conclude that tested LLMs can be effective and offer rationales in their evaluated settings. | Useful when considering LLMs, but cost, latency, privacy, and Korean-to-Kazakh/Russian transferability must be weighed. |
| 9 | Lochstampfor & Roy (2026), arXiv preprint | Presents a synthetic dataset of 3,201 multi-round conversational smishing dialogues. | Compares classical ML and Transformer models using TF-IDF and conversational features. | Reports XGBoost with TF-IDF at 72.5% accuracy and 0.691 macro-F1. | Suggests lexical features are competitive; however, this is a preprint and multi-turn detection is outside the single-message scope. |
| 10 | Shahbazov (2026), *EUREKA: Physics and Engineering* | Targets three-way classification of legitimate SMS, spam, and smishing with privacy-aware mobile inference. | Proposes a two-stage approach: structural features first, then a compact TextCNN. | Reports F1 of 97.40% and average prediction time of 30 ms per message. | Highlights on-device versus server trade-offs for privacy and model updates. |
| 11 | Devlin et al. (2019), NAACL-HLT | Introduces contextual language representations pre-trained from large text corpora. | Presents BERT and fine-tuning for downstream NLP tasks. | Reports strong results on multiple NLP benchmarks. | Foundational support for Transformer encoders, though not a smishing paper. |
| 12 | Almeida & Hidalgo (2011), UCI Machine Learning Repository | Public labelled SMS corpus used for spam/legitimate text classification (5,574 messages). | Common baseline dataset for text-classification experiments. | Provides a documented, reproducible benchmark with ham/spam labels. | Useful for building a reproducible pipeline, but English-focused and limited by binary definitions. |

## 4. Critical synthesis

### 4.1 Classical ML as a necessary baseline
Traditional machine learning remains a robust starting point for SMS spam and phishing detection because models like Logistic Regression and Linear SVM are lightweight, fast, and highly interpretable. Recent studies consistently evaluate TF-IDF feature extraction alongside ensemble approaches to establish reliable performance floors. However, lexical models are prone to overfitting dataset-specific vocabulary, making them vulnerable to adversarial spelling changes, obfuscated URLs, and shifting scam patterns. Therefore, benchmark accuracy alone must not dictate model selection.

### 4.2 Transformers and LLMs: Capabilities and constraints
While foundational architectures like BERT offer powerful contextual representations, newer research explores domain adaptation, multi-class threat taxonomies via RoBERTa, and large language model zero-shot/few-shot prompting. Although these advanced models demonstrate strong capabilities, their deployment on mobile devices introduces strict constraints regarding inference latency, computational resource consumption, data privacy, and API costs. 

### 4.3 The Kazakh and Russian language research gap
Existing benchmarks—such as the UCI SMS Collection, MIMICS-3500, and various multilingual corpora—predominantly focus on English, Portuguese, Korean, or machine-translated text. While cross-lingual and multilingual investigations show promise, performance on English or unrelated languages cannot be directly generalized to Kazakh and Russian. These target languages possess distinct morphology, Cyrillic and Latin script variations, code-switching, and regional fraud templates that necessitate dedicated evaluation datasets.

### 4.4 Evaluation rigor and data leakage prevention
Methodological integrity is critical for reliable threat detection. Research shows that issues like class imbalance, improper data splitting, and data leakage through premature oversampling (such as SMOTE) severely distort evaluation metrics. Evaluations must rely on class-wise precision, recall, macro-F1 score, and confusion matrices rather than overall accuracy alone. Furthermore, privacy-aware architectures—such as on-device processing versus cloud-based inference—must be carefully balanced against update flexibility.

## 5. Implications for the project

Based on the reviewed literature, the project will follow a structured evaluation methodology:
1. **Baseline Model:** Implement TF-IDF feature extraction paired with Logistic Regression and Linear SVM.
2. **Advanced Models:** Explore compact Transformer models or multilingual embeddings only if computational and data constraints permit.
3. **Language Scope:** Explicitly isolate and evaluate performance on Russian and Kazakh message samples, documenting any limitations where data is scarce.
4. **Robustness Testing:** Test model resilience against deliberate spelling variations, formatting changes, and temporal concept drift.
5. **Evaluation Protocol:** Enforce strict data splitting prior to any augmentation, utilizing macro-F1, precision, and recall.
6. **Privacy and Output:** Minimize data retention, avoid unnecessary raw log transmission, and frame predictions strictly as **risk assessments** rather than absolute guarantees.

## 6. References

* Ababneh, A., & Bani Younes, M. (2026). ML-based SMS messaging spam detection: Impacts of text feature extraction techniques. *Journal of Cybersecurity and Privacy*, *6*(4), Article 125. https://doi.org/10.3390/jcp6040125
* Al Saidat, M. R., Yerima, S. Y., & Shaalan, K. (2024). Advancements of SMS Spam Detection: A Comprehensive Survey of NLP and ML Techniques. *Procedia Computer Science*, *244*, 248–259. https://doi.org/10.1016/j.procs.2024.10.198
* Ali, F. D. M. A., Saide, S. M., Sousa-Silva, R., & Lopes Cardoso, H. (2025). MOZ-Smishing: A benchmark dataset for detecting mobile money frauds. In *Proceedings of the Sixth Workshop on African Natural Language Processing* (pp. 158–166). Association for Computational Linguistics. https://doi.org/10.18653/v1/2025.africanlp-1.23
* Almeida, T., & Hidalgo, J. (2011). *SMS Spam Collection* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5CC84
* Altunay, H. C., & Albayrak, Z. (2024). SMS spam detection system based on deep learning architectures for Turkish and English messages. *Applied Sciences*, *14*(24), Article 11804. https://doi.org/10.3390/app142411804
* Amaral Cejas, O., Guo, Y., & Tang, Q. (2026). Large-scale multilingual SMS fraud detection for telecom networks. In *Proceedings of the Second International Conference on Natural Language Processing and Artificial Intelligence for Cyber Security* (pp. 64–73). ACL Anthology. https://aclanthology.org/2026.nlpaics-1.7/
* Birthriya, S. K., Ahlawat, P., & Jain, A. K. (2026). Machine learning-based smishing detection using fuzzy logic and TF-IDF feature engineering. *Franklin Open*, *14*, Article 100506. https://doi.org/10.1016/j.fraope.2026.100506
* Devlin, J., Chang, M.-W., Lee, K., & Toutanova, K. (2019). BERT: Pre-training of deep bidirectional transformers for language understanding. In *Proceedings of NAACL-HLT 2019* (pp. 4171–4186). https://doi.org/10.18653/v1/N19-1423
* Filali, A., Shorfuzzaman, M., Abdellaoui Alaoui, E., Merras, M., Es-Sabry, M., Berrajaa, A., Alroobaea, R., & Yousef, A. (2026). Cross-lingual SMS spam detection using GAN-based augmentation for imbalanced datasets. *Scientific Reports*, *16*, Article 7128. https://doi.org/10.1038/s41598-026-37769-4
* Hur, M., Seo, S., Hwang, J., & Min, M. (2026). Are large language models effective for detecting spam messages? *International Journal of Information Security*, *25*, Article 127. https://doi.org/10.1007/s10207-026-01283-5
* Lochstampfor, C., & Roy, A. (2026). A synthetic conversational smishing dataset for social engineering detection. *arXiv*. https://arxiv.org/abs/2604.11752
* Martínez-Mendoza, A., Fidalgo, E., Alegre, E., & Fernández-Robles, L. (2026). Building a multi-class Short Message Service dataset for smishing detection using agglomerative clustering and dataset fusion. *Engineering Applications of Artificial Intelligence*, *163*, Article 112864. https://doi.org/10.1016/j.engappai.2025.112864
* Roy, P. K., Singh, J. P., & Banerjee, S. (2020). Deep learning to filter SMS spam. *Future Generation Computer Systems*, *102*, 524–533. https://doi.org/10.1016/j.future.2019.09.001
* Salman, M., Ikram, M., & Kaafar, M. A. (2024). Investigating evasive techniques in SMS spam filtering: A comparative analysis of machine learning models. *IEEE Access*, *12*, 24306–24324. https://doi.org/10.1109/ACCESS.2024.3364671
* Shahbazov, V. (2026). Development of a lightweight two-stage hybrid classifier for privacy-preserving on-device multi-class SMS threat detection. *EUREKA: Physics and Engineering*, (5), 194–209. https://doi.org/10.21303/2461-4262.2026.004397
* Xu, H., Qadir, A., & Sadiq, S. (2025). Malicious SMS detection using ensemble learning and SMOTE to improve mobile cybersecurity. *Computers & Security*, *154*, Article 104443. https://doi.org/10.1016/j.cose.2025.104443