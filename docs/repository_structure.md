# Repository Structure

This repository preserves the original course/project context while adding professional documentation for portfolio use.

```text
.
├── README.md
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

## Directory Purpose

### `docs/`

Contains project-facing documentation: overview, methods, repository structure, limitations, and ethics.

### `analysis/`

Reserved for scripts, notebooks, or Quarto files used to clean, analyze, and visualize political discourse data.

### `data/`

Reserved for raw or processed datasets. Public repositories should not include restricted, private, or non-shareable data.

### `outputs/`

Reserved for generated tables, figures, and reports.

### `figures/`

Reserved for visualizations such as time-series plots, frame distributions, sentiment distributions, or conceptual diagrams.

## Suggested Future Cleanup

A production-ready version could use the following structure:

```text
analysis/
  01_data_cleaning.qmd
  02_sentiment_stance_analysis.qmd
  03_framing_analysis.qmd
  04_visualization.qmd
data/
  raw/
  processed/
outputs/
  tables/
  figures/
docs/
```
