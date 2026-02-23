# Quantum Kernel Random Forest

Experimental implementation and evaluation of a kernel-based Quantum Random Forest (QRF) inspired by:

> Srikumar et al., *"A kernel-based quantum random forest for improved classification"*, 2022.

This repository contains an academic reproduction and extension of the model, developed as part of a university course in Quantum Machine Learning.


## Overview

This project investigates a hybrid classification approach combining:

- Quantum-inspired kernel construction  
- Nyström kernel approximation  
- Random Forest classification  
- Classical simulation of quantum circuits (Cirq / Qiskit)  

The primary focus is on improving landmark point selection within the Nyström approximation and evaluating classification performance under different configurations.

## Project Report

A detailed technical report including theoretical background, methodology, experimental analysis, and the Cholesky-based Nyström extension can be found here:

📄 [Project Report (PDF)](Quantum_Kernel_Random_Forest_Report.pdf)

### Key Findings

- Cholesky-based landmark selection slightly improved generalization (~1%)
- Computational complexity increased marginally
- Ensemble correlation behavior confirmed theoretical expectations

## My Contributions

The conceptual foundation and core architecture are based on the referenced paper and its original implementation.

My contributions focused on extending and adapting the model for experimental evaluation:

- Implemented an alternative landmark point selection strategy for the Nyström approximation using **Incomplete Cholesky Decomposition with column pivoting** (`nystrom_cholesky.py`)
- Modified the Nyström `fit()` method to support configurable Cholesky-based landmark selection
- Refactored execution logic to ensure compatibility with Apple Silicon by removing incompatible parallelization components
- Designed and implemented a reproducible experimental evaluation workflow in `Submission Notebook.ipynb`
- Conducted comparative experiments and documented results in the accompanying report

## Method Pipeline

1. Dataset preprocessing  
2. Kernel construction via simulated quantum feature maps  
3. Nyström low-rank approximation  
4. Random Forest training on approximated kernel space  
5. Performance evaluation  

The model runs entirely on classical hardware.


## Installation

Tested with:

- Python 3.10  

Main dependencies:

- `cirq==0.11.0`
- `qiskit==0.27.0`
- `scikit-learn==0.24.2`
- `numpy==1.19.5`
- `scipy==1.7.0`
- `tensorflow==2.4.1`

Install dependencies via:

```bash
pip install -r requirements.txt
```

## Usage

An example workflow is provided in:

Submission Notebook.ipynb

The notebook demonstrates:
- Data loading
- Kernel construction
- Nyström approximation
- Model training
- Evaluation metrics

## Disclaimer

This repository is an academic research project and is not intended for production use.
Conceptual foundations belong to the cited authors.