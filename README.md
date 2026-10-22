# RHC-PPI: Relation-Aware Heterogeneous Graphs with Contrastive Learning for Protein-Protein Interaction Prediction

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.12+-ee4c2c.svg)](https://pytorch.org/)

Official repository for the manuscript **"RHC-PPI: Relation-Aware Heterogeneous Graphs with Contrastive Learning for Protein-Protein Interaction Prediction"**.

---

## 📖 Overview

Accurately predicting Protein-Protein Interactions (PPIs) is essential for elucidating disease mechanisms and discovering potential drug targets. **RHC-PPI** is a relation-aware heterogeneous graph neural network framework that synergistically integrates 1D amino acid sequences and AlphaFold2-predicted 3D structures.

### Key Highlights of the Framework:
* **Multi-Relational Heterogeneous Protein Graph**: Constructs residue-level graphs incorporating primary sequence topological edges ($R_{seq}$), local geometric $K$-nearest neighbor edges ($R_{knn}$, $K=10$), and global distance threshold contact edges ($R_{dis}$, $\tau = 10\text{ \AA}$).
* **Cross-Modal Contrastive Learning**: Aligns sequence embeddings (extracted via Depthwise Separable Convolution + SE-Block) and structural embeddings (extracted via GraphSAGE + SAGPool) using an InfoNCE objective while preserving initial residue physicochemical properties.
* **Relation-Level Multi-Head Attention (RLMHA)**: Introduces a learnable relational bias ($B_{rel}$), dynamic gating mechanism, and global context-aware aggregation to adaptively fuse multi-source relational representations.

---

## 🛠️ Environment & Dependencies

The model is implemented in Python using PyTorch and PyTorch Geometric (PyG) / DGL. To set up the required environment:

```bash
conda create -n rhc_ppi python=3.9
conda activate rhc_ppi

# Core dependencies
pip install torch>=1.12.0 torchvision
pip install torch-geometric
pip install numpy scipy scikit-learn pandas tqdm
pip install biopython rdkit
