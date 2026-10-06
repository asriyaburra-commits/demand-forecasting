# Demand Forecasting Prototype

## About the Project

This project is about predicting future product sales using historical sales data.

I used sales data containing information about the date, store, item and number of sales.

The main idea of the project is to use previous sales patterns to predict future demand. This type of prediction can be useful for planning inventory and understanding how much stock may be needed.

This project was completed as part of the **Arrowstack Machine Learning Internship**.

## Objective

The main things I worked on in this project were:

* Understanding the sales data.
* Checking sales patterns over time.
* Preparing the data for forecasting.
* Creating date-based features.
* Creating lag features.
* Creating rolling features.
* Splitting the data based on time.
* Creating a simple baseline.
* Training a forecasting model.
* Comparing the model with the baseline.
* Evaluating the predictions using MAE and RMSE.
* Checking prediction errors.
* Saving the final model and results.

## Dataset

I used a store-item sales dataset.

The main columns are:

```text
date
store
item
sales
```

The `sales` column is the value that I am trying to predict.

The `date` column is important because this is a time-series problem. The data needs to be arranged in the correct time order before creating the forecasting features.

## Project Structure

```text
Project_3_Demand_Forecasting/
│
├── data/
│   ├── train.csv
│   └── test.csv
│
├── notebooks/
│   └── demand_forecasting.ipynb
│
├── models/
│   └── demand_forecasting_model.pkl
│
├── results/
│   ├── forecasting_results.csv
│   └── actual_vs_predicted.png
│
├── src/
│
├── README.md
├── model_card.md
└── requirements.txt
```

## Data Preparation

I first converted the `date` column into datetime format.

Then I sorted the data using:

```text
store
item
date
```

This was important because the model should use past sales to predict future sales.

I also checked the data for missing values and other issues before creating the new features.

## Exploratory Data Analysis

I looked at the sales data to understand how demand changes over time.

Some of the things I checked were:

* Sales over time.
* Sales for different stores.
* Sales for different items.
* Monthly sales patterns.
* Weekly sales patterns.

I used Matplotlib and Seaborn to create the visualizations.

## Feature Engineering

I created some features from the date column.

These include:

```text
year
month
day
day_of_week
week_of_year
```

I also created lag features.

For example:

```text
lag_1  → previous day's sales
lag_7  → sales from 7 days before
lag_30 → sales from 30 days before
```

I also created rolling features using previous sales values:

```text
rolling_7
rolling_30
```

These features help the model understand recent sales patterns.

I made sure that future sales values were not used when creating these features.

## Train and Validation Data

Since this is a time-series project, I did not randomly shuffle the data for the train and validation split.

I used the earlier dates for training and the later dates for validation.

The last part of the historical data was kept for validation.

This makes the validation setup closer to the actual situation where we use past data to predict future sales.

## Baseline

I created a simple baseline using the previous day's sales.

This uses:

```text
lag_1
```

The baseline gives me a simple result to compare with the machine learning model.

The final model should perform better than this baseline to show that the additional features and model are actually useful.

## Model Used

I used a **Random Forest Regressor** for this project.

The model uses the date, lag and rolling features to predict sales.

I trained the model using the training period and then checked its performance on the later validation period.

## Model Evaluation

I used two metrics to evaluate the predictions.

### MAE

MAE stands for Mean Absolute Error.

It tells me the average difference between the actual sales and predicted sales.

### RMSE

RMSE stands for Root Mean Squared Error.

It gives more importance to larger prediction errors.

I used both MAE and RMSE to compare the baseline and the Random Forest model.

## Error Analysis

After making the predictions, I compared the predicted sales with the actual sales.

I also created an actual-vs-predicted graph to see how closely the model predictions follow the actual sales.

Large differences between the actual and predicted values were considered while checking the model performance.

## Results

The final forecasting results are saved in:

```text
results/forecasting_results.csv
```

The actual-vs-predicted graph is saved in:

```text
results/actual_vs_predicted.png
```

The notebook contains the complete analysis, feature engineering, model training and evaluation.

## Saved Model

The trained model is saved here:

```text
models/demand_forecasting_model.pkl
```

I used Joblib to save the model so that it can be loaded later without training it again.

## Model Card

The `model_card.md` file contains information about:

* Purpose of the model.
* Dataset used.
* Features used.
* Model used.
* Evaluation results.
* Limitations.
* Possible improvements.

## Limitations

There are some limitations to this project.

* Future sales may not always follow the same pattern as historical sales.
* Unexpected events can change demand.
* Promotions and holidays can affect sales.
* Weather and other external factors may also affect demand.
* The model is mainly based on the information available in the dataset.
* The model should be checked regularly when new sales data becomes available.

## Future Improvements

Some improvements that can be added later are:

* Try other forecasting models.
* Try statistical forecasting methods.
* Compare different models and forecasting methods.
* Add holiday information.
* Add promotional information if available.
* Perform hyperparameter tuning.
* Try different forecasting periods.
* Monitor forecasting errors over time.
* Build a dashboard for inventory planning.
* Deploy the model using an API.

## How to Run

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

### 2. Open the project folder

```bash
cd Project_3_Demand_Forecasting
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the environment

For Windows:

```bash
venv\Scripts\activate
```

### 5. Install the packages

```bash
pip install -r requirements.txt
```

### 6. Open the notebook

```text
notebooks/demand_forecasting.ipynb
```

Run the notebook cells from beginning to end.

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Joblib
* Jupyter Notebook

## Project Status

**Completed**

**Project:** Demand Forecasting Prototype

**Internship:** Arrowstack Machine Learning Internship
