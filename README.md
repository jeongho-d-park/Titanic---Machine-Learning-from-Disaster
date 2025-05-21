
# 🛳 Titanic - Machine Learning from Disaster

This repository contains my complete analysis, feature engineering, and modeling workflow for the classic **Titanic survival prediction** problem on Kaggle.

## 📁 Project Structure

- `Titanic.ipynb`: Jupyter notebook with all steps from EDA to model training and prediction
- `submission.csv`: Example format for Kaggle submission (not included here)

---

## 🚀 Objective

Predict whether a passenger survived the Titanic shipwreck based on personal attributes such as class, age, sex, fare, and family relationships.

---

## 🧠 Feature Engineering Highlights (Feature descriptions follow at the bottom)

Over 30 different feature combinations were tested to optimize model performance. Key strategies included:

- Derived features: `Age_Fare`, `Age_Pclass`, `GroupSize`
- Interaction terms: `FarelogOverAge`, `IsAlone`, `with_kids_case`
- Binning and transformations: `FareLog`, `FamilySizeBand`, `TicketGroupSizeBand`

Final features that achieved the best leaderboard score (`0.78947`) were:

```python
features = ['Pclass', 'Fare', 'Title', 'FamilySize', 'TicketGroupSize', 'Age_Fare', 'Age_Pclass']
```

> ✅ Note: Using raw `Fare` instead of `FareLog` increased score by ~0.005.

---

## 📊 Model Performance

- **Model**: Custom ensemble of classifiers
- **Validation Split**: 80% training data used for model tuning
- **Public Leaderboard Score**: **0.78947**

Interestingly, using **80% of training data** yielded a **higher Kaggle score** than using 100%, likely due to reduced overfitting and better generalization.

---

## 🔧 Tools & Libraries

- Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
- Jupyter Notebook

---

## 📌 Notes

- This project focuses not only on accuracy, but on **interpretability and experimental tracking**.
- Feature selection was guided by empirical score improvements, not just intuition.

---

## 📤 Submission Format

Expected format for submission:

```csv
PassengerId,Survived
892,0
893,1
...
```

---

## 📎 Kaggle Link

You can find the original competition [here](https://www.kaggle.com/c/titanic).

---

## 📬 Contact

For any questions, feel free to reach out via GitHub Issues or pull requests.

---

## 🧬 Feature Definitions & Rationale

Several custom features were engineered to capture complex relationships between variables. Below are brief descriptions of each:

### 🔹 Derived Features
- `Age_Fare`: Multiplication of age and fare, representing the combined effect of wealth and age.
- `Age_Pclass`: Age multiplied by passenger class; used to reflect how age may interact with social class.
- `TicketGroupSize`: The number of passengers sharing the same ticket. This feature approximates group travel size beyond family ties, often capturing friends, colleagues, or extended groups traveling together. It proved useful in understanding group-based survival dynamics.
- `GroupSize`: The larger of `FamilySize` and `TicketGroupSize`, representing the maximum group association.

### 🔹 Interaction Terms
- `FarelogOverAge`: Log of fare divided by age, to represent cost relative to age (as a proxy for dependency or ticket worth).
- `IsAlone`: Boolean indicating whether a passenger had no family members on board.
- `with_kids_case`: Indicates the sex and if the passenger was in a group that included young children.

### 🔹 Binning & Transformations
- `FareLog`: Logarithmic transformation of fare to reduce skewness.
- `FamilySizeBand`: Binned version of `FamilySize` to generalize small vs. large families.
- `TicketGroupSizeBand`: Binned version of ticket group size for robustness against outliers.

---

## ⚖️ Simpler Features, Better Results

Although many complex features were engineered and tested, empirical validation showed that using **fewer and simpler features often led to better generalization**.

Despite early gains in training or validation accuracy, many engineered variables (like `FarelogOverAge`, `FareLog`, or `with_kids_case`) **did not consistently improve Kaggle leaderboard scores**. In fact, removing them often resulted in:

- **Less overfitting**
- **More stable predictions**
- **Improved public leaderboard performance**

As a result, the final selected feature set was leaner and focused on **core predictive variables** with proven generalizability.
