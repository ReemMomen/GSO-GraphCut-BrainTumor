# Glider Snake Optimizer for Graph Cut-Based Brain Tumor Segmentation

**A Lightweight and Interpretable Approach**

## Overview

This repository contains the Python implementation of the research paper **"Glider Snake Optimizer for Graph Cut-Based Brain Tumor Segmentation: A Lightweight and Interpretable Approach."**

The proposed framework integrates the **Glider Snake Optimizer (GSO)** with a classical **Graph Cut segmentation algorithm** to automatically optimize segmentation parameters for brain tumor detection in MRI images.

The approach emphasizes computational efficiency, interpretability, and data efficiency, providing an alternative to resource-intensive deep learning methods.

## Key Features

- Automated optimization of six Graph Cut parameters using GSO.
- Automatic foreground and background seed generation.
- Brain mask extraction and morphological post-processing.
- Patient-level data splitting to prevent data leakage.
- Evaluation on LGG-MRI and BraTS 2020 datasets.
- Cross-dataset generalization without additional parameter tuning.
- Baseline comparison, ablation studies, and statistical significance testing.
- Lightweight segmentation using classical energy minimization.

## Datasets

The framework is evaluated using two publicly available brain MRI datasets:

**1. LGG-MRI Dataset**

Used for parameter optimization and primary performance evaluation.

- 3,929 MRI slices from 110 patients.
- Patient-level training and validation split.
- 100 tumor-positive training slices selected for GSO optimization.
- Images resized to 128 × 128 pixels.

**2. BraTS 2020 Dataset**

Used to evaluate cross-dataset generalization.

- Multi-modal MRI data, including T1, T1CE, T2, and FLAIR.
- T2-weighted images used as the primary segmentation input.
- Binary tumor masks generated from the provided ground-truth labels.
- LGG-optimized parameters evaluated without additional tuning.

## Methodology

The proposed pipeline consists of:

1. MRI image preprocessing and normalization.
2. Automatic brain mask extraction.
3. Foreground and background seed generation.
4. GSO-based optimization of Graph Cut parameters.
5. Graph Cut segmentation through energy minimization.
6. Morphological post-processing and component selection.
7. Quantitative evaluation against ground-truth masks.

GSO optimizes six parameters:

`λ, γ, β, σFG, σBG, α`

The optimization objective is to minimize:

`Fitness = 1 − Mean Dice Score`

## Reported Results

| Evaluation | Mean Dice |
|---|---:|
| LGG-MRI — Baseline Graph Cut | 0.166 |
| LGG-MRI — Proposed GSO + Graph Cut | 0.665 |
| BraTS 2020 — Cross-dataset evaluation | 0.470 |

Additional evaluations include IoU, precision, recall, specificity, ablation studies, parameter sensitivity analysis, and the Wilcoxon signed-rank statistical test.

These values are reported in the accompanying research paper.

## Repository Structure

The main implementation includes:

- `run_gso_graphcut_paper_only_clean.ipynb` — Main experimental pipeline and evaluation code.
- `GSO.py` — Glider Snake Optimizer implementation.

The datasets are distributed separately and are not included in this repository.

## Requirements

Python 3 and the scientific computing and medical image-processing libraries imported by the notebook are required.

Install the necessary dependencies before running the experiments, and configure the dataset paths according to your local environment.

## Usage

1. Download or clone the repository.
2. Prepare the LGG-MRI and BraTS 2020 datasets.
3. Keep `GSO.py` accessible to the main notebook.
4. Configure dataset paths and experimental settings.
5. Execute the notebook to reproduce the experimental workflow.

**Note:** Reproduction may require access to the original datasets, configuration settings, and a compatible Python environment.

## Research Paper

**Title:** Glider Snake Optimizer for Graph Cut-Based Brain Tumor Segmentation: A Lightweight and Interpretable Approach

**Authors:** Reem M. Mostafa, M. S. Salim, H. Z. Zidan, Abdelmonem M. Ibrahim, and Ahmed Ayman.

**Affiliation:** Faculty of Science, Al-Azhar University, Assiut, Egypt.

## Citation

If you use this implementation in your research, please cite the accompanying paper.

The formal publication citation and DOI will be added when available.

## License

No license is specified at this stage. All rights are reserved unless a license is explicitly added to this repository.
