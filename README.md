# Instructor Effectiveness Modeling

## 📌 Project Overview

This project focuses on analyzing and predicting instructor effectiveness using Machine Learning.

The dataset contains information about course batches, learner outcomes, learner engagement, and learner feedback. The goal is to create an overall instructor effectiveness score and classify instructors into three performance tiers:

- Low
- Medium
- High

A Random Forest Classifier is used to predict the effectiveness tier of instructors.

---

## 🎯 Project Objectives

- Analyze instructor and learner performance data
- Perform Exploratory Data Analysis (EDA)
- Identify missing values, duplicates, correlations, and anomalies
- Create a composite Instructor Effectiveness Score
- Aggregate batch-level data to instructor level
- Classify instructors into Low, Medium, and High effectiveness tiers
- Train a Machine Learning classification model
- Evaluate model performance using appropriate metrics
- Identify the most influential features

---

## 📊 Dataset

Each row in the dataset represents a course batch.

### Identifier Features

- `batch_id` – Unique batch identifier
- `instructor_id` – Unique instructor identifier
- `course_id` – Course identifier

### Learner Outcome Features

- `completion_rate`
- `dropout_rate`
- `avg_score_improvement`
- `avg_quiz_score`

### Engagement Features

- `avg_watch_time`
- `assignment_submission_rate`
- `forum_activity_rate`

### Feedback Features

- `avg_feedback_score`
- `feedback_response_rate`

---

## 🧮 Instructor Effectiveness Score

A composite effectiveness score was created using learner outcomes, engagement, and feedback.

Higher weights were given to learner outcome metrics because they provide stronger evidence of learning effectiveness.

The score includes:

- Completion rate
- Dropout rate
- Score improvement
- Quiz performance
- Watch time
- Assignment submission
- Forum activity
- Learner feedback

The final score was used to classify instructors into:

**Low | Medium | High**

---

## 🔄 Data Aggregation

Since the original dataset contains batch-level records, the data was aggregated to the instructor level.

Average values were calculated across multiple batches for each instructor.

A `batch_count` feature was also created to show how many batches were associated with each instructor.

This helps distinguish instructors with limited batch history from instructors with more stable historical performance.

---

## 🤖 Machine Learning Model

### Random Forest Classifier

A Random Forest Classifier was selected for this project because it:

- Works well with tabular data
- Can capture non-linear relationships
- Handles multiple features effectively
- Provides feature importance for interpretation

### Train-Test Split

The dataset was divided into:

- **80% Training Data**
- **20% Testing Data**

Stratified sampling was used to maintain the distribution of effectiveness tiers.

---

## 📈 Model Performance

The Random Forest model achieved:

**Accuracy: 95.83%**

### Classification Results

| Class | F1-Score |
|-------|----------|
| Low | 0.94 |
| Medium | 0.93 |
| High | 1.00 |

The confusion matrix showed that most instructors were correctly classified, with only one misclassification in the test set.

---

## 🔍 Feature Importance

The most influential features identified by the Random Forest model were:

| Feature | Importance |
|---------|------------|
| `avg_score_improvement` | 0.269 |
| `dropout_rate` | 0.194 |
| `completion_rate` | 0.187 |
| `avg_quiz_score` | 0.120 |
| `feedback_response_rate` | 0.059 |
| `forum_activity_rate` | 0.049 |
| `avg_feedback_score` | 0.043 |
| `avg_watch_time` | 0.034 |
| `assignment_submission_rate` | 0.023 |
| `batch_count` | 0.014 |

`avg_score_improvement` was the most important feature, followed by `dropout_rate` and `completion_rate`.

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook / Google Colab
- Machine Learning
- Exploratory Data Analysis (EDA)

---

## 📁 Project Structure

```text
instructor-effectiveness-modeling/
│
├── instructor_effectiveness_modeling.ipynb
├── dataset.csv
├── README.md
└── requirements.txt
