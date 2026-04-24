# Edge Visual Anomaly Detection for Cloud-to-Edge Deployment

Production-ready repository layout for training and evaluating a convolutional autoencoder on the ShanghaiTech dataset, then packaging outputs for edge deployment workflows.

## Repository Structure

```
.
|-- assets/                        # Final report images and comparison plots
|-- configs/                       # Runtime/training configuration files
|-- data/                          # Local data workspace (not committed)
|-- notebooks/
|   `-- edge_anomaly_detection.ipynb
|-- scripts/                       # Automation scripts (training/export/deploy)
|-- src/                           # Python package code (model, data, inference)
|-- SHANGHAI_TRAIN/                # Dataset (kept local, gitignored)
|-- SHANGHAI_TEST/                 # Dataset (kept local, gitignored)
`-- artifacts/                     # Model checkpoints and generated outputs (gitignored)
```

## What Is Included

- End-to-end notebook pipeline for data loading, training, thresholding, and evaluation.
- Saved plots for model diagnostics in `assets/`.
- Local artifact directory for checkpoints and run outputs in `artifacts/`.

## Quick Start

1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Keep dataset folders at repository root:
   - `SHANGHAI_TRAIN/`
   - `SHANGHAI_TEST/`
4. Open and run `notebooks/edge_anomaly_detection.ipynb`.

## Production/GitHub Recommendations

- Commit source and docs; do not commit raw data or large model checkpoints.
- Use release assets or cloud/object storage for trained weights.
- Pin environment dependencies and keep training/inference logic under `src/` over time.
- Add CI checks (lint + smoke inference) before publishing production tags.

## Suggested Next Improvements

- Extract notebook classes/functions into `src/` modules:
  - `src/models/autoencoder.py`
  - `src/data/dataset.py`
  - `src/train.py`
  - `src/evaluate.py`
- Add reproducible config files in `configs/`.
- Add an inference CLI for edge-side runtime benchmarking.
