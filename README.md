# Drug–ADE Pharmacovigilance Framework

A hybrid pharmacovigilance framework for analyzing patient drug reviews to extract and structure **Drug–Adverse Drug Event (ADE)** information, incorporate severity, frequency, confidence and sentiment features, evaluate machine-learning models, and discover Drug–ADE associations through **Apriori and FP-Growth**.

## Overview

This project explores how patient-generated drug reviews can be transformed from unstructured text into structured pharmacovigilance knowledge.

**Overall workflow:**

`Patient Reviews → Hybrid NLP → Structured Drug–ADE Features → Sentiment → Machine Learning → Association Rule Mining → Drug–ADE Insights`

The project combines transformer-based information extraction, rule-based NLP processing, sentiment analysis, supervised machine learning, and association rule mining in an integrated workflow.

## Research Questions

**RQ1:** How accurately can drug entities and adverse drug events be extracted and identified from patient review text using NLP techniques?

**RQ2:** How can sentiment-aware analysis and structured relationship construction improve the performance of machine learning models in detecting and structuring adverse drug event information?

**RQ3:** How can association rule mining and pattern analysis techniques uncover meaningful relationships between drugs and adverse side effects in patient review data?
## Key Contributions

- Developed a **hybrid NLP pipeline** combining transformer-based ADE extraction with rule-based post-processing.
- Converted unstructured patient reviews into structured Drug–ADE features.
- Incorporated **ADE count, severity, frequency, confidence, and sentiment** into downstream analysis.
- Compared five classical ML models across progressively richer feature sets.
- Applied **Apriori and FP-Growth** to discover interpretable Drug→ADE association patterns.

## Methodology

### 1. Data

The project uses the **UCI Drug Review Dataset** ( https://huggingface.co/datasets/dd-n-kk/uci-drug-review-cleaned ) containing patient-generated medication reviews and associated metadata such as drug name, condition, rating, date, and useful count.

### 2. Hybrid NLP Pipeline

The pipeline combines:

**Transformer-based ADE extraction**
- A pretrained SpanBERT-based ADE model extracts adverse-event spans from reviews.

**Rule-based post-processing**
- ADE normalization
- Negation detection
- Severity detection
- Frequency detection
- Confidence aggregation
- Silver-label generation

The resulting structured information includes:

- Drug
- ADE entities
- ADE count
- Maximum confidence
- Maximum severity
- Maximum frequency
- Silver label

### 3. Sentiment Analysis

Context-aware sentiment analysis produces:

- Sentiment label
- Sentiment score/confidence

These features are added to the final ML feature set to investigate the contribution of sentiment-aware information.

### 4. Machine Learning

Three feature sets were evaluated:

| Feature Set | Features |
|---|---|
| **A — Baseline** | TF-IDF |
| **B — Hybrid** | TF-IDF + Rating + Maximum Severity + Maximum Frequency |
| **C — Hybrid + Sentiment** | TF-IDF + Rating + Maximum Severity + Maximum Frequency + Sentiment + Sentiment Score |

Five models were compared:

- Random Forest
- SVM
- XGBoost
- LightGBM
- CatBoost

Evaluation metrics:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

The experiments function as a controlled feature comparison to evaluate whether structured hybrid and sentiment-aware features improve ADE-related prediction.

### 5. Association Rule Mining

Association Rule Mining was performed separately from supervised classification to discover interpretable Drug–ADE patterns.

Algorithms:

- **Apriori**
- **FP-Growth**

Rule metrics:

- Support
- Confidence
- Lift

The main relationship of interest is:

`Drug → ADE`

## ARM Results

Under the selected ARM configuration:

- **342** frequent itemsets
- **75** total association rules
- **7** Drug→ADE rules

Apriori and FP-Growth produced the same counts under the selected settings.

Examples of strong associations observed:

| Drug → ADE | Confidence | Lift |
|---|---:|---:|
| Miconazole → Itching | 70.4% | 35.24 |
| Phentermine → Dry Mouth | 58.4% | 17.22 |
| Citalopram → Anxiety | 61.1% | 3.76 |
| Zoloft → Anxiety | 59.7% | 3.67 |
| Sertraline → Anxiety | 59.5% | 3.66 |

These are **statistical associations in the review data, not evidence of clinical causality**.

## Final Dataset

The orginal UCI Drug Review Dataset contains seven attributes:

- `uniqueID`
- `drugName`
- `condition`
- `review`
- `rating`
- `date`
- `usefulCount`

The original patient reviews were processed through the proposed
Hybrid Drug–ADE Extraction Pipeline. The pipeline combines
transformer-based ADE extraction with rule-based NLP processing,
including ADE normalization, negation detection, severity detection,
frequency detection, and confidence aggregation.

Context-aware sentiment analysis was subsequently applied to the
reviews.

This process generated an enhanced silver-labelled dataset containing
the original attributes together with structured Drug–ADE and
sentiment features.

### Final Dataset Features

| Feature | Description |
|---|---|
| `uniqueID` | Original review identifier |
| `drugName` | Drug name |
| `condition` | Medical condition |
| `review` | Patient review |
| `rating` | Original patient rating |
| `date` | Review date |
| `usefulCount` | Original usefulness count |
| `ade_entities` | Extracted ADE entities |
| `ade_count` | Number of extracted ADEs |
| `silver_label` | Generated silver ADE label |
| `max_confidence` | Maximum ADE extraction confidence |
| `max_severity` | Maximum detected severity |
| `max_frequency` | Maximum detected frequency |
| `sentiment` | Review sentiment |
| `sentiment_score` | Sentiment score |

The complete processed dataset is not included in this repository
because of its large file size. The repository instead contains the
processing code and rule-based dictionaries used to generate the
enhanced dataset.


## Architecture

```text
Patient Drug Reviews
        │
        ▼
Hybrid NLP Pipeline
        │
        ├── Transformer ADE Extraction
        └── Rule-Based Processing
              ├── Normalization
              ├── Negation
              ├── Severity
              ├── Frequency
              └── Confidence
        │
        ▼
Structured Drug–ADE Features
        │
        ▼
Sentiment Analysis
        │
        ▼
Feature Sets A / B / C
        │
        ▼
ML Models
┌──────────────────────────────────────┐
│ RF │ SVM │ XGBoost │ LGBM │ CatBoost │
└──────────────────────────────────────┘
        │
        ▼
Model Evaluation

Structured Drug–ADE Transactions
        │
        ▼
Apriori + FP-Growth
        │
        ▼
Support / Confidence / Lift
        │
        ▼
Drug–ADE Relationship Insights
```

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- Hugging Face Transformers
- TF-IDF
- XGBoost
- SVM
- Random Forest
- LightGBM
- CatBoost
- mlxtend
- NetworkX
- Matplotlib
- Seaborn
- Google Colab

## Future Direction

The research provides the foundation for a potential **Drug–ADE Insight Engine** where a user could enter a drug name and patient review and receive:

1. Detected ADEs
2. Severity and frequency information
3. Sentiment/context analysis
4. ADE-related prediction
5. Relevant Drug–ADE relationship insights

Future work includes human-annotated validation, external dataset validation, improved/domain-specific NLP models, multilingual analysis, temporal monitoring, and clinical/pharmacovigilance validation.

## Limitations

- Patient reviews can be noisy, subjective, informal, and incomplete.
- Automatically generated silver labels require further validation against expert annotations.
- Results require validation on external datasets.
- ARM identifies co-occurrence patterns and does not establish drug–ADE causality.
- Clinical validation is required before real-world pharmacovigilance deployment.

## Disclaimer

> **Research prototype only.** This project is not a medical diagnostic system and should not be used to provide medical advice or establish drug causality. Association-rule results represent patterns in the analyzed dataset and require clinical validation.

## Authors
**Nanzeeba Ayman, Nadia Mahzabin, Umme Hafsa Mazumder**
Department of Computer Science, Asian University for Women

