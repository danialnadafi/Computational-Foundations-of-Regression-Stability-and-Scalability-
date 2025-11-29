<div align="center">

# Computational Foundations of Linear Regression  
**Numerical Stability • Scalability • From-Scratch Implementation**

**Main Notebook:** `CDM_3_Final.ipynb`  

**Dataset:** [UCI Auto MPG](https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/auto-mpg.data)  
**Author:** Danial Nadafi  
**University:** Amirkabir University of Technology (Tehran Polytechnic)  
**Supervisor:** Dr. Mehdi Ghatee  
**Teaching Assistant:** Dr. Behnam Yousefimehr  

</div>

---

## Prerequisites
- **Python 3.8+**  
- **pip** (Python package manager)  
- **Jupyter Notebook** or **JupyterLab**  

---

## Project Overview
This repository contains a full academic-level implementation and empirical comparison of the four fundamental methods for solving linear regression — all coded **from scratch** using only NumPy:

- Normal Equations (closed-form solution)  
- Singular Value Decomposition (SVD)  
- Batch Gradient Descent (BGD)  
- Stochastic Gradient Descent (SGD)  

The project is structured around two core investigations:  
1. **Numerical Stability** – synthetic experiments with extreme multicollinearity  
2. **Scalability & Practical Performance** – real-world analysis on the UCI Auto MPG dataset with polynomial extension  

---

## Installation & Quick Start
```bash
git clone https://github.com/your-username/linear-regression-stability-scalability.git
cd linear-regression-stability-scalability
pip install numpy pandas scikit-learn matplotlib jupyter
jupyter notebook CDM__3_Final.ipynb
```
The notebook automatically downloads the dataset and is fully reproducible (`np.random.seed(42)`).

---

## Research Objectives
- Prove why **Normal Equations fail dramatically** under multicollinearity while **SVD stays perfectly stable**  
- Compare **convergence speed**, noise level, and **wall-clock performance** of BGD vs SGD  
- Show how **simple polynomial features + SGD** can effectively model non-linear patterns  
- Deliver clean, educational, well-commented **from-scratch code** ideal for learning and teaching  

---

## Implemented Algorithms (Pure NumPy)

| Algorithm | Type | Description |
|----------|------|-------------|
| **Normal Equations** | Analytical | Solves θ = (AᵀA)⁻¹Aᵀy. Fast for small data but unstable if **A is singular** or features are **collinear**. |
| **SVD (Pseudoinverse)** | Numerical | Solves θ = A⁺y using Singular Value Decomposition. Handles **collinearity robustly** by managing near-zero singular values. |
| **BGD (Batch Gradient Descent)** | Iterative | Updates weights using the gradient of the **entire dataset** at each step. Smooth convergence but **computationally expensive** for large data. |
| **SGD (Stochastic Gradient Descent)** | Iterative | Updates weights using **one random training example** per step. Much faster but produces a **noisy convergence path**. |
| **Polynomial Regression** | Feature Eng. | Adds polynomial terms (e.g., x²) to model **curvature and non-linear relationships** in data. |

---

## Experimental Pipeline

### Phase 1 – Stability under Severe Collinearity
- Tiny synthetic dataset (4 samples)  
- Inject near-perfect duplicate column (noise = 1e-12)  
- Watch Normal Equations explode while SVD handles it gracefully  

### Phase 2 – Real-World Performance (Auto MPG)
- 392 cleaned samples after removing missing values  
- Feature standardization (essential for fast GD convergence)  
- Train linear models with BGD and SGD  
- Upgrade to degree-2 polynomial features → retrain with SGD  

---

## Key Results & Visualizations

| Visualization             | What It Shows                                                                 |
|---------------------------|--------------------------------------------------------------------------------|
| Loss Curves (BGD vs SGD)  | BGD = perfectly smooth; SGD = highly oscillatory but reaches low loss dramatically faster |
| Polynomial Regression Fit | Red quadratic curve capturing the non-linear MPG vs Horsepower trend |

**Core Conclusion:**  
SVD is the only reliable analytical method.  
SGD (and its variants) dominate real-world applications due to superior scalability.

---

## Ideal For
- Machine Learning / Numerical Linear Algebra courses  
- Understanding why scikit-learn uses SVD by default  
- Learning why pure Batch Gradient Descent is virtually extinct in 2025  

**Star the repo if you find it helpful for studying, teaching, or just love clean ML fundamentals!**

Happy learning and coding!  
**Danial Nadafi**
