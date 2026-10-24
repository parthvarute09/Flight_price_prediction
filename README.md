# ✈️ Flight Price Prediction

A machine learning project that estimates flight ticket prices using historical flight details. The project covers exploratory data analysis, data cleaning, feature engineering, categorical encoding, feature selection, regression modelling, evaluation, and hyperparameter tuning.

## 📌 Project Overview

Flight prices can vary depending on the airline, route, journey date, departure and arrival times, number of stops, and flight duration. This project explores these factors and trains regression models to estimate ticket prices.

The main implementation is provided in the Jupyter notebook: `flight_prediction.ipynb`.

## 🎯 Objectives

- Explore and understand flight ticket data.
- Clean missing values and prepare features for modelling.
- Extract useful date, time, and duration features.
- Encode categorical columns into numeric representations.
- Examine outliers and select informative features.
- Train regression models and evaluate their predictions.
- Tune a Random Forest model using cross-validation.
- Save a trained model with Python's `pickle` module for later use.

## 📂 Dataset

The project uses two Excel files:

- `Data_Train.xlsx` — training data, including the target column `Price`.
- `Test_set.xlsx` — test/input data for which prices may need to be predicted.

The notebook works with fields such as:

| Feature | Description |
|---|---|
| `Airline` | Airline operating the flight |
| `Date_of_Journey` | Date of the journey |
| `Source` | Departure city |
| `Destination` | Arrival city |
| `Route` | Flight route information |
| `Dep_Time` | Departure time |
| `Arrival_Time` | Arrival time |
| `Duration` | Total flight duration |
| `Total_Stops` | Number of stops |
| `Additional_Info` | Additional flight information |
| `Price` | Ticket price; target variable in the training data |

The exact columns should be checked against the supplied Excel files before running the notebook.

## 🧰 Technologies Used

- **Python**
- **Jupyter Notebook**
- **Pandas** and **NumPy** — data loading and manipulation
- **Matplotlib** and **Seaborn** — visualization and exploratory data analysis
- **Scikit-learn** — feature selection, model training, evaluation, and hyperparameter search
- **Pickle** — model serialization

## 🔄 Workflow

1. **Load the data** from Excel files using Pandas.
2. **Handle missing values** and clean the dataset.
3. **Feature engineering**
   - Extract day, month, and year from `Date_of_Journey`.
   - Extract hour and minute from departure and arrival times.
   - Convert `Duration` into numeric hour/minute features.
4. **Exploratory data analysis**
   - Investigate flight timing and duration.
   - Compare prices across airlines and other flight characteristics.
   - Use plots to inspect distributions and potential outliers.
5. **Encode categorical features**
   - Apply one-hot encoding and target-guided mean encoding where appropriate.
   - Convert stop information into numeric values.
6. **Feature preparation**
   - Remove redundant columns where appropriate.
   - Inspect outliers and use `mutual_info_regression` for feature importance.
7. **Train regression models**
   - Train a `RandomForestRegressor`.
   - Compare with a `DecisionTreeRegressor`.
8. **Evaluate predictions** with R², MAE, MSE, RMSE, and MAPE.
9. **Tune hyperparameters** using `RandomizedSearchCV` with cross-validation.
10. **Save and reload the model** using `pickle`.

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/parthvarute09/Flight_price_prediction.git
cd Flight_price_prediction
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv .venv
```

Activate it:

**Windows**
```bash
.venv\Scripts\activate
```

**macOS / Linux**
```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

### 4. Place the dataset files

Keep `Data_Train.xlsx` and `Test_set.xlsx` in the project directory, or update the file paths in the notebook to match where you saved them.

### 5. Run the notebook

```bash
jupyter notebook flight_prediction_shan_singh.ipynb
```

Run the cells from top to bottom. The notebook currently contains a machine-specific Windows path in its Excel-loading and model-saving examples (under `Z:\Flight_Price\Datasets\`). Replace those paths with paths that exist on your computer before running those cells.

## 📊 Model Evaluation

The notebook evaluates regression predictions using:

- **R² score** — proportion of target variance explained by the model.
- **MAE (Mean Absolute Error)** — average absolute prediction error.
- **MSE (Mean Squared Error)** — average squared prediction error.
- **RMSE (Root Mean Squared Error)** — square root of MSE, expressed in the target's units.
- **MAPE (Mean Absolute Percentage Error)** — average absolute percentage error.

The notebook includes a baseline Random Forest model and a Decision Tree comparison, followed by a `RandomizedSearchCV` workflow for hyperparameter tuning. Actual performance values depend on the data split, preprocessing, and environment; no fixed accuracy score is claimed here.

## 💾 Saving the Model

The notebook demonstrates saving and loading a fitted model with `pickle`. For example:

```python
import pickle

with open("rf_random.pkl", "wb") as file:
    pickle.dump(ml_model, file)

with open("rf_random.pkl", "rb") as file:
    loaded_model = pickle.load(file)
```

**Important:** A saved estimator alone is not enough if predictions require the same preprocessing and feature-column order used during training. Apply the identical transformations to new data before calling `predict()`.

Only load pickle files from trusted sources, because unpickling can execute arbitrary code.

## 📁 Project Files

```text
Flight_price_prediction/
├── Data_Train.xlsx
├── Test_set.xlsx
├── flight_prediction_shan_singh.ipynb
└── README.md
```

The dataset files and notebook may be stored in different folders in the GitHub repository; adjust this outline to match the actual repository layout.

## 🔮 Future Improvements

- Build a single reusable preprocessing-and-model pipeline.
- Ensure preprocessing is fitted only on training data to prevent data leakage.
- Evaluate models using a fixed train/test split or cross-validation.
- Compare additional regression algorithms and report measured results.
- Add a simple web interface or API for price estimates.
- Add a `requirements.txt` file and make all data/model paths relative.

## 🤝 Contributing

Suggestions and improvements are welcome. Fork the repository, create a feature branch, make your changes, and open a pull request.


---

**Author:** [parthvarute09](https://github.com/parthvarute09)

