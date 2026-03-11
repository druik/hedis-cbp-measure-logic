# HEDIS CBP Measure Logic: Controlling High Blood Pressure

This is a portfolio project demonstrating how I approach clinical quality 
measure logic. It translates the NCQA HEDIS CBP specification into working 
SQL and Python, including denominator construction, clinical exclusions, 
numerator evaluation, and a COVID-19 impact analysis layer.

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

## Known Simplifications

This project is a portfolio demonstration, not a production implementation. 
A few intentional simplifications worth noting:

**Denominator:**
The full NCQA CBP specification requires at least two outpatient visits with 
a hypertension diagnosis on different dates of service. This implementation 
uses a single visit for simplicity.

**BP Selection Rule:**
The NCQA specification requires using the most recent BP reading during the 
measurement year on or after the second hypertension diagnosis. If multiple 
readings occur on the same date, the lowest systolic and lowest diastolic are 
used. This implementation uses any BP reading on file without applying the 
most-recent or same-day selection rules.

**Data Source:**
Production HEDIS reporting uses hybrid methodology combining administrative 
claims data with medical record review. This implementation uses synthetic 
data only.

These simplifications are documented here because understanding where a 
pipeline diverges from the full specification is part of working inside 
measure logic.

A future iteration will implement multiple BP readings per member with 
most-recent selection logic and same-day tie-breaking per the full NCQA 
specification.
