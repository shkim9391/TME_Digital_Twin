# TME_Digital_Twin
A multimodal Tumor Microenvironment (TME) Digital Twin framework that learns an interpretable latent biology state (z) from spatial transcriptomics and trains image→z models from histology, enabling cross-modal alignment and simulation-ready state representations.

This repository implements a Tumor Microenvironment (TME) Digital Twin framework that integrates spatial transcriptomics and tissue imaging into a shared, interpretable latent state space **z**. We use 10x Visium HD (CRC and breast) as a spatial + histology anchor to (i) define **z_spatial** (cell-type composition + gene programs + QC) at the bin level and (ii) supervise patch-level **WSI → z** models. The resulting state representation is designed to be compatible with bulk RNA-seq and radiology anchors (e.g., TCGA/GDC), supporting downstream simulation and outcome modeling.

Current pipeline (working end-to-end):
1. Load Visium HD 8µm binned outputs and Loupe graph-based clusters  
2. Coarse cluster annotation → cell-type/state labels  
3. Compute a unified 21-dim `z_spatial` schema across datasets  
4. Create patch-level supervision indices (WSI crops ↔ z targets)  
5. Train baseline image→z models (ResNet-based)

This repo is organized to support reproducible dataset builds and modular extensions to additional cohorts and modalities.
