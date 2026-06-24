# llm-safety-mental-health-benchmark
An LLM safety evaluation project featuring benchmark design, response classification, consistency analysis, and human-annotation reliability testing.


# Master's Thesis Analysis

This repository contains the data-analysis code used to reproduce the quantitative results, tables, and figures in the master's thesis:

**Evaluating Safety Boundaries of Large Language Models Across Mental Health Risk Scenarios: A Benchmark Study**

## Important methodological note

The thesis tables and figures are based on the **original A–E classifications** in the dataset.

Human-verification labels are used only for the inter-rater reliability analysis. They do **not** replace the original labels in the main model-comparison analyses.

The value `B(Region Error)` is normalized to Category `D`, because the thesis treats geographically inappropriate crisis resources as contextual misclassification.

One ambiguous human-verification label, `B/D`, is excluded from the reliability analysis.

## Repository structure

```text
data/
  clean.2026.csv

notebooks/
  01_thesis_analysis.ipynb
  archive/
    Untitled4_original.ipynb

results/
  figures/
  tables/
```

## Reproduced thesis outputs

The main notebook reproduces:

- Table 4.1: A–E response distributions for the four focal scenario groups
- Figure 4.1: Safety-boundary patterns
- Table 4.2: Category stability across paraphrased subcategories
- Figure 4.2: Complete consistency rate
- Figure 4.3: Overview heatmap of strengths and failure patterns
- Table 4.3: Systematic comparison metrics
- Table 4.4: Overall reliability
- Table 4.5: Reliability by model

## How to run

Create and activate a virtual environment, then install the dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

On Windows:

```bash
.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

Open `notebooks/01_thesis_analysis.ipynb` and run all cells from top to bottom.

The notebook automatically detects whether it is being run from the repository root or from the `notebooks` directory.

## Reproducibility limitations

The repository reproduces the downstream data processing, classification summaries, consistency analysis, reliability analysis, tables, and figures.

The original model responses were collected manually from user-facing commercial systems. Because these systems are continuously updated, the original responses cannot necessarily be reproduced by querying the models again.

## Privacy and public release

This repository contains synthetic mental-health-risk prompts and full model responses. It is suitable for a private thesis-submission repository.

Before making the repository public for job applications, review the dataset and consider publishing only a small, safe example subset rather than the complete response file.

