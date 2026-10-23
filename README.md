# Delhi Urban Mobility Data Engineering Platform

## Overview

The **Delhi Urban Mobility Data Engineering Platform** is an end-to-end data engineering project built using Azure Data Lake Storage Gen2, Azure Databricks, PySpark, Delta Lake, and SQL.

The project processes Delhi bus transit data through a Medallion Architecture (Bronze, Silver, and Gold) to create structured, analytics-ready datasets.

The objective is to demonstrate data ingestion, transformation, data quality validation, dimensional modeling, and analytical querying using cloud data engineering technologies.

## Architecture

```text
Delhi Bus Transit Data
        |
        v
Azure Data Lake Storage Gen2
        |
        v
Azure Databricks
        |
        |-- Bronze Layer
        |     Raw data ingestion
        |
        |-- Silver Layer
        |     Data cleaning and validation
        |
        |-- Gold Layer
              Dimensional modeling
              Fact table
              SQL analytics
```

## Tech Stack

- Azure Data Lake Storage Gen2
- Azure Databricks
- PySpark
- SQL
- GitHub

## Data Pipeline

### 1. Bronze Layer
- Ingested raw Delhi bus transit data from ADLS Gen2.
- Created Bronze tables for routes, stops, trips, and stop times.

### 2. Silver Layer
- Cleaned and transformed transit datasets using PySpark.
- Validated unique identifiers and missing values.
- Created structured Silver tables for downstream processing.

### 3. Gold Layer
- Created dimensional tables for routes, stops, and trips.
- Built a fact table representing trip-stop occurrences.
- Prepared data for analytical SQL queries.

## Data Model

**Dimension Tables**
- `dim_route`
- `dim_stop`
- `dim_trip`

**Fact Table**
- `fact_trip_stop`

The fact table connects trip, route, and stop information to support transit route and stop-level analysis.

## Project Results

| Metric | Result |
|---|---:|
| Routes | 2,403 |
| Stops | 10,559 |
| Trips | 89,393 |
| Fact table records | 3,724,320 |

### Key Findings

- Processed **3.72 million trip-stop records** into the Gold fact table.
- Analyzed **89,393 trips** across **2,403 routes** and **10,559 stops**.
- Average trip contains approximately **41.66 stops**.
- Identified trips with fewer than 5 stops and trips exceeding 100 stops for further data validation.
- Validated route stop sequences, including a route containing 197 stops with sequential stop ordering.
- Created analytics-ready dimensional tables to support route-level, trip-level, and stop-level SQL analysis.

### Data Quality

- Verified uniqueness of route, stop, and trip identifiers in the Silver layer.
- Checked missing identifiers during data validation.
- Compared Bronze and Silver record counts to verify expected data retention.
- Validated stop sequence consistency for selected trips and routes.

## Analytics

The project supports SQL analysis of:

- Route and trip distribution
- Stops served by trips
- Stop occurrences across routes
- Number of stops per trip
- Route-level and stop-level patterns

## Repository Contents

- `README.md` — Project overview and documentation
- `project-structure.md` — Pipeline architecture and project structure
- `notebooks/` — Databricks project notebook




