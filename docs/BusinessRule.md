# BusinessRules

# Business Rules

This document describes the business rules applied during the Silver and Gold layer transformations.

---

# Data Quality Rules

## Duplicate Records

Rule

Duplicate rows are removed.

Reason

Prevent double-counting of trips.

---

## Fare Amount

Rule

fare_amount >= 0

Reason

Taxi fares cannot be negative.

---

## Total Amount

Rule

total_amount >= 0

Reason

Negative total revenue is invalid.

---

## Trip Distance

Rule

0 <= trip_distance <= 100

Reason

Trips longer than 100 miles are considered outliers for this dataset.

---

## Timestamp Validation

Rule

Pickup time must occur before Dropoff time.

Reason

Negative trip durations are invalid.

---

## Airport Fee

Rule

Null values replaced with 0.

Reason

Most trips do not include airport fees.

---

## Congestion Surcharge

Rule

Null values replaced with 0.

Reason

Congestion charges are optional.

---

## Passenger Count

Rule

Null values retained.

Reason

Passenger count is not mandatory for all trips.

---

## RateCodeID

Rule

Null values retained.

Reason

Missing RateCode values do not invalidate a trip.

---

# Enrichment Rules

Taxi Zone Lookup

Rule

Join Silver table using:

PULocationID

↓

LocationID

Reason

Convert numeric IDs into readable zone names.

---

# Gold Layer Rules

Daily Summary

Aggregated by:

trip_date

Metrics

- Trips
- Revenue
- Average Fare

---

Hourly Summary

Aggregated by:

pickup_hour

Metrics

- Total Trips

---

Payment Summary

Grouped by:

payment_type

Metrics

- Trips
- Revenue

---

Vendor Summary

Grouped by:

VendorID

Metrics

- Total Trips
- Revenue
- Average Fare

---

Zone Summary

Grouped by:

Zone

Metrics

- Trips
- Revenue
- Average Fare

---

# Dashboard Rules

Dashboard reads only Gold tables.

Reason

Gold tables are optimized for reporting and eliminate expensive aggregations during dashboard execution.
