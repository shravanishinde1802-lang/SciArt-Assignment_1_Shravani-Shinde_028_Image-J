# ImageJ Particle Counting Protocol

## Overview

This repository contains a reproducible workflow for particle detection and analysis using ImageJ on fluorescence microscopy images.

---

## Step 0: Image Acquisition

- Source: OpenCell / ImageJ sample datasets

- Raw image stored in: `data/raw/`

- Metadata recorded separately (magnification, pixel size, staining, etc.)

---

## Step 1: Pre-processing

1. Open image: `File → Open`

2. Convert to 8-bit:

   `Image → Type → 8-bit`

3. Background subtraction:

   `Process → Subtract Background`

   - Rolling ball radius: **12 pixels**

   - Light background: **No**

4. Adjust brightness/contrast:

   `Image → Adjust → Brightness/Contrast`

   - Auto + manual fine-tuning

---

## Step 2: Thresholding

1. Apply threshold:

   `Image → Adjust → Threshold`

   - Method: Default

   - Range: **217–255**

   - Mode: Black & White

2. Convert to binary

3. Apply watershed:

   `Process → Binary → Watershed`

---

## Step 3: Measurements

`Analyze → Set Measurements`

- Area

- Perimeter

- Feret’s Diameter

- Shape Descriptors

- Mean Gray Value

---

## Step 4: Particle Analysis

`Analyze → Analyze Particles`

Parameters:

- Size: **50 – Infinity pixels²**

- Circularity: **0.4 – 1.0**

Options:

- Display Results

- Summarize

- Exclude on Edges

- Add to Manager

- Overlay

---

## Step 5: Export Results

- Save CSV:

  `results/stats/particle_count_results.csv`

- Flatten overlay:

  `Image → Overlay → Flatten`

- Save processed image:

  `data/processed/particle_analysis_annotated.tif`

---

## Output

- Quantitative particle measurements (CSV)

- Annotated TIFF image

---

## Notes

- Measurements are in pixel units (no calibration applied)

- Parameters may need adjustment depending on image quality
