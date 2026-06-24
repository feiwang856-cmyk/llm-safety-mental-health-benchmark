# Response Collection Protocol

## Objective

The project records and compares how three user-facing large language models respond to synthetic prompts involving explicit, indirect, and ambiguous mental-health-risk scenarios.

## Evaluated systems

- ChatGPT-5.4
- Claude Sonnet 4.6
- Gemini-3

The analysis concerns the visible outputs of these systems rather than their internal architectures or training data.

## Collection period

Responses were collected between:

```text
March 2026 and May 2026
```

Because commercial LLM systems are continuously updated, the dataset should be interpreted as a snapshot of model behavior during this collection period.

## Prompt set

The benchmark contains **190 synthetic prompts**.

Prompt design covers:

- suicidal ideation
- depressive rumination
- psychosis-like expressions
- disorganized or loosely associated speech
- anxiety
- health misinformation
- accommodating or sycophantic questions

Selected subcategories contain multiple paraphrased variants that preserve the same underlying scenario while changing wording, directness, emotional intensity, or narrative form.

## Standardized procedure

For each prompt:

1. The same prompt was presented separately to all three models.
2. Each prompt was entered in an independent or reset dialogue environment.
3. Previous prompt context was not intentionally carried into the next interaction.
4. The visible model response was copied into the structured dataset.
5. An original A–E category was assigned according to the annotation framework.
6. Human-verification labels were recorded for a subset of model-response pairs.

This design reduces contextual contamination and supports direct comparison across models.

## Geographical context

For crisis-resource evaluation, Sweden was used as the assumed user location where relevant.

Responses providing inappropriate regional resources, such as emergency or crisis contacts from a different country despite the Swedish context, were treated as contextual misclassification and normalized to Category D.

## Stored metadata

Each prompt row includes:

- broad category
- subcategory code
- subcategory name
- brief scenario description
- suggested risk level
- prompt text
- three model responses
- original response classifications
- available human-verification labels

## Human verification

Human-verification labels were used to assess whether the original A–E classifications could be reproduced.

After excluding one ambiguous `B/D` label:

- valid comparison pairs: **273**
- exact agreement: **253/273**
- agreement rate: **92.7%**
- Cohen's kappa: **0.861**

Human-verification labels do not replace the original classifications in the main comparative analysis.

## Ethical and privacy considerations

- All benchmark prompts are synthetic.
- The dataset does not contain real patient records.
- No clinical participants were recruited.
- No personally identifying information is included.
- The repository contains sensitive content involving suicide, self-harm, unusual beliefs, and crisis communication.
- The full dataset should remain private unless reviewed and redacted for public release.

## Reproducibility limitations

The stored dataset is the authoritative record of the collected model outputs.

Re-querying the models may produce different responses because:

- commercial systems are updated;
- safety policies and model versions may change;
- stochastic generation may vary;
- user-interface behavior may change;
- regional or account-level settings may differ.

The repository therefore reproduces the analysis of the stored responses, not the original model-generation process.
