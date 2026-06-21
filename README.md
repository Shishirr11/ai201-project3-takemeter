# Physics Text Classification using DistilBERT + Groq Baseline

## 📌 Overview

This project builds a text classification system for Reddit-style physics posts. The goal is to classify each post into one of four categories:

- Concept Explanation
- Problem Solving
- Interpretation
- Reaction/Curiosity

The project compares a zero-shot LLM baseline (Groq) with a fine-tuned DistilBERT model.

## 📊 Dataset

- **Size:** 200+ labeled Reddit-style physics posts
- **Format:** CSV (`text`, `label`, `notes`)
- **Style:** Long-form, noisy, realistic physics discussions
- Includes ambiguous "hard cases" to simulate real-world uncertainty

## 🏷️ Labels

| Label | Description |
|---|---|
| Concept Explanation | Definitions and explanations of physics concepts |
| Problem Solving | Numerical / equation-based problems |
| Interpretation | Conceptual meaning / philosophical reasoning |
| Reaction/Curiosity | Emotional or informal reactions |

## 🤖 Models

**Baseline (Groq Zero-shot)**
- Accuracy: 0.8125

**Fine-tuned Model (DistilBERT)**
- Accuracy: 0.9375
- Improvement: +0.125

## 📈 Per-Class Metrics (Fine-tuned)

| Class | Precision | Recall | F1 |
|---|---|---|---|
| Concept Explanation | 1.00 | 0.75 | 0.86 |
| Problem Solving | 1.00 | 1.00 | 1.00 |
| Interpretation | 0.82 | 1.00 | 0.90 |
| Reaction/Curiosity | 1.00 | 1.00 | 1.00 |

## 📉 Confusion Matrix (Fine-tuned Model)

| Actual \ Predicted | Concept | Problem | Interpretation | Reaction |
|---|---|---|---|---|
| Concept Explanation | 6 | 0 | 2 | 0 |
| Problem Solving | 0 | 8 | 0 | 0 |
| Interpretation | 0 | 0 | 9 | 0 |
| Reaction/Curiosity | 0 | 0 | 0 | 7 |

## ❌ Error Analysis

**Error 1: Concept Explanation → Interpretation**
Model misclassified due to uncertainty language ("I'm confused"), showing over-reliance on tone.

**Error 2: Concept Explanation → Interpretation**
Short definitional sentences misclassified due to lack of explicit instructional structure.

## 🧠 Key Insight

The model does not struggle with physics knowledge, but with intent detection vs. linguistic tone.

**Main confusion:** Concept Explanation vs Interpretation

## 📊 Sample Predictions

| Text | Predicted Label | Confidence |
|---|---|---|
| "Black holes are insane to think about" | Reaction/Curiosity | 0.38 |
| "Newton's laws describe motion…" | Concept Explanation | 0.34 |
| "Relativity feels like time is changing" | Interpretation | 0.31 |

## 🔍 Reflection

The model learns:
- Structured reasoning → Problem Solving
- Emotional tone → Reaction/Curiosity

But struggles with:
- Distinguishing explanation vs. interpretation

## ⚖️ Spec Reflection

✔ Helped enforce strict label definitions
❌ Diverged because real Reddit posts often mix explanation + interpretation

## 🤖 AI Usage

- Used AI to design classification prompts for Groq
- Used AI to analyze misclassified examples and identify patterns
- Manually verified and corrected dataset and labels
