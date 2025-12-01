## E-Commerce-Order-Management-Analytics-Platform

A complete end-to-end Azure Data Engineering project that processes e-commerce order, customer, and product data through a scalable Bronze → Silver → Gold ETL architecture. The platform uses Azure Data Factory, Azure Databricks, Delta Lake, ADLS Gen2, and SQL to deliver an optimized analytics-ready data model.

# Features

- Automated ingestion via ADF pipelines

- Databricks-based transformations (PySpark)

- Bronze, Silver, Gold Delta Lake architecture

- SCD Type 1 & Type 2 dimensions

- Fact tables for Orders, Customers, Products, Payments

- Delta OPTIMIZE + VACUUM for performance

- Data Quality checks (duplicates, schema drift, row counts)

- Azure SQL serving layer

- GitHub version-controlled code & pipelines

# Directory Structure

storage-account/
├── source-data/
│   ├── orders/
│   ├── customers/
│   ├── products/
│   ├── payments/
├── bronze/
│   ├── orders_raw/
│   ├── customers_raw/
│   ├── products_raw/
│   ├── payments_raw/
├── silver/
│   ├── orders_clean/
│   ├── customers_clean/
│   ├── products_clean/
│   ├── payments_clean/
├── gold/
│   ├── dimensions/
│   ├── facts/

# ETL Pipeline Flow

# Bronze Layer – Raw Ingestion

- Raw data copied from source-data/ via ADF

- Stored without modifications

- Maintains source fidelity

# Silver Layer – Cleaned Data

- Schema enforcement

- Null handling

- Deduplication

- Data type standardization

- Stored as optimized Delta tables

# Gold Layer – Business Layer

- SCD Type 1 & Type 2 dimensions

- Fact tables (Orders, Products, Customers, Payments)

- Z-ORDER & OPTIMIZE

- Business-ready model for reporting

# Data Quality Checks

- Duplicate detection

- Schema drift alerts

- Row count validation

- Rejected record logging

- Data profiling metrics

# Analytics Generated

- Monthly/Weekly Sales Metrics

- Top Customers (CLV)

- Best-selling Products

- Order Fulfillment Time

- Cancellation & Return Patterns

# Optimization Techniques Used

OPTIMIZE gold.orders ZORDER BY (order_id);
VACUUM gold.orders RETAIN 168 HOURS;


- Auto-compaction

- File size optimization

- Predicate pushdown

- Partition pruning

# Future Enhancements

- Power BI dashboards

- Streaming ingestion using Auto Loader

- Unity Catalog migration

- Great Expectations data quality framework

- CI/CD for ADF + Databricks
