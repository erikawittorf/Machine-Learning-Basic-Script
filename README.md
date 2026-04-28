1. Dataset Construction and Scope
The script begins with a small, manually labeled dataset consisting of short text samples and binary labels:

1 → text that may exhibit manipulative linguistic patterns
0 → text that appears neutral or non‑manipulative

This dataset is explicitly limited in size and scope. Its purpose is illustrative and methodological, not definitive. In research terms, it serves as a proof‑of‑concept corpus rather than a representative sample of real‑world discourse.
Key implications:

Labels reflect human interpretation, not objective truth.
Disagreements among annotators would be expected at scale.
Model performance must be interpreted cautiously.

This constraint is intentional and aligns with best practices for ethically sensitive NLP tasks.

2. Train–Test Split: Enabling Measurement
The dataset is divided into training and testing subsets using a stratified split. This ensures:

Each split preserves the proportion of labeled classes
Evaluation occurs on unseen data, mitigating memorization

This step establishes the foundation for measurable outcomes. Without it, model performance could not be meaningfully evaluated.
From a research perspective, this represents a basic form of internal validity control—separating learning from evaluation.

3. Text Vectorization: Translating Language into Features
The script uses TF‑IDF (Term Frequency–Inverse Document Frequency) vectorization to convert text into numerical features.
What TF‑IDF does:

Measures how often words or word pairs appear in a text
Down‑weights terms that appear frequently across all texts
Emphasizes terms that are more distinctive

The use of unigrams and bigrams allows the model to capture:

Single words (e.g., never, always)
Short phrases (e.g., if you cared, after everything)

Stop words are removed to reduce noise, focusing the model on semantically meaningful units.
Importantly, this choice prioritizes interpretability over complexity. Each feature corresponds to observable language patterns, which can later be inspected.

4. Classifier Choice: Logistic Regression
The classifier used is logistic regression, a linear probabilistic model commonly employed in text classification research.
Reasons this choice is appropriate:

Produces probabilistic outputs instead of hard claims
Offers transparent decision boundaries
Performs well on sparse text data
Can be inspected for feature contributions

The class_weight="balanced" parameter compensates for small or uneven datasets, ensuring neither label is implicitly privileged.
From a methodological standpoint, logistic regression serves as a baseline, against which more complex models might later be compared.

5. Training Phase: Learning Statistical Associations
During training, the model learns associations between TF‑IDF features and labels.
Critically:

The model is not learning rules
It is not identifying intent
It is learning correlations between linguistic patterns and annotations

For example, phrases that recur in labeled manipulative examples may receive higher weights. This reflects statistical regularity, not moral or psychological judgment.
This distinction is essential for interpretive honesty.

6. Evaluation Metrics: Measuring Performance Responsibly
The script evaluates performance using multiple metrics:
Accuracy
Overall correctness. Useful but insufficient on its own, especially with small datasets.
Precision
How often texts flagged as manipulative truly belonged to that class.
This matters because false positives carry ethical risk.
Recall
How much labeled manipulative language the model successfully identified.
This reflects sensitivity to potential harm signals.
F1 Score
Balances precision and recall, offering a more stable summary metric.
Confusion Matrix
Provides a granular view of error types:

False positives (over‑flagging)
False negatives (missed patterns)

This enables qualitative error analysis—a cornerstone of responsible ML research.

7. Probabilistic Outputs: Avoiding Binary Claims
Rather than stopping at predicted labels, the script outputs probability scores.
This design choice reflects an ethical stance:

Language exists on a spectrum
Certainty is unwarranted in socially nuanced tasks
Scores support human judgment rather than replace it

Researchers can later analyze thresholds, uncertainty zones, or borderline cases.

8. Result Inspection: Transparency and Reflexivity
The final output pairs each test example with:

Its true label
The model’s prediction
The associated probability

This supports:

Error analysis
Dataset refinement
Reflection on annotation assumptions

In other words, the script doesn’t just produce results—it invites critique of those results.

9. What the Script Does Not Claim to Do
Equally important is what this script explicitly does not do:

It does not detect psychological manipulation
It does not infer speaker intent
It does not account for relationships or power dynamics
It does not generalize reliably beyond its dataset

These limitations are not failures; they are research boundaries.

10. Research Value of This Script
This script functions as:

A baseline model for comparative experiments
A tool for studying linguistic tendencies, not behavior
A scaffold for feature engineering or theoretical inquiry
A defensible starting point for ethically constrained NLP work

Its primary value lies in measurement, transparency, and falsifiability, not prediction alone.
