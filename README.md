# 🎯 Target Retail Data Pipeline

An end-to-end data engineering pipeline that processes retail sales transaction data using **Kafka**, **PySpark**, and **Hive** — simulating a real-world data pipeline for Target Corporation's retail operations across Brazil.

---

## 📌 Project Overview

This project demonstrates a complete data engineering workflow:

```
CSV Data → Kafka (Stream) → PySpark (Process) → Hive (Store)
```

- **Kafka** simulates real-time streaming of 1,000+ sales transactions
- **PySpark** performs data cleaning, transformation, and analytics
- **Hive** stores the final processed data as persistent tables

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core programming language |
| Kafka (kafka-python) | Data streaming simulation |
| PySpark | Distributed data processing |
| Hive | Data warehousing and storage |
| Pandas | Initial CSV ingestion |
| Google Colab | Development environment |

---

## 📂 Dataset

- **Source:** Target retail sales transaction data
- **Size:** 1,000 rows × 12 columns
- **After cleaning:** 978 rows (22 null rows removed)

### Columns:
| Column | Description |
|--------|-------------|
| Id | Unique order identifier |
| order_status | Status of order (delivered, shipped, canceled, etc.) |
| order_products_value | Total product value of order |
| order_freight_value | Shipping cost of order |
| order_items_qty | Number of items in order |
| order_purchase_timestamp | Date and time order was placed |
| order_aproved_at | Date and time order was approved |
| order_delivered_customer_date | Date and time order was delivered |
| customer_city | City of customer |
| customer_state | State of customer |
| customer_zip_code_prefix | Zip code prefix of customer |
| review_score | Customer review score (1-5) |

---

## 🔄 Pipeline Architecture

```
┌─────────────┐     ┌──────────────────────┐     ┌─────────────────┐
│  CSV File   │────▶│   Kafka Producer     │────▶│  Kafka Topic    │
│ (1000 rows) │     │ (row by row stream)  │     │ (target-sales)  │
└─────────────┘     └──────────────────────┘     └────────┬────────┘
                                                           │
                                                           ▼
┌─────────────┐     ┌──────────────────────┐     ┌─────────────────┐
│ Hive Tables │◀────│  PySpark Processing  │◀────│ Kafka Consumer  │
│  (stored)   │     │ (clean + analyze)    │     │ (collect rows)  │
└─────────────┘     └──────────────────────┘     └─────────────────┘
```

---

## 📊 Key Findings

### EDA Results
| Metric | Value |
|--------|-------|
| Average Product Value | $127.85 |
| Average Freight Value | $21.41 |
| Delivery Rate | 98.26% |
| Unique States | 26 |
| Top City by Orders | Sao Paulo (141 orders) |

### Business Analytics Results
| Analysis | Finding |
|----------|---------|
| Top Revenue City | Sao Paulo ($15,542.07) |
| Average Delivery Time | 12.33 days |
| Average Approval Time | 10.41 hours |
| Average Review Score | 4.09 / 5.0 |
| Fastest Delivery City | Recife (7.41 days) |
| Slowest Delivery City | Nova Iguacu (18.59 days) |
| Freight vs Qty Correlation | 0.63 (Moderate) |
| Delivery vs Review Correlation | 0.02 (No relationship) |

---

## 🔍 Analysis Performed

### Exploratory Data Analysis (EDA)
1. Mean of order product value and freight value
2. Distribution of order status
3. Count of unique customer states
4. Missing value detection and handling
5. Top 5 cities by order volume
6. Percentage breakdown of order statuses

### Data Processing & Business Analytics
1. Total sales revenue per city
2. Correlation between order value, freight, and item quantity
3. Average delivery and approval times
4. Average review score per order status
5. Top 3 fastest and slowest delivery cities
6. Relationship between delivery time and review score

---

## 💡 Business Insights

- **Sao Paulo dominates** — generates 37% more revenue than Rio de Janeiro
- **98.26% delivery rate** indicates excellent fulfillment operations
- **Delivery time alone** does not strongly impact review scores (correlation: 0.02)
- **Shipping costs** are more influenced by item quantity (0.63) than product value (0.47)
- **11-day gap** exists between fastest (Recife) and slowest (Nova Iguacu) delivery cities

---

## 🚀 How to Run

### 1. Open in Google Colab
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com)

### 2. Upload Dataset
Upload `target_data.csv` to Colab files section

### 3. Install Dependencies
```python
!pip install kafka-python pyspark
```

### 4. Run All Cells
Run cells sequentially from top to bottom

---

## 📁 Project Structure

```
target-data-pipeline/
│
├── Target_Data_Pipeline.ipynb    # Main notebook
├── target_data.csv               # Dataset
└── README.md                     # Project documentation
```

---

## 👤 Author

**Surya Jaya Sai Padala**
- 📧 jaisaipadala@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/jaya-sai-surya-padala)
- 🎓 M.S. Applied Computer Science — Southeast Missouri State University

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).
