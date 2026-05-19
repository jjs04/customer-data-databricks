# Mini Project 1 — Customer Data Read & Process

A PySpark project built in Databricks that reads, cleans, analyses, and joins customer and orders data.

---

## Project Overview

This notebook demonstrates a typical data engineering workflow using PySpark on Databricks:

- Reading CSV data from Databricks Volumes
- Cleaning and transforming raw data
- Performing exploratory analysis (aggregations, pivots, window functions)
- Joining multiple datasets for insights
- Writing processed output as Parquet

---

## Dataset

Two dummy CSV files are used:

### `customers.csv`
| Column | Type | Description |
|---|---|---|
| customer_id | String | Unique customer identifier |
| name | String | Customer full name |
| city | String | City of residence |
| state | String | State of residence |
| country | String | Country of residence |
| registration_date | Date (yyyy-MM-dd) | Date the customer registered |
| is_active | Boolean | Whether the customer is currently active |

### `orders.csv`
| Column | Type | Description |
|---|---|---|
| order_id | String | Unique order identifier |
| customer_id | String | Reference to customers table |
| order_date | Date | Date the order was placed |
| total_amount | Float | Total value of the order |
| status | String | Order status (e.g. completed, pending) |

---

## What the Notebook Does

1. **Setup** — Initialises a Spark session
2. **Load & Clean Customer Data** — Reads the CSV, casts data types, fills null location values
3. **Feature Engineering** — Extracts registration year and month
4. **Exploratory Analysis** — Unique city/state/country counts, distribution by location, pivot table of active vs inactive customers per state
5. **Window Functions** — Ranks customers within each state by registration date
6. **Load & Analyse Orders** — Revenue per customer, monthly revenue trends, order status breakdown
7. **Join & Combined Analysis** — Joins customers and orders to find top spenders, order frequency, and high-frequency low-spend customers
8. **Save Outputs** — Writes processed DataFrames to Parquet

---

## Tech Stack

- **Platform:** Databricks (Free Edition)
- **Language:** Python (PySpark)
- **Storage:** Databricks Volumes
- **Output Format:** Parquet

---

## How to Run

1. Upload `customers.csv` and `orders.csv` to your Databricks Volume at:
   ```
   /Volumes/workspace/default/mini_project_1/
   ```
2. Import the notebook into your Databricks workspace
3. Attach to a cluster (or use default Serverless compute if using free edition) with Spark and run all cells top to bottom

---

## Output Files

| File | Description |
|---|---|
| `Processed_customers/` | Cleaned and enriched customer data (Parquet) |
| `Final_customer_orders/` | Joined customers and orders (Parquet) |
| `Final_rank_orders/` | Ranked customers by total spend (Parquet) |
