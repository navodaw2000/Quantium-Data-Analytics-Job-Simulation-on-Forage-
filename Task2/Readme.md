# Quantium Virtual Internship Task 2 – Control Store Selection and Trial Analysis

## Project Overview
This project performs a control store selection and trial analysis for a supermarket dataset, as part of the **Quantium Virtual Internship Task 2**. The goal is to identify control stores that closely resemble trial stores based on sales and customer metrics and assess the impact of a trial on store performance.

The analysis includes:
- Preprocessing sales transaction data
- Calculating store metrics over time
- Selecting control stores using correlation and magnitude distance
- Visualizing trial vs control store performance
- Measuring trial uplift in sales and customer counts

---

## Dataset
The project uses the dataset provided by Quantium:

- **QVI_data.csv** – Contains transactional data including:
  - `DATE` – Transaction date
  - `STORE_NBR` – Store number
  - `LYLTY_CARD_NBR` – Customer ID
  - `TOT_SALES` – Total sales amount
  - `PROD_QTY` – Quantity of products purchased

> Note: Ensure the CSV file is placed in the same folder as the R script for proper loading.

---

## Key Features
1. **Store Metrics Calculation**  
   Computes monthly metrics for each store, including:
   - Total sales
   - Number of unique customers
   - Average transactions per customer
   - Average price per unit

2. **Control Store Selection**  
   - Calculates **correlation** between trial and potential control stores
   - Calculates **magnitude distance** for store metrics
   - Combines correlation and magnitude to select the most similar control store

3. **Visualization**  
   - Plots time series of total sales for trial and control stores
   - Allows comparison of pre-trial and trial period performance

4. **Trial Analysis**  
   - Computes percentage differences between trial and control stores
   - Measures trial uplift in sales and customer counts

---

## R Script
The main R script (`task2_analysis.R`) includes:
- Data loading and preprocessing
- Functions for correlation and magnitude distance
- Control store selection
- Visualization of results

---

## How to Run
1. Install required R packages (if not already installed):
```r
install.packages(c("data.table", "ggplot2", "lubridate"))

