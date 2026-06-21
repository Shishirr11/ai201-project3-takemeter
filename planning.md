## 📌 1. Project Goal

The goal of this project is to build a text classification system that categorizes Reddit-style physics posts into meaningful intent-based labels. The system should distinguish between conceptual understanding, problem-solving behavior, interpretation of physics ideas, and emotional reactions.

The final objective is to evaluate how well a machine learning model can capture intent in scientific text, not just keywords.

## 🏷️ 2. Label Definitions

**Concept Explanation**
Posts that explain or define physics laws, formulas, or principles in a structured way.
Example: *Newton's second law states that force equals mass times acceleration.*

**Problem Solving**
Posts involving numerical computation, equations, or step-by-step problem solving.
Example: *A 5kg object is pushed with 20N force. Find acceleration.*

**Interpretation**
Posts discussing meaning, implications, or philosophical interpretation of physics concepts.
Example: *Does relativity imply that time is not absolute across observers?*

**Reaction/Curiosity**
Posts expressing emotional reaction, curiosity, confusion, or fascination without structured reasoning.
Example: *Black holes are honestly mind blowing.*

## 📊 3. Dataset Plan

- Target size: ~200+ samples
- Source style: Reddit-like physics discussions
- Format: CSV with columns:
  - `text`
  - `label`
  - `notes` (optional)

**Key Design Choice:**
Posts are intentionally written in long-form natural language to simulate real-world noisy data rather than clean textbook sentences.

## ⚠️ 4. Hard Cases Strategy

Some samples are intentionally ambiguous to simulate real-world classification challenges.

Examples of ambiguity:
- Concept Explanation vs Interpretation
- Problem Solving vs Concept Explanation

These are labeled carefully and documented in the `notes` column.
At least 2–3 hard cases are explicitly tracked.

## ⚖️ 5. Labeling Rules

- Each example must have exactly one label
- Labels must match exactly (case-sensitive)
- If a post contains mixed intent:
  - choose dominant intent
  - document ambiguity in `notes`

## 🧪 6. Evaluation Plan

The model will be evaluated using:

**Metrics:**
- Accuracy
- Precision / Recall / F1-score
- Confusion Matrix

**Baseline:**
- Zero-shot classification using Groq LLM

**Fine-tuned Model:**
- DistilBERT fine-tuned on labeled dataset

## 🤖 7. AI Usage Plan

AI tools are used for:
- Assisting with dataset diversity and realism
- Helping design classification prompts
- Identifying patterns in misclassified predictions

All AI-generated outputs are manually reviewed and corrected before use.

## 🔍 8. Expected Challenges

- Overlap between Concept Explanation and Interpretation
- Short posts lacking structural signals
- Emotional language influencing classification
- Ambiguous scientific phrasing

## 📈 9. Success Criteria

The project is considered successful if:
- Fine-tuned model significantly outperforms baseline
- Confusion matrix shows clear structure
- Error cases are explainable and consistent
- Model demonstrates understanding of intent beyond keywords

## 🧠 10. Key Insight (Design Philosophy)

This project focuses on intent classification in scientific discourse, not factual physics understanding.

The key question is:
*Can a model distinguish between explaining physics, solving physics, interpreting physics, and reacting emotionally to physics?*
