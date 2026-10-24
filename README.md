# E(3)-Equivariant Graph Neural Networks for Molecular Property Prediction

Predict molecular dipole moment (μ) from the QM9 dataset using E(3)-equivariant graph neural networks that respect 3D rotation/translation symmetry.

## Overview

This project implements and compares three graph neural network architectures for molecular property prediction:

1. **Simple GCN** - Standard graph convolutional network (9K params)
2. **MPNN** - Message Passing Neural Network with edge features (29K params)
3. **E(3)-Equivariant GNN** - Distance-based equivariant network (150K params)

## Dataset

**QM9**: 130,831 small organic molecules with 3D coordinates and quantum chemical properties.
- Atoms: C, N, O, F, H
- Target: Dipole moment (μ) in Debye
- Source: [MoleculeNet](https://moleculenet.ai/)

## Results

| Model | Test MAE (Debye) | R² | Parameters | vs GCN |
|-------|:---:|:---:|:---:|:---:|
| GCN | 0.771 | 0.467 | 9,153 | baseline |
| MPNN | 0.717 | 0.548 | 28,993 | +7.0% |
| E(3)-Equivariant | 0.515 | 0.759 | 149,825 | +33.2% |

The E(3)-equivariant model achieves **33.2% lower MAE** compared to the non-equivariant GCN baseline and demonstrates perfect rotation invariance (prediction std < 0.001 Debye under arbitrary rotations).

## Key Features

- 3D molecular structure visualization
- Training curves and model comparison plots
- Rotation equivariance demonstration
- Checkpoint save/load from Google Drive
- Designed to run on Google Colab with GPU

## How to Run

1. Open `molecular_property_prediction.ipynb` in Google Colab
2. Run cells in order (setup, data loading, training, evaluation)
3. Figures and checkpoints are saved to Google Drive

## Requirements

- PyTorch Geometric
- RDKit
- e3nn
- NumPy, Matplotlib, Seaborn

## References

1. Satorras et al. "E(n) Equivariant Graph Neural Networks" ICML 2021
2. Bronstein et al. "Geometric Deep Learning" 2021
3. Ramakrishnan et al. "Quantum chemistry structures and properties of 134k molecules" Scientific Data 2014
4. Wu et al. "MoleculeNet: A Benchmark for Molecular Machine Learning" Chemical Science 2018

## License

MIT
