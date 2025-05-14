
# 🛳 Titanic - Machine Learning from Disaster

This repository contains my complete analysis, feature engineering, and modeling workflow for the classic **Titanic survival prediction** problem on Kaggle.

## 📁 Project Structure

- `Titanic.ipynb`: Jupyter notebook with all steps from EDA to model training and prediction
- `submission.csv`: Example format for Kaggle submission (not included here)

---

## 🚀 Objective

Predict whether a passenger survived the Titanic shipwreck based on personal attributes such as class, age, sex, fare, and family relationships.

---

## 🧠 Feature Engineering Highlights

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
