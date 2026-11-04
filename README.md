# ml-aleph-bet

> *Learning the fundamentals of Machine Learning from first principles, implemented from scratch in pure Python with zero third-party dependencies.*

---

## 📖 Overview

**`ml-aleph-bet`** (derived from the Hebrew alphabet "Aleph-Bet", denoting the ABCs and building blocks) is an educational, hands-on repository dedicated to implementing classical machine learning algorithms from scratch.

### Core Principles
1. **Zero External Algorithm Dependencies**: Every algorithm is written purely using Python standard library primitives (`math`, `random`, `heapq`, `collections`). No `numpy`, `scipy`, or `scikit-learn` are used in the core algorithmic logic.
2. **Mathematical Rigor & Transparency**: Clear step-by-step breakdown of cost functions, gradients, and optimization rules with LaTeX mathematical derivations.
3. **Pedagogical Visualizations**: Clean, illustrative plots via `matplotlib` to inspect decision boundaries, loss trajectories, and clustering geometry.
4. **Clean Code & Type Safety**: Type annotations (`typing`), docstrings, and algorithmic complexity notes.

---

## 🗂 Implemented Algorithms (Phase 1)

| Algorithm | Notebook | Paradigm | Task | Time Complexity | Space Complexity |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Linear Regression** | [`notebooks/linear_regression.ipynb`](./notebooks/linear_regression.ipynb) | Supervised | Regression | $\mathcal{O}(N D^2 + D^3)$ (OLS) / $\mathcal{O}(E N D)$ (GD) | $\mathcal{O}(D^2)$ |
| **K-Means Clustering** | [`notebooks/kmeans.ipynb`](./notebooks/kmeans.ipynb) | Unsupervised | Clustering | $\mathcal{O}(I \cdot K \cdot N \cdot D)$ | $\mathcal{O}(N \cdot D + K \cdot D)$ |
| **K-Nearest Neighbors (KNN)** | [`notebooks/knn.ipynb`](./notebooks/knn.ipynb) | Supervised | Classification | $\mathcal{O}(N \cdot D + N \log K)$ | $\mathcal{O}(K)$ (streaming) |
| **Single Artificial Neuron** | [`notebooks/neuron.ipynb`](./notebooks/neuron.ipynb) | Supervised | Binary Classification | $\mathcal{O}(E \cdot N \cdot D)$ | $\mathcal{O}(D)$ |
| **Principal Component Analysis (PCA)** | [`notebooks/pca.ipynb`](./notebooks/pca.ipynb) | Unsupervised | Dimensionality Reduction | $\mathcal{O}(N \cdot D^2 + K \cdot I \cdot D^2)$ | $\mathcal{O}(D^2)$ |

*Notation:*  
- $N$: Number of samples  
- $D$: Number of features / dimensions  
- $K$: Number of clusters / neighbors / components  
- $I$: Number of convergence iterations  
- $E$: Number of training epochs  

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9+ (developed and tested on Python 3.12)
- Standard library modules: `math`, `random`, `heapq`, `collections`, `typing`

### Optional Visualization Dependency
While the algorithms run with zero third-party libraries, `matplotlib` is recommended to display the notebooks' visual plots:

```bash
# Clone the repository
git clone https://github.com/stefanogamba/ml-aleph-bet.git
cd ml-aleph-bet

# Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install Jupyter and Matplotlib
pip install jupyter matplotlib
```

### Running the Notebooks
Launch the Jupyter environment:
```bash
jupyter notebook
```
Navigate to the `notebooks/` folder and open any notebook to explore the theory, run the code, and view the generated visualizations.

---

## 🗺️ Roadmap (Phase 2)

The following classical algorithms are planned for implementation from scratch in the next phase:

- [x] **Linear Regression**: Ordinary Least Squares (Closed-form Normal Equation) & Gradient Descent.
- [ ] **Logistic Regression**: Binary and Multi-class Softmax classification with Cross-Entropy Loss.
- [ ] **Decision Trees & Random Forest**: Recursive tree building with Shannon Entropy, Information Gain, and Gini Impurity.
- [ ] **Multi-Layer Perceptron (MLP)**: Modular forward/backward pass and backpropagation across multiple hidden layers.
- [ ] **Naive Bayes**: Gaussian and Multinomial likelihood estimation applying Bayes' Theorem.
- [ ] **Support Vector Machine (Linear SVM)**: Sub-gradient descent on soft-margin Hinge Loss.

---

## 🛡️ Security & Agent Guidelines

For guidelines on repository rules, security standards, and AI agent instructions, see [`GEMINI.md`](./GEMINI.md).
