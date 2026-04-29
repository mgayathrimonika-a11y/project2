# 🩺 Diabetes Disease Prediction

A Machine Learning project to predict whether a patient is likely to have diabetes based on medical diagnostic measurements, using the Pima Indians Diabetes Dataset.

---

## 🎯 Objective

To build a classification model that predicts the onset of diabetes in patients using health metrics such as Glucose level, BMI, Age, and Insulin — enabling early medical intervention.

---

## 📁 Dataset

- **Source:** [Plotly Datasets — Pima Indians Diabetes](https://raw.githubusercontent.com/plotly/datasets/master/diabetes.csv)
- **Records:** 768 patients
- **Features:** 9 columns (8 features + 1 target)
- **Target Variable:** `Outcome` (1 = Diabetic, 0 = Non-Diabetic)

### Features:
| Feature | Description |
|---|---|
| `Pregnancies` | Number of times pregnant |
| `Glucose` | Plasma glucose concentration |
| `BloodPressure` | Diastolic blood pressure (mm Hg) |
| `SkinThickness` | Triceps skin fold thickness (mm) |
| `Insulin` | 2-Hour serum insulin (mu U/ml) |
| `BMI` | Body Mass Index |
| `DiabetesPedigreeFunction` | Diabetes likelihood based on family history |
| `Age` | Age of the patient |
| `Outcome` | 1 = Diabetic, 0 = Non-Diabetic (Target) |

---

## 🔧 Tech Stack

| Tool | Purpose |
|---|---|
| Python | Programming Language |
| Google Colab | Development Environment |
| Pandas | Data manipulation |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical plots |
| Scikit-learn | ML model, scaling & evaluation |

---

## 🧹 Data Preprocessing

- Loaded dataset directly from URL using `pd.read_csv()`
- **Medical Validity Check:** Replaced biologically impossible `0` values in `Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, and `BMI` with `NaN`
- Filled missing values using **median imputation** (`df.fillna(df.median())`)
- Applied **StandardScaler** to normalize all features before model training
- Train-Test Split: **80% train / 20% test** (`random_state=42`)

---

## 🔍 Exploratory Data Analysis (EDA)

Visualizations created to understand the data:

- **Disease Distribution** — Count of diabetic vs non-diabetic patients
- **Glucose Level vs Disease** — Higher glucose strongly correlates with diabetes
- **Correlation Heatmap** — Glucose (0.49) and BMI (0.31) are most correlated with Outcome

---

## 🤖 Model

**Algorithm:** Random Forest Classifier

```python
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier(random_state=42)
model.fit(X_train, y_train)
```

---

## 📈 Model Performance

| Metric | Score |
|---|---|
| **Accuracy** | 74.03% |
| **ROC-AUC** | Plotted with curve |

### Classification Report:
```
              precision    recall  f1-score   support
           0       0.80      0.79      0.80       99
           1       0.63      0.65      0.64       55
    accuracy                           0.74      154
   macro avg       0.72      0.72      0.72      154
weighted avg       0.74      0.74      0.74      154
```

---

## 🏆 Feature Importance

Top features that contribute most to diabetes prediction:

| Rank | Feature | Importance |
|---|---|---|
| 1 | **Glucose** | Highest |
| 2 | **BMI** | High |
| 3 | **Age** | Medium-High |
| 4 | DiabetesPedigreeFunction | Medium |
| 5 | Insulin | Medium |
| 6 | BloodPressure | Lower |

> Glucose is by far the most important predictor of diabetes in this model.

---

## 💡 Key Insights

- **Glucose** is the strongest predictor — diabetic patients have significantly higher glucose levels
- Patients with **higher BMI** are more likely to be diabetic
- **Older patients** have a higher risk of diabetes
- The model correctly identifies ~65% of actual diabetic cases (Recall = 0.65)

---

## 🚀 How to Run

1. Open [Google Colab](https://colab.research.google.com/)
2. Upload `project2.ipynb`
3. Run all cells — dataset loads automatically from URL:
   ```python
   url = "https://raw.githubusercontent.com/plotly/datasets/master/diabetes.csv"
   df = pd.read_csv(url)
   ```
4. No Kaggle API key needed — direct URL download ✅

---

## 📂 Project Structure

```
📦 diabetes-prediction
 ┣ 📓 project2.ipynb       ← Main Jupyter Notebook
 ┗ 📄 README.md            ← Project Documentation
```

---

## 🔗 View Notebook

[![NBViewer](https://img.shields.io/badge/Open%20in-NBViewer-orange)](https://nbviewer.org/github/mgayathrimonika-a11y/project2/blob/main/project2.ipynb)

---

## 👩‍💻 Author

**Gayathrimonika**
- GitHub: [@mgayathrimonika-a11y](https://github.com/mgayathrimonika-a11y)

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).
