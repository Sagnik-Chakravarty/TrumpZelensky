# Trump–Zelensky / Ukraine Discourse Stance Classification

This repository documents a computational social science project analyzing Reddit discourse around the Ukraine–Russia conflict and Trump–Zelensky political context. The project compares traditional machine learning and large language model approaches for stance classification in small, imbalanced political text data.

## Repository Description

Computational social science project comparing SVM, Decision Tree, and LLM-based stance classification for Reddit discourse about Ukraine, U.S. involvement, and Trump–Zelensky political framing.

## Project Motivation

High-salience political events are interpreted differently across media outlets, platforms, and political communities. These interpretations shape public attention, trust, and policy debate. This project uses Reddit discourse around Ukraine-related political discussion as a case study for measuring stance and narrative framing in digital trace data.

The project is designed as a research portfolio artifact showing how political discourse can be converted into structured, analyzable labels while preserving caution about class imbalance, measurement validity, platform bias, and interpretive uncertainty.

## Research Questions

1. Can traditional machine learning models classify stance in Ukraine-related Reddit posts?
2. How do SVM and Decision Tree models compare in a small hand-labeled political text dataset?
3. Can LLM prompting classify stance as effectively as supervised ML in this setting?
4. How does class imbalance affect accuracy, recall, precision, and interpretation?
5. What are the limitations of using digital trace data to infer broader public opinion?

## Report

The main report is available as a readable Markdown file:

- `reports/assignment3_stance_classification_report.md`

The original report analyzed approximately 400 hand-coded Reddit posts and compared:

- Support Vector Machine classification,
- Decision Tree classification,
- Gemma-based LLM stance classification,
- confusion matrices and class-specific performance,
- accuracy, precision, recall, sensitivity, specificity, and class imbalance issues.

## Methods

The project framework includes:

- Reddit political discourse data,
- manual stance labels,
- text cleaning and preprocessing,
- unigram and Word2Vec feature extraction,
- SVM with radial kernel,
- Decision Tree classification,
- Gemma LLM stance classification,
- train/test split evaluation,
- confusion matrix comparison,
- accuracy, precision, recall, sensitivity, specificity, and kappa evaluation,
- interpretation of class imbalance and minority-label failure.

## Key Findings

- The SVM model achieved the strongest overall performance with approximately 58% accuracy.
- The Decision Tree model was more interpretable but weaker, with approximately 46.77% accuracy.
- The LLM achieved approximately 56.5% accuracy, but precision and recall were very low.
- All approaches struggled with the dominant `Irrelevant` class and underrepresented `Favor` and `Oppose` labels.
- Accuracy alone was misleading because models could achieve moderate accuracy by overpredicting the majority class.
- The results suggest that traditional ML, especially SVM, was more reliable than zero-/few-shot LLM prompting for this small, imbalanced stance classification task.

## Repository Structure

```text
.
├── README.md
├── reports/
│   ├── README.md
│   └── assignment3_stance_classification_report.md
├── docs/
│   ├── project_overview.md
│   ├── methods_summary.md
│   ├── repository_structure.md
│   └── limitations_and_ethics.md
├── analysis/
│   └── README.md
├── data/
│   └── README.md
├── outputs/
│   └── README.md
└── figures/
    └── README.md
```

## Documentation

- `reports/assignment3_stance_classification_report.md`: Markdown version of the stance classification report.
- `docs/project_overview.md`: Research motivation, questions, and project context.
- `docs/methods_summary.md`: Summary of the text-as-data and public-discourse analysis workflow.
- `docs/repository_structure.md`: Explanation of the repository layout.
- `docs/limitations_and_ethics.md`: Notes on data limitations, political interpretation, and responsible use.

## Skills Demonstrated

- Computational social science
- Political discourse analysis
- Text-as-data methods
- Stance classification
- Sentiment/framing analysis
- SVM and Decision Tree modeling
- LLM evaluation
- Word2Vec feature extraction
- Confusion matrix evaluation
- Class imbalance diagnosis
- Data cleaning and documentation
- Reproducible project organization

## Limitations

This repository should be interpreted as a political discourse analysis project, not as a population-representative measure of public opinion. Reddit data reflect platform selection, posting behavior, subreddit composition, engagement dynamics, and moderation. The labeled dataset is small and imbalanced, which makes minority stance categories difficult to predict. Results should therefore be interpreted as evidence about observed discourse and model behavior rather than direct evidence about the broader public.

## Suggested Rename

For a more professional GitHub title, consider renaming this repository to:

```text
Trump-Zelensky-Stance-Classification
```

or:

```text
Ukraine-Discourse-Stance-Classification
```

## Author

**Sagnik Chakravarty**  
M.S. Survey and Data Science, University of Maryland, College Park  
Portfolio: https://sagnik-chakravarty.github.io/  
GitHub: https://github.com/Sagnik-Chakravarty
