# Wheat Kernel Classification with Supervised Learning

This project focuses on the classification of wheat kernels into three distinct varieties—**Kama**, **Rosa**, and **Canadian**—using geometrical measurements obtained through a soft X-ray imaging technique. The objective is to predict the wheat variety based on quantitative kernel shape parameters derived from non-destructive imaging.

## Dataset Overview

The dataset contains measurements from kernels belonging to three wheat varieties, with **70 samples from each variety**. High-resolution internal structure imaging was performed using a **soft X-ray technique** and processed using the **GRAINS** software package. This imaging approach is cost-effective compared to more sophisticated techniques like scanning microscopy or laser technology and preserves the integrity of the grain.

The kernels originated from combine-harvested wheat grain grown in experimental fields and studied at the **Institute of Agrophysics, Polish Academy of Sciences in Lublin**.

Each observation represents a single kernel and contains **seven continuous features** characterizing its size, shape, and symmetry. These parameters enable effective classification and can also be used for cluster analysis.

**Target Variable:** `variety`
- **Kama**
- **Rosa**
- **Canadian**

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
- **Scaling:** All continuous features scaled using `StandardScaler` for use in distance-based models and neural networks.  
- **Train/test/validation split:** The dataset was divided into training, testing, and validation subsets to ensure unbiased evaluation.

---

## Models Trained

The following supervised learning algorithms were implemented and evaluated:

- **k-Nearest Neighbors (KNN)**
- **Naive Bayes (GaussianNB)**
- **Logistic Regression**
- **Support Vector Classifier (SVC)**
- **Neural Network** (via TensorFlow/Keras)  
  - Tuned hyperparameters: hidden layer size, dropout rate, learning rate, batch size

Models were evaluated using:
- Accuracy score
- Classification reports
- Validation loss curves

A hyperparameter tuning loop was used for the neural network to find the architecture that minimized validation loss.

---

## Results

Performance comparisons across traditional ML models and the tuned neural network revealed the strengths and trade-offs of each approach. The best-performing model achieved high classification accuracy across all three wheat varieties, demonstrating the effectiveness of geometric kernel parameters for varietal classification.

---

## References

Institute of Agrophysics, Polish Academy of Sciences, Lublin.  
Wheat Kernels Dataset. UCI Machine Learning Repository.  
https://doi.org/10.24432/C5T59S
