# Protein Active-Site Prediction: Random Forest vs ESM-2

An exploratory comparison of a classical machine-learning baseline and a pretrained protein language-model embedding approach for residue-level protein active-site prediction.

## Project objective

Compare:
1. **Random Forest** using residue physicochemical properties and 3D coordinates.
2. **ESM-2 embeddings + neural-network classifier** using residue representations from a pretrained protein language model.

The goal is to explore how these approaches behave on an imbalanced residue-level classification task—not to claim a validated production-ready predictor.

## Methods

### Random Forest baseline
The notebook uses residue-level features including hydrophobicity, molecular weight, and X/Y/Z structural coordinates. The Random Forest classifier uses class weighting to account for label imbalance.

### ESM-2-based approach
The notebook extracts residue embeddings using the pretrained `esm2_t6_8M_UR50D` model and feeds them to a neural-network classifier.

### Evaluation
The notebook evaluates classification using:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix

## Results recorded in the notebook

| Metric | Random Forest | ESM-2 embeddings + classifier |
|---|---:|---:|
| Accuracy | 98.56% | 97.45% |
| Precision | 0.0000 | 0.1818 |
| Recall | 0.0000 | 0.2222 |
| F1-score | 0.0000 | 0.2000 |
| ROC-AUC | 0.4453 | 0.5609 |

The recorded test set contains 627 residues, including 9 positive active-site residues and 618 negative residues. Random Forest predicted no positive residues at the evaluated threshold; the ESM-2-based classifier identified 2 of the 9 positive residues, with 9 false-positive predictions.

**Interpretation:** accuracy alone is misleading for this heavily imbalanced task. These results are exploratory and do not establish that either approach is a reliable active-site predictor.

## Important limitations and next steps

- Verify UniProt-to-PDB residue numbering and active-site label mapping.
- Confirm all preprocessing and split decisions to rule out data leakage.
- Prefer protein-level held-out evaluation so residues from the same protein do not leak across train and test sets.
- Tune thresholds only on validation data, not on the final test set.
- Report class-wise metrics and compare against simple baselines.
- Re-run the notebook from a clean runtime before treating the saved metrics as final.

## Repository structure

```text
protein-active-site-prediction/
├── README.md
├── requirements.txt
├── RESULTS_SUMMARY.md
└── notebooks/
    └── random_forest_vs_esm2_active_site_prediction.ipynb
```

## How to run

1. Open the notebook in Google Colab or Jupyter.
2. Run cells in order, following any dataset/model download instructions in the notebook.
3. Confirm required packages and runtime/GPU availability for ESM-2.
4. Re-check the label mapping and evaluation split before interpreting metrics.

## Tools

Python, Biopython, pandas, scikit-learn, PyTorch, ESM-2, PDB structures, UniProt resources.

## Status

Exploratory project; results and residue mapping require further validation before scientific conclusions are drawn.
