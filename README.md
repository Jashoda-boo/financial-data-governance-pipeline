# Enterprise Financial Data Governance & Compliance Pipeline

## Project Overview
This project demonstrates a production-ready, zero-trust **Medallion Architecture** designed to handle volatile financial market transaction data. Built using Databricks, the pipeline programmatically ingests raw transaction feeds, enforces strict institutional data quality guardrails, isolates non-compliant records to a quarantine table, and secures sensitive corporate identifiers (PII) before analytical consumption.

## Architecture Blueprint
The pipeline processes data through three distinct organizational layers:
1. **Bronze Layer:** Raw ingestion zone capturing incoming transactional streams (simulating a live market feed).
2. **Silver Layer (Audit Gate):** Applies real-time data validations. Records with missing identifiers (ISINs) or invalid numeric values (negative price/volume) are automatically diverted to a **Compliance Quarantine Table** for auditing, preserving data integrity.
3. **Gold Layer (Masked Presentation):** A secure presentation layer that applies column-level obfuscation to sensitive Trader PAN numbers to enforce financial data privacy mandates.

## Key Metrics & Results
* **Data Volume Processed:** 100 raw transaction records ingested per batch.
* **Pipeline Efficiency:** Successfully caught and isolated **34 corrupted compliance records** without halting pipeline execution.
* **Data Security Integrity:** Achieved 100% masking compliance on PII columns for downstream analytics views.

## Technical Stack
* **Platform:** Databricks Serverless
* **Engine:** Apache Spark (Spark SQL & PySpark)
* **Storage Framework:** Delta Lake Core
