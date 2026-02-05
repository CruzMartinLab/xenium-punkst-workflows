# Xenium ROI Cropping (Napari-based)

This folder contains a **Napari-based ROI cropping workflow** for 10x Xenium transcript-level spatial data.  
The cropping step enables **region-of-interest (ROI)–focused analysis** by extracting transcripts within manually defined anatomical or spatial boundaries, which can then be passed downstream to **punkst / FICTURE** for segmentation-free factorization.

This workflow was developed as part of the **Xenium ROI Cropping + FICTURE Workflows** project.

---

## Overview

Xenium datasets often contain millions of transcripts spanning large tissue sections. For many biological analyses (e.g., hippocampus-only analysis, cortical layers, or subregional structures), it is desirable to:

- interactively define an ROI using spatial context  
- extract only transcripts within that ROI  
- preserve transcript-level resolution and gene identities  
- pass the cropped data to downstream models without reformatting  

This notebook implements that process using **Napari for interactive ROI selection** and **polygon-based spatial filtering**.

---

## Workflow Summary

The cropping pipeline consists of the following steps:

1. **Load Xenium transcripts**
   - Reads a `transcripts.tsv` file exported from 10x Xenium
   - Stores coordinates, gene names, and counts with memory-efficient dtypes

2. **Interactive visualization**
   - Randomly samples transcripts for fast rendering
   - Displays spatial coordinates in Napari
   - User manually draws a polygon ROI using Napari’s Shapes tool

3. **ROI import**
   - Polygon coordinates are exported from Napari as CSV
   - The polygon is reloaded and validated

4. **Transcript cropping**
   - Transcripts are filtered using point-in-polygon logic
   - Only transcripts inside the ROI are retained

5. **ROI statistics**
   - Polygon area is computed using the shoelace formula
   - Transcript density and basic gene statistics are reported

6. **Output generation**
   - Cropped transcripts are saved as a TSV file
   - Polygon coordinates are saved for provenance and reuse
   - Optional summary plots are generated

The resulting cropped transcript file is **directly compatible** with downstream punkst / FICTURE workflows.

---

## Input Requirements

- **Transcripts file**  
  A Xenium `transcripts.tsv` file containing spatial coordinates and gene identities.

- **Napari ROI polygon**  
  A CSV file exported from Napari’s Shapes layer containing polygon vertices.

No additional preprocessing is required.

---

## Outputs

The notebook produces:

- **Cropped transcripts (`.tsv`)**  
  Transcript-level data restricted to the ROI, suitable for downstream analysis.

- **ROI polygon (`.tsv`)**  
  Polygon vertex coordinates defining the cropped region.

- **Summary statistics**
  - Number of transcripts
  - Number of unique genes
  - ROI area
  - Transcript density

- **Optional visualizations**
  - Top genes within the ROI
  - Spatial distribution of cropped transcripts

---

## Relationship to punkst / FICTURE

This cropping step is designed to be used **upstream of punkst / FICTURE**.

Typical usage patterns include:
- single-sample ROI analysis  
- multi-sample ROI analysis  
- anatomical subregion comparison  
- reduced-memory workflows for very large datasets  

The cropped transcript output can be passed directly into the FICTURE pipeline without modification.

---

## Reproducibility Notes

- ROI definition is **manual but explicit**: polygon coordinates are saved and versionable.
- The cropping operation is deterministic given the same polygon and transcript input.
- The notebook is intended for **interactive use**, not batch execution.

---

## Citation

If you use this ROI cropping workflow or notebook, please cite:

Sabir Y, Huang M, Cruz-Martín A.  
*Xenium ROI Cropping + FICTURE Workflows*.  
Zenodo. https://doi.org/10.5281/zenodo.18490063

Please also cite the original FICTURE publication when using downstream factorization.

---

## License

This workflow is released under the **MIT License**.  
See the repository root for full license text.
