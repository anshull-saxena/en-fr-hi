# Multilingual Translation Experiments (EN-FR-HI)

Notebook-first machine translation experiments using Hugging Face MarianMT models for English, French, and Hindi.

## Table of contents

- [Project overview](#project-overview)
- [Repository layout](#repository-layout)
- [Supported workflows](#supported-workflows)
- [Quick start](#quick-start)
- [Data requirements](#data-requirements)
- [Execution flow](#execution-flow)
- [Artifacts and outputs](#artifacts-and-outputs)
- [Evaluation approach](#evaluation-approach)
- [Documentation index](#documentation-index)
- [Known limitations](#known-limitations)
- [Contributing](#contributing)
- [License](#license)

## Project overview

This repository contains four Jupyter notebooks that cover:

1. Translation training/inference for **English <-> French**
2. Translation training/inference for **English <-> Hindi**
3. Dual-direction Hindi/English checkpoint handling
4. Offline evaluation with **BLEU**, **METEOR**, and **TER**

The repo is intentionally lightweight and research-oriented (no packaged Python module yet).

## Repository layout

| Path | Type | Description |
| --- | --- | --- |
| `NLP2_en_fr.ipynb` | Notebook | EN<->FR training and translation checks |
| `en_to_hi.ipynb` | Notebook | EN<->HI training and translation checks |
| `hi to en (1).ipynb` | Notebook | EN<->HI and HI<->EN save/load workflow |
| `test.ipynb` | Notebook | Batch inference and metric evaluation |
| `README.md` | Doc | Project entrypoint documentation |
| `CONTRIBUTING.md` | Doc | Contribution process and quality expectations |
| `docs/FILE_REFERENCE.md` | Doc | Detailed, file-by-file documentation |
| `docs/NOTEBOOK_EXECUTION_GUIDE.md` | Doc | Notebook run order, prerequisites, and expected outputs |
| `docs/REPRODUCIBILITY.md` | Doc | Reproducibility and experiment tracking guidance |

## Supported workflows

| Workflow | Base model(s) | Notebook(s) |
| --- | --- | --- |
| English -> French | `Helsinki-NLP/opus-mt-en-fr` | `NLP2_en_fr.ipynb` |
| French -> English | `Helsinki-NLP/opus-mt-fr-en` | `NLP2_en_fr.ipynb` |
| English -> Hindi | `Helsinki-NLP/opus-mt-en-hi` | `en_to_hi.ipynb`, `hi to en (1).ipynb` |
| Hindi -> English | `Helsinki-NLP/opus-mt-hi-en` | `en_to_hi.ipynb`, `hi to en (1).ipynb` |
| Metric evaluation | Saved checkpoint + reference corpus | `test.ipynb` |

## Quick start

### 1. Clone

```bash
git clone https://github.com/anshull-saxena/en-fr-hi.git
cd en-fr-hi
```

### 2. Create and activate virtual environment

```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install torch transformers sentencepiece sacremoses nltk sacrebleu jupyter
```

### 4. Open notebooks

```bash
jupyter notebook
```

Run notebook cells top-to-bottom for each workflow.

## Data requirements

The notebooks reference local corpus files. Keep them in repository root (or update paths in notebook cells):

| Purpose | File(s) referenced |
| --- | --- |
| EN-FR training data | `en_to_fr.txt`, `fr_to_en.txt` |
| EN-HI training data | `en_to_hi.txt`, `hi_to_en.txt` |
| Evaluation in `test.ipynb` | `europarl-v7.fr-en.en`, target/reference file(s), and output file `predictions.fr` |

## Execution flow

1. Pick language-pair notebook (`NLP2_en_fr.ipynb`, `en_to_hi.ipynb`, or `hi to en (1).ipynb`).
2. Confirm dataset file paths.
3. Run training and checkpoint-save cells.
4. Run translation sanity-check cells.
5. Run `test.ipynb` for BLEU/METEOR/TER evaluation.

For step-by-step notebook-level guidance, see `docs/NOTEBOOK_EXECUTION_GUIDE.md`.

## Artifacts and outputs

The notebooks save checkpoints under these names:

- `en_to_fr_model_checkpoint`
- `fr_to_en_model_ckpt`
- `en_to_hi_model`
- `en_to_hi_tokenizer`
- `hi_model_checkpoint/en_hi_model`
- `hi_model_checkpoint/en_hi_tokenizer`
- `hi_model_checkpoint/hi_en_model`
- `hi_model_checkpoint/hi_en_tokenizer`

## Evaluation approach

`test.ipynb` computes:

- **BLEU** (`nltk.translate.bleu_score`)
- **METEOR** (`nltk.translate.meteor_score`)
- **TER** (`sacrebleu`)

It uses helper functions like `load_sentences`, `translate_batch_batched`, and `evaluate_model`.

## Documentation index

- `docs/FILE_REFERENCE.md`
- `docs/NOTEBOOK_EXECUTION_GUIDE.md`
- `docs/REPRODUCIBILITY.md`
- `CONTRIBUTING.md`

## Known limitations

- The codebase is notebook-first; there is no packaged training pipeline yet.
- Checkpoint naming conventions are currently inconsistent across notebooks.
- Some notebooks include inline `!pip install` commands; prefer pre-installing dependencies in a clean environment.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
