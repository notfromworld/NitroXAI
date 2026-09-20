# NitroXAI

**NitroXAI** is an interpretable framework for residue-level **S-nitrosylation (SNO) site prediction**. It provides two frozen ensemble predictors for identifying candidate S-nitrosylated cysteine residues from complete protein sequences:

- **NitroXAI** — a hybrid model integrating handcrafted biochemical and positional descriptors with contextual **ESM-2 protein language model representations** through attention-based fusion.
- **SNO-CLIM** — a lightweight **CNN-BiLSTM** baseline using handcrafted biochemical and positional features.

Both predictors support residue-level SNO probability estimation, all-cysteine scanning, FASTA and optional UniProt workflows, batch prediction, and **Integrated Gradients-based interpretation**.

---

## Installation

To set up the environment and install NitroXAI and SNO-CLIM from the source distribution, follow the steps below.

### 1. Create and activate the Conda environment

Create the Conda environment using the configuration file provided in the `reproducibility/` directory:

```bash
conda env create -f reproducibility/environment-nitroxai-cv.yml
conda activate nitroxai-cv
```

### 2. Install the packages

Install the locally built wheel distributions:

```bash
pip install dist/nitroxai-0.1.1-py3-none-any.whl
pip install dist/snoclim-0.1.1-py3-none-any.whl
```

> **Note:** These releases are not currently distributed through PyPI. If you downloaded the repository as a ZIP file from GitHub, extract it first and run the installation commands from the **root directory of the extracted project**, where the `dist/` directory is located.

---

## Release and Citation

**NitroXAI v0.1.1** is permanently archived on Zenodo.

**Zenodo DOI:** `10.5281/zenodo.22238589`

The archived release contains:

- Frozen inference software
- Trained model checkpoints
- Fold-specific preprocessing resources
- Ensemble rules
- Decision thresholds
- Interpretability workflows

The inference pipeline is fully frozen. It **does not retrain models, refit preprocessing scalers, optimize decision thresholds, or fine-tune ESM-2** during prediction.

If you use NitroXAI in academic work, please cite the **Zenodo software record** until the associated manuscript becomes available.

---

## Key Capabilities

- Residue-level S-nitrosylation site prediction
- Complete-protein **ESM-2 inference** with NitroXAI
- Lightweight handcrafted-feature inference with SNO-CLIM
- Raw protein sequence input
- FASTA input
- Optional UniProt sequence retrieval
- Batch prediction workflows
- Individual-cysteine prediction
- All-cysteine scanning
- Integrated Gradients-based residue-level attribution
- CPU inference
- Optional CUDA-accelerated inference

---

## Important Input Rule

> **For NitroXAI, always provide the complete protein sequence.**

NitroXAI first encodes the **full protein sequence** using frozen ESM-2 representations and subsequently extracts **cysteine-centred 61-residue contextual windows** for prediction.

**Do not provide a pre-extracted 61-residue fragment as the input protein sequence.**

Providing the complete sequence ensures that ESM-2 generates each residue representation within its appropriate full-protein sequence context.

---

## Model Overview

### NitroXAI

NitroXAI combines:

**Protein sequence → ESM-2 contextual representations → cysteine-centred context extraction → attention-based representation → handcrafted biochemical/positional features → feature fusion → SNO probability**

The model is designed to combine learned protein-language representations with biologically motivated residue-level descriptors while retaining residue-level interpretability.

### SNO-CLIM

SNO-CLIM provides a computationally lighter baseline:

**Cysteine-centred sequence context → handcrafted biochemical/positional features → CNN-BiLSTM → SNO probability**

It does not require ESM-2 inference and can therefore be useful when computational resources are limited.

---

## Interpretability

NitroXAI includes **Integrated Gradients (IG)** workflows for examining residue-level contributions to individual predictions.

These attribution scores can be used to investigate which residues within the local cysteine environment contribute most strongly to the predicted S-nitrosylation probability.

Interpretability outputs should be treated as **model explanations rather than direct evidence of biochemical causality**.

---

## Scope and Intended Use

NitroXAI is intended for:

- Computational prioritization of candidate S-nitrosylation sites
- Hypothesis generation
- Large-scale protein screening
- Comparative computational analysis
- Investigation of sequence determinants associated with S-nitrosylation

Predictions represent **candidate S-nitrosylation sites** and require appropriate experimental validation before biological conclusions are drawn.

This release provides frozen inference assets and interpretability workflows. The **complete training pipeline, processed datasets, and associated materials will be released separately upon publication**.

---

## License

Copyright © 2026 **Soumyadeep Ray and Ganesh Bagler**

NitroXAI is distributed under the **MIT License**. See `LICENSE` for details.

Third-party resources and dependencies, including **UniProt services and ESM-2 model weights**, remain subject to their respective licenses and terms of use.
