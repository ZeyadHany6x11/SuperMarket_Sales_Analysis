# Superstore Sales Report System

This project analyzes Superstore sales data, prepares a cleaned dataset, builds a simple machine learning model to classify high-sales orders, and includes a Power BI dashboard for business reporting.

## Project Files

| File | Description |
| --- | --- |
| `SuperStore_Sales_Dataset.csv` | Raw Superstore sales dataset with 5,901 rows and 23 columns. |
| `cleaned_superstore .csv` | Cleaned and feature-engineered dataset with 5,901 rows and 25 columns. |
| `Sales_Report_System.ipynb` | Jupyter notebook for data cleaning, feature engineering, model training, and evaluation. |
| `Superstore Sales DashBoard.pbix` | Power BI dashboard for sales reporting and visualization. |

## Dataset Overview

The raw dataset contains order-level sales records with customer, product, region, shipping, return, payment, sales, quantity, and profit information.

Important fields include:

- `Order Date` and `Ship Date`
- `Ship Mode`
- `Customer Name` and `Segment`
- `Country`, `City`, `State`, and `Region`
- `Category`, `Sub-Category`, and `Product Name`
- `Sales`, `Quantity`, and `Profit`
- `Returns`
- `Payment Mode`

## Notebook Workflow

The notebook performs the following steps:

1. Imports analysis, visualization, and machine learning libraries.
2. Loads the raw dataset from `SuperStore_Sales_Dataset.csv`.
3. Explores the dataset using `head()`, `info()`, `describe()`, and missing-value checks.
4. Cleans the data by removing unnecessary columns and converting date fields.
5. Converts return information into a binary `Returned` feature.
6. Creates additional features:
   - `High Sales`
   - `Year`
   - `Month`
   - `Shipping Days`
   - `Sales Per Item`
7. Encodes categorical variables such as `Category` and `Region`.
8. Splits the data into training and testing sets.
9. Scales numeric features with `StandardScaler`.
10. Trains a Logistic Regression model.
11. Evaluates the model using:
    - Accuracy score
    - Classification report
    - Confusion matrix
    - ROC curve
    - Train/test accuracy comparison

## Machine Learning Goal

The machine learning task is binary classification. The notebook predicts whether an order belongs to the `High Sales` class.

`High Sales` is created by comparing each order's `Sales` value against the median sales value:

```python
df["High Sales"] = np.where(df["Sales"] > df["Sales"].median(), 1, 0)
```

## Requirements

Install the required Python libraries before running the notebook:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Power BI Desktop is required to open and edit the `.pbix` dashboard file.

## How to Run

1. Open the project folder.
2. Start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

3. Open `Sales_Report_System.ipynb`.
4. Run the cells from top to bottom.
5. Open `Superstore Sales DashBoard.pbix` in Power BI Desktop to view the dashboard.

## Notes

- The notebook reads the raw CSV file using Latin-1 encoding:

  ```python
  pd.read_csv("SuperStore_Sales_Dataset.csv", encoding="latin1")
  ```

- The cleaned CSV filename currently contains a space before `.csv`: `cleaned_superstore .csv`.
- The final notebook cell for exporting a cleaned CSV is commented out. If needed, uncomment it and adjust the filename:

  ```python
  df.to_csv("cleaned_superstore.csv", index=False)
  ```

## Project Purpose

This project is useful for practicing an end-to-end data-driven workflow:

- Data understanding
- Data cleaning
- Feature engineering
- Classification modeling
- Model evaluation
- Business dashboard reporting
