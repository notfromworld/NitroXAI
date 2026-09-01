# NitroXAI

NitroXAI is an interpretable framework for residue-level
S-nitrosylation (SNO) site prediction. It provides two frozen ensemble
predictors for identifying candidate S-nitrosylated cysteine residues
from complete protein sequences:

- **NitroXAI**: a hybrid model that integrates handcrafted biochemical
  and positional descriptors with contextual ESM-2 protein
  language-model representations through attention-based fusion.
- **SNO-CLIM**: a lightweight CNN-BiLSTM baseline using handcrafted
  biochemical and positional features.

Both predictors provide residue-level SNO probabilities, all-cysteine
scanning, FASTA and optional UniProt workflows, batch prediction, and
Integrated Gradients-based interpretation.

## Release and citation

NitroXAI v0.1.1 is archived on Zenodo:

**Zenodo:** [10.5281/zenodo.22238589](https://doi.org/10.5281/zenodo.22238589)

The release contains frozen inference software, model checkpoints,
fold-specific preprocessing resources, ensemble rules, decision
thresholds, and interpretability workflows. Inference does not retrain
models, refit scalers, optimize thresholds, or fine-tune ESM-2.

If you use NitroXAI in academic work, please cite the Zenodo software
record until the associated manuscript becomes available.

## Key capabilities

- Residue-level S-nitrosylation site prediction
- Complete-protein ESM-2 inference for NitroXAI
- Lightweight handcrafted-feature inference with SNO-CLIM
- Raw sequence, FASTA, optional UniProt, and batch workflows
- Individual-cysteine prediction and all-cysteine scanning
- Integrated Gradients-based residue-level attribution
- CPU inference and optional CUDA inference

## Important input rule

For NitroXAI, provide the **complete protein sequence**. The model first
encodes the full sequence using frozen ESM-2 and then extracts
cysteine-centred 61-residue contextual windows. Do not provide a
pre-extracted 61-residue fragment as the input sequence.

## Scope

NitroXAI is intended for computational prioritization and hypothesis
generation. Predictions represent candidate S-nitrosylation sites and
require experimental validation.

This release contains frozen inference assets and interpretability
workflows. The complete training pipeline, processed datasets, and
associated materials will be released separately upon publication.

## License

Copyright © 2026 Soumyadeep Ray and Ganesh Bagler. Distributed under
the [MIT License](LICENSE). Third-party resources, including UniProt
retrieval and ESM-2 weights, remain subject to their respective terms.
