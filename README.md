# 🧬 Protein Classification using ProtBERT

This project implements a structural bioinformatics pipeline to classify human proteins into **Enzymes (1)** and **Non-Enzymes (0)** based on their amino acid sequences using the **ProtBERT** transformer model.

## 📁 Project Structure

```text
Labs/
├── data/
│   ├── raw/                 # Original UniProt dataset (gzipped TSV)
│   └── processed/           # ProtBERT embeddings and labels (.npy arrays)
├── Notebooks/
│   ├── 01_data_prep_and_embedding.ipynb     # Preprocessing & feature extraction
│   └── 02_model_training_and_evaluation.ipynb # Neural Network & RF training
├── results/                 # Exported metrics, reports, and confusion matrices
├── .venv/                   # Python Virtual Environment
└── requirements.txt         # Project dependencies
```

## 🚀 Workflow

### 1. Data Preparation & Embedding Extraction
Run `Notebooks/01_data_prep_and_embedding.ipynb` to:
- Load raw UniProt data.
- Sample a balanced dataset of 2000 proteins (1000 enzymes / 1000 non-enzymes).
- Extract 1024-dimensional contextual embeddings using **ProtBERT**.
- Save the processed features to `data/processed/`.

### 2. Model Training & Evaluation
Run `Notebooks/02_model_training_and_evaluation.ipynb` to:
- Load the pre-computed embeddings.
- Train and compare two models: **Random Forest** and **Multi-Layer Perceptron (Neural Network)**.
- **5-Fold Cross-Validation:** Statistical validation to ensure model stability (Mean F1: ~0.87 for MLP).
- **ROC and Precision-Recall Curves:** Visual diagnostics for classification thresholds.
- **Explainable AI (SHAP):** Identification of top influential features in the embedding space.
- **Dimensionality Reduction (UMAP):** 2D visual representation of the 1024D Protein space.
- **Detailed Classification Reports:** Precision, Recall, and F1-score for each class.
- Export results to the `results/` folder.

### 3. Explainable AI (XAI) & Visualization
Run `Notebooks/03_explainability_and_visualization.ipynb` to:
- **UMAP Prediction:** Visualize the high-dimensional protein embedding space in 2D.
- **SHAP Analysis:** Identify which embedding dimensions are most influential for enzyme classification.
- **Global Interpretability:** Understand the model's decision-making process.

## 🛠️ Installation

Ensure you have Python 3.10+ installed.

1.  **Activate Virtual Environment**:
    ```powershell
    .\.venv\Scripts\activate
    ```
2.  **Install Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

## 📊 Results Summary

- **Primary Model**: Multi-Layer Perceptron (Base Neural Network).
- **Performance**: Achieves high precision (~93%) and strong overall F1-score (~87%).
- **Key Visuals**: See `results/confusion_matrix_base.png` for a detailed performance breakdown.
