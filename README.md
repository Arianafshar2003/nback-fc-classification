# nback-fc-classification
# 🧠 Classifying Working Memory Performance using Functional Connectivity

This project aims to classify individuals as high or low performers in a working memory task (N-back), using **block-level functional connectivity (FC)** derived from task-based fMRI data. We applied various **classical machine learning models** (SVM, Random Forest, Logistic Regression, Gradient Boosting) on functional connectivity features extracted from the **Human Connectome Project (HCP)**.

---

## 📌 Table of Contents
- [Background & Motivation](#background--motivation)
- [Research Question](#research-question)
- [Dataset](#dataset)
- [Methods](#methods)
- [Modeling Pipeline](#modeling-pipeline)
- [Results](#results)
- [Presentation](#presentation)
- [Installation & Usage](#installation--usage)
- [License](#license)

---

## 📚 Background & Motivation

Working memory (WM) is a key component of cognitive function and is supported by **network-level brain interactions**. Traditional behavioral assessments may be affected by non-cognitive factors (e.g. fatigue), so brain-based classifiers offer a complementary approach.

---

## ❓ Research Question

> Can block-level functional connectivity patterns during the N-back task classify individuals as high vs. low performers based on their behavioral accuracy?

### Hypotheses
- **H1**: Distinct predictive connectivity patterns exist in high performers (esp. in frontoparietal/task-positive systems).
- **H0**: No significant FC differences; performance near chance level.

---

## 📊 Dataset

- **Source**: Human Connectome Project (HCP)
- **Participants**: 100 healthy adults
- **Task**: 2-back WM task with faces, places, tools, and body parts
- **Behavioral Labels**: Accuracy-based (e.g., median split, 67th percentile, GMM clustering)

---

## 🧠 Methods

### Feature Extraction
- **Parcellation**: Glasser 360-ROI atlas
- **Types of FC**:
  - Whole-Brain FC (upper triangle)
  - Between-Network FC (12 networks)
- **Preprocessing**: StandardScaler + PCA (retain 95% variance)

---

## 🧪 Modeling Pipeline

### Classification
- Models: `SVM`, `Random Forest`, `Logistic Regression`, `Gradient Boosting`
- Labeling strategies: Median, 67th Percentile, GMM Clustering
- Validation: GridSearchCV + Stratified 3-Fold CV

### Exploratory Regression
- Models: `SVR`, `Ridge`, `Lasso`, `RF`, `GB`, `KNN`
- Outcome: R², MAE, MSE — **Regression results were consistently poor**

---

## ✅ Results

### Best Classifier Performance:
- **Network FC (BP_ACC, 67th percentile)** → `Random Forest`, Accuracy ≈ **0.80**
- **Whole-Brain FC (FACES_ACC, TOOLS_ACC, GMM)** → `SVM`, Accuracy ≈ **0.75**

### Insights:
- SVM and RF models performed best.
- GMM clustering and 67th percentile were most effective label strategies.
- **PLACES_ACC** performed worst (~0.65) due to spatial processing noise.

> Regression models showed weak predictive ability (low R²).

---

## 🎯 Presentation

You can view a detailed PDF presentation of the project [here](./presentation.pdf).

---

## ⚙️ Installation & Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/nback-fc-classification.git
   cd nback-fc-classification
2. Install required packages (e.g., via requirements.txt):
   ```bash
   pip install -r requirements.txt
4. Open the notebook:
```bash
jupyter notebook code.ipynb

