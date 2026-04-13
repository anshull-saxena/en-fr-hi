# File Reference

This document explains the role of each tracked file in the repository.

## Root files

| File | Purpose | Inputs | Outputs |
| --- | --- | --- | --- |
| `README.md` | Project-level documentation and quick start | N/A | N/A |
| `CONTRIBUTING.md` | Contribution workflow and quality expectations | N/A | N/A |
| `LICENSE` | Legal license terms (MIT) | N/A | N/A |
| `NLP2_en_fr.ipynb` | EN<->FR training/inference workflow | `en_to_fr.txt`, `fr_to_en.txt` | `en_to_fr_model_checkpoint`, `fr_to_en_model_ckpt` |
| `en_to_hi.ipynb` | EN<->HI training/inference workflow | `en_to_hi.txt`, `hi_to_en.txt` | `en_to_hi_model`, `en_to_hi_tokenizer` |
| `hi to en (1).ipynb` | Dual-direction EN<->HI checkpoint workflow | `en_to_hi.txt`, `hi_to_en.txt` | `hi_model_checkpoint/*` model/tokenizer pairs |
| `test.ipynb` | Translation metric evaluation notebook | Source/target text files, saved checkpoint | Metric scores + `predictions.fr` |

## Documentation files

| File | Purpose |
| --- | --- |
| `docs/FILE_REFERENCE.md` | Detailed explanation of repository files |
| `docs/NOTEBOOK_EXECUTION_GUIDE.md` | Operational guide for running notebooks correctly |
| `docs/REPRODUCIBILITY.md` | Reproducibility practices and experiment controls |

## Notes

- Notebook names are preserved as currently present in the repository.
- Some checkpoint naming differs across notebooks (`..._checkpoint`, `..._ckpt`, `..._model`).
- If new notebooks or scripts are added, update this file and the root `README.md`.
