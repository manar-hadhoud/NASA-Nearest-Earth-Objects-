# 🌍🚀 NASA | Nearest Earth Objects (1910-2024) - Classification Task  

## 📌 Project Overview  
This project aims to develop a **machine learning model** that accurately predicts whether a **Near-Earth Object (NEO)** is **hazardous or not**. The dataset is sourced from **Kaggle**:  

🔗 [**NASA Nearest Earth Objects (1910-2024) Dataset**](https://www.kaggle.com/datasets/ivansher/nasa-nearest-earth-objects-1910-2024/data)  

---

## 📊 Dataset Description  
The dataset contains information about asteroids, including their **estimated size, velocity, distance from Earth**, and classification as **hazardous or not**.

### 🔑 Key Features:
| Feature                    | Description |
|----------------------------|-------------|
| `neo_id`                   | Unique identifier for each asteroid |
| `name`                     | Name assigned by NASA |
| `absolute_magnitude`       | Intrinsic luminosity of the asteroid |
| `estimated_diameter_min`   | Minimum estimated size (km) |
| `estimated_diameter_max`   | Maximum estimated size (km) |
| `orbiting_body`            | Planet the asteroid orbits (Earth in this dataset) |
| `relative_velocity`        | Speed relative to Earth (km/h) |
| `miss_distance`            | Closest distance to Earth (km) |
| `is_hazardous` *(Target)*  | Whether the asteroid is potentially hazardous (`True` or `False`) |

---

## 🛠 Data Preprocessing & Cleaning  
✅ **Handled missing values**  
  📌 columns with missing values
  - absolute_magnitude        28
  - estimated_diameter_min    28
  - estimated_diameter_max    28
  📌 Little's MCAR Test (Statistical Test for MCAR)
  - the missingness is probably MAR (Missing at Random), meaning it depends on other observed data.
  📌 check percentage
  - since it is small percent of data , we will see its target vale count after and before drop and decide.
  decision:
  - Drop rows with any missing values inplace
✅ **Handled duplicates**
  - no duplicates
✅ **Exploratory Data Analysis (EDA)**
  - distriubutin for categorigal data ['orbiting_body', 'is_hazardous' , 'name']
  - The Chi-square test: is a statistical test used to determine if there is a significant association between two categorical variables.
        1️⃣ orbiting_body vs. is_hazardous
        
        - The Chi-square statistic is 0.0, meaning there is no variation in the distribution of is_hazardous across orbiting_body.
        - The p-value is 1.0, meaning there is no significant relationship between orbiting_body and is_hazardous.
        - This suggests that all objects in your dataset orbit Earth, so orbiting_body is not a useful feature for predicting hazard status.
        
        2️⃣ name vs. is_hazardous
        
        - The Chi-square statistic is extremely high (338,171.0), indicating a very strong association.
        - The p-value is 0.0, meaning the relationship is highly significant.
  - distriubutin for Numerical columns. ['absolute_magnitude', 'estimated_diameter_min', 'estimated_diameter_max', 'relative_velocity', 'miss_distance']
✅ **Converted categorical features**  "skipped for no categorical data"
✅ **feature selection**   "drop one of coorlated columns drop low related columns with target."
✅ **Detecting Outliers**
  - (A) Using Box Plot
  - (B) Using Z-Score
  - (C) Using IQR (Interquartile Range)

        1- Relative Velocity:
        Shows extreme right-skewness (high values far from the main distribution).
        Several high outliers beyond Q3, suggesting a long-tailed distribution.
        
        2- Estimated Diameter Max:
        Some significant outliers on the upper end.
        The main data distribution is concentrated within a smaller range.
        
        3- Absolute Magnitude:
        Fewer outliers compared to the other features.
        Mostly a well-behaved distribution, with a few extreme values.

        Percentage of outliers in neo_id: 0.00%
        - Percentage of outliers in absolute_magnitude: 0.12%
        - Percentage of outliers in estimated_diameter_max: 7.74%
        - Percentage of outliers in relative_velocity: 1.61%
    
✅ **Train-Test spliting**  
✅ **Data Scaling**  
✅ **Data balancing**  
  📌 Oversampling (Increase Minority Class)
  📌 Undersampling (Reduce Majority Class)
  📌 Class Weighting (Alternative)
 

---

## 🤖 Machine Learning Models Used  
The notebook explores different **classification models**, including:

## 1️⃣ Linear Models  
These models assume a linear relationship between input features and the target variable.  

| Model | Description |
|-----------------------------|------------------------------------------------------|
| **Logistic Regression** | Models probability using a logistic function. |
| **Linear Discriminant Analysis (LDA)** | Projects data onto a new axis to maximize class separation. |
| **Quadratic Discriminant Analysis (QDA)** | Extends LDA by allowing different covariance matrices for each class. |


# 2️⃣ Distance-Based Models

| Model | Description |
|-----------------------------|------------------------------------------------------|
| **K-Nearest Neighbors (KNN)** | Assigns class labels based on the nearest neighbors. |


# 3️⃣ Tree-Based Models

| Model | Description |
|-----------------------------|------------------------------------------------------|
| **Decision Tree** | Splits data into hierarchical decision rules. |
| **Random Forest** | An ensemble of decision trees to improve accuracy. |
| **Extra Trees** | Uses more randomness for better generalization. |
| **Gradient Boosting** | Sequentially improves weak learners. |
| **AdaBoost** | Assigns higher weight to misclassified samples. |
| **Bagging Classifier** | Uses bootstrapping to reduce variance. |
| **XGBoost** | Optimized gradient boosting framework. |
| **LightGBM** | Faster and more efficient gradient boosting. |
| **CatBoost** | Gradient boosting with categorical feature support. |

# 4️⃣ Support Vector Machines

| Model | Description |
|-----------------------------|------------------------------------------------------|
| **Support Vector Classifier (SVC)** | Maximizes margin between different classes. |


# 5️⃣ Neural Networks

| Model | Description |
|-----------------------------|------------------------------------------------------|
| **Multi-layer Perceptron (MLP)** | A feedforward neural network with hidden layers. |

# 6️⃣ Probabilistic & Bayesian Models

| Model | Description |
|-----------------------------|------------------------------------------------------|
| **Gaussian Naive Bayes** | Assumes Gaussian distribution for continuous features. |
| **Multinomial Naive Bayes** | Best for text classification & count data. |
| **Bernoulli Naive Bayes** | Works well with binary features. |
| **Complement Naive Bayes** | Adjusted for imbalanced datasets. |
| **Categorical Naive Bayes** | Handles categorical features. |
| **Gaussian Process Classifier** | Provides probabilistic classification. |

---
# Model Evaluation:
  # 1️⃣ trials before balancing
    
  | Model            | Accuracy | Precision | Recall | F1-score | ROC AUC Score |
  |-----------------|----------|-----------|--------|----------|--------------|
  | Decision Tree   | 0.8898   | 0.5667    | 0.5822 | 0.5743   | 0.7585       |
  | Random Forest  | 0.9171   | 0.7113    | 0.5894 | 0.6446   | 0.9490       |
  | Extra Trees    | 0.9198   | 0.7151    | 0.6183 | 0.6632   | 0.9512       |
  | Gradient Boosting | 0.8856 | 0.7306    | 0.1646 | 0.2687   | 0.8944       |
  | AdaBoost       | 0.8840   | 0.7053    | 0.1564 | 0.2560   | 0.8691       |
  | Bagging        | 0.9061   | 0.6858    | 0.4880 | 0.5702   | 0.9164       |
  | XGBoost        | 0.8943   | 0.7124    | 0.2889 | 0.4111   | 0.9146       |
  | CatBoost       | 0.8932   | 0.7032    | 0.2764 | 0.3964   | 0.9123       |

  ## Observations 📌

- 🌳 **Decision Tree:** Overfits the data, leading to lower ROC AUC.
- 🌲 **Random Forest:** Performs well with high ROC AUC and balanced precision-recall.
- 🌿 **Extra Trees:** Slightly better than Random Forest due to feature randomness.
- 🚀 **Gradient Boosting:** High precision but poor recall, indicating class imbalance.
- ⚡ **AdaBoost:** Similar to Gradient Boosting but struggles with recall.
- 🏗️ **Bagging:** Good performance with moderate recall and precision.
- 🔥 **XGBoost:** Balanced performance but recall is lower than expected.
- 🐱 **CatBoost:** Performs similarly to XGBoost but with slight improvements in some metrics.

  # 2️⃣ trials after balancing
  - bad performance detected after balancing in the three ways so it is obvious that models perform better for both classes without balancing

-----

## 📦 Next steps  
- Exploring deep learning approaches for improved accuracy
- Conducting further analysis to identify additional hidden patterns
- Trying other models to compare performance
- Hyperparameter tuning: Fine-tune Extra Trees and Random Forest models to enhance performance further

-----

## 📦 Dependencies  

Ensure you have the following Python libraries installed:  

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn xgboost lightgbm catboost missingno

