# Single-Cell RNA-seq data analysis with PCA and Negative-Binomial VAE

A comparison of **PCA** and a **Negative-Binomial Variational Autoencoder (NB-VAE)** for learning low-dimensional representations of single-cell RNA-seq data.

The project uses the **Segerstolpe human pancreatic islet dataset** and evaluates how well each representation captures cell-type structure and generalizes to previously unseen donors.

## Approach

* Quality filtering using the dataset's provided annotations
* Selection of 2,000 highly variable genes
* **PCA** on normalized/log-transformed expression
* **NB-VAE** trained on raw count data using PyTorch
* 10-dimensional latent representations
* Donor-level holdout evaluation
* KNN classification and K-means clustering
* UMAP visualization

## Evaluation

Representations are compared using:

| Task                          | Metrics            |
| ----------------------------- | ------------------ |
| Held-out donor classification | Accuracy, Macro F1 |
| Cell-type clustering          | ARI, NMI           |
| Visualization                 | UMAP               |

The donor-level split ensures that test cells come from individuals that were not used during training.

## Tech Stack

**Python · PyTorch · Scanpy · AnnData · scikit-learn · NumPy · Pandas**

## Project Structure

```text
.
├── notebooks/
│   ├── 01_data_extraction.ipynb
│   └── 02_analysis.ipynb
├── raw_data/
├── requirements.txt
└── README.md
```

## Getting Started

```bash
git clone [https://github.com/mustaphazeezat/analysing-scrna-deep-learning](https://github.com/mustaphazeezat/analysing-scrna-deep-learning)
cd analysing-scrna-deep-learning

python -m venv .venv
source .venv/bin/activate

pip install -r requirements.txt
jupyter notebook
```

Open `notebooks/analysis.ipynb` to run the analysis.

## Dataset

Segerstolpe et al. — human pancreatic islet single-cell RNA-seq dataset.

The raw dataset is not included in this repository.

## Motivation

This project explores whether a count-aware deep-learning model can learn useful biological representations from scRNA-seq data compared with a classical PCA baseline.

It extends my broader interest in **statistical modelling, machine learning, and computational biology**.
