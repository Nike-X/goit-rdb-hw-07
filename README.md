# Homework 7 — Time Series and JSONB

This homework uses PostgreSQL to build time-series ML features from NYC Taxi trips and analyze semi-structured event data with JSONB.

## Dataset

- **Source:** [NYC TLC Yellow Taxi Trip Records](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

- **File:** `yellow_tripdata_2024-03.parquet` (March 2024)

- **Download:** Automatically retrieved from the official TLC Parquet URL in the notebook

- **Processing:** Deterministic sampling and cleaning produce 430,007 trips. A calendar spine creates 7,595 daily records across 245 pickup zones.

- **Event data:** 50,000 synthetic JSONB events across five event types, generated in PostgreSQL.

## Implementation

- **Time series:** Daily pickup-zone aggregation, lag features (1, 7, 30 days), rolling 7-day fare average, 30-day volatility, and expanding trip statistics.

- **JSONB:** Containment, key-existence, and JSONPath queries over varying event payloads.

- **Performance:** GIN and expression B-tree indexes evaluated with `EXPLAIN (ANALYZE, BUFFERS)`.

- **Comparison:** JSONB checkout aggregation versus a normalized checkout table, with findings and reflection.

## Repository

- `hw7_nyc_taxi_Kalashnikov_Mykola.ipynb` — SQL, Python, explanations, and saved outputs

- `README.md` — project overview and instructions

## How to Run

1. Open the notebook in **Google Colab**.

2. Select **Runtime → Restart session and run all**.

3. The notebook installs dependencies, starts local PostgreSQL using `pgserver==0.1.4`, downloads the TLC data, and runs all SQL analyses.

Internet access is required. No separate PostgreSQL server or local Parquet file is needed.
