# Architecture.md

# System Architecture

## Overview

This project implements an end-to-end Lakehouse Data Engineering pipeline using the Medallion Architecture on Databricks. Raw NYC Yellow Taxi trip records are ingested, cleaned, enriched, transformed into business-ready datasets, and visualized using an interactive dashboard.

The pipeline is designed to closely resemble production data engineering workflows used in modern data platforms.

---

# High-Level Architecture

```
                   NYC TLC Dataset
                           │
                           ▼
              Parquet Files (Jan–Mar 2024)
                           │
                           ▼
                Databricks Volume Storage
                           │
                           ▼
                Bronze Delta Table (Raw)
                           │
                           ▼
            Silver Delta Table (Cleaned Data)
                           │
               Taxi Zone Lookup Join
                           │
                           ▼
              Gold Business Tables
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
   SQL Analytics     Delta Lake Ops     Dashboard
                           │
                           ▼
                  Business Insights
```

---

# Technology Stack

| Component | Technology |
|------------|------------|
| Platform | Databricks Free Edition |
| Storage | Unity Catalog Volumes |
| Processing | Apache Spark (PySpark) |
| Query Engine | Spark SQL |
| Storage Format | Delta Lake |
| Dashboard | Databricks Lakeview Dashboard |

---

# Pipeline Stages

## 1. Data Ingestion

Raw NYC Taxi trip records are uploaded into a Databricks Unity Catalog Volume.

Files Used:

- yellow_tripdata_2024-01.parquet
- yellow_tripdata_2024-02.parquet
- yellow_tripdata_2024-03.parquet
- taxi_zone_lookup.csv

---

## 2. Bronze Layer

Purpose:

- Preserve raw source data
- No business transformations
- Maintain original schema
- Enable data recovery

Output Table

workspace.nyc_taxi.bronze_trips

---

## 3. Silver Layer

Purpose:

Clean and validate the Bronze data.

Transformations include:

- Remove duplicate records
- Remove invalid fares
- Remove impossible trip distances
- Validate pickup/dropoff timestamps
- Handle null values
- Improve overall data quality

Output Table

workspace.nyc_taxi.silver_trips

---

## 4. Data Enrichment

The cleaned taxi data is enriched by joining with the NYC Taxi Zone Lookup dataset.

This converts:

PULocationID

↓

Human-readable Zone Names

Examples:

- JFK Airport
- Midtown East
- Upper East Side North

---

## 5. Gold Layer

Business-ready aggregate tables are generated for reporting.

Tables include:

- gold_daily_summary
- gold_hourly_summary
- gold_payment_summary
- gold_vendor_summary
- gold_zone_summary

These tables are optimized for analytical queries instead of transactional workloads.

---

## 6. SQL Analytics

Spark SQL is used to perform:

- Aggregations
- Window Functions
- Ranking
- Business KPIs
- Time-based analysis

---

## 7. Delta Lake Operations

Implemented features:

- UPDATE
- DELETE
- MERGE
- DESCRIBE HISTORY
- Time Travel
- RESTORE
- OPTIMIZE
- ZORDER
- VACUUM

---

## 8. Dashboard

A Lakeview Dashboard was built using Gold layer tables.

Business KPIs include:

- Total Trips
- Total Revenue
- Average Fare
- Average Trip Distance
- Daily Revenue Trend
- Hourly Trip Distribution
- Payment Distribution
- Top Pickup Zones
- Vendor Performance

---

# Data Flow Summary

Raw Files

↓

Bronze

↓

Silver

↓

Enrichment

↓

Gold

↓

Dashboard

---

# Project Outcome

The final solution processes more than 9.4 million taxi trips and converts raw operational data into analytics-ready business datasets using a scalable Medallion Architecture.
