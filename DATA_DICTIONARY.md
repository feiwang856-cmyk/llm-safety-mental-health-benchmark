# Data Dictionary

## Dataset

File:

```text
data/clean.2026.csv
```

Shape:

- **190 rows**
- one row per synthetic prompt
- separate response, original-category, and human-verification columns for each of three models

The analysis reshapes this wide table into **570 model-response records**.

## Columns

| Column | Description |
|---|---|
| `Broad Category` | Original broad scenario grouping used during dataset construction. Some values contain spacing inconsistencies and are not used as the primary analysis key. |
| `Subcategory Code` | Stable scenario code used for grouping and consistency analysis, for example `A1a`, `A2b`, or `A4a`. |
| `Subcategory` | Human-readable name of the prompt subcategory. |
| `Brief Scenario Description` | Short description of the underlying scenario or intended risk pattern. |
| `Suggested Risk Level` | Suggested prompt-risk level: `Low`, `Low-Medium`, `Medium`, `High`, or `Crisis`. |
| `Unnamed: 5` | Empty separator column inherited from the source spreadsheet. Ignored by the analysis. |
| `Prompt (English)` | Synthetic English prompt given to all three models. |
| `Claude Response` | Response collected from Claude Sonnet 4.6. |
| `Claude_Category` | Original A–E classification for the Claude response. |
| `Human verification` | Human-verification label for the Claude classification, when available. |
| `GPT5.4 Response` | Response collected from ChatGPT-5.4. |
| `GPT5.4 New Category` | Original A–E classification for the ChatGPT response. |
| `Human verification.1` | Human-verification label for the ChatGPT classification, when available. |
| `Gemini3 Respnse` | Response collected from Gemini-3. The spelling `Respnse` is retained because it is the original source-column name. |
| `Gemini 3 Category` | Original classification for the Gemini response. The source data also contains `B(Region Error)`, which is normalized to `D` in the analysis. |
| `Human verification.2` | Human-verification label for the Gemini classification, when available. |

## Core subcategories used for consistency analysis

| Code | Description | Number of variants |
|---|---|---:|
| `A1a` | Passive suicidal ideation | 9 |
| `A1b` | Active suicidal ideation | 9 |
| `A1c` | Suicide-method-seeking prompts | 9 |
| `A2a` | Possible paranoid or persecutory belief | 11 |
| `A2b` | Possible referential belief | 11 |
| `A3a` | Depressive rumination | 8 |
| `A4a` | Disorganized or loosely associated speech | 11 |

## Additional subcategories

| Code | Dataset label |
|---|---|
| `A2c` | Persecutory delusion |
| `A2d` | Auditory hallucinations |
| `A2e` | Grandiose delusion |
| `A3b` | Generalized anxiety |
| `A3c` | Social anxiety |
| `A3d` | Panic symptoms |
| `A3e` | Eating disorder – body image distortion |
| `B1a` | Unverified health claims |
| `B1b` | Conspiracy theories |
| `B1c` | Distorted self-perception |
| `B2a` | Seeking validation |
| `B2b` | Emotional dependence |
| `B2c` | Echoing false beliefs |

## Four focal scenario groups

The detailed model-comparison analyses use the following mappings:

| Focal group | Included codes |
|---|---|
| Suicidal ideation | `A1a`, `A1b`, `A1c` |
| Depressive rumination | `A3a` |
| Psychosis-like expressions | all `A2` subcategories |
| Disorganized or loosely associated speech | `A4a` |

## Category normalization

Valid analysis categories are:

```text
A, B, C, D, E
```

Normalization rules:

- `B(Region Error)` → `D`
- `B/D` → missing for reliability analysis
- all other unexpected values → missing and flagged by validation

## Long-format fields created by the notebook

The notebook creates these analysis fields:

| Field | Description |
|---|---|
| `prompt_id` | Sequential prompt identifier from 1 to 190. |
| `broad_category` | Cleaned broad-category text. |
| `subcategory_code` | Stable subcategory code. |
| `subcategory` | Human-readable subcategory. |
| `scenario_description` | Brief scenario description. |
| `risk_level` | Suggested risk level. |
| `prompt` | Prompt text. |
| `model` | Model name. |
| `response` | Model response. |
| `original_category` | Normalized original classification used in main analysis. |
| `human_category` | Normalized human-verification label used only for reliability. |
| `scenario_group` | One of the four focal scenario groups, when applicable. |
