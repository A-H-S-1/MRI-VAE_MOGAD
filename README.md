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

## Data Preprocessing

### Pipeline Overview

Each MRI undergoes the following preprocessing steps:

1. Skull stripping using SynthStrip
2. Orientation normalization (RAS)
3. Bias field correction (N4)
4. Resampling to uniform voxel spacing
5. Intensity normalization
6. Center cropping / padding to fixed shape
7. Conversion to NumPy format

### Output Format

* Shape: `(1, 160, 192, 160)`
* Type: `float32`
* Stored as `.npy`

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
