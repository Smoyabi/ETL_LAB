# DSA 2040A Load Phase — ETL Project

## Overview
This project demonstrates the **Load Phase** of the ETL (Extract, Transform, Load) pipeline.  
The focus is to load previously transformed datasets into a **SQLite** database and verify the successful load process.

---

## Objectives
- Load transformed datasets into a SQLite database.
- Verify data integrity by reading a sample of records.
- Maintain a clean, professional, and well-documented GitHub repository.

---

## Folder Structure
ETL_Lab/
etl_lab/
├── transformed/
│ ├── transformed_full.csv
│ └── transformed_incremental.csv
│
├── loaded/
│ ├── full_data.db
│ ├── incremental_data.db
│ ├── full_data.parquet
│ └── incremental_data.parquet
│
├── etl_load.ipynb
├── README.md


---

## Tools and Libraries
- **Python 3.13**
- **pandas** — for data loading and inspection  
- **sqlite3** — built-in Python library for SQLite database management
---

## Load Implementation Summary

### SQLite Loading
The transformed CSV files were read using pandas and stored into SQLite databases using:
pandas & sqlite3 

Output: Displayed the top 5 records, confirming that data, columns, and data types were loaded successfully.

Full Data from SQLite:
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>invoice_no</th>
      <th>stock_code</th>
      <th>description</th>
      <th>quantity</th>
      <th>invoice_date</th>
      <th>unit_price</th>
      <th>customer_id</th>
      <th>country</th>
      <th>total_cost</th>
      <th>order_week</th>
      <th>order_day</th>
      <th>product_name</th>
      <th>product_detail</th>
      <th>sales_bracket</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>536365</td>
      <td>85123A</td>
      <td>WHITE HANGING HEART T-LIGHT HOLDER</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>2.55</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
      <td>15.30</td>
      <td>48</td>
      <td>2010-12-01</td>
      <td>WHITE HANGING HEART T-LIGHT HOLDER</td>
      <td>None</td>
      <td>Very Low</td>
    </tr>
    <tr>
      <th>1</th>
      <td>536365</td>
      <td>71053</td>
      <td>WHITE METAL LANTERN</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
      <td>20.34</td>
      <td>48</td>
      <td>2010-12-01</td>
      <td>WHITE METAL LANTERN</td>
      <td>None</td>
      <td>Low</td>
    </tr>
    <tr>
      <th>2</th>
      <td>536365</td>
      <td>84406B</td>
      <td>CREAM CUPID HEARTS COAT HANGER</td>
      <td>8</td>
      <td>2010-12-01 08:26:00</td>
      <td>2.75</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
      <td>22.00</td>
      <td>48</td>
      <td>2010-12-01</td>
      <td>CREAM CUPID HEARTS COAT HANGER</td>
      <td>None</td>
      <td>Low</td>
    </tr>
    <tr>
      <th>3</th>
      <td>536365</td>
      <td>84029G</td>
      <td>KNITTED UNION FLAG HOT WATER BOTTLE</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
      <td>20.34</td>
      <td>48</td>
      <td>2010-12-01</td>
      <td>KNITTED UNION FLAG HOT WATER BOTTLE</td>
      <td>None</td>
      <td>Low</td>
    </tr>
    <tr>
      <th>4</th>
      <td>536365</td>
      <td>84029E</td>
      <td>RED WOOLLY HOTTIE WHITE HEART.</td>
      <td>6</td>
      <td>2010-12-01 08:26:00</td>
      <td>3.39</td>
      <td>17850.0</td>
      <td>United Kingdom</td>
      <td>20.34</td>
      <td>48</td>
      <td>2010-12-01</td>
      <td>RED WOOLLY HOTTIE WHITE HEART.</td>
      <td>None</td>
      <td>Low</td>
    </tr>
  </tbody>
</table>
</div>

Incremental Data from SQLite:
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>invoice_no</th>
      <th>stock_code</th>
      <th>description</th>
      <th>quantity</th>
      <th>invoice_date</th>
      <th>unit_price</th>
      <th>customer_id</th>
      <th>country</th>
      <th>total_cost</th>
      <th>order_week</th>
      <th>order_day</th>
      <th>product_name</th>
      <th>product_detail</th>
      <th>sales_bracket</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>575317</td>
      <td>23544</td>
      <td>WALL ART MID CENTURY MODERN</td>
      <td>2</td>
      <td>2011-11-09 13:12:00</td>
      <td>8.25</td>
      <td>17402.0</td>
      <td>United Kingdom</td>
      <td>16.50</td>
      <td>45</td>
      <td>2011-11-09</td>
      <td>WALL ART MID CENTURY MODERN</td>
      <td>None</td>
      <td>Very Low</td>
    </tr>
    <tr>
      <th>1</th>
      <td>575317</td>
      <td>21790</td>
      <td>VINTAGE SNAP CARDS</td>
      <td>12</td>
      <td>2011-11-09 13:12:00</td>
      <td>0.85</td>
      <td>17402.0</td>
      <td>United Kingdom</td>
      <td>10.20</td>
      <td>45</td>
      <td>2011-11-09</td>
      <td>VINTAGE SNAP CARDS</td>
      <td>None</td>
      <td>Very Low</td>
    </tr>
    <tr>
      <th>2</th>
      <td>575317</td>
      <td>21791</td>
      <td>VINTAGE HEADS AND TAILS CARD GAME</td>
      <td>12</td>
      <td>2011-11-09 13:12:00</td>
      <td>1.25</td>
      <td>17402.0</td>
      <td>United Kingdom</td>
      <td>15.00</td>
      <td>45</td>
      <td>2011-11-09</td>
      <td>VINTAGE HEADS AND TAILS CARD GAME</td>
      <td>None</td>
      <td>Very Low</td>
    </tr>
    <tr>
      <th>3</th>
      <td>575317</td>
      <td>22619</td>
      <td>SET OF 6 SOLDIER SKITTLES</td>
      <td>80</td>
      <td>2011-11-09 13:12:00</td>
      <td>3.39</td>
      <td>17402.0</td>
      <td>United Kingdom</td>
      <td>271.20</td>
      <td>45</td>
      <td>2011-11-09</td>
      <td>SET OF 6 SOLDIER SKITTLES</td>
      <td>None</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>4</th>
      <td>575318</td>
      <td>23318</td>
      <td>BOX OF 6 MINI VINTAGE CRACKERS</td>
      <td>12</td>
      <td>2011-11-09 13:17:00</td>
      <td>2.49</td>
      <td>14921.0</td>
      <td>United Kingdom</td>
      <td>29.88</td>
      <td>45</td>
      <td>2011-11-09</td>
      <td>BOX OF 6 MINI VINTAGE CRACKERS</td>
      <td>None</td>
      <td>Low</td>
    </tr>
  </tbody>
</table>
</div>

# Issues & Resolutions

issues:
1. sqlite3 installation error --- Cause: Tried to install using pip --- Soln: Recognized sqlite3 is built-in; used import sqlite3 directly

2. Folder not found error --- Cause: Missing loaded/ directory --- Soln: Added os.makedirs('loaded', exist_ok=True) before saving files

## Author

Name: Sammi Oyabi
Course: DSA 2040A — Data Science & Analytics
Institution: United States International University - Africa
Date: October 2025

# License

This project is for academic and educational purposes only.
Feel free to reference or reuse the code with proper attribution.



