# Supervised Learning with Scikit-learn

![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=flat-square&logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-22C55E?style=flat-square)
![Type](https://img.shields.io/badge/Type-Learning%20Repository-6366F1?style=flat-square)

A structured, hands-on documentation of my supervised learning journey using Scikit-learn — covering algorithms, evaluation metrics, regularization, and hyperparameter tuning with a focus on understanding the mathematics and engineering decisions behind each concept, not just the code.

---

## Overview

Most ML learning resources teach you *how* to call `.fit()` and `.predict()`. This repository is about understanding *why* — why KNN fails in high dimensions, why Ridge outperforms OLS when features are correlated, why cross-validation gives a more honest accuracy estimate than a single train/test split.

Every concept here was implemented in a Jupyter Notebook, then reimplemented from scratch to test real understanding, then studied from first principles using additional resources. The goal was not to collect implementations — it was to build intuition.

---

## Topics Covered

### ML Workflow

| Step | Concept | Notes |
|---|---|---|
| 1 | Model Instantiation | Understanding estimator API design |
| 2 | Model Training | `.fit()` — what actually happens |
| 3 | Prediction | `.predict()` vs `.predict_proba()` |
| 4 | Evaluation | Choosing the right metric for the task |

### Supervised Learning Algorithms

| Algorithm | Type | Key Concept Studied |
|---|---|---|
| K-Nearest Neighbors | Classification / Regression | Distance metrics, curse of dimensionality |
| Linear Regression | Regression | OLS, coefficient interpretation |
| Logistic Regression | Classification | Sigmoid function, log-odds, decision boundary |
| Ridge Regression | Regression | L2 regularization, shrinkage |
| Lasso Regression | Regression | L1 regularization, feature selection via sparsity |

### Model Evaluation

| Metric | When It Matters |
|---|---|
| Accuracy | Balanced class distributions |
| Precision | When false positives are costly |
| Recall | When false negatives are costly (e.g. medical screening) |
| F1-Score | Imbalanced classes — balances Precision and Recall |
| Confusion Matrix | Full breakdown of TP / TN / FP / FN |

### Validation & Tuning

- **Train-Test Split** — baseline evaluation with `test_size` considerations
- **Cross-Validation** — k-fold CV for more reliable performance estimates
- **GridSearchCV** — exhaustive hyperparameter search
- **RandomizedSearchCV** — efficient search over large parameter spaces
- **Bias-Variance Tradeoff** — understanding underfitting vs overfitting

---

## Repository Structure

```
supervised-learning-with-scikit-learn/
│
├── supervised_learning.ipynb    # Main notebook — all implementations
├── requirements.txt             # Python dependencies
└── README.md                    # This file
```

> This is a focused learning repository. One notebook, done properly, covers more ground than a dozen half-finished ones.

---

## Technologies

| Tool | Purpose |
|---|---|
| Python 3.9+ | Core language |
| Scikit-learn | ML algorithms, preprocessing, evaluation |
| Pandas | Data loading and manipulation |
| NumPy | Numerical computation |
| Matplotlib | Visualization |
| Jupyter Notebook | Interactive development and documentation |

---

## Installation

```bash
# Clone the repository
git clone https://github.com/haseeb-ml-engineer/supervised-learning-with-scikit-learn.git
cd supervised-learning-with-scikit-learn

# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows

# Install dependencies
pip install -r requirements.txt
```

## Running the Notebook

```bash
# Start Jupyter
jupyter notebook

# Or open directly
jupyter notebook supervised_learning.ipynb
```

Alternatively, open the notebook directly in **Google Colab** — no local setup required:

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/haseeb-ml-engineer/supervised-learning-with-scikit-learn/blob/main/supervised_learning.ipynb)

---

## Key Takeaways

These are not summaries from documentation. These are things that only became clear after implementing them:

**On KNN:** The algorithm has no training phase — it just memorises the data. Its performance degrades sharply in high-dimensional spaces because distance metrics lose meaning when every point is roughly equidistant from every other.

**On Regularization:** Ridge and Lasso are not just "tools to prevent overfitting." Ridge shrinks all coefficients toward zero but keeps all features. Lasso actually zeroes out coefficients entirely — making it a feature selection method in disguise. The choice between them depends on whether you believe all features are relevant.

**On Cross-Validation:** A single train/test split gives you one data point about your model's performance. Cross-validation gives you a distribution. The difference matters, especially on small datasets where a single unlucky split can mislead you significantly.

**On Evaluation Metrics:** Accuracy is almost never the right metric on its own. A model that predicts "no disease" for every patient can achieve 90% accuracy on a dataset where 90% of patients are healthy — and catch zero sick people. Recall is what actually matters in that context.

**On ML fundamentals:** Machine Learning is not magic. Behind every model are mathematical assumptions, data requirements, and engineering trade-offs. The more I've learned, the more I've come to appreciate that strong fundamentals are what separate someone who can run a model from someone who can debug one.

---

## Learning Approach

This repository reflects a deliberate learning methodology:

- **Implement → Break → Understand → Reimplement.** Every concept was coded, then reimplemented from scratch without reference to test genuine understanding.
- **First principles over API calls.** Understanding what `GridSearchCV` is doing internally matters more than knowing its parameter names.
- **Andrew Ng's ML courses** were used alongside hands-on implementation for mathematical grounding — particularly for understanding cost functions, gradient descent intuition, and the bias-variance tradeoff.
- **Experimentation over passive reading.** Every claim was tested empirically in the notebook.

---

## Roadmap

This repository documents the foundation. What comes next:

```
Completed ✅
├── KNN
├── Linear / Logistic Regression
├── Ridge / Lasso Regularization
├── Cross-Validation
└── GridSearchCV / RandomizedSearchCV

In Progress 🔨
└── Decision Trees

Planned 📋
├── Random Forest & Ensemble Methods
├── XGBoost / Gradient Boosting
├── Deep Learning (TensorFlow)
├── Computer Vision
└── MLOps & model deployment pipelines
```

---

## Resources

| Resource | Used For |
|---|---|
| [Andrew Ng — Machine Learning Specialization](https://www.coursera.org/specializations/machine-learning-introduction) | Mathematical intuition and theory |
| [Scikit-learn Documentation](https://scikit-learn.org/stable/) | API reference and algorithm details |
| [DataCamp — ML with Scikit-learn](https://www.datacamp.com) | Hands-on structured exercises |

---

## Author

**Haseeb Tariq**
BS Information Technology · Specialisation: Machine Learning / AI
Machine Learning Engineer Intern @ FlyRank

This repository is part of a deliberate, long-term effort to build genuine ML engineering competence — starting from fundamentals and working toward production systems. Other projects in this journey:

- [`multi-disease-prediction-system`](https://github.com/haseeb-ml-engineer/multi-disease-prediction-system) — End-to-end ML healthcare app (Diabetes, Heart Disease, COVID-19)
- [`truelens-ai`](https://github.com/haseeb-ml-engineer) — AI-powered deepfake detection platform (in development)

---

## Connect

| | |
|---|---|
| 💼 LinkedIn | [linkedin.com/in/haseeb-tariq-0x](https://linkedin.com/in/haseeb-tariq-0x) |
| 🐙 GitHub | [github.com/haseeb-ml-engineer](https://github.com/haseeb-ml-engineer) |
| 📧 Email | [haseebtariq.babbar@gmail.com](mailto:haseebtariq.babbar@gmail.com) |

---

*Strong fundamentals are not the slow path to ML competence. They are the only path.*
