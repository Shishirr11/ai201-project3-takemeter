# TakeMeter Planning Document

## Community

For this project, I chose the Reddit r/AskPhysics community. I selected this community because it contains a wide variety of physics discussions, including conceptual explanations, problem-solving questions, theoretical interpretations, and curiosity-driven reactions. These discussions are text-heavy and naturally structured in different ways, making them ideal for classification.

Unlike general science communities, r/AskPhysics has clear distinctions between educational explanations, mathematical problem-solving, deeper analytical discussions, and emotional curiosity posts. These differences create meaningful categories that reflect how people engage with physics.

---

## Labels

### 1. Concept Explanation
A Concept Explanation is a post or comment that explains a physics law, principle, or phenomenon in an educational way.

Examples:
- “Entropy measures the number of microstates available to a system.”
- “Electric fields point in the direction a positive test charge would move.”

---

### 2. Problem Solving
A Problem Solving post focuses on calculating, deriving, or solving a physics problem.

Examples:
- “A car accelerates at 2 m/s² for 5 seconds. Find final velocity.”
- “Find the equivalent resistance in this circuit.”

---

### 3. Interpretation / Analysis
An Interpretation post discusses the meaning, implications, or reasoning behind physical laws or experimental results.

Examples:
- “Does quantum superposition imply particles exist in multiple states simultaneously?”
- “Why does energy conservation still hold in relativistic systems?”

---

### 4. Reaction / Curiosity
A Reaction post expresses fascination, confusion, or curiosity without structured explanation or problem-solving.

Examples:
- “Black holes bending time is wild.”
- “Quantum entanglement feels impossible to understand.”

---

## Hard Edge Cases

The hardest edge case in this dataset will be distinguishing between Concept Explanation and Interpretation.

Hard Case 1:
Text: "Does relativity mean time is not absolute?"
Possible labels: Concept Explanation / Interpretation
Decision: Interpretation
Reason: Focus is on implication, not teaching the theory.

Hard Case 2:
Text: "Entropy increases because systems move toward higher probability states."
Possible labels: Concept Explanation / Interpretation
Decision: Concept Explanation
Reason: Direct explanation of a physical principle.

Hard Case 3:
Text: "Quantum mechanics makes no sense to me."
Possible labels: Reaction / Interpretation
Decision: Reaction
Reason: Emotional confusion, no analytical structure.

### Decision Rule:
I will classify based on primary intent:

- If the post mainly teaches or explains a concept → Concept Explanation
- If the post mainly discusses implications or meaning → Interpretation

This rule will improve consistency during annotation.

---

## Data Collection Plan

I will collect at least 200 public posts/comments from Reddit r/AskPhysics.

Target distribution:

- Concept Explanation: 50
- Problem Solving: 50
- Interpretation: 50
- Reaction/Curiosity: 50

This balanced distribution will reduce class imbalance.

If one label is underrepresented after 200 examples, I will search using keywords like:

- “why”
- “explain”
- “calculate”
- “derive”
- “mind blowing”

Dataset format:

- text
- label
- notes

---

## Evaluation Metrics

### Accuracy
Measures the overall percentage of correct predictions.

### Precision
Important because I want predictions for technical labels like Problem Solving to be reliable.

### Recall
Important because short reaction posts may be harder to detect.

### F1 Score
Balances precision and recall for each class.

### Confusion Matrix
Helps identify common mistakes such as confusing Concept Explanation with Interpretation.

Accuracy alone is not enough because it does not show per-class weaknesses.

---

## Definition of Success

I will consider this classifier successful if:

- Overall accuracy ≥ 78%
- Each class has F1 ≥ 0.70
- Fine-tuned model outperforms Groq baseline by at least 10%
- Confusion matrix shows clear separation between Problem Solving and Concept Explanation

For deployment, the model should consistently classify educational vs analytical posts with high reliability.

---

## AI Tool Plan

### Label Stress Testing
I will use ChatGPT to generate 5–10 ambiguous physics posts between labels such as Concept Explanation vs Interpretation and Problem Solving vs Concept Explanation.

This will help refine label definitions before annotation.

---

### Annotation Assistance
I may use ChatGPT to pre-label a small batch of physics posts before manually reviewing them.

If used, I will mark them in the notes column and disclose them in README.

---

### Failure Analysis
After training, I will provide incorrect predictions to ChatGPT and ask it to identify patterns such as:

- short-text confusion
- conceptual ambiguity
- overlap between explanation and interpretation

I will verify all identified patterns manually.
