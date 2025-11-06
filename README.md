# Parametric-Curve-Fitting-FLAM-AI-and-Research
A hands-on implementation of parametric curve fitting using Python — optimized for L1 accuracy.
## 📘 Project Overview

This project focuses on **fitting a parametric curve** to a given set of 2D data points.  
The goal is to estimate the best-fit parameters that minimize the **L1 distance** (sum of absolute differences) between the predicted and the actual points.

The approach combines two optimization methods:
1. **Differential Evolution (DE)** – for a broad global search.
2. **Least Squares Refinement** – for fine-tuning locally.

This was done as part of the **Assignment for Research and Development / AI**, where the evaluation is based on L1 accuracy, explanation, and code quality.

---

## ⚙️ Equation Used
<img width="526" height="552" alt="image" src="https://github.com/user-attachments/assets/89b06bc9-93aa-43e4-93dc-9e554579fa23" />

The curve is defined by the following parametric equations:

\[
x = t \cos(\theta) - e^{M|t|}\sin(0.3t)\sin(\theta) + X
\]
\[
y = 42 + t\sin(\theta) + e^{M|t|}\sin(0.3t)\cos(\theta)
\]

where:
- **θ (theta)** – rotation angle  
- **M** – exponential scaling factor  
- **X** – horizontal translation  
- **a, b** – linear scaling and shift for the parameter `t`

---

## 🧠 Thought Process and Approach

At first, I started by analyzing the pattern in the given data points.  
It was clear that the curve was non-linear and needed a flexible parametric representation.  
To estimate the unknown parameters, I decided to use a two-stage optimization process:

1. **Global Search (Differential Evolution):**
   - Finds a good starting region for parameters.
   - Useful because our equation involves trigonometric and exponential terms → very non-linear.

2. **Local Refinement (Least Squares):**
   - Uses the DE result as an initial guess.
   - Minimizes residuals (`x_pred - x_actual`, `y_pred - y_actual`) efficiently.

3. **Error Calculation (L1 Distance):**
   - The L1 metric (sum of absolute differences) was used since it’s the same as the scoring metric in evaluation.
   - More robust to outliers compared to L2.

4. **Results:**
<img width="528" height="391" alt="image" src="https://github.com/user-attachments/assets/b651a3bc-b528-40be-bdf5-29c04c19efdc" />


5. **Visualization and Verification:**
   - Two plots are generated:
     - Actual vs Fitted Curve
     - Error over the parameter `t`
     - <img width="1389" height="490" alt="image" src="https://github.com/user-attachments/assets/5aaf8f09-10a7-41e1-8b55-e40cd8779072" />

   - A final **Desmos-compatible expression** is printed for external visualization. :
   
   \left(t\cos(0.8726646259971647)-e^{-0.04999999999999996\left|t\right|}\sin(0.3t)\sin(0.8726646259971647)+72.34735539496822,42+t\sin(0.8726646259971647)+e^{-0.04999999999999996\left|t\right|}\sin(0.3t)\cos(0.8726646259971647)\right)

   When this equation is given in desmos.com,<img width="1311" height="626" alt="image" src="https://github.com/user-attachments/assets/ac0e3234-f1d6-42b1-b467-dcfdca927aa1" />

---
