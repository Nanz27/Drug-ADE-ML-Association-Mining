# Drug Insight Engine

Build a One-Page Web Application: “Drug–ADE Insight Engine”

Create a polished, modern, responsive one-page research prototype called:

Drug–ADE Insight Engine

This is a conceptual pharmacovigilance research application designed for a university research presentation. It demonstrates how patient-generated drug reviews could be processed through a hybrid NLP pipeline, an XGBoost prediction model, and association rule mining to produce interpretable Drug–ADE insights.

The application should feel like a real future research product, not a generic chatbot and not a hospital-management dashboard.

1. CORE CONCEPT

The application demonstrates this end-to-end workflow:

Patient Review
↓
Hybrid NLP Analysis
↓
ADE + Context Extraction
↓
TF-IDF + Hybrid NLP Features + Sentiment
↓
XGBoost Prediction
↓
ADE Prediction
↓
Association Rule Mining
↓
Drug–ADE Relationship Insights

The technical pipeline should be visually understandable, but the main focus must remain on the results presented to the user.

2. VISUAL DESIGN

Use a clean, modern academic health-tech aesthetic.

Design language

White / very light background

Navy, blue, and teal as primary accent colors

Dark navy text

Soft gray borders

Rounded cards

Subtle shadows

Clean typography

Generous whitespace

Small, meaningful icons

Minimal charts

Professional data visualization

Responsive design

Desktop-first but mobile-friendly

The design should resemble a polished research technology prototype, rather than a commercial medical portal.

Avoid

Generic chatbot UI

Chat bubbles

Hospital-management-system styling

Excessive gradients

Excessive animations

Large decorative illustrations

Dense dashboards

Too many metrics

Unnecessary technical jargon

Overly complicated navigation

3. PAGE STRUCTURE

Everything must fit naturally into one scrollable page.

Use a simple structure:

Header / Hero

Review Input

Review Analysis

ADE Prediction

Drug–ADE Relationship Insights

Analysis Summary

Research Pipeline Overview

Disclaimer Footer

Do not create multiple pages.

4. HEADER / HERO

At the top, create a compact professional header.

Brand

Drug–ADE Insight Engine

Small subtitle:

Hybrid NLP-powered Drug–Adverse Event Analysis

Add a short description:

Analyze patient-generated medication reviews to identify possible adverse drug events, predict ADE-related reviews, and explore Drug–ADE patterns discovered from review data.

Include a small visual indicator such as:

Research Prototype

This should clearly communicate that this is an academic prototype.

5. USER INPUT SECTION

Create a prominent card titled:

Analyze a Patient Review

Include two fields.

Drug Name

Label:

Drug Name

Placeholder:

Enter drug name

Patient Review

Label:

Patient Review

Use a larger textarea.

Placeholder:

Enter a patient review about the medication...

Below the textarea, include a small secondary button:

Try Example

When clicked, populate the fields with a realistic example review.

Example:

Drug Name:
Sertraline

Review:
I started taking sertraline a few weeks ago. It has helped with my mood, but I occasionally feel nauseous and dizzy, especially after taking my morning dose.

Primary CTA:

Analyze Review

Use a strong navy/blue button.

The button should trigger the demo analysis flow.

6. REVIEW ANALYSIS

After analysis, display a section titled:

Review Analysis

Add a subtle status indicator:

✓ Analysis completed

Do NOT expose every internal NLP step. Only show the important user-facing results.

Create a clean grid of result cards.

Detected ADEs

Show:

Nausea
Dizziness

Use pill/tag components.

ADE Count

2

Severity

Moderate

Frequency

Occasional

Sentiment

Negative

Confidence

91%

For confidence, use a compact horizontal progress indicator.

Each result should have a small relevant icon where appropriate.

7. NLP PROCESSING INDICATOR

Below or beside the Review Analysis results, include a small expandable or compact technical information area titled:

Hybrid NLP Analysis

Keep it visually secondary.

Show the conceptual stages as small steps:

ADE Extraction → Normalization → Negation → Severity → Frequency → Sentiment

Use subtle connected lines or arrows.

Do not overwhelm the user with implementation details.

This section exists primarily to demonstrate the research methodology during a presentation.

8. ADE PREDICTION SECTION

Create the main prediction card titled:

ADE Prediction

Add a small model badge:

XGBoost

Below it show:

Feature Set

TF-IDF + Hybrid NLP Features + Sentiment

Then create a prominent prediction result.

Prediction

ADE-related

Confidence

87%

Display the confidence using a large but clean probability/progress visualization.

For example:

87%

with a horizontal confidence bar.

Add a small explanatory line:

The model predicts that this review is likely to contain an adverse drug event.

IMPORTANT:

The interface must distinguish between demo/mock output and an actual connected machine-learning model.

Include a subtle label such as:

Demo prediction — connect trained XGBoost model for live inference

The architecture must be prepared so that a real trained:

XGBoost model

TF-IDF vectorizer

preprocessing pipeline

feature transformation pipeline

can be connected later.

Do NOT present hard-coded demo predictions as if they were generated by a real trained model.

9. DRUG–ADE RELATIONSHIP INSIGHTS

Create a visually distinct section titled:

Drug–ADE Relationship Insights

Add a short explanation:

Association rule mining can identify recurring relationships between medications and adverse drug events across the available review dataset.

Clearly label this as:

Association Rule Mining

Then show relevant discovered relationships.

Example demo relationship:

Sertraline → Anxiety

Display:

Support: 16.3%
Confidence: 59.5%
Lift: 3.66×

Use a clean horizontal relationship card:

Sertraline → Anxiety

with the metrics underneath.

10. ASSOCIATION VISUALIZATION

Add a small, minimal visualization titled:

Strongest Drug–ADE Associations

Use a clean horizontal bar chart or node-link style visualization.

Keep it simple.

Example:

Sertraline → Anxiety
Sertraline → Nausea
Fluoxetine → Headache

However:

IMPORTANT DATA BEHAVIOR

These are demo relationships only.

Do NOT hard-code the example ARM results as a permanent knowledge base.

The architecture should allow future association-rule results to be loaded dynamically from a dataset or backend.

The visualization must automatically update when new rules are supplied.

The application should support fields such as:

Drug

ADE

Support

Confidence

Lift

If no relevant association exists for the entered drug, display:

No strong Drug–ADE relationship identified in the available data.

Do NOT invent relationships.

11. ANALYSIS SUMMARY

At the bottom of the results area, create a concise card titled:

Analysis Summary

Present the key findings in an easy-to-scan format.

Example:

Drug
Sertraline

Detected ADEs
Nausea, Dizziness

Sentiment
Negative

ADE Prediction
ADE-related

Confidence
87%

Related Drug–ADE Patterns
3 identified

Use a clean two-column layout on desktop and stack on mobile.

12. ANALYZE ANOTHER REVIEW

At the end of the results section, add a prominent secondary CTA:

Analyze Another Review

When clicked:

Clear the current results

Reset the input fields

Return focus to the review input area

Keep the interaction simple and smooth.

13. RESEARCH PIPELINE OVERVIEW

Near the bottom of the page, add a compact section titled:

How the Engine Works

Do not make this the main focus.

Use a horizontal workflow on desktop and a vertical workflow on mobile:

PATIENT REVIEW
↓
HYBRID NLP
↓
ADE + CONTEXT EXTRACTION
↓
TF-IDF + HYBRID FEATURES + SENTIMENT
↓
XGBOOST
↓
ADE PREDICTION
↓
ASSOCIATION RULE MINING
↓
DRUG–ADE INSIGHTS

Use simple icons and thin connecting arrows.

Keep the labels concise.

Add a small caption:

The prototype represents a future end-to-end pharmacovigilance analysis workflow.

14. DEMO / MOCK DATA BEHAVIOR

The application should be fully interactive even before the real ML backend is connected.

For demonstration purposes:

Provide a Try Example button.

Populate realistic example input.

Show example analysis results after clicking Analyze Review.

Clearly label these outputs as Demo Results or Prototype Results where appropriate.

Do NOT claim that the prototype is currently running a trained XGBoost model unless the model is actually connected.

Structure the frontend so that the demo inference logic can later be replaced with an API call.

For example, conceptually structure the application around:

POST /analyze

with future response fields such as:

drug

detected_ades

ade_count

severity

frequency

sentiment

sentiment_confidence

prediction

prediction_confidence

related_rules

Do not require the backend to exist now.

15. FUTURE MODEL INTEGRATION

Design the frontend architecture so these components can later be connected:

NLP Pipeline

Transformer-based ADE extraction

ADE normalization

Negation detection

Severity detection

Frequency detection

Confidence aggregation

Context-aware sentiment analysis

Feature Engineering

TF-IDF features

Hybrid Drug–ADE features

Sentiment features

Prediction

XGBoost

The XGBoost model should be clearly identified as the primary ADE classification model.

Association Mining

Future dynamic results from:

Apriori

FP-Growth

Other association-rule mining methods

The UI should not depend on a fixed list of drugs or ADEs.

16. IMPORTANT RESEARCH ACCURACY RULES

This is a research prototype, so avoid misleading medical claims.

Do NOT say:

"This drug causes..."

"The patient has..."

"This confirms an adverse event."

"This proves causality."

Instead use language such as:

"Detected possible ADE"

"ADE-related prediction"

"Association identified in review data"

"Pattern observed in available data"

"Possible relationship"

Association rule mining must be presented as pattern discovery, not causal inference.

17. RESPONSIVE DESIGN

Desktop:

Centered content container

Maximum width around 1100–1200px

Comfortable spacing

Two-column layouts where appropriate

Tablet:

Reduce column widths

Preserve readability

Mobile:

Stack cards vertically

Full-width input fields

Full-width buttons

Horizontal workflow becomes vertical

Charts remain readable

No horizontal page scrolling

18. MICRO-INTERACTIONS

Keep animations subtle.

Allowed:

Smooth section reveal after analysis

Button loading state

Progress animation for confidence

Small hover effects

Smooth scrolling to results

Avoid:

Excessive motion

Spinning loaders everywhere

Animated backgrounds

Chat-style typing animations

When the user clicks Analyze Review, show a brief loading state:

Analyzing review...

Then reveal the results.

19. ACCESSIBILITY

Use:

High text contrast

Clearly associated labels

Large enough click targets

Keyboard-friendly controls

Visible focus states

Semantic HTML

Accessible chart labels

Do not rely only on color to communicate prediction status.

20. FOOTER

Add a small, subtle footer:

Research prototype based on patient-generated review data. Predictions and associations indicate patterns in the data and do not establish medical causality or provide medical advice.

Also include:

Drug–ADE Insight Engine · Research Prototype

21. OVERALL USER EXPERIENCE

The entire page should communicate one simple idea:

I enter a drug and patient review → the engine analyzes the review → identifies possible adverse events → evaluates sentiment and context → predicts whether the review is ADE-related using XGBoost → and shows broader Drug–ADE patterns discovered from review data.

The application should feel:

Research-focused + modern + interpretable + lightweight + credible

It should be something I can confidently demonstrate during a university research presentation.

Prioritize clarity over complexity.

The most important content on the page should be:

Patient Review Input

Detected ADEs

Sentiment / Context

XGBoost ADE Prediction

Drug–ADE Relationship Insights

Concise Analysis Summary

Everything else should remain visually secondary.

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
