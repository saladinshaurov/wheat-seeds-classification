# Wheat Kernel Clustering with Unsupervised Learning

This project applies unsupervised learning techniques to group wheat kernels into clusters based on their geometrical properties. The dataset contains measurements from three actual wheat varieties—**Kama**, **Rosa**, and **Canadian**—but the clustering is performed without using these labels during training. The main goal is to explore whether the natural structure of the data can recover the varietal separation.

## Dataset Overview

The dataset contains measurements from kernels belonging to three wheat varieties, with **70 samples from each variety**. High-resolution internal structure imaging was performed using a **soft X-ray technique** and processed using the **GRAINS** software package. This imaging method is cost-effective compared to more advanced techniques like scanning microscopy or laser technology, and it is non-destructive.

The kernels originated from combine-harvested wheat grain grown in experimental fields and studied at the **Institute of Agrophysics, Polish Academy of Sciences in Lublin**.

Each observation represents a single kernel and contains **seven continuous features** characterizing its size, shape, and symmetry.

---

## Feature Summary

| Feature                | Description                                                       | Units / Formula                      |
|------------------------|-------------------------------------------------------------------|----------------------------------------|
| `area`                 | Cross-sectional area of the kernel                               | mm²                                   |
| `perimeter`            | Perimeter length of the kernel                                   | mm                                    |
| `compactness`          | Compactness metric                                               | \( C = \frac{4\pi A}{P^2} \)          |
| `length`               | Length of the kernel                                             | mm                                    |
| `width`                | Width of the kernel                                              | mm                                    |
| `asymmetry_coef`       | Asymmetry coefficient of the kernel shape                        | –                                     |
| `groove_length`        | Length of the kernel groove                                      | mm                                    |

---

## Preprocessing

- **Missing values:** None  
- **Scaling:** All continuous features were standardized using `StandardScaler` to ensure equal contribution to clustering.  
- **Dimensionality Reduction:** Principal Component Analysis (PCA) was applied to reduce the 7D feature space to 2 principal components for visualization and to capture the maximum variance.

---

## Methods

The project uses the following unsupervised learning techniques:

- **K-Means Clustering**
  - Number of clusters set to 3 (matching the known number of wheat varieties)
  - Model trained on the standardized features
  - Cluster assignments compared to true labels for evaluation (only after training)

- **Principal Component Analysis (PCA)**
  - Reduced features from 7 dimensions to 2 components
  - Visualized clustering results in the PCA space

---

## Evaluation

Since clustering is unsupervised, the model’s performance was evaluated using:

- **Cluster purity** (matching clusters to true varieties post hoc)
- **Adjusted Rand Index (ARI)**
- **Visualization of PCA components colored by cluster and true label**

---

## Results

- PCA revealed clear separation between some varieties, with partial overlap.
- K-Means achieved meaningful grouping, with an ARI indicating moderate to strong alignment with true labels.
- Visualization of the PCA scatter plot demonstrated that even without labels, the wheat varieties have distinguishable patterns in their geometrical measurements.

---

## References

Institute of Agrophysics, Polish Academy of Sciences, Lublin.  
Wheat Kernels Dataset. UCI Machine Learning Repository.  
https://doi.org/10.24432/C5T59S
