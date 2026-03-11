# Characterizing-Latent-Bottlenecks-in-Molecular-Language-Models

# Characterizing Latent Bottlenecks in Molecular Language Models

**ECE 285 – Deep Generative Models**  
**Author:** Balaaditya Mukundan  
**University:** UC San Diego  

---

## Overview

This project studies **efficiency–quality tradeoffs in molecular language models** for SMILES generation.

We investigate how **latent bottlenecks affect generative performance** when modeling molecular structures using deep learning.

Specifically, the project compares:

- Autoregressive language models (GRU-based)
- Variational Autoencoders (VAE) for SMILES generation

We analyze how model design choices influence:

- Validity of generated molecules
- Uniqueness of samples
- Novelty relative to the training dataset
- Chemical property distributions

Experiments are conducted on:

- **QM9 dataset**
- **MOSES molecular benchmark**

The goal is to understand how **latent dimensionality and KL regularization techniques (Free Bits)** impact generative performance.

---

## Project Structure

The project is organized as a sequence of notebooks corresponding to different experimental stages.

### Data Processing

`01_preprocessing_qm9.ipynb`  
Preprocesses the QM9 dataset and converts molecules into **canonical SMILES representations** suitable for training.

---

### Evaluation Metrics

`02_evaluation_metrics.ipynb`  

Implements evaluation metrics used throughout the project:

- Validity
- Uniqueness
- Novelty
- Molecular property statistics (MW, LogP, QED)

These metrics are used to evaluate generated molecules.

---

### Baseline Models

`03_baseline_gru_lm.ipynb`

Trains a **GRU-based autoregressive language model** to generate SMILES sequences token-by-token.  
This serves as the primary baseline.

---

### Variational Autoencoder

`04_smiles_vae_gru.ipynb`

Implements a **SMILES Variational Autoencoder (VAE)** with:

- GRU encoder
- Latent bottleneck
- GRU decoder

Used to study latent representations for molecule generation.

---

### Latent Dimension Experiments

`05_z_sweep_vae.ipynb`

Evaluates the effect of **latent dimensionality (z_dim)** on generation quality.

Experiments analyze how increasing latent capacity impacts:

- KL divergence
- Validity
- Novelty

---

### Free Bits Regularization

`06_freebits.ipynb`

Introduces **Free Bits KL regularization** to mitigate posterior collapse in VAEs.

`07_freebits-extended.ipynb`

Extends the Free Bits experiments with additional hyperparameter analysis.

---

### MOSES Dataset Experiments

`09_moses_gru.ipynb`

Trains the baseline GRU model on the **MOSES molecular benchmark**.

`10_zsweep_vae_moses.ipynb`

Repeats latent dimension sweep experiments on MOSES.

`11_freebits_moses.ipynb`

Applies **Free Bits regularization** to VAE models trained on MOSES.

`12_moses_full.ipynb`

Final large-scale experiment using the best hyperparameters identified during earlier studies.

---

### Molecule Generation

`13_generate_examples_mols.ipynb`

Generates example molecules from the trained models and evaluates their chemical properties.

---

## Evaluation Metrics

Generated molecules are evaluated using:

- **Validity** – percentage of chemically valid SMILES
- **Uniqueness** – fraction of unique generated molecules
- **Novelty** – fraction not present in the training dataset

Additional chemical property statistics:

- Molecular Weight (MW)
- LogP
- QED

---

## Key Research Questions

This project investigates:

1. How does **latent dimensionality** affect molecular generation quality?
2. Does **Free Bits regularization** improve VAE training stability?
3. How do **VAEs compare to autoregressive models** for SMILES generation?
4. Do results generalize from **QM9 to MOSES datasets**?

---

## Requirements

Main dependencies:
- Python 3.9+
- PyTorch
- RDKit
- NumPy
- Pandas
- Matplotlib
- tqdm
- datasets

---

## Running the Project

The notebooks should generally be executed in the following order:
- 01_preprocessing_qm9.ipynb
- 02_evaluation_metrics.ipynb
- 03_baseline_gru_lm.ipynb
- 04_smiles_vae_gru.ipynb
- 05_z_sweep_vae.ipynb
- 06_freebits.ipynb
- 07_freebits-extended.ipynb
- 09_moses_gru.ipynb
- 10_zsweep_vae_moses.ipynb
- 11_freebits_moses.ipynb
- 12_moses_full.ipynb
- 13_generate_examples_mols.ipynb
