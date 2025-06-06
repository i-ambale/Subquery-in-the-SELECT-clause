# 📊 Subqueries in the SELECT Clause – SQL Practice
This project demonstrates how to use subqueries in the `SELECT` clause to perform advanced calculations using SQL. It is designed to run locally alongside a MySQL server and the `united_nations` database created in MySQL Workbench.

| ⚠️ **Note**: This notebook does not run on Google Colab, as it requires a connection to a local MySQL server instance.

## 🧠 Learning Objectives
In this notebook, you'll learn:

  - ✅ How to use subqueries in the SELECT clause instead of static values to make calculations dynamic.
  
  - ✅ How to write correlated subqueries to calculate results based on row-level or group-level context.
  
  - ✅ How to calculate a country’s land area as a percentage of the total land area of its sub-region.
    
## 🗂️ Data Overview
We use the `Geographic_location` table from the `united_nations` database.

### Sample Use Case:
| Calculate what percentage of land area each country occupies in the sub-region of **Middle Africa**.

This involves:

  - A main query that lists each country.
  
  - A subquery in the SELECT clause that sums land areas for the sub-region.
  
  - An optional correlated subquery for row-level comparisons.

## ⚙️ Requirements
- MySQL Server (preferably 8.x)

- MySQL Workbench

- Jupyter Notebook (running locally, not in Colab)

- Python packages:

  - `mysql-connector-python` or `SQLAlchemy`
  
  - `pandas`

Install dependencies using pip:
```
pip install mysql-connector-python pandas
```
## 🏗️ Setup Instructions
1. Clone this repository:
```
git clone https://github.com/your-username/sql-subquery-select-clause.git
cd sql-subquery-select-clause
```

2. Ensure the MySQL server is running and the `united_nations` database is available.

3. Update the database connection parameters in the notebook:
```
connection = mysql.connector.connect(
    host="localhost",
    user="your_username",
    password="your_password",
    database="united_nations"
)
```

4. Launch the notebook locally using Jupyter:
```
jupyter notebook
```

5. Open the notebook and run through the cells step by step.

📈 Example Query
```
SELECT 
    country_name,
    land_area,
    (land_area / (
        SELECT SUM(land_area)
        FROM Geographic_location
        WHERE subregion = 'Middle Africa'
    )) * 100 AS percent_of_subregion
FROM Geographic_location
WHERE subregion = 'Middle Africa';
```

## 🧩 Extensions
- Adapt the subquery to support multiple sub-regions using correlated subqueries.

- Visualize the results using Python libraries such as matplotlib or seaborn.

- Compare land area proportions over time (if temporal data is included).

## 📜 License
This project is licensed under the MIT License.

## 🙌 Acknowledgements
Inspired by real-world data analysis use cases and powered by the `united_nations` database schema.

