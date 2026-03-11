# HEDIS CBP Measure Logic: Controlling High Blood Pressure

This project demonstrates hands-on HEDIS measure logic using Python, DuckDB, and SQL. 
It implements the Controlling High Blood Pressure (CBP) measure per NCQA specifications, 
including denominator construction, clinical exclusions, numerator evaluation, and a 
COVID-19 impact analysis layer.

## What this project does

- Builds a four-table clinical database (members, diagnoses, encounters, observations)
- Constructs the CBP denominator using ICD-10 codes, outpatient encounter data, and age criteria
- Applies NCQA exclusions for ESRD (N18.6) and hospice (Z51.5)
- Evaluates BP control against the 140/90 mmHg threshold
- Flags members with a COVID-19 diagnosis (U07.1) within 90 days of their BP reading
- Produces a final measure report with pass/fail disposition and measure rate

## Why I built this

I have experience working with HEDIS reporting workflows and automated compliance outputs. 
This project reflects how I approach measure logic from the inside: starting from the NCQA 
specification, translating it into data rules, and building validation that catches data 
quality issues before they affect reporting.

## Tools used

- Python 3.13
- DuckDB 1.5.0
- Pandas
- Jupyter Notebook

## How to run it

1. Clone this repository
2. Create a virtual environment: `python3 -m venv hedis-env`
3. Activate it: `source hedis-env/bin/activate`
4. Install dependencies: `pip install duckdb jupyter pandas`
5. Launch Jupyter: `jupyter notebook`
6. Open `hedis_cbp_measure_logic.ipynb` and run all cells in order
