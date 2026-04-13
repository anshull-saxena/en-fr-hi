# Reproducibility Guide

This project uses notebooks, so reproducibility depends on environment control and consistent execution order.

## 1. Environment consistency

- Use a dedicated virtual environment per project clone.
- Pin package versions for stable reruns (for example via a frozen requirements snapshot).
- Keep Python version consistent across runs.

## 2. Data consistency

- Use immutable copies of dataset files for each experiment cycle.
- Document exact input filenames and preprocessing assumptions.
- Keep source-target line alignment unchanged between training and evaluation.

## 3. Execution consistency

- Restart kernel and run all cells in order before comparing results.
- Avoid running cells out of order when checkpoint paths are reused.
- Prefer deterministic hardware mode where possible (CPU or fixed CUDA setup).

## 4. Randomness control

When training or sampling behavior is sensitive, set deterministic seeds at notebook start:

```python
import random
import numpy as np
import torch

SEED = 42
random.seed(SEED)
np.random.seed(SEED)
torch.manual_seed(SEED)
if torch.cuda.is_available():
    torch.cuda.manual_seed_all(SEED)
```

## 5. Artifact traceability

- Record which notebook produced each checkpoint.
- Keep checkpoint names and evaluation reports together per run.
- Avoid overwriting prior checkpoints without version suffixes.

## 6. Evaluation reproducibility

- Evaluate against fixed source/reference files.
- Keep sentence limits (if any) explicit and unchanged.
- Use the same tokenization/metric setup across comparison runs.

## 7. Suggested experiment log fields

For each run, track:

- Notebook name
- Date/time
- Dataset files used
- Model checkpoint paths
- Device (`cpu`/`cuda`)
- Hyperparameters
- BLEU/METEOR/TER outputs
