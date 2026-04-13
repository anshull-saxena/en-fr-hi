# Notebook Execution Guide

This guide documents how to run each notebook safely and consistently.

## Prerequisites

- Python 3.8+
- Installed packages:
  - `torch`
  - `transformers`
  - `sentencepiece`
  - `sacremoses`
  - `nltk`
  - `sacrebleu`
  - `jupyter`

## Required local files

Place required corpus files in repository root unless you update paths in notebook cells:

- `en_to_fr.txt`
- `fr_to_en.txt`
- `en_to_hi.txt`
- `hi_to_en.txt`
- Evaluation files referenced by `test.ipynb`

## Recommended run order

1. `NLP2_en_fr.ipynb` (for EN<->FR experiments)
2. `en_to_hi.ipynb` or `hi to en (1).ipynb` (for EN<->HI / HI<->EN experiments)
3. `test.ipynb` (evaluation)

## Notebook-specific behavior

### `NLP2_en_fr.ipynb`

- Loads EN-FR corpora
- Builds dataset and dataloader
- Uses `Helsinki-NLP/opus-mt-en-fr` and `Helsinki-NLP/opus-mt-fr-en`
- Saves checkpoints:
  - `en_to_fr_model_checkpoint`
  - `fr_to_en_model_ckpt`

### `en_to_hi.ipynb`

- Loads EN-HI and HI-EN corpora
- Uses `Helsinki-NLP/opus-mt-en-hi` and `Helsinki-NLP/opus-mt-hi-en`
- Saves outputs:
  - `en_to_hi_model`
  - `en_to_hi_tokenizer`

### `hi to en (1).ipynb`

- Runs dual model/tokenizer setup for EN-HI and HI-EN
- Saves under `hi_model_checkpoint/`:
  - `en_hi_model`
  - `en_hi_tokenizer`
  - `hi_en_model`
  - `hi_en_tokenizer`

### `test.ipynb`

- Loads checkpoint and tokenizer
- Performs batch translation
- Computes BLEU, METEOR, and TER metrics
- Writes prediction output file(s)

## Operational tips

- Execute notebook cells top-to-bottom after kernel restart.
- Ensure checkpoint save paths exist and are writable.
- Keep paths relative to repository root for portability.
- Verify that source and target files are aligned line-by-line before evaluation.
