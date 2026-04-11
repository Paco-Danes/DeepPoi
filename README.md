# Hierarchical Multi-Task Graph Recurrent Attention Network for next Point of Interest recommendation

DeepPoi is a deep learning framework for **point-of-interest (PoI) detection in high-contrast imaging data**, combining statistical preprocessing with convolutional neural networks to improve detection sensitivity and robustness.

## Objective

The goal of this project is to accurately detect faint signals (PoIs) embedded in highly noisy and structured backgrounds.  
This is a challenging task due to:

- Extremely **low signal-to-noise ratio (SNR)**
- Strong **spatial and temporal correlations** in noise
- Presence of structured artifacts that resemble true signals

The project aims to enhance detection performance by integrating **model-based preprocessing** with **data-driven learning**.

---

## Methodology

The pipeline is composed of two main stages:

### 1. Statistical Preprocessing

- Input data is first transformed using a **local statistical model** that captures spatial correlations.
- This step:
  - Reduces non-stationarity
  - Normalizes structured noise
  - Improves contrast between signal and background

The output is a residual representation where PoI signatures are more separable.

---

### 2. Deep Learning Detection

A supervised deep learning approach is applied on the preprocessed data:

#### Detection Network
- A **Convolutional Neural Network (CNN)** is trained to:
  - Identify spatial patterns corresponding to PoIs
  - Produce a **detection map** over the input

#### Training Strategy
- Synthetic signal injection is used to generate labeled data
- The model learns to distinguish:
  - True signals
  - Residual noise artifacts

---

### 3. (Optional) Characterization Stage

- A secondary model can be used to estimate properties of detected signals (e.g., intensity/photometry)
- This stage refines the output beyond binary detection

---

## Results

The proposed approach shows:

- **Improved detection sensitivity** compared to classical baselines
- Better robustness to structured noise and artifacts
- More accurate localization of faint signals

Key observations:

- The preprocessing step significantly enhances separability
- CNN-based detection captures residual patterns not modeled statistically
- The combined approach outperforms purely model-based or purely deep learning methods

---

## Key Insights

- Hybrid pipelines (statistical + deep learning) are highly effective for structured noise problems
- Learning directly on raw data is suboptimal without proper normalization
- Synthetic data augmentation is essential for supervised training in low-signal regimes
