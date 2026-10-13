# Results summary

These are the metrics recorded in the uploaded notebook and should be re-verified by a clean rerun.

| Metric | Random Forest | ESM-2 embeddings + classifier |
|---|---:|---:|
| Accuracy | 0.9856 | 0.9745 |
| Precision | 0.0000 | 0.1818 |
| Recall | 0.0000 | 0.2222 |
| F1-score | 0.0000 | 0.2000 |
| ROC-AUC | 0.4453 | 0.5609 |

Test set: 627 residues (9 active-site positive, 618 negative).

Interpretation: Random Forest's higher accuracy reflects the severe class imbalance and its failure to predict any positive residues at the selected threshold. The ESM-2-based classifier identified 2 positive residues but also made 9 false-positive predictions. Do not claim that either model is validated or that accuracy alone establishes superiority.
