# Xenium ROI Cropping + FICTURE Workflows

This repository provides an **open-source, reproducible workflow** for analyzing 10x Xenium spatial transcriptomics data using **segmentation-free spatial factorization (FICTURE / punkst)**, with support for **ROI-based transcript cropping** and **multi-sample joint inference**.

---

## What this workflow does

- **Interactive ROI cropping**  
  Manually define anatomical regions using Napari and extract transcript-level data from Xenium datasets.

- **Segmentation-free spatial factorization**  
  Apply punkst / FICTURE to cropped or full datasets without cell segmentation.

- **Multi-sample analysis**  
  Jointly analyze multiple Xenium samples (e.g., 22 brain sections) using custom Makefile orchestration.

---

## Typical use cases

- Subregion-specific analysis (e.g., hippocampus, cortical layers)
- Memory-efficient analysis of large Xenium datasets
- Cross-sample comparison using shared latent factors
- ROI-focused exploratory spatial analysis

---

## Repository contents

- `cropping/` – Napari-based ROI cropping notebook  
- `punkst/` – punkst / FICTURE (included as a submodule)  
- `workflows/` – single-sample, multi-sample, and cropped workflows  
- `docs/` – usage guides and reproducibility notes  

---

## Citation

If you use this workflow, please cite:

Sabir Y, Huang M, Cruz-Martín A.  
*Xenium ROI Cropping + FICTURE Workflows*.  
Zenodo. https://doi.org/10.5281/zenodo.18490063

Please also cite the original FICTURE publication.

---

## Get started

👉 **Repository:**  
https://github.com/CruzMartinLab/xenium-punkst-workflows

---

*QR code scanned from poster presentation.*
