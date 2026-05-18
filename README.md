# East African Development Indicators — Data Cleaning & Analysis
**World Bank WDI | 8 Countries | 2010–2024**

## Project Summary
This project cleans and analyzes World Development Indicators (WDI) 
data from the World Bank DataBank, covering eight East African countries 
across five macroeconomic indicators from 2010 to 2024.

**Target application:** Policy and development analysis for institutions 
including the Central Bank of Somalia, African Development Bank, and UN agencies.

---

## Countries Covered
Burundi, Congo Dem. Rep., Kenya, Rwanda, 
Somalia, South Sudan, Tanzania, Uganda

## Indicators Analyzed
- Inflation, consumer prices (annual %)
- GDP per capita (current LCU)
- Unemployment, total (% of total labor force)
- Gross national expenditure (% of GDP)
- Population, total

---

## Key Findings

**Somalia Data Gaps:** Inflation and Unemployment data are entirely 
absent for Somalia across the full 2010–2024 window, making national 
price stability and labor market analysis impossible without supplementary sources.

**DRC Nominal Growth Anomaly:** DRC shows a GDP per capita index 
rising from 100 to nearly 600 (2010=100) in nominal LCU terms. 
Given missing CPI data from 2017 onward, this likely reflects 
currency depreciation and inflation rather than real output growth. 
Cross-validation against USD-denominated GDP series is recommended.

**South Sudan Decline:** South Sudan is the only country whose 
GDP per capita index fell below its 2010 baseline, consistent 
with conflict disruption and oil sector volatility.

---

## Data Cleaning Steps
1. Removed metadata contamination from Excel footer rows
2. Replaced World Bank `..` encoding with proper NaN values
3. Converted all year columns from object to float64
4. Standardized column names from `2010 [YR2010]` to `2010`
5. Dropped empty 2025 column (100% missing)
6. Reshaped from wide format (40×19) to long format (600×6)

Full cleaning documentation is in the notebook.

## SQL Findings
Five SQL queries answering real policy questions using the cleaned 
EAC dataset. Covers SELECT, JOIN, GROUP BY, HAVING, window functions 
(RANK, LAG), and Python-SQL integration via sqlite3.

Key findings:
- Somalia ranks 1st in gross national expenditure every year 2012–2024
- South Sudan experienced 380% inflation in 2016 with no GDP data available
- Unemployment data is unreliable across all EAC countries — no country 
  has complete coverage
---

## Repository Structure
