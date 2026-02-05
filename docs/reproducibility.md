# Reproducibility Notes

This document describes reproducibility considerations for the
**Xenium ROI Cropping + FICTURE Workflows** repository.

The goal is to clearly distinguish deterministic computation from
interactive or user-defined steps, and to document how results can be
reproduced or audited.

---

## Versioning and releases

This repository is versioned using Git and archived via Zenodo.

- Each GitHub release corresponds to a Zenodo snapshot
- The DOI represents the exact state of the repository at release time
- Users should cite the **concept DOI** for general use

For strict reproducibility, users should:
- use a tagged release
- record the commit hash of this repository
- record the commit hash of the punkst submodule

---

## Deterministic components

The following steps are deterministic given the same inputs:

- transcript loading and filtering
- point-in-polygon transcript selection
- polygon area calculation
- summary statistics and gene counts
- downstream execution of punkst / FICTURE

Given identical input files and polygon coordinates, the cropped
transcript outputs will be identical.

---

## Interactive components

The following steps are **interactive by design**:

- ROI definition using Napari’s Shapes tool
- Manual selection of anatomical boundaries

To support reproducibility:
- polygon coordinates are exported and saved as files
- polygons can be reused, versioned, and shared
- downstream analyses can be re-run using saved polygons

---

## ROI provenance

Each ROI is defined by an explicit polygon file:

- polygon vertices are stored as coordinate pairs
- polygon files can be committed to version control
- ROI definitions can be reused across analyses

This makes ROI selection transparent and auditable.

---

## Submodule reproducibility

punkst / FICTURE is included as a Git submodule.

This ensures:
- exact upstream versions are preserved
- changes to upstream code are explicit
- analyses can be reproduced with the same FICTURE implementation

Users cloning the repository should use:

```bash
git clone --recurse-submodules
