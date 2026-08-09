# Drug–ADE Insight Engine

A conceptual web application prototype demonstrating a future pharmacovigilance system for discovering potential **Adverse Drug Events (ADEs)** and **Drug–ADE relationships** from patient-generated drug reviews.

> **Conceptual Research Prototype · UI Demonstration · Pharmacovigilance**

---

## Overview

The **Drug–ADE Insight Engine** is a one-page web application designed to demonstrate the proposed user experience and analytical workflow of our research project.

The webpage does **not implement the complete NLP, machine-learning, or association-rule-mining pipeline**. Instead, it provides a visual and interactive demonstration of how these components could be integrated into a future end-to-end system.

The proposed workflow is:

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
Association Rule Mining
        ↓
Drug–ADE Relationship Insights
```

The models and methods shown in the interface are based on the methodology developed in the accompanying research project.

---

## Purpose of the Prototype

The purpose of this webpage is to:

* Demonstrate the proposed Drug–ADE analysis workflow.
* Provide an intuitive interface for entering patient reviews.
* Illustrate how NLP-derived information could be presented to users.
* Demonstrate how machine-learning predictions could appear in a future system.
* Visualize potential Drug–ADE relationships obtained through association rule mining.
* Provide a proof-of-concept interface for future backend integration.

**The current webpage is a demonstration interface rather than a fully deployed analytical system.**

---

## Demonstrated Workflow

### 1. Patient Review Input

The user provides:

* **Drug Name**
* **Patient Review**

A sample review can also be loaded using the **Try Example** option.

---

### 2. Hybrid Drug–ADE Analysis

The prototype presents the concept of a hybrid NLP pipeline combining:

* Transformer-based Drug–ADE extraction
* ADE normalization
* Negation detection
* Severity detection
* Frequency detection
* Confidence aggregation
* Silver-label generation

The actual research pipeline uses **SpanBERT-based Drug–ADE extraction combined with rule-based NLP processing**.

The webpage only demonstrates how the resulting information could be presented in a future application.

---

### 3. Context-Aware Sentiment Analysis

The research methodology incorporates **Twitter-RoBERTa** for sentiment analysis.

**Model used in the research:**

`cardiffnlp/twitter-roberta-base-sentiment-latest`

The prototype demonstrates the presentation of:

* Sentiment
* Sentiment score

The webpage itself does not run the transformer model.

---

### 4. Machine Learning Prediction

The research workflow uses a **Support Vector Machine (SVM)** as the machine-learning classifier.

The proposed feature representation combines:

```text
TF-IDF Features
        +
Drug–ADE Features
        +
Sentiment Features
        ↓
      SVM
        ↓
ADE-related Prediction
```

The webpage demonstrates how an SVM prediction and confidence value could be displayed to a user.

**The trained SVM model is not executed directly by the current frontend.**

---

### 5. Drug–ADE Relationship Insights

The research project also incorporates **Association Rule Mining (ARM)** to identify recurring patterns between drugs and ADEs.

The prototype demonstrates how potential rules could be presented using measures such as:

* Support
* Confidence
* Lift

These visualized relationships are intended to demonstrate the concept of the future system rather than provide live, dynamically generated association rules.

> Association rules represent patterns in the analyzed data and do not establish causal relationships between drugs and adverse events.

---

## Research Models Referenced

The prototype is based on the following research methodology:

| Component             | Model / Method              | Role                                         |
| --------------------- | --------------------------- | -------------------------------------------- |
| Drug–ADE Extraction   | SpanBERT-ADE                | Drug and ADE extraction                      |
| Rule-Based Processing | Custom dictionaries & rules | Normalization, negation, severity, frequency |
| Sentiment Analysis    | Twitter-RoBERTa             | Sentiment classification                     |
| Machine Learning      | SVM                         | ADE-related prediction                       |
| Association Mining    | ARM                         | Drug–ADE relationship discovery              |

These components represent the **research methodology behind the prototype** and are not all directly executed within the webpage.

---

## Interface Sections

The one-page application demonstrates the following sections:

### Analyze a Patient Review

Input interface for:

* Drug name
* Patient review
* Example review
* Analyze Review action

### Review Analysis

Conceptual display of:

* Detected ADEs
* ADE count
* Severity
* Frequency
* Sentiment
* Confidence

### Hybrid NLP Analysis

Visual explanation of the proposed NLP workflow.

### ADE Prediction

Conceptual display of:

* SVM prediction
* Prediction confidence

### Drug–ADE Relationship Insights

Demonstration of potential association-rule results containing:

* Drug
* ADE
* Support
* Confidence
* Lift

### Research Pipeline

A visual summary of the complete proposed workflow.

---

## Prototype Architecture

```text
                    WEB APPLICATION
                          │
                          ▼
                Patient Review Input
                          │
                          ▼
                 Demonstration Layer
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
        ▼                 ▼                 ▼
   Hybrid NLP        Sentiment          SVM Prediction
   Analysis          Analysis           Demonstration
        │                 │                 │
        └─────────────────┼─────────────────┘
                          ▼
                Drug–ADE Insights
                          │
                          ▼
             Association Mining Concept
```

The interface is intentionally designed as a **frontend demonstration layer** for the proposed research architecture.

---

## Data

The underlying research uses the **UCI Drug Review Dataset** containing patient-generated medication reviews.

The original dataset contains:

```text
uniqueID
drugName
condition
review
rating
date
usefulCount
```

The research pipeline enriches the original data with Drug–ADE and sentiment-related features, including:

```text
ade_entities
ade_count
silver_label
max_confidence
max_severity
max_frequency
sentiment
sentiment_score
```

The complete datasets are not included in this webpage repository because of their large file size.

---

## Important Limitation

This application should be understood as a **conceptual proof-of-concept**, not a fully operational pharmacovigilance engine.

The webpage currently demonstrates the **idea, workflow, and intended user experience** rather than executing the complete research pipeline in real time.

In particular, the frontend does not independently perform:

* Transformer-based ADE extraction
* Rule-based NLP processing
* Real-time sentiment inference
* SVM model inference
* Live association-rule mining

These components represent the analytical methods proposed and implemented separately as part of the research work.

---

## Future Development

The prototype can be extended into a complete end-to-end application by connecting the interface to the actual research pipeline through a backend API.

A future implementation could:

```text
Web Interface
      ↓
Backend API
      ↓
Hybrid NLP Pipeline
      ↓
Twitter-RoBERTa
      ↓
Feature Engineering
      ↓
Trained SVM
      ↓
Association Rule Mining
      ↓
Live Results
```

This would allow patient reviews entered through the webpage to be processed by the actual trained models and return dynamically generated results.

---

## Research Disclaimer

**Drug–ADE Insight Engine is a conceptual research prototype. The information presented by the interface is intended to demonstrate a proposed pharmacovigilance workflow and should not be interpreted as confirmed adverse drug events, medical diagnoses, causal relationships, or medical advice.**

---

## Authors

**Nanzeeba Ayman, Nadia Mahzabin, Umme Hafsa Mazumder**
Department of Computer Science, Asian University for Women

---

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
