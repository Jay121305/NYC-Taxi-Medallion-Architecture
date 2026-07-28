# Interview Questions

## 1. What is Medallion Architecture?

A layered data architecture consisting of Bronze, Silver and Gold tables.

---

## 2. Why use Bronze?

To preserve raw source data with minimal transformation.

---

## 3. Why use Silver?

To clean, validate and standardise data.

---

## 4. Why use Gold?

To create analytics-ready business tables.

---

## 5. Why use Delta Lake instead of Parquet?

Delta Lake provides:

- ACID Transactions
- Time Travel
- MERGE
- Schema Enforcement
- Version History

---

## 6. What is Time Travel?

The ability to query previous table versions.

---

## 7. Difference between OPTIMIZE and ZORDER?

OPTIMIZE reduces the number of files.

ZORDER improves data skipping by clustering data.

---

## 8. What does VACUUM do?

Deletes obsolete files after the retention period.

---

## 9. What is MERGE?

A single operation that performs INSERT, UPDATE and optionally DELETE.

---

## 10. Why build Gold tables?

Gold tables reduce dashboard complexity and improve query performance.

---

## 11. Why did you use Databricks?

To combine Spark, Delta Lake and SQL into a unified Lakehouse platform.

---

## 12. Why enrich the data?

Joining with the Taxi Zone Lookup makes dashboards understandable for business users by replacing numeric location IDs with readable zone names.

---

## 13. How many records did your project process?

Approximately 9.4 million NYC Yellow Taxi trips.

---

## 14. What dashboard insights were produced?

- Total Trips
- Total Revenue
- Average Fare
- Average Trip Distance
- Daily Revenue Trend
- Hourly Trip Distribution
- Payment Distribution
- Vendor Performance
- Top Pickup Zones

---

## 15. What would you improve next?

- Incremental ingestion
- Databricks Jobs
- Automated pipeline scheduling
- CI/CD deployment
- Data quality monitoring
- Unit testing
