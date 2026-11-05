<div align="center">
  <h1>📱 Social Media Addiction Predictor</h1>
</div>

> **Six classifiers, one question: how hooked is this student?**  
> Comparing machine learning models that predict a student's social media addiction score from their habits, sleep, and wellbeing.

---

## 🧠 What Is This Project?

Can a few facts about a student's daily life predict how addicted they are to social media? This project trains six classifiers on survey data, compares them head to head, and finds the best one. The full write-up is in **[the final paper](Paper/CCMACLRL_Final%20Paper.pdf)**, _Evaluation of Machine Learning Classification Algorithms for Predicting Social Media Addiction Level Among Students_.

---

## 📦 The Data

The dataset is **Students' Social Media Addiction** by Adil Shamim on Kaggle: a self-reported survey of **705 students from 110 countries**, aged 18 to 24.

- 🎯 **Target**: `Addicted_Score`, whole numbers from 2 to 9, with each score treated as its own class
- 🧾 **Features**: age, gender, academic level, country, daily usage hours, most-used platform, effect on academics, sleep hours, mental health score, relationship status, and conflicts over social media

Because it's self-reported and a single snapshot in time, it can show patterns but can't prove cause and effect.

---

## 🔬 How It Works

1. 🧹 **Clean** (`Preprocessing/data_cleaning.ipynb`): drop `Student_ID` and label-encode the text columns
2. 📊 **Explore** (`Preprocessing/data_visualization.ipynb`): visualize the original data
3. 🤖 **Train** (`Model Training/`): one notebook per algorithm, each trying different setups, such as all features versus a selected five, or different values of K for KNN
4. 🏆 **Compare** (`Model Training/best_model.ipynb`): put each algorithm's best setup through an 80/20 test, 5-fold cross-validation, and grid search tuning

The selected five features are conflicts over social media, mental health score, sleep hours, effect on academics, and daily usage hours.

---

## 🏆 Results

**Random Forest takes the crown**, finishing first in every column.

| Model | Setup | Test accuracy | Test F1 | 5-fold CV accuracy | Tuned test accuracy |
| --- | --- | --- | --- | --- | --- |
| 🥇 **Random Forest** | All features | **0.9504** | **0.9501** | **0.8695** | **0.9504** |
| 🥈 Decision Tree | All features | 0.9291 | 0.9288 | 0.8213 | 0.9291 |
| 🥉 Logistic Regression | All features | 0.9078 | 0.8993 | 0.7844 | 0.9149 |
| KNN | Selected, K = 5 | 0.8794 | 0.8764 | 0.7943 | 0.8582 |
| SVM | Selected | 0.8582 | 0.8373 | 0.8298 | 0.8582 |
| Naive Bayes | All features | 0.8511 | 0.8171 | 0.7348 | 0.9149 |

Test scores come from a single 80/20 split, while cross-validation averages five splits. The 0.87 for Random Forest is the more cautious number to quote.

---

## 🛠️ Tech Stack

| | |
| --- | --- |
| **Language** | Python |
| **Data** | pandas and NumPy |
| **Modeling** | scikit-learn |
| **Charts** | Matplotlib and seaborn |
| **Environment** | Jupyter |

---

## 🚀 How to Run

```bash
git clone https://github.com/leonnmarcoo/CCMACLRL_COM232_PROJECT.git
cd CCMACLRL_COM232_PROJECT
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt notebook
jupyter notebook
```

`cleaned_data.csv` is already in the repo, so you can open any notebook in `Model Training/` right away. To see the whole comparison in one place, start with `best_model.ipynb`. Its grid searches can take a few minutes.

---

## 🗂️ What's in Here

| Path | What it is |
| --- | --- |
| `data.csv` | The original survey data |
| `cleaned_data.csv` | The encoded data used for training |
| `Preprocessing/` | Cleaning and visualization notebooks |
| `Model Training/` | One notebook per algorithm, plus `best_model.ipynb` |
| `Paper/` | The final paper and its plagiarism report |

---

## 🤝 Authors

**Leon Marco Devela** and **Rae Paulos**, College of Computing and Information Technologies, National University, Manila.
