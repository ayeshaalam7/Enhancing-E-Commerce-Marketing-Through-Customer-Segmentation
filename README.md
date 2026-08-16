# Enhancing E-Commerce Marketing Through Customer Segmentation

A big-data analytics project for **customer segmentation and personalized product recommendation** using transactional e-commerce data.

The project applies:

* **Locality Sensitive Hashing (LSH)** for finding similar customers.
* **Item-item collaborative filtering** using cosine similarity for product recommendations.
* **PySpark ALS** for collaborative filtering and recommendation generation.

## Dataset

The project uses the **Online Retail** dataset from the UCI Machine Learning Repository. It contains transaction-level information from a UK-based online retailer, including invoice, product, quantity, date, price, customer, country, and sales information.

The dataset is used to analyze **customer purchasing behavior and product transactions** for customer similarity and personalized recommendations.

**Original source:** [UCI Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail)

The dataset was locally renamed for the project and used as `superstoredata` in the notebooks.

## Project Workflow

```text
Online Retail transactions
        ↓
Data loading \& inspection
        ↓
Data cleaning \& preprocessing
        ↓
Exploratory data analysis
        ↓
Sales / country / product analysis
        ↓
Customer similarity using LSH
        ↓
Customer–item interaction matrix
        ↓
Item similarity using cosine similarity
        ↓
Product recommendations
        ↓
PySpark ALS recommendations
```

## 1\. Data Preprocessing

The project:

* loads the transaction dataset,
* converts `InvoiceDate` to datetime,
* handles missing `Description` values,
* removes rows with missing `CustomerID`,
* removes negative `Quantity` values,
* removes rows with zero `UnitPrice`.

## 2\. Exploratory Data Analysis

The notebooks analyze:

* dataset structure and statistics,
* missing values,
* correlations,
* transactions by country,
* monthly/yearly sales,
* top products by frequency, volume and sales,
* product trends over time.

## 3\. Customer Segmentation with LSH

Locality Sensitive Hashing is used to identify similar customers based on:

* `Quantity`
* `UnitPrice`
* `CustomerID`
* `Sales`

The LSH Forest query is used to find **5 nearest neighbors** for each customer.

## 4\. Collaborative Filtering

A customer-item interaction matrix is created using:

* `CustomerID`
* `StockCode`
* `Quantity`

Cosine similarity is then used to calculate similarity between products.

The project also uses item popularity to provide recommendations for a new user.

## 5\. PySpark ALS

The project includes a separate PySpark implementation covering preprocessing/filtering and collaborative filtering with **Alternating Least Squares (ALS)**.

The Spark workflow includes:

* loading the data with Spark,
* preprocessing and filtering,
* preparing customer/item/rating data,
* train/test splitting,
* ALS model training,
* RMSE evaluation,
* top-10 recommendations,
* recommendations for an individual customer.

## Repository Structure

```text
ecommerce-big-data-customer-segmentation/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── raw/
│       └── superstoredata.xlsx
│
├── notebooks/
│   ├── Project\_Big\_Data.ipynb
│   └── Big\_Data\_Project\_Spark.ipynb
│
└── docs/
    └── README.md
```

## Requirements

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
mlxtend
datasketch
pyspark
openpyxl
jupyter
```

Install with:

```bash
pip install -r requirements.txt
```

## Running the Project

Open the notebooks in Jupyter:

```text
notebooks/Project\_Big\_Data.ipynb
notebooks/Big\_Data\_Project\_Spark.ipynb
```

## 

