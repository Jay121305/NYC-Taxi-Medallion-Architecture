# Delta Lake

## What is Delta Lake?

Delta Lake is an open table format built on top of Apache Spark.

It adds:

- ACID Transactions
- Schema Enforcement
- Time Travel
- Version History
- MERGE Operations
- Data Optimisation

---

# Delta Features Demonstrated

## UPDATE

Used to modify existing rows.

Example:

- Correcting business data
- Fixing invalid values

---

## DELETE

Used to remove unwanted records.

Typical use cases:

- GDPR requests
- Bad data removal

---

## MERGE

Combines INSERT and UPDATE operations into one atomic transaction.

Used for incremental ETL pipelines.

---

## DESCRIBE HISTORY

Displays every version of a Delta table.

Useful for:

- Auditing
- Debugging
- Data lineage

---

## Time Travel

Allows querying older versions of a table.

Example:

SELECT * FROM table VERSION AS OF 3;

---

## RESTORE

Restores an older version as the latest table version.

Useful for recovering from accidental updates.

---

## OPTIMIZE

Compacts many small files into fewer larger files.

Benefits:

- Faster reads
- Reduced metadata overhead

---

## ZORDER

Clusters related records together inside Delta files.

Benefits:

- Better data skipping
- Faster filtered queries

---

## VACUUM

Deletes obsolete files no longer referenced by the current table version.

Benefits:

- Storage cleanup
- Reduced storage costs

---

## Project Usage

This project demonstrates:

- UPDATE
- MERGE
- RESTORE
- DESCRIBE HISTORY
- Time Travel
- OPTIMIZE
- ZORDER
- VACUUM

using Databricks Delta Lake.
