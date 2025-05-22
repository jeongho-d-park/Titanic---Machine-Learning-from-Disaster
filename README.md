
# 🛳 Titanic - Machine Learning from Disaster

This project goes beyond basic model fitting by leveraging domain knowledge and exploratory data analysis (EDA) to guide feature engineering and model selection.

---

### 🧠 Original Feature Insights & Extraction

In addition to standard exploratory analysis, I introduced original features that captured subtle group-based and social dynamics:

- **with_kids**: Female passengers traveling with young children (Age < 7, same ticket) had significantly *lower* survival (50%) compared to those without (80%).  
  For males, the pattern reversed: those with kids had *higher* survival (29% vs. 18%).  
  → This suggests nuanced group effects and the social prioritization of families.

- **GroupSize**: Defined as the maximum of `FamilySize` and `TicketGroupSize`, this represents the broadest social or logistical unit a passenger may belong to.

In contrast, I also incorporated several engineered features inspired by community insights and prior solutions:

- **Title**: Extracted from names (`Mr`, `Mrs`, `Miss`, `Master`) to infer social role and help with age imputation.
- **Cabin Initial**: First letter of the cabin, which often correlates with class or deck.
- **Age_Fare**: Product of age and fare; a proxy for socio-economic impact on survival.
- **FarelogOverAge**: Logarithmic fare divided by age; a proxy for socio-economic impact on survival.
- **Age_Pclass**: Interaction of age and passenger class to reflect age-based stratification.
- **TicketGroupSize**: Count of passengers sharing the same ticket, capturing group travel dynamics (e.g., friends, servants, or multi-family groups).

---

## ⚖️ Simpler Features, Better Results

Although many complex features were engineered and tested, empirical validation showed that using **fewer and simpler features often led to better generalization**.

Despite early gains in training or validation accuracy, many engineered variables (like `FarelogOverAge`, `FareLog`, or `with_kids`) **did not consistently improve Kaggle leaderboard scores**. In fact, removing them often resulted in:

- **Less overfitting**
- **More stable predictions**
- **Improved public leaderboard performance**

As a result, the final selected feature set was leaner and focused on **core predictive variables** with proven generalizability.

---

### 🧠 Final features that achieved the best leaderboard score (`0.78947`) were:

features = ['Pclass', 'Fare', 'Title', 'FamilySize', 'TicketGroupSize', 'Age_Fare', 'Age_Pclass']

---

### 🧠 Final model:

I used a custom ensemble of several models with optimized hyperparameters:
- Random Forest Classifier
- Gradient Boosting Classifier
- Support Vector Machine
- Logistic Regression

---

## 📌 Notes

- This project focuses not only on accuracy, but on **interpretability and experimental tracking**.
- Feature selection was guided by empirical score improvements, not just intuition.

---

### 🔍 Insights from EDA

Several meaningful patterns emerged from analyzing the data:

- **Passenger Class (`Pclass`) matters**: Survival rates vary significantly across classes  
  - 1st Class: 63%  
  - 2nd Class: 47%  
  - 3rd Class: 24%

- **Sex is a strong predictor**:  
  - Female: 74% survival  
  - Male: 19% survival  
  → This suggests that *social and cultural codes (e.g. "women and children first") may have heavily influenced survival outcomes.*

- **Family connections matter**:  
  - Passengers with at least one sibling/spouse aboard (`SibSp > 0`) had higher survival than those with none, but for SibSp > 0, the survival rate was inversely proportional to SibSp.

- **Port of embarkation (`Embarked`) influences survival**:  
  - C: 55%, Q: 39%, S: 34%  
  - This variable may capture regional, demographic, or boarding location effects.

---

## 📁 Project Structure

- `Titanic.ipynb`: Jupyter notebook with all steps from EDA to model training and prediction
- `submission.csv`: Example format for Kaggle submission (not included here)

---

## 🚀 Objective

Predict whether a passenger survived the Titanic shipwreck based on personal attributes such as class, age, sex, fare, and family relationships.

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
