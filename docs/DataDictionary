# DataDictionary

# Data Dictionary

This document describes the important datasets used throughout the project.

---

# Bronze Table

Table

workspace.nyc_taxi.bronze_trips

Purpose

Stores raw NYC Taxi trip records without business transformations.

---

# Silver Table

Table

workspace.nyc_taxi.silver_trips

Purpose

Stores cleaned and validated taxi trips.

Important Columns

| Column | Description |
|----------|-------------|
| VendorID | Taxi vendor identifier |
| tpep_pickup_datetime | Pickup timestamp |
| tpep_dropoff_datetime | Dropoff timestamp |
| passenger_count | Number of passengers |
| trip_distance | Distance travelled (miles) |
| RatecodeID | Fare rate type |
| PULocationID | Pickup location |
| DOLocationID | Dropoff location |
| payment_type | Payment method |
| fare_amount | Base fare |
| tip_amount | Driver tip |
| tolls_amount | Toll charges |
| total_amount | Total trip cost |

---

# Taxi Zone Lookup

Purpose

Maps Location IDs to readable geographical names.

Important Columns

| Column | Description |
|----------|-------------|
| LocationID | Zone identifier |
| Borough | NYC Borough |
| Zone | Zone Name |
| service_zone | Taxi service region |

---

# Gold Tables

## gold_daily_summary

Purpose

Daily business metrics.

Columns

| Column | Description |
|----------|-------------|
| trip_date | Date |
| trips | Number of trips |
| revenue | Daily revenue |
| average_fare | Average fare |

---

## gold_hourly_summary

Purpose

Trip demand by hour.

Columns

| Column | Description |
|----------|-------------|
| pickup_hour | Hour of day |
| total_trips | Number of trips |

---

## gold_payment_summary

Purpose

Revenue by payment method.

Columns

| Column | Description |
|----------|-------------|
| payment_type | Payment method ID |
| trips | Number of trips |
| revenue | Revenue generated |

Payment Types

| ID | Description |
|----|-------------|
| 0 | Flex Fare / Unknown |
| 1 | Credit Card |
| 2 | Cash |
| 3 | No Charge |
| 4 | Dispute |
| 5 | Unknown |
| 6 | Voided Trip |

---

## gold_vendor_summary

Purpose

Vendor performance metrics.

Columns

| Column | Description |
|----------|-------------|
| VendorID | Vendor identifier |
| total_trips | Total completed trips |
| revenue | Revenue generated |
| average_fare | Average fare |

---

## gold_zone_summary

Purpose

Top pickup locations.

Columns

| Column | Description |
|----------|-------------|
| Zone | Pickup zone |
| Borough | Borough |
| Trips | Total trips |
| Revenue | Revenue |
| Average Fare | Average fare |
