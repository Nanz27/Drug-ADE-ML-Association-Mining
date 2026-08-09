# Drug–ADE Insight Engine

A modern research prototype for discovering potential **Adverse Drug Events (ADEs)** and **Drug–ADE associations** from patient-generated drug reviews.

> **Research Prototype · Hybrid NLP · Sentiment Analysis · Machine Learning · Association Rule Mining**

---

## Overview

The **Drug–ADE Insight Engine** demonstrates a conceptual end-to-end pharmacovigilance workflow that transforms unstructured patient drug reviews into structured Drug–ADE insights.

The system combines transformer-based NLP, rule-based processing, sentiment analysis, machine learning, and association rule mining:

```text
Patient Drug Review
        ↓
Hybrid Drug–ADE NLP Analysis
        ↓
Structured Drug–ADE Features
        ↓
Context-Aware Sentiment Analysis
        ↓
Feature Engineering
        ↓
SVM Prediction
        ↓
Drug–ADE Association Mining
        ↓
Interpretable Drug–ADE Insights
```

The application is designed as an **academic research prototype** demonstrating how patient-generated medication reviews could be analyzed to support pharmacovigilance research.

---

## Key Features

### 1. Patient Review Input

Users can provide:

* **Drug Name**
* **Patient Review**

The interface also provides a **Try Example** option for quickly demonstrating the system.

---

### 2. Hybrid Drug–ADE Extraction

The Drug–ADE extraction stage combines a transformer-based model with rule-based NLP processing.

The transformer component uses:

**SpanBERT-large fine-tuned on ADE Corpus v2**

Model:

`abhibisht89/spanbert-large-cased-finetuned-ade_corpus_v2`

The extracted entities are further processed using rule-based techniques including:

* ADE normalization
* Negation detection
* Severity detection
* Frequency detection
* Confidence aggregation
* Silver-label generation

This produces structured Drug–ADE information from unstructured patient reviews.

---

### 3. Context-Aware Sentiment Analysis

The system uses **Twitter-RoBERTa** for sentiment analysis.

Model:

`cardiffnlp/twitter-roberta-base-sentiment-latest`

The model classifies the patient review into:

* Positive
* Neutral
* Negative

and provides a corresponding sentiment score.

The sentiment information is incorporated into the downstream feature representation.

---

### 4. SVM-Based ADE Prediction

The machine-learning stage uses a **Support Vector Machine (SVM)** classifier to predict whether a review is **ADE-related**.

The prediction features combine information generated throughout the NLP pipeline:

```text
TF-IDF Features
       +
Hybrid Drug–ADE Features
       +
Sentiment Features
       ↓
    SVM Model
       ↓
ADE Prediction + Confidence
```

The web interface displays the predicted ADE-related status together with the model confidence.

---

### 5. Drug–ADE Association Rule Mining

Following the prediction stage, the system identifies recurring Drug–ADE relationships using **Association Rule Mining (ARM)**.

The resulting rules can contain:

* Drug
* ADE
* Support
* Confidence
* Lift

These measures help identify frequently occurring Drug–ADE patterns within the patient review dataset.

> Association rules represent statistical patterns in the observed review data and do not establish a causal relationship between a drug and an adverse event.

---

## Hybrid NLP Pipeline

The core Drug–ADE processing workflow is:

```text
Patient Review
      ↓
Text Preprocessing
      ↓
SpanBERT-ADE
      ↓
Drug & ADE Entity Extraction
      ↓
Rule-Based NLP Processing
      ├── ADE Normalization
      ├── Negation Detection
      ├── Severity Detection
      ├── Frequency Detection
      └── Confidence Aggregation
      ↓
Structured Drug–ADE Features
      ↓
Silver Label
```

The resulting features form the basis for subsequent sentiment analysis and machine-learning stages.

---

## Feature Engineering

The final feature representation combines multiple sources of information:

### Original Review Features

* Drug name
* Condition
* Review text
* Rating
* Date
* Useful count

### Drug–ADE Features

* ADE entities
* ADE count
* Silver label
* Maximum confidence
* Maximum severity
* Maximum frequency

### Sentiment Features

* Sentiment
* Sentiment score

These features are combined to construct the input representation for the machine-learning stage.

---

## Final Enhanced Dataset

The original UCI Drug Review dataset contains:

```text
uniqueID
drugName
condition
review
rating
date
usefulCount
```

The proposed pipeline enriches these original attributes with structured Drug–ADE and sentiment features.

The final enhanced dataset contains:

```text
uniqueID
drugName
condition
review
rating
date
usefulCount
ade_entities
ade_count
silver_label
max_confidence
max_severity
max_frequency
sentiment
sentiment_score
```

This enhanced dataset is used for subsequent **machine-learning prediction and association rule mining**.

Due to the large size of the processed dataset, the complete dataset is not included directly in this web application repository.

---

## Research Workflow

```text
                 PATIENT REVIEW
                       │
                       ▼
             ┌──────────────────┐
             │  Hybrid NLP      │
             │  Drug–ADE        │
             │  Extraction      │
             └────────┬─────────┘
                      │
                      ▼
             Drug–ADE Features
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
   Sentiment Analysis       Silver Label
   Twitter-RoBERTa               │
          │                      │
          └──────────┬───────────┘
                     ▼
              Feature Engineering
                     │
                     ▼
                   SVM
                     │
                     ▼
              ADE Prediction
                     │
                     ▼
          Association Rule Mining
                     │
                     ▼
           Drug–ADE Relationships
```

---

## Web Application

The webpage provides an interactive interface for demonstrating the research workflow.

The main sections include:

1. **Research Prototype Introduction**
2. **Patient Review Input**
3. **Review Analysis**
4. **Hybrid NLP Analysis**
5. **ADE Prediction**
6. **Drug–ADE Relationship Insights**
7. **Analysis Summary**
8. **Research Pipeline**
9. **Research Disclaimer**

The interface is designed with a clean academic health-tech aesthetic to make the analytical results understandable to both technical and non-technical audiences.

---

## Prototype Mode

The current webpage serves as a **research demonstration interface**.

Users can:

1. Enter a drug name.
2. Enter a patient review.
3. Analyze the review.
4. View extracted ADE information.
5. View sentiment results.
6. View the SVM-based ADE prediction.
7. Explore Drug–ADE relationship insights.

The interface is structured so that the frontend can later be connected directly to the complete NLP and machine-learning backend.

---

## Technologies & Models

### Natural Language Processing

* Python
* Transformer-based NLP
* Rule-based NLP
* SpanBERT

### Drug–ADE Extraction

**Model:** `abhibisht89/spanbert-large-cased-finetuned-ade_corpus_v2`

Purpose:

> Drug and ADE entity/span extraction from patient reviews.

### Sentiment Analysis

**Model:** `cardiffnlp/twitter-roberta-base-sentiment-latest`

Purpose:

> Context-aware sentiment classification of patient reviews.

### Machine Learning

**Model:** Support Vector Machine (SVM)

Purpose:

> Predict whether a patient review is ADE-related.

### Feature Engineering

* TF-IDF
* Drug–ADE features
* Sentiment features
* Review metadata

### Association Rule Mining

The system is designed to identify recurring Drug–ADE relationships using association-rule-mining techniques such as:

* Apriori
* FP-Growth

---

## Project Structure

```text
Drug-ADE-Insight-Engine/
│
├── website/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
│
├── notebooks/
│
├── src/
│   ├── preprocessing/
│   ├── ade_extraction/
│   ├── sentiment/
│   ├── feature_engineering/
│   ├── machine_learning/
│   └── association_mining/
│
├── data/
│   ├── README.md
│   └── dictionaries/
│       ├── ade_lexicon.json
│       ├── normalization_mapping.json
│       ├── negation_words.json
│       ├── severity_terms.json
│       └── frequency_terms.json
│
├── results/
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Research Purpose

The purpose of the **Drug–ADE Insight Engine** is to demonstrate how patient-generated medication reviews can be transformed into structured pharmacovigilance information using a combination of:

**Hybrid NLP + Sentiment Analysis + Feature Engineering + SVM + Association Rule Mining**

The prototype demonstrates a potential future workflow for discovering and analyzing Drug–ADE patterns from large-scale patient-generated review data.

---

## Limitations

This system is a **research prototype** and should not be considered a clinical decision-support system.

The predictions and extracted ADEs:

* Do not establish medical causality.
* Do not constitute a medical diagnosis.
* Do not replace professional medical judgment.
* Represent patterns identified from patient-generated review data.

Similarly, association rules identify statistical relationships in the analyzed data but **do not prove that a drug caused an adverse event**.

---

## Disclaimer

> **Drug–ADE Insight Engine is a research prototype based on patient-generated drug reviews. Detected ADEs, predictions, sentiments, and association rules represent patterns identified from the available data and should not be interpreted as confirmed medical causality, diagnosis, or medical advice.**

---

## Authors

**Nanzeeba Ayman, Nadia Mahzabin, Umme Hafsa Mazumder**
Department of Computer Science, Asian University for Women

---

## Project Status

**Research Prototype**

The web application demonstrates the proposed end-to-end Drug–ADE analysis workflow and provides an interactive interface for presenting the research findings.


This project was built with [Lovable](https://lovable.dev).

**Live app**: https://drugade-explorer.lovable.app

## Build with Lovable

Continue developing this project in the [Lovable editor](https://lovable.dev/projects/dfea7df1-c47c-495a-bcae-3f0c30c9036c).

- **Ship faster**: describe what you want to build and Lovable handles the code.
- **Stay in sync**: every change made in Lovable is committed straight to this repository.
- **Full ownership**: this code is yours. Push to `main` on GitHub and your changes sync back into Lovable, ready for your next prompt.

## Development

Prefer working locally? You need Node.js and npm — [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating).

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm run dev
```
