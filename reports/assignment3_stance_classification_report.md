# Assignment 3: Trump–Zelensky / Ukraine Discourse Stance Classification

**Authors:** Sagnik Chakravarty, Xiaoqing Liu, Yuchen Ding, Lingchen Meng

## Overview

This report extends previous work analyzing Reddit posts about the Ukraine–Russia conflict before and after the Trump election / Zelensky White House visit context. The goal is to classify Reddit posts into stance categories using both traditional machine learning and large language models.

The task evaluates whether posts express a stance that is:

- `Favor`
- `Oppose`
- `Neutral`
- `Irrelevant`

The project compares supervised machine learning models trained on manually labeled data with LLM-based stance classification using prompting.

## Research Question

How well can traditional machine learning models and large language models classify stance in Reddit discourse about U.S. involvement in Ukraine-related political discussion?

## Data Context

The analysis uses a manually labeled subset of Reddit posts from earlier project work. The labeled dataset contains approximately **400 hand-coded observations**.

The analysis builds on prior results showing that many Reddit threads were labeled as **Irrelevant**, but that posts after Zelensky’s White House visit showed a noticeable increase in opposing views toward the United States. Subreddit-level differences were also observed, with the Ukraine subreddit showing comparatively more favorable sentiment toward the United States than other communities.

## Methods

### Machine Learning Models

Two supervised machine learning models were evaluated:

1. **Support Vector Machine (SVM)**
2. **Decision Tree**

### Feature Extraction

The feature-engineering workflow included:

- unigram features,
- Word2Vec embeddings,
- punctuation removal,
- stopword removal,
- retention of rare but politically meaningful proper nouns.

Rare words were not aggressively removed because names such as `Trump`, `Biden`, and other political entities can carry important stance information even when they appear infrequently.

For Word2Vec, the project used:

- `cbow` training rather than skip-gram,
- embedding dimension of 100.

CBOW was selected because it is computationally efficient and performs well when the goal is to learn contextual similarity patterns across a corpus.

### Train/Test Split

The manually labeled dataset was split into:

- 80% training,
- 20% testing.

### LLM Model

The LLM component used **Gemma** models for stance classification. The report discusses use of `google/gemma-1.1-7b-it` and later evaluation with Groq’s `gemma2-9b-it`.

Prompting approaches included:

- zero-shot prompting,
- few-shot prompting,
- stance labels: `Favor`, `Oppose`, `Neutral`, `Irrelevant`.

The LLM was evaluated on the same test split used for the ML models to avoid data leakage and enable direct comparison.

## Results

### Machine Learning Results

The SVM model performed best among the traditional ML models:

| Model | Accuracy | Kappa | Notes |
|---|---:|---:|---|
| SVM | 58.0% | -0.05 | Best overall accuracy; strong bias toward Irrelevant class |
| Decision Tree | 46.77% | -0.03 | More interpretable but weaker performance |

The SVM achieved high sensitivity for the dominant **Irrelevant** class, around **94.3%**, but performed poorly on minority categories such as `Favor` and `Oppose`.

The Decision Tree also showed strong bias toward high-frequency classes. The model occasionally identified `Oppose` and `Neutral` cases, but many non-Irrelevant posts were still misclassified as `Irrelevant`.

### LLM Results

The LLM model achieved approximately **56.5% accuracy**, but precision and recall were very low:

| Model | Accuracy | Precision | Recall | Notes |
|---|---:|---:|---:|---|
| Gemma LLM | 56.5% | 19.0% | 7.5% | Favored dominant labels and ignored some minority classes |

Warnings during evaluation indicated that some stance categories were never predicted. This suggests that the LLM defaulted heavily toward certain labels and had poor coverage of minority categories.

## Discussion

The results show that accuracy alone was not a sufficient evaluation metric because the dataset was highly imbalanced. Several models achieved moderate accuracy by overpredicting the dominant `Irrelevant` class.

The SVM was ultimately the strongest model because it most closely reflected the hand-coded sentiment/stance distribution. However, it still struggled with underrepresented categories.

The LLM showed flexibility but did not outperform the traditional ML workflow in this small, imbalanced stance classification task. Its low recall and precision indicate that zero-shot or few-shot prompting without additional tuning may not be reliable for nuanced political stance detection.

## Key Takeaways

- SVM performed best overall in this setting.
- Decision Tree was more interpretable but less accurate.
- LLM prompting struggled with class imbalance and minority stance categories.
- The dominant `Irrelevant` class distorted accuracy-based evaluation.
- Future work should use stratified sampling, class balancing, synthetic augmentation, or more labeled examples.
- Multimodal context may matter because some Reddit posts rely on image content that was not available to text-only classifiers.

## Conclusion

The project finds that traditional machine learning, especially SVM, provided more reliable performance than LLM prompting for this specific stance detection task. However, all models struggled with class imbalance and minority categories. The results highlight the importance of evaluation beyond accuracy and the difficulty of automated political stance classification in small, imbalanced datasets.
