# Xenium Punkst Workflows

This repository provides an **open-source, reproducible workflow** for analyzing
10x Xenium spatial transcriptomics data using **segmentation-free spatial
factorization (FICTURE / punkst)**, with extensions for **ROI-based transcript
cropping**.

The project combines:
- interactive transcript-level ROI cropping using Napari
- integration with punkst / FICTURE for segmentation-free modeling
- orchestration of single-sample and multi-sample analyses
- documentation designed for reproducibility and academic reuse

This repository is intended to serve as both a **research pipeline** and a
**citable software artifact**.

---

## Overview

Xenium datasets often contain millions of transcripts spanning large tissue
sections. While whole-slide analysis is valuable, many biological questions
focus on specific anatomical regions or require joint analysis across multiple
samples.

This workflow supports:
- region-of-interest (ROI)–focused analysis
- transcript-level filtering without cell segmentation
- consistent analysis across many Xenium samples
- scalable workflows for large spatial datasets

A high-level conceptual description is provided in
[`docs/overview.md`](docs/overview.md).

---
## Key components

### ROI-based transcript cropping (`cropping/`)

- Interactive visualization and ROI definition using Napari
- Polygon-based transcript filtering
- Deterministic cropping given the same polygon
- Outputs compatible with downstream punkst / FICTURE analysis

See [`cropping/README.md`](cropping/README.md) for details.

---

### Segmentation-free spatial factorization (`punkst/`)

- punkst / FICTURE is included as a **Git submodule**
- Upstream code is not copied or modified directly
- Authorship, licensing, and versioning are preserved

Original repository:
https://github.com/yichen-si/punkst

This repository contributes workflows and orchestration around FICTURE, not a
reimplementation of the method itself.

---

### Analysis workflows (`workflows/`)

- Single-sample workflows
- Multi-sample joint analysis workflows
- SVG flowcharts suitable for presentations and posters

See [`workflows/README.md`](workflows/README.md).

---

## Reproducibility

Reproducibility considerations are documented in
[`docs/reproducibility.md`](docs/reproducibility.md), including:

- deterministic vs interactive steps
- ROI provenance
- submodule versioning
- environment considerations

Zenodo is used to archive tagged releases and provide a DOI.

---

## Citation

If you use this workflow, please cite:

Sabir Y, Huang M, Cruz-Martín A.  
*Xenium ROI Cropping + FICTURE Workflows*.  
Zenodo. https://doi.org/10.5281/zenodo.18490063

Please also cite the original FICTURE publication when using downstream
factorization.

---

## License

This project is released under the **MIT License**.

See the `LICENSE` file for details.

---

## Notes

- Large Xenium datasets are not included in this repository.
- This workflow is designed for research and exploratory analysis.
- Contributions and issues are welcome via GitHub.
