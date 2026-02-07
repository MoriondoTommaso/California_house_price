

# California Housing Price Prediction


The goal is to predict the **median house value** in Californian districts using data from the 1990 US Census.

## Dataset
The dataset used in this project is the **California Housing Prices** dataset.
You can download it directly from Kaggle here:
[California Housing Prices - Kaggle](https://www.kaggle.com/datasets/camnugent/california-housing-prices?resource=download)


## Project Workflow

### 1. Exploratory Data Analysis (EDA)

Deep dive into the dataset to understand variable relationships:

* **Geospatial Analysis:** Visualized housing prices and population density using **Plotly** and **Seaborn**, revealing that coastal proximity is a primary price driver.
* **Correlation Analysis:** Investigated the relationship between median income and house value.
* **Data Cleaning:** Identified and filtered out artificial price caps (e.g., houses capped at $500,001).

### 2. Feature Engineering

Created derived features to increase the model's predictive power:

* `rooms_per_household`: Average size of the house.
* `bedrooms_per_room`: Ratio of sleeping areas to living areas (proxy for luxury/space).
* `population_per_household`: Crowding index per housing unit.

### 3. Preprocessing Pipeline

Built a robust and reproducible pipeline using **Scikit-Learn**:

* **Train/Test Split:** 80/20 split to ensure valid evaluation.
* **Imputation:**
* *Numerical:* Filled missing values with the median.
* *Categorical:* Filled missing values with a constant ('unknown').


* **Encoding:** Applied One-Hot Encoding to the categorical feature `ocean_proximity`.
* **Scaling:** Applied `StandardScaler` to numerical features to ensure correct weighting in the linear model.

### 4. Modeling & Evaluation

* **Model:** Linear Regression.
* **Baseline:** Compared performance against a "Dummy Regressor" (predicting the mean of the training set).
* **Metrics:** Evaluated using RMSE (Root Mean Squared Error) and  Score.


## Key Results

The Linear Regression model significantly outperformed the baseline, validating the effectiveness of the engineered features and the preprocessing pipeline.

| Metric | Baseline (Mean Predictor) | Linear Regression Model |
| --- | --- | --- |
| **R^2 Score** | 0.00 | **0.62** |
| **RMSE** | ~$98,435 | **~$60,629** |

> **Insight:** The model explains approximately **62% of the variance** in housing prices. While a good start for a linear model, there is room for improvement using non-linear models (e.g., Random Forest or XGBoost).


## 🛠️ Tech Stack

* **Python 3.12.4**
* **Pandas & NumPy:** Data manipulation and vectorization.
* **Matplotlib, Seaborn, Plotly:** Static and interactive data visualization.
* **Scikit-Learn:** Machine Learning pipelines, preprocessing, and metrics.