Here is a more complete and professional version of the README in English, incorporating code snippets and details from your project:

---

# Cardiovascular Disease Prediction

This project focuses on building a machine learning pipeline to predict the risk of cardiovascular diseases (CVD) using various classification algorithms. The goal is to improve the accuracy of early diagnosis and assist medical professionals in identifying at-risk patients more effectively.

## Overview

The project is built on a dataset with various patient medical attributes, such as blood pressure, cholesterol levels, and physical activity, sourced from the Kaggle platform. We apply robust data preprocessing techniques, exploratory data analysis (EDA), feature engineering, and various machine learning models to predict the presence of cardiovascular disease. The project follows the **CRISP-DM** methodology to ensure an iterative and structured approach.

<p align="center">
  <img src="https://github.com/LuisNagano/cardiovascular_disease_prediction/blob/main/coracao-de-atleta-868.jpg" width="50%" alt="Cardiovascular System" />
</p>

---

## Dataset Information

This dataset contains patient data with various medical features:

### Features:
- **Age**: in days
- **Height**: in cm
- **Weight**: in kg
- **Gender**: categorical (1: female, 2: male)
- **Systolic blood pressure**: integer
- **Diastolic blood pressure**: integer
- **Cholesterol levels**: 1 (normal), 2 (above normal), 3 (well above normal)
- **Glucose levels**: 1 (normal), 2 (above normal), 3 (well above normal)
- **Smoking**: binary (0: no, 1: yes)
- **Alcohol intake**: binary (0: no, 1: yes)
- **Physical activity**: binary (0: no, 1: yes)
- **Target (cardio)**: binary (0: no cardiovascular disease, 1: cardiovascular disease)

---

## Project Pipeline

The workflow is broken down into several key stages:

### 1. **Data Preprocessing and Feature Engineering**

- **Data Cleaning**: Removing outliers and handling missing values.
- **Feature Engineering**: Creating new features like Body Mass Index (BMI) and life stages based on age.
  
    ```python
    def calcBMI(weight, height):
        return np.round(weight / (height/100)**2, 1)
    
    def getLifeStage(age):
        if age <= 20:
            return 'Youth'
        elif age <= 60:
            return 'Adult'
        else:
            return 'Senior'
    ```
  
- **Categorical Encoding**: One-hot encoding for categorical variables such as `gender`, `smoking`, and `cholesterol`.

    ```python
    df = pd.get_dummies(df, columns=['gender', 'smoking', 'alcohol'], drop_first=True)
    ```

### 2. **Exploratory Data Analysis (EDA)**

- **Correlation Analysis**: Heatmaps and correlation matrices are used to understand the relationships between variables.
  
    ```python
    sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
    ```

- **Distribution Plots**: Visualizing the distribution of key variables like `age`, `cholesterol`, and `blood pressure`.

    ```python
    sns.histplot(df['age_years'], kde=True)
    ```

### 3. **Machine Learning Models**

Several models were trained to predict cardiovascular disease, including:

- **Logistic Regression**
  
    ```python
    from sklearn.linear_model import LogisticRegression
    model = LogisticRegression()
    model.fit(X_train, y_train)
    ```

- **K-Nearest Neighbors (KNN)**

    ```python
    from sklearn.neighbors import KNeighborsClassifier
    knn = KNeighborsClassifier(n_neighbors=5)
    knn.fit(X_train, y_train)
    ```

- **Random Forest**
  
    ```python
    from sklearn.ensemble import RandomForestClassifier
    rf = RandomForestClassifier()
    rf.fit(X_train, y_train)
    ```

- **XGBoost**
  
    ```python
    from xgboost import XGBClassifier
    xgb = XGBClassifier()
    xgb.fit(X_train, y_train)
    ```

### 4. **Model Evaluation**

Each model's performance was evaluated using the following metrics:
- **Accuracy**
- **Precision**
- **Recall**
- **F1 Score**

    ```python
    from sklearn.metrics import classification_report
    y_pred = model.predict(X_test)
    print(classification_report(y_test, y_pred))
    ```

#### Cross-Validation

A 5-fold cross-validation approach was used to ensure robust model performance.

    ```python
    from sklearn.model_selection import cross_val_score
    scores = cross_val_score(model, X, y, cv=5, scoring='accuracy')
    print("Cross-validation accuracy: ", scores.mean())
    ```

### 5. **Hyperparameter Tuning**

Hyperparameter optimization was performed using RandomizedSearchCV for the XGBoost model to fine-tune key parameters like learning rate and number of estimators.

    ```python
    from sklearn.model_selection import RandomizedSearchCV
    
    param_grid = {
        'learning_rate': [0.01, 0.1, 0.2],
        'n_estimators': [100, 200, 500],
        'subsample': [0.8, 0.9, 1.0]
    }
    
    search = RandomizedSearchCV(xgb, param_grid, n_iter=10, cv=3, verbose=1)
    search.fit(X_train, y_train)
    ```

### 6. **Model Deployment**

The final model was serialized using `joblib` for deployment in a production environment.

    ```python
    from joblib import dump
    dump(final_model, 'cardio_model.joblib')
    ```

---

## Results and Business Insights

### Model Performance
The best-performing model was the **XGBoost Classifier**, achieving:

- **Accuracy**: 71.8%
- **Precision**: 73.4%
- **Recall**: 67.3%
- **F1 Score**: 70.2%

### Business Impact

The model's high precision and recall rates provide reliable cardiovascular disease predictions, reducing diagnostic errors and allowing for early interventions. The model can generate significant cost savings for medical facilities by automating the diagnostic process and improving efficiency.

### Profit Estimation

Using the model’s predictions, the business could potentially save **R$ 11,285,500** based on improved diagnostic accuracy, as calculated in the notebook.

---

## Conclusion

The project successfully developed and deployed a model capable of predicting cardiovascular disease with a high level of accuracy. Future work could include additional feature engineering, using more advanced models such as deep learning, or incorporating real-time data pipelines for live diagnostics.

---

## How to Run the Project

1. **Clone the repository**:
    ```bash
    git clone https://github.com/LuisNagano/cardiovascular_disease_prediction.git
    ```
   
2. **Install the required dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

3. **Run the Jupyter notebook** for step-by-step analysis:
    ```bash
    jupyter notebook
    ```

4. **Train the models**:
    ```python
    python train_model.py
    ```

5. **Test the API** (optional):
    Deploy the trained model using a REST API and make predictions by sending POST requests.

    ```bash
    curl -X POST -H "Content-Type: application/json" -d @data.json http://localhost:5000/predict
    ```

---

## References

- [Kaggle: Cardiovascular Disease Dataset](#)
- [Be a Data Scientist](#)
- [CRISP-DM Methodology](#)
