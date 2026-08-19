# 🎓 Student Placement Prediction

An end-to-end machine learning project that predicts student placement outcomes using academic performance, technical skills, internships, projects, interview performance, and other student-related factors.

---

## 📌 Project Overview

The goal of this project is to build a machine learning classification system that predicts whether a student is likely to be placed.

The project follows a complete machine learning workflow:

- Data loading
- Data cleaning
- Duplicate and missing-value analysis
- Exploratory Data Analysis (EDA)
- Feature analysis
- Categorical feature encoding
- Numerical feature scaling
- Stratified train-test splitting
- Multiple machine learning models
- Model evaluation
- Model comparison
- Feature interpretation
- Final model selection

---

## 📊 Dataset

The dataset contains:

- **100,000 student records**
- **26 original columns**
- **24 columns after removing two columns**
- **23 input features**
- **1 target variable**

### Target Variable

The target variable is:

`placement_status`

It was encoded as:

| Value | Meaning    |
| ----: | ---------- |
|   `1` | Placed     |
|   `0` | Not Placed |

### Target Distribution

| Placement Status |  Count | Percentage |
| ---------------- | -----: | ---------: |
| Placed           | 54,459 |     54.46% |
| Not Placed       | 45,541 |     45.54% |

The dataset contains no missing values and no duplicate rows after cleaning.

---

## 🧹 Data Cleaning

The following steps were performed:

- Checked dataset dimensions
- Checked missing values
- Checked duplicate rows
- Removed unnecessary columns
- Converted the target variable into binary format
- Verified numerical and categorical features
- Confirmed the final dataset structure

### Removed Columns

The following columns were excluded from model training:

- `student_id`
- `salary_package_lpa`

`salary_package_lpa` was excluded because salary information would not be available when making a placement prediction.

---

## 🔎 Exploratory Data Analysis

Several academic, technical, behavioral, and extracurricular factors were analyzed.

### Features Analyzed

- Age
- Gender
- CGPA
- Branch
- College tier
- Internships
- Projects
- Certifications
- Coding skill
- Aptitude
- Communication skills
- Logical reasoning
- Hackathons
- GitHub repositories
- LinkedIn connections
- Mock interview score
- Attendance
- Backlogs
- Extracurricular score
- Leadership score
- Volunteer experience
- Sleep hours
- Study hours per day

### Key EDA Findings

#### Internships

Placement rates generally increased as the number of internships increased.

Students with more internship experience showed a stronger positive association with placement.

#### Projects

Students with more projects generally showed higher placement rates.

#### Backlogs

Backlogs showed a clear negative association with placement.

As the number of backlogs increased, placement rates generally decreased.

#### Coding Skills

Placed students had a slightly higher average coding skill score than non-placed students.

#### Aptitude

Placed students had a slightly higher average aptitude score.

#### Communication Skills

Placed students had a slightly higher average communication skill score.

#### Logical Reasoning

Placed students had a slightly higher average logical reasoning score.

#### Mock Interviews

Placed students had a slightly higher average mock interview score.

#### Attendance

Attendance showed very little difference between placed and non-placed students.

#### College Tier

Placement rates were relatively similar across Tier 1, Tier 2, and Tier 3 colleges.

#### Branch

Placement rates were also relatively similar across the major branches.

#### Volunteer Experience

Volunteer experience showed very little difference in placement outcomes.

> These observations represent associations found in the dataset and should not be interpreted as proof of causation.

---

## ⚙️ Data Preprocessing

The dataset contained both numerical and categorical features.

### Categorical Features

- `gender`
- `branch`
- `college_tier`
- `volunteer_experience`

### Numerical Features

- `age`
- `cgpa`
- `internships_count`
- `projects_count`
- `certifications_count`
- `coding_skill_score`
- `aptitude_score`
- `communication_skill_score`
- `logical_reasoning_score`
- `hackathons_participated`
- `github_repos`
- `linkedin_connections`
- `mock_interview_score`
- `attendance_percentage`
- `backlogs`
- `extracurricular_score`
- `leadership_score`
- `sleep_hours`
- `study_hours_per_day`

### Preprocessing Steps

Numerical features were standardized using:

`StandardScaler`

Categorical features were encoded using:

`OneHotEncoder`

A `ColumnTransformer` was used to apply the appropriate preprocessing to each feature type.

---

## 🔀 Train-Test Split

The dataset was divided using an **80/20 stratified train-test split**.

- Training samples: **80,000**
- Testing samples: **20,000**

Stratification was used to preserve the original placement-status distribution in both training and testing datasets.

---

## 🤖 Machine Learning Models

Four classification algorithms were trained and evaluated:

### 1. Logistic Regression

Used as a strong and interpretable baseline classification model.

### 2. Random Forest

Used to capture non-linear relationships and interactions between features.

### 3. Support Vector Machine (SVM)

Used as another classification approach for comparison with the other models.

### 4. K-Nearest Neighbors (KNN)

Used as a distance-based classification model.

---

## 📈 Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix
- Classification Report

### Model Performance

| Model                   |   Accuracy |  Precision |     Recall |   F1 Score |
| ----------------------- | ---------: | ---------: | ---------: | ---------: |
| **Logistic Regression** | **57.00%** | **57.89%** |     77.24% | **66.18%** |
| Random Forest           |     55.26% |     57.08% |     71.96% |     63.66% |
| SVM                     |     56.96% |     57.85% | **77.31%** | **66.18%** |
| KNN                     |     52.12% |     55.62% |     59.72% |     57.60% |

---

## 🏆 Best Model

### Logistic Regression

Logistic Regression was selected as the final model.

It achieved:

- **Accuracy:** 57.00%
- **Precision:** 57.89%
- **Recall:** 77.24%
- **F1 Score:** 66.18%

SVM achieved a slightly higher recall of 77.31%, but the difference was very small.

Logistic Regression achieved the highest accuracy and essentially matched SVM in F1 score.

Therefore, Logistic Regression was selected as the final model for this project.

---

## 🧠 Feature Interpretation

The Logistic Regression coefficients were analyzed to understand which features had the strongest influence on model predictions.

### Strongest Features

| Feature               | Coefficient | Direction |
| --------------------- | ----------: | --------- |
| Backlogs              |      -0.173 | Negative  |
| Internships           |      +0.128 | Positive  |
| Projects              |      +0.126 | Positive  |
| Coding Skill          |      +0.106 | Positive  |
| Mock Interview Score  |      +0.094 | Positive  |
| Logical Reasoning     |      +0.074 | Positive  |
| Aptitude Score        |      +0.066 | Positive  |
| Communication Skill   |      +0.062 | Positive  |
| Leadership Score      |      +0.047 | Positive  |
| Extracurricular Score |      +0.041 | Positive  |

### Interpretation

The strongest negative coefficient was associated with:

**Backlogs**

This indicates that higher backlog values pushed the Logistic Regression model toward predicting a lower probability of placement.

The strongest positive coefficients included:

- Internships
- Projects
- Coding Skill
- Mock Interview Score
- Logical Reasoning
- Aptitude
- Communication Skills

These features pushed the model more strongly toward predicting placement.

> The coefficients represent relationships learned by the model. They do not establish causal relationships.

---

## 📊 Model Comparison

The comparison showed that:

- Logistic Regression achieved the highest accuracy.
- Logistic Regression and SVM achieved almost identical F1 scores.
- SVM achieved the highest recall by a very small margin.
- Random Forest performed below Logistic Regression and SVM.
- KNN achieved the lowest overall performance among the four models.

This demonstrates why evaluating multiple algorithms is important rather than selecting a model without comparison.

---

## 🛠️ Technologies Used

### Programming Language

- Python

### Data Analysis

- Pandas
- NumPy

### Visualization

- Matplotlib
- Seaborn

### Machine Learning

- Scikit-learn

### Development

- Jupyter Notebook
- VS Code

### Version Control

- Git
- GitHub

---

## 📁 Project Structure

```text
student-placement-prediction/
│
├── Student_Placement_Prediction.ipynb
├── student_placement_prediction_dataset_2026.csv
├── README.md
└── .gitignore
```

🚀 How to Run the Project

1. Clone the Repository
   git clone https://github.com/piyush31-sketch/student-placement-prediction.git
2. Enter the Project Directory
   cd student-placement-prediction
3. Install Dependencies
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
4. Launch Jupyter Notebook
   jupyter notebook
5. Open the Notebook

Open:

Student_Placement_Prediction.ipynb

Run the notebook cells in order.

⚠️ Limitations

The models achieved moderate predictive performance, with accuracy ranging from approximately 52% to 57%.

This indicates that the available features do not completely explain student placement outcomes.

Some categories with extreme values contained relatively few observations, so their placement percentages should be interpreted cautiously.

The dataset may also contain simplified relationships between variables, meaning performance on an independent real-world dataset could differ.

🔮 Future Improvements

Future versions of this project could include:

Hyperparameter tuning
K-fold cross-validation
Gradient Boosting
XGBoost
More advanced feature engineering
Feature interaction analysis
Probability calibration
Decision-threshold optimization
Class-weight optimization
Testing on independent real-world data
Model deployment using Streamlit
REST API deployment using Flask or FastAPI
Experiment tracking
Model monitoring
🎯 Conclusion

This project demonstrates a complete machine learning workflow for binary classification.

Starting from a dataset containing 100,000 student records, the project covered:

Data cleaning
Exploratory analysis
Preprocessing
Feature encoding
Feature scaling
Model training
Model evaluation
Model comparison
Model interpretation

Four machine learning models were compared:

Logistic Regression
Random Forest
SVM
KNN

Logistic Regression was selected as the final model based on its combination of accuracy and F1 score.

The feature analysis also showed that factors such as internships, projects, coding skills, mock interview performance, and backlogs had relatively strong relationships with the model's predictions.

Overall, this project demonstrates practical experience with the end-to-end machine learning development process using Python and Scikit-learn.
