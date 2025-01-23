# Dataset Anonymization and Utility Preservation

## Overview
This repository contains implementations of methods for dataset anonymization and utility preservation. The primary focus is on anonymizing network data features while maintaining their utility for machine learning tasks. Two approaches have been implemented:

1. **Feature Anonymization with Differential Privacy and Clustering**
2. **Utility-Preserving Dataset Condensation with Gradient Matching**

The repository is structured to include separate files for each approach, with detailed implementation and usage guidelines.

---

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Feature Anonymization with Differential Privacy and Clustering](#feature-anonymization-with-differential-privacy-and-clustering)
- [Utility-Preserving Dataset Condensation with Gradient Matching](#utility-preserving-dataset-condensation-with-gradient-matching)
- [Results](#results)

---

## Features
1. Anonymization of timestamps, duration, and packet size using clustering and differential privacy.
2. Anonymization of IP addresses with prefix-preserving hashing and clustering.
3. Implementation of Dataset Condensation with Gradient Matching to synthesize utility-preserving datasets.
4. Testing and evaluation of anonymized datasets using KNN classifiers and other models.

---

## Feature Anonymization with Differential Privacy and Clustering
### Methodology
1. **Timestamps, Duration, and Packet Size Anonymization:**
   - Clustering algorithms were employed to anonymize numerical features.
   - Differential Privacy (DP) was implemented by adding Laplace noise to the clusters.

2. **IP Address Anonymization:**
   - The network part of the IP address was anonymized using the SHA algorithm (prefix-preserving).
   - The host part was anonymized by clustering host addresses and replacing each with the mean value of its cluster.

### Results
- Accuracy of the dataset before anonymization: **99.52%** (KNN classifier).
- Accuracy of the dataset after anonymization: **99.51%** (KNN classifier).
- Correlation matrices for anonymized features showed minimal deviation from original values.

---

## Utility-Preserving Dataset Condensation with Gradient Matching
### Methodology
1. **Initialization:**
   - Synthetic data points (e.g., 1000) were initialized randomly.
   - A set of simple neural networks, including convolutional models, was defined.

2. **Outer and Inner Steps:**
   - At each "outer step," a random model and real data points (256 per class) were selected.
   - The synthetic data points were trained for 10 "inner steps," updating them based on gradient loss calculated with cosine similarity between gradients of real and synthetic data points.

3. **Generalization:**
   - Models were reset to zero gradient at each step to prevent overfitting.
   - The synthesized dataset was designed for general use, not limited to any specific use case (e.g., IDS).

### Results
- Synthesized datasets maintained utility comparable to the original dataset.
- Testing on separate models confirmed similar accuracy and performance metrics.

---

## Results
1. Accuracy before anonymization: **99.55%**.
2. Accuracy after anonymization with DP and clustering: **97.57%**.
3. Accuracy after dataset condensation: Comparable results with generalized utility.

---

## File Structure
```
|-- DP_implementation.ipynb   # Implementation of Differential Privacy and Clustering
|-- Dataset_condensation_gradient_matching.ipynb      # Implementation of Gradient Matching Condensation
|-- README.md                       
