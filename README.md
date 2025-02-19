Project Overview
This project aims to develop a machine learning model that accurately predicts whether a Near-Earth Object (NEO) is hazardous or not. The dataset is sourced from Kaggle:
🔗 NASA Nearest Earth Objects (1910-2024) Dataset

Dataset Description
The dataset contains information about asteroids, including their estimated size, velocity, distance from Earth, and classification as hazardous or not.

Key Features:
neo_id - Unique identifier for each asteroid
name - Name assigned by NASA
absolute_magnitude - Intrinsic luminosity of the asteroid
estimated_diameter_min - Minimum estimated size (km)
estimated_diameter_max - Maximum estimated size (km)
orbiting_body - Planet the asteroid orbits (Earth in this dataset)
relative_velocity - Speed relative to Earth (km/h)
miss_distance - Closest distance to Earth (km)
is_hazardous (Target) - Whether the asteroid is potentially hazardous (True or False)
Data Preprocessing & Cleaning
Handled missing values.
Converted categorical features.
Scaled numerical values.
Machine Learning Models Used
The notebook explores different classification models, including:

CatBoostClassifier
RandomForestClassifier
Support Vector Machine (SVM)
Logistic Regression
Dependencies
The project requires the following Python libraries:

bash
Copy
Edit
pip install catboost scikit-learn matplotlib pandas numpy seaborn
Results & Evaluation
The best-performing model was [Model Name], achieving an accuracy of [XX]%.
Performance metrics include accuracy, precision, recall, and F1-score.
Usage
To run the notebook:

Download the dataset from Kaggle.
Install dependencies.
Execute the Jupyter Notebook.
