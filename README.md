# Retail Sales & Financial Analytics Pipeline

This repository contains a technical data analysis project designed to process, validate, and evaluate retail sales performance and profitability over a 13-month period.

## Keywords & Technologies

* **Languages & Libraries:** Python, Pandas, NumPy, Matplotlib, NetworkX.
* **Concepts:** ETL (Extract, Transform, Load), Relational Data Modeling, Feature Engineering, Financial KPIs, Time-Series Aggregation.

## Data Architecture

The analysis is built on a standard star-schema structure, integrating transactional data with descriptive dimensions:

* **Fact Table:** `fato_vendas.xlsx` containing over 161,900 sales records.

* **Dimension Tables:** `dim_produtos.xlsx` (Product specifications and unit costs), `dim_familia_produtos.xlsx` (Category classifications), and `dim_vendedor.xlsx` (Salesperson data).

## Methodology & Pipeline

* **Data Ingestion & Validation:** The pipeline reads raw Excel files and performs immediate logical consistency checks. It verifies the absence of negative sale quantities, ensures revenue and discount values are mathematically sound, and establishes the dataset's timeline from January 2, 2025, to January 31, 2026.
* **Anomaly Handling:** The script identifies orphaned transactions lacking client ID codes and correctly retains them for macro-level revenue calculations while noting their exclusion from client-specific analytics.
* **Relational Merging:** Utilizes programmatic left-joins to unify the dimensional metadata (products, families, sellers) into the central sales fact table.
* **Feature Engineering:** Calculates vital financial metrics per transaction, including Gross Revenue (`faturamento_bruto`), Total Cost (`custo_total`), Net Profit (`lucro`), and exact Discount Percentages (`percentual_desconto`).
* **Aggregation & Reporting:** Converts daily transaction timestamps into monthly periods (`ano_mes`) to aggregate and compare total net revenue against pre-discount gross expectations.

## Getting Started

1. Clone this repository to your local machine.
2. Ensure the working directory contains a `data/` folder populated with the necessary source Excel files (`fato_vendas.xlsx`, `dim_produtos.xlsx`, etc.).
3. Install the required Python dependencies: `pip install pandas numpy matplotlib networkx`
4. Execute the Jupyter Notebook to process the data and generate the final `base.csv` and `mensal.csv` analytical outputs.
