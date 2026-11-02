# Model Training and Evaluation

Training and comparison of four classification models (Logistic Regression, Decision Tree, Random Forest, SVM) on the Breast Cancer Wisconsin (Diagnostic) dataset.

## Contents

| File | Description |
|---|---|
| `model_training_and_evaluation.ipynb` | Main notebook: model selection, data splitting, training, evaluation, comparison and summary |
| `artifacts/training.log` | Training log with all model parameters |
| `artifacts/model_params.json` | Parameters, fit time, train accuracy and CV F1 per model |
| `artifacts/model_comparison.csv` | Comparison table of metrics |
| `artifacts/*.png` | Confusion matrices and metric comparison chart |
| `requirements.txt` | Python dependencies |

## How to run

```bash
pip install -r requirements.txt
jupyter notebook model_training_and_evaluation.ipynb
```

Or upload the notebook to Google Colab and run all cells (no extra installs needed).

To use your own preprocessed dataset, set `USE_OWN_DATA = True`, `DATA_PATH` and `TARGET_COL` in the data loading cell.

## Results (test set, 80/20 stratified split, `random_state=42`)

| Model | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| **SVM (RBF)** | **0.974** | **1.000** | **0.929** | **0.963** |
| Random Forest | 0.974 | 1.000 | 0.929 | 0.963 |
| Logistic Regression | 0.965 | 0.975 | 0.929 | 0.951 |
| Decision Tree | 0.904 | 0.919 | 0.810 | 0.861 |

**Best model: SVM (RBF).** It matches Random Forest on the test set, but has a higher and more stable 5-fold cross-validation F1 (0.961 ± 0.008 vs 0.943 ± 0.032) and trains much faster. See section 6 of the notebook for the full analysis and trade-offs.
