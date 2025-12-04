# Quantium Virtual Internship – Retail Strategy & Analytics (Task 1)

## 📌 Project Overview

This project is part of the **Quantium Virtual Internship – Retail Strategy and Analytics (Task 1)**.  
The objective is to explore, clean, and analyse retail transaction data in order to generate insights about customer purchasing behaviour and product trends.

The analysis focuses on:
- Data cleaning and preparation
- Removing outliers
- Extracting useful features (e.g. pack size from product names)
- Understanding product and customer purchasing patterns

---

## 📂 Datasets Used

Two main datasets are used in this analysis:

1. `QVI_transaction_data.csv`  
   Contains information such as:
   - Transaction date
   - Store number
   - Loyalty card number
   - Product name
   - Product quantity
   - Total sales

2. `QVI_purchase_behaviour.csv`  
   Contains customer information related to purchasing behaviour.

---

## 🛠 Tools & Libraries Used

- **R**
- **data.table**
- **ggplot2**
- **readr**

Example of libraries loaded:

```r
library(data.table)
library(ggplot2)
library(readr)
```

---

## 🔍 Key Steps in Task 1

### 1. Data Loading
```r
transactionData <- read.csv("QVI_transaction_data.csv")
customerData <- read.csv("QVI_purchase_behaviour.csv")
```

### 2. Convert Date Column
```r
transactionData <- as.data.table(transactionData)
transactionData[, DATA := as.Date(DATE, origin="1899-12-30")]
```

### 3. Product Name Analysis
- Split product names into individual words
- Removed numbers and special characters
- Found most common keywords (e.g. Chips, Smiths, Kettle)

### 4. Outlier Detection and Removal
A customer (`LYLTY_CARD_NBR = 226000`) purchased **200 packets** in a single transaction – unrealistic for normal retail behaviour.

```r
transactionData <- transactionData[LYLTY_CARD_NBR != 226000, ]
```

This removed abnormal transactions to make analysis more accurate.

### 5. Pack Size Extraction
Extracted pack sizes directly from product names:

```r
transactionData[, PACK_SIZE := parse_number(PROD_NAME)]
```

Then counted each pack size:

```r
transactionData[, .N, PACK_SIZE][order(PACK_SIZE)]
```

This helps understand which pack sizes are most popular.

---

## 📊 Insights So Far

- Most products contain variations of **“Chips”**
- Popular brands include:
  - Smiths
  - Kettle
  - Doritos
- Most common pack sizes include:
  - 150g
  - 170g
  - 175g
  - 200g

These insights will support customer segmentation and strategic recommendations in later tasks.

---

## ✅ Project Status

✔ Data loaded and cleaned  
✔ Outliers removed  
✔ Pack sizes extracted  
✔ Product word frequency analysed  
⬜ Further analysis & visualization (next tasks)

---

## 👩‍💻 Author

**Chalani Navoda**  

