# ALTA Shared Task

This repository contains the code, data, and reproducible experiment outputs for an ALTA shared-task system covering sentiment and sarcasm classification.

## Repository layout

| Path | Purpose |
| --- | --- |
| `alta2026_public_data/` | Provided training and validation data. |
| `alta_2026_scoring_program/` | Official evaluation script. |
| `deberta/` | DeBERTa experiments, notebooks, configurations, metrics, and predictions. |
| `Mistral7b/` | Mistral 7B QLoRA experiment outputs and predictions. |
| `llama3.2/` | Llama 3.2 QLoRA experiment outputs and predictions. |
| `sample_test/` | Example prediction file. |

## Workflow

1. Review the schema in `alta2026_public_data/train.csv` and `alta2026_public_data/valid.csv`.
2. Choose a model workflow: DeBERTa notebooks in `deberta/`, Mistral experiments in `Mistral7b/`, or Llama experiments in `llama3.2/`.
3. Train or fine-tune the selected model using the corresponding notebook and configuration.
4. Save predictions in the task submission format (see the CSV files in each run directory).
5. Evaluate a submission with the supplied scorer:

```powershell
python alta_2026_scoring_program/evaluate.py --help
```

6. Record evaluation artifacts in the relevant run directory, including `metrics/`, `answer.csv`, and `run_config.json`.

## Results and reproducibility

Each dated run directory preserves the prediction CSV, run configuration, metrics, tokenizer/configuration files, and trainer logs needed to inspect an experiment. Model-weight checkpoints are deliberately not versioned because they exceed GitHub's file-size limit. Recreate them by running the associated notebook with the recorded configuration.

## Contributing

Keep changes focused and reproducible:

- Put new training code or notebooks in the relevant model directory.
- Add a dated run directory for new outputs; include predictions, configuration, and metrics.
- Do not commit checkpoint weights (`.pt` or `.safetensors`) or paper files.
- Before opening a pull request, run the scorer against your prediction file and describe the model, data split, and result.
