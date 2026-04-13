# Contributing Guide

Thank you for contributing to this project.

## Scope

This repository is a notebook-first machine translation project. Contributions are welcome for:

- Documentation quality and clarity
- Notebook correctness and maintainability
- Reproducibility improvements
- Evaluation quality and metric reporting

## Local setup

1. Fork and clone the repository.
2. Create a virtual environment.
3. Install dependencies:

```bash
pip install torch transformers sentencepiece sacremoses nltk sacrebleu jupyter
```

## Development standards

### Notebook standards

- Keep notebook cells in logical run order.
- Avoid hardcoded machine-specific absolute paths.
- Use clear variable names for datasets, checkpoints, and outputs.
- Add or update explanatory markdown when behavior changes.
- Do not commit large model binaries or datasets.

### Documentation standards

- Keep README and docs aligned with actual file names and outputs.
- Document new artifacts (checkpoints, generated files, expected inputs).
- Prefer concise, explicit instructions over implicit assumptions.

## Pull request expectations

Each pull request should include:

1. Clear summary of what changed and why.
2. Updated docs when behavior or usage changes.
3. Any assumptions made (dataset format, expected path layout, hardware constraints).

## Commit message guidance

- Use descriptive commit titles.
- Group related documentation changes in the same commit.
- Keep commits focused and reviewable.

## Reporting issues

When reporting a bug, include:

- Notebook name
- Exact cell or step where failure occurred
- Error trace
- Environment details (Python version, OS, CPU/GPU)

## Code of conduct

Be respectful and constructive in all project interactions.
