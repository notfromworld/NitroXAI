# NitroXAI

NitroXAI is an interpretable framework for residue-level S-nitrosylation (SNO) site prediction that integrates protein language models, lightweight sequence-based baselines, explainable artificial intelligence (XAI), and structure-aware visualization. The framework is designed to identify candidate S-nitrosylated cysteine residues directly from protein sequence while providing mechanistic insights into the sequence determinants associated with S-nitrosylation.

The NitroXAI ecosystem consists of two complementary models:

* **NitroXAI** – a protein language model (PLM)-based framework that leverages contextual protein representations for SNO site prediction.
* **SNOCLIM** – a lightweight CNN–BiLSTM ensemble based on handcrafted sequence-derived features, developed as an interpretable and computationally efficient companion model.

Despite using approximately three orders of magnitude fewer parameters than PLM-based approaches, SNOCLIM achieves competitive predictive performance, highlighting the value of biologically informed feature engineering for residue-level post-translational modification prediction.

Key capabilities include:

* Residue-level S-nitrosylation prediction
* Protein language model inference
* Lightweight CNN–BiLSTM baseline prediction
* Integrated Gradients–based interpretability
* Residue-level attribution analysis
* UniProt accession support
* FASTA sequence support
* PDB and mmCIF structure support
* Structure-aware visualization through PyMOL
* Batch prediction workflows

NitroXAI is intended as a computational prioritization framework for hypothesis generation and biological discovery. Predictions should be interpreted as candidate sites requiring experimental validation.
