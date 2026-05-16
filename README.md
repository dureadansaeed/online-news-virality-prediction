# 📊 Online News Popularity Analysis

### Probability & Statistics Final Project

## 👨‍🏫 Instructor

* Sir Muhammad Ali 

## 👩‍💻 Authors

* Dur E Adan (24i-3037)
* Ayna Khan (24i-0097)

## 🏫 Department

**Department of Artificial Intelligence**
FAST-NUCES Islamabad
Section: AI-4C

---

## 📌 Project Overview

This project explores the factors that influence the **online popularity of news articles**, measured by the number of social media shares.

Using statistical techniques and machine learning models, we analyze and predict article virality based on content, timing, and sentiment features.

---

## 📂 Dataset Description

* Dataset: **Online News Popularity Dataset (UCI)**
* Total Articles: **39,644**
* Features: **61**
* Target Variable: **shares**

### 🔍 Key Characteristics

* Mean shares: **3,395**
* Standard deviation: **11,627**
* Range: **1 → 843,300**
* Distribution: **Highly right-skewed**

### 📊 Feature Categories

* Content structure (words, images, videos, links)
* Keywords statistics
* Publication timing (weekday/weekend)
* Topic modeling (LDA scores)
* Sentiment metrics (polarity, subjectivity)

---

## 🔎 Data Analysis Process

### 📥 Data Loading & Inspection

* Loaded dataset using pandas
* Checked data types and missing values (`df.info()`)
* Generated descriptive statistics (`df.describe()`)
* Cleaned column names

---

### 📊 Exploratory Data Analysis (EDA)

#### 📌 Target Variable Transformation

* Shares were highly skewed
* Applied transformation:

  * `log(shares + 1)`
* Result: Near-normal distribution

---

#### 🔗 Correlation Insights

**Positive Correlations:**

* `is_weekend` → 0.156
* `kw_avg_avg` → 0.151
* `data_channel_is_socmed` → 0.120
* `data_channel_is_tech` → 0.117

**Negative Correlations:**

* `data_channel_is_world` → -0.150
* `LDA_02` → -0.150

#### 💡 Interpretation

* Weekend content performs better (user behavior)
* Tech & social media articles get more shares
* World news is less likely to be shared
* Popular keywords increase virality

---

### ⚠️ Redundant Features

High multicollinearity detected:

* `n_unique_tokens`, `n_non_stop_words`, `n_non_stop_unique_tokens` (r = 1.00)
* `kw_max_min`, `kw_avg_min` (r = 0.94)

➡️ Dropped redundant features to improve model performance

---

### 🧹 Data Preprocessing

* Removed highly correlated features
* Performed **VIF (Variance Inflation Factor)** analysis
* Dropped features with high multicollinearity:

  * Weekday indicators
  * LDA topic features
  * Token-related features

---

### 🔀 Train-Test Split

* 80% Training
* 20% Testing

---

### ⚖️ Feature Scaling

* Applied **StandardScaler**
* Ensured all features contribute equally

---

## 📈 Regression Model

### 🔹 Linear Regression

* Trained on scaled data
* Predicted `log(shares)`

### ✅ Model Evaluation

* MAE
* MSE
* RMSE
* R² Score

### 📊 Performance

* R² = **0.1240**
* Outperformed baseline model significantly

---

### ⚠️ Assumption Checks

* **Homoscedasticity:** Slight violations observed
* **Normality:** Minor deviations from normal distribution

---

## 🤖 Classification Model

### 🎯 Objective

Classify articles into:

* **High Popularity**
* **Low Popularity**

(based on median of `shares_log`)

---

### 🔹 Logistic Regression

* Applied same preprocessing steps
* Evaluated using:

  * Accuracy
  * Confusion Matrix

---

### 🔍 Important Features

* `kw_avg_avg`
* `kw_max_avg`
* `data_channel_is_tech`

---

## 🧪 Hypothesis Testing

| Feature                   | Test    | Result      |
| ------------------------- | ------- | ----------- |
| data_channel_is_tech      | t-test  | Significant |
| data_channel_is_socmed    | t-test  | Significant |
| n_tokens_content          | Pearson | Significant |
| global_sentiment_polarity | Pearson | Significant |
| kw_avg_avg                | Pearson | Significant |

➡️ All selected features showed **statistically significant relationships** with article popularity

---

## 📉 Data Visualization

Scatter plots were used to analyze relationships between:

* Content length (`n_tokens_content`)
* Number of links (`num_hrefs`)
* Videos (`num_videos`)
* Positive word rate

These provided intuitive insights into feature impact.

---

## 🎯 Key Findings

* 📌 Keyword performance (`kw_avg_avg`) is the strongest predictor
* 📌 Tech & social media articles perform better
* 📌 Weekend publishing increases engagement
* 📌 Sentiment & content length have weak practical impact

---

## 🚀 Future Work

* Use advanced models:

  * Random Forest
  * Gradient Boosting
* Capture non-linear relationships
* Improve prediction accuracy
* Explore deep learning approaches

---

## 📌 Conclusion

The project demonstrates that while certain features significantly influence article popularity, predicting virality remains challenging due to its inherently unpredictable nature.

Even so, the regression model successfully outperformed a baseline approach, validating the effectiveness of statistical modeling in this domain.

---
