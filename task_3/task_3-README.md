# Project Name

This repository contains Jupyter notebooks and Python scripts to clean and analyze [data source] data on [description of what the data is, the jurisdiction it covers] from [years the data covers]. 

[Add any additional context needed or limitations to the dataset.]

To reproduce my analysis in a spreadsheet, download a clean version of the dataset from clean_data/cleaned_data.csv. I've created spreadsheets in the output folder for a map of Dallas County and a bar chart showing the trends in the data from the past [X] years. 

To see exact steps, view the comments in my Jupyter notebook

## Data dictionary
The data includes the following columns:
* column_1 - This is the unique ID for each row in the dataset
* column_2 - [description of column]
* column_3 - [description of column]
* ...

## Contents
* `requirements.txt`: Everything needed to set up to run my analysis locally on your laptop.
* `raw_data/`: This is the original dataset I received. Do not modify!
* `output/`: Final data formatted for graphics: `formatted_data_bar_chart.csv`, `formatted_data_map.csv`, for bar chart and map, respectively.
* `analysis/`: Scripts and notebooks: `analysis.ipynb` contains the main analysis; `analysis_helper_functions.py` contains helper functions for the analysis imported in the notebook; `clean_data.py` is a script to clean the raw data and output a clean sheet in `clean_data/`.
## Getting started (Python)
* You will need Python 3.12 for this analysis

### Creating a virtual environment (on macOS)
```
python3 -m venv .venv # create a venv
source .venv/bin/activate # activate the environment
python --version # check python ver.
```

### Using pip to set up your virtual environment

Ensure your terminal shows (.venv) in the prompt to confirm the environment is active. In your terminal, run:

```
pip install -r requirements.txt
```
This will install all of the packages I used in my Python scripts and Jupyter notebook, so each runs smoothly.

## Clean data 

### Python
```
python3 clean_data.py # run script to clean raw data and export to a new CSV

```


### Spreadsheets
1. Start with raw files from raw_data/ in your working environment
2. Remove duplicate rows and unnecessary columns
3. Standardize the names of your columns and ensure the types of each column are accurate
4. Check for NA or missing values, and drop or fill them with placeholders.
5. Save the clean dataset to clean_data/cleaned_data.csv
    * To verify my analysis without using Python, open this CSV in Sheets or Excel to recreate my methodology.

## Methodology and analysis
Add methodology here, including steps that could feasibly be reproduced in a spreadsheet, such as filtering for X in a certain column, or grouping by a specific column, or creating a pivot table. [If the analysis cannot be reproduced in a spreadsheet, refer to the Jupyter notebook comments for exact steps.]

E.g.:
1. Filter only rows where [column_name] is [value] and assign it to a new dataframe.
2. Create a pivot table to calculate totals or averages for [column_name]
3. Create a new column for percentage change [or create any other new column]
4. Group by `column_1` and rank descending
5. ...
6. Export summarized data as csvs to output/ to use in viz.
