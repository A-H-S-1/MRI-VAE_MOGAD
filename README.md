# TITLE??????

## Project Overview

This project develops a deep learning framework for detecting early, subtle signs of cognitive decline in structural MRI data using counterfactual modeling.

The core idea is to learn a latent representation of brain structure and simulate disease progression through counterfactual transformations. 

---

## Objectives

* Learn a robust latent representation of brain MRI
* Model disease progression as a continuous latent direction
* Generate counterfactual MRIs 
* Detect subtle anomalies associated with early cognitive decline
* Predict clinical cognitive scores 

---

## Dataset

**Source:** OASIS-3 dataset

**MRI Modalities used:**

* T1-weighted MRI (T1w)
* T2-weighted MRI (T2w)

**Additional data:**

* Clinical scores (CDRSUM)
* Demographics (age, sex)

**Cohort description:**

> OASIS-3 is a retrospective dataset of 1378 participants collected over 30 years, including cognitively normal individuals and patients at various stages of cognitive decline.

### Inclusion Criteria

* [TODO]

### Exclusion Criteria

* MRIs with incorrect voxel spacing
* 1.5 Tesla
* [TODO: additional exclusions]

### 🔹 Dataset Splits

* **Training set:** [TODO]
* **Validation set:** [TODO]
* **Test set:** [TODO]

---

## Data Processing

### Pipeline Overview

All MRI volumes were processed using a standardized pipeline to ensure consistent intensity distribution, spatial resolution, and anatomical alignment across MRIs. This is critical for learning meaningful representations in 3D deep learning models.

Each MRI underwent the following steps:

1. Skull stripping using SynthStrip  
2. Orientation normalization to RAS  
3. Bias field correction (N4)  
4. Resampling to uniform voxel spacing  
5. Intensity normalization  
6. Center cropping / padding to fixed shape  
7. Conversion to NumPy format  

---

### 1. Skull Stripping

Non-brain tissue (e.g., skull, scalp, neck) was removed using **SynthStrip** from FreeSurfer to isolate brain tissue and reduce irrelevant variation. Synthstrip takes a NIfTI volume as input and outputs a skull-stripped NIfTI volume. Scans that failed skull stripping were excluded from further processing, and their paths were saved.

---

### 2. Orientation Normalization

All MRIs were converted to **RAS (Right–Anterior–Superior)** orientation using `nibabel.as_closest_canonical` to ensure consistent anatomical alignment across subjects
and prevent axis inconsistencies during model training.

---

### 3. Bias Field Correction

We applied **N4 bias field correction** using SimpleITK to correct low-frequency intensity inhomogeneities. This is important for MRI data due to scanner field artifacts, as it improves intensity consistency across scans.

---

### 4. Resampling to Uniform Voxel Spacing

All volumes were resampled to a fixed voxel spacing: `(160, 192, 160)`. If the volume was larger, it was center-cropped; if it was smaller, it was zero-padded. This ensures consistent tensor dimensions and compatibility with 3d CNNs training. 

---

### 7. Final Formatting

Each processed MRI is stored as:

- Shape: `(1, 160, 192, 160)`  
- Data type: `float32`  
- Format: `.npy`  

The channel dimension is added to support PyTorch 3D convolutional models.

---

### Quality Control

- Failed preprocessing steps (e.g., skull stripping errors) were logged and excluded  
- Visual inspection was performed on sample scans to verify anatomical integrity  
- Central slices (sagittal, coronal, axial) were used for manual sanity checks  

---

## Model Architecture

---

## Counterfactual Framework

---

## Data Splitting Strategy


---

## Training Details

---

## Evaluation


---

## Limitations

* Class imbalance (many cognitively normal subjects and MRIs)
* Limited longitudinal progression data
* MRI acquisition variability

---

## 📜 References

* OASIS-3 dataset!!!!
* SynthStrip (FreeSurfer)!!!!

---
