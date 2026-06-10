# CRBN End-to-End Pipeline

This repository documents my end-to-end computational drug discovery pipeline for **Cereblon (CRBN) bioactivity modelling, virtual screening, and hit interpretation**. Through this project, I built a complete workflow starting from raw ChEMBL bioactivity data and progressing through data cleaning, feature engineering, machine learning, virtual screening, chemical annotation, critical evaluation, and graph neural network modelling.

My goal in this project was not only to train predictive models, but also to understand how to build a **scientifically meaningful, reproducible, and interpretable cheminformatics workflow**.

---

## Project Overview

In this project, I:

- verified and configured my Python cheminformatics environment
- curated and cleaned **CRBN-specific bioactivity data** from ChEMBL
- standardised activity values and generated **pActivity** and **binary binding labels**
- engineered molecular representations using **Morgan fingerprints** and **RDKit descriptors**
- trained **Random Forest classification and regression models**
- generated and screened two molecular libraries:
  - a focused **IMiD-like analogue library**
  - a **SELFIES-based generative library**
- ranked and interpreted predicted hits
- flagged chemically unrealistic molecules
- critically evaluated the limitations of the pipeline
- extended the project with a **Graph Neural Network (GNN)** baseline using PyTorch Geometric

---

## What I Learned

This project taught me how to think and work more like a **computational drug discovery researcher**. I learned how to move from raw molecular bioactivity data to modelling-ready datasets, how to represent molecules numerically, how to train and evaluate predictive models, and how to interpret screening results with chemical caution rather than trusting scores blindly.

More specifically, I learned how to:

- curate and preprocess **real medicinal chemistry datasets**
- work with **SMILES**, **RDKit**, and molecular fingerprints
- standardise assay data and derive **pActivity** values
- build **classification** and **regression** models for molecular activity prediction
- evaluate models using appropriate scientific metrics
- generate new molecules using **SELFIES**
- design a simple **virtual screening workflow**
- distinguish between **high-scoring molecules** and **chemically meaningful hits**
- identify limitations in dataset quality, model generalisation, and chemical realism
- represent molecules as graphs and train a **GNN** for activity prediction
- compare classical ML baselines with graph-based deep learning approaches

---

## Skills I Acquired

### Cheminformatics and molecular modelling

Through this pipeline, I gained practical experience in:

- **RDKit-based molecular parsing**
- **Morgan / ECFP fingerprint generation**
- **physicochemical descriptor engineering**
- **SMILES validation and molecular preprocessing**
- **chemical feature analysis**
- **hit annotation and triage**

### Data science and machine learning

I also developed skills in:

- **data cleaning and curation**
- **feature matrix construction**
- **binary classification**
- **regression modelling**
- **Random Forest modelling**
- **model evaluation and visualisation**
- **feature importance analysis**
- **model saving and reuse**

### Deep learning and graph modelling

In the later stages of the project, I learned how to:

- convert molecules into **graph representations**
- define **atom-level features**
- build a minimal **Graph Convolutional Network**
- use **PyTorch** and **PyTorch Geometric**
- compare **descriptor-based** and **graph-based** molecular models
- create a simple **ensemble prediction workflow**

### Research and scientific thinking

This project also helped me strengthen:

- **reproducible research workflow design**
- **critical model assessment**
- **scientific interpretation of ML outputs**
- **chemical reasoning for hit selection**
- **awareness of limitations in generative molecular design**
- **ability to propose realistic future improvements**

---

## Pipeline Flowchart

The following diagram summarises the workflow I built in this repository:

```mermaid
flowchart TD
    A[Milestone 1: Environment setup and library verification] --> B[Milestone 2: CRBN bioactivity data acquisition from ChEMBL]
    B --> C[Data cleaning and standardisation]
    C --> C1[Filter target: CHEMBL3763008]
    C1 --> C2[Keep IC50 and Ki only]
    C2 --> C3[Convert units to nM]
    C3 --> C4[Compute pActivity]
    C4 --> C5[Create binding_label]
    C5 --> D[Cleaned CRBN dataset]

    D --> E[Milestone 3: Feature engineering]
    E --> E1[Parse SMILES with RDKit]
    E1 --> E2[Generate Morgan fingerprints]
    E2 --> E3[Compute RDKit descriptors]
    E3 --> E4[Assemble modelling-ready feature matrix]

    E4 --> F[Milestone 4: Predictive modelling]
    F --> F1[Random Forest classification]
    F --> F2[Random Forest regression]
    F1 --> F3[Classification metrics: ROC-AUC, PR-AUC, Accuracy, Confusion Matrix]
    F2 --> F4[Regression metrics: R2, MSE, MAE]
    F3 --> F5[Feature importance analysis]
    F4 --> F5
    F5 --> G[Save trained models]

    G --> H[Milestone 5: Library generation]
    H --> H1[IMiD-like analogue library]
    H --> H2[SELFIES-based generative library]

    H1 --> I[Milestone 6: Virtual screening]
    H2 --> I
    I --> I1[Generate features for new molecules]
    I1 --> I2[Predict binding probability]
    I2 --> I3[Predict pActivity]
    I3 --> I4[Rank hits across both libraries]

    I4 --> J[Milestone 7: Hit interpretation]
    J --> J1[Annotate chemical features]
    J1 --> J2[Flag unrealistic or charged molecules]
    J2 --> J3[Identify chemically reasonable hits]

    J3 --> K[Milestone 8: Critical evaluation]
    K --> K1[Assess model limitations]
    K1 --> K2[Assess chemical validity limitations]
    K2 --> K3[Propose future improvements]

    K3 --> L[Milestone 9: Graph neural network extension]
    L --> L1[Convert molecules to graphs]
    L1 --> L2[Train GNN for pIC50 prediction]
    L2 --> L3[Compare GNN vs Random Forest]
    L3 --> L4[Build simple ensemble]

    L4 --> M[Final outcome: AI-driven CRBN bioactivity prediction and virtual screening workflow]
