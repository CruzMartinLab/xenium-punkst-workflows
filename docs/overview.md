# Overview: Xenium ROI Cropping + FICTURE Workflows

This repository provides an open-source, reproducible workflow for analyzing
10x Xenium spatial transcriptomics data using **segmentation-free spatial
factorization (FICTURE / punkst)**, with extensions for **ROI-based transcript
cropping** and **multi-sample joint analysis**.

The workflow is designed to support exploratory and comparative spatial analyses
in large Xenium datasets while preserving transcript-level resolution.

---

## Motivation

Xenium spatial transcriptomics datasets often contain millions of transcripts
across large tissue sections. While whole-slide analysis is valuable, many
biological questions focus on:

- specific anatomical regions
- substructures within a tissue
- comparisons across multiple sections or samples

Standard pipelines frequently require either full-slide processing or cell
segmentation, which may be unnecessary or undesirable for certain analyses.

This project addresses these challenges by combining:
1. **Interactive ROI cropping** at the transcript level
2. **Segmentation-free spatial factorization** using FICTURE
3. **Multi-sample orchestration** for joint analysis across many Xenium samples

---

## High-level workflow

The overall workflow consists of four conceptual stages:

1. **Input data**
   - Transcript-level Xenium outputs (`transcripts.tsv`)
   - Spatial coordinates and gene identities

2. **ROI-based transcript cropping**
   - Interactive visualization using Napari
   - Manual polygon definition of anatomical regions
   - Extraction of transcripts within the ROI
   - Preservation of transcript-level information

3. **Segmentation-free factorization**
   - Cropped or full datasets passed to punkst / FICTURE
   - No cell segmentation required
   - Latent spatial factors inferred directly from transcript distributions

4. **Single-sample or multi-sample analysis**
   - Independent analysis of individual samples
   - Joint inference across multiple samples using shared latent factors
   - Support for large-scale analyses (e.g., dozens of brain sections)

---

## Project components

This repository is organized into the following components:

- **`cropping/`**  
  Napari-based ROI cropping notebook for Xenium transcript data.

- **`punkst/`**  
  Included as a Git submodule to preserve upstream authorship and versioning.

- **`workflows/`**  
  Documentation and orchestration logic for:
  - single-sample analysis
  - multi-sample analysis
  - cropped multi-sample workflows

- **`docs/`**  
  High-level documentation, reproducibility notes, and poster materials.

---

## Upstream software and attribution

This workflow builds on **punkst / FICTURE**, which is developed and maintained
by its original authors.

punkst is included as a **Git submodule**:
- upstream code is not copied or modified directly
- authorship and licensing are preserved
- updates can be tracked cleanly

Users of this repository should cite:
- this workflow (for ROI cropping and orchestration)
- the original FICTURE publication (for the core method)

---

## Scope of contributions

This repository contributes:

- a Napari-based ROI cropping workflow for Xenium data
- integration of cropped transcript outputs with FICTURE
- multi-sample execution and orchestration logic
- documentation for reproducible use in spatial transcriptomics studies

The core FICTURE method itself is not reimplemented here.

---

## Intended audience

This repository is intended for:
- spatial transcriptomics researchers
- computational biologists working with Xenium data
- users interested in segmentation-free spatial modeling
- labs performing multi-sample or ROI-focused analyses

No prior experience with FICTURE is assumed.
