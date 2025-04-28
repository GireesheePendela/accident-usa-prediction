[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/5GqajVEC)
# MSDS-597 Project

Group: 17

## Project summary

Our project summary can be found:

- as a notebook on `nbviewer`

https://nbviewer.org/gist/YOUR-GH-USERNAME/????????????????????????/

OR

- as a website:

https://moran-teaching.github.io/project-repo/????????????

## Accessing data

Our raw data can be downloaded here:

https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents

- **Dataset Title:** US Accidents (3.0 Million records)
- **Provided By:** Sobhan Moosavi (Kaggle user)
The primary dataset used for this project is the **US Accidents (3.0 million records)** dataset.  
It was sourced from **Kaggle**, a popular platform for sharing datasets and competitions in data science.

The dataset is compiled and provided by **Sobhan Moosavi**, who aggregated and shared the accident reports data.  
The original accident data is collected from various US traffic incident reporting services and public sources such as:

- US Department of Transportation
- Local transportation agencies
- Traffic APIs and sensors


[Insert link to processed data]

NOTE: do not include your data in your git repo - it will likely be too large and cause issues.


## Python scripts / notebooks

The following scripts/notebooks were used produce the summary:

- `src/script.py`
- `notebooks/data_cleaning.ipynb`
- `notebooks/data_enrichment.ipynb`
- `notebooks/data_analysis.ipynb`

[Give a short description of what the notebooks contain, and their location in the git repo]

## Reproducibility

Provide a `requirements.txt` file with packages and versions of all python packages to run the analysis.

## Guide

### Summary

Your summary should include the following. 

Note: You do not need code in your summary - instead, reference where in your github repo the code is. The priority should be a concise, readable summary. You should include visualizations and conclusions regarding your data analysis.

1. ## Data Format

- **File Type:** CSV (Comma-Separated Values)
- **Size:** ~300 MB (after extraction)
- **Structure:** 
  - Each row represents one traffic accident/incident report.
  - Columns include fields like time of accident, location (city, state, latitude, longitude), weather conditions at the time of the accident, and environment features (e.g., presence of traffic signals).

  ## 1.1 Nature of the Data

- **Scope:** Covers accident data across 49 states in the United States (excluding Hawaii and Alaska).
- **Time Period:** Data collected from February 2016 to March 2023.
- **Data Fields Include:**
  - Accident timestamp and duration
  - Geographic location (city, county, state, coordinates)
  - Weather conditions at the time of accident (temperature, visibility, wind, precipitation)
  - Road features (presence of bumps, crossings, traffic signals, etc.)
- **Update Frequency:** 
  - The Kaggle dataset is static — it was last updated by the contributor in 2023.
  - It is **not automatically updated** with new accidents unless manually uploaded again by the contributor.


2. # Data Retrieval

## 2.1 Retrieval Method

The US Accidents dataset was **manually downloaded** from Kaggle.

- **Not retrieved using an API**: Kaggle datasets require user login and manual agreement to licensing terms, so direct API access was not possible.
- **Not retrieved using web scraping**: The dataset was already provided as a downloadable CSV file through the Kaggle interface, so no web scraping was needed.

Instead, the retrieval involved:

1. Logging into a Kaggle account.
2. Navigating to the [US Accidents dataset page](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents).
3. Clicking "Download" to obtain the dataset ZIP archive.
4. Extracting the `US_Accidents_March23.csv` file from the archive.
5. Saving the CSV file locally in the `/data/` directory of the project repository (excluded from Git tracking).

## 2.2 Note on Automation

If the dataset had been publicly accessible without authentication, retrieval could have been automated using:

- Python `requests` library for direct file download.
- Kaggle's CLI tool (`kaggle datasets download`) if project permissions allowed.

However, due to manual login requirements on Kaggle, **the retrieval process was manual** for this project.


# 3. From Raw Data to Tidy Tabular Data

## 3.1 Initial Raw Data Format

The raw dataset was loaded from a CSV file into a pandas DataFrame.  
Each row represents a single accident report, with columns including time, location, weather conditions, and road attributes.

The initial dataset contained:
- Timestamp columns (`Start_Time`, `End_Time`) as string objects.
- Location coordinates (`Start_Lat`, `Start_Lng`) as numeric values.
- Some missing values in weather-related fields.
- Extra columns not directly relevant to the main analysis.

## 3.2 Data Cleaning and Transformation Steps

Several steps were performed to clean and prepare the dataset:

- **Datetime Conversion:**  
  Converted the `Start_Time` and `End_Time` columns from string to `datetime` format using `pandas.to_datetime()`.  
  This enabled accurate extraction of temporal features such as "hour of day".

- **Feature Extraction:**  
  Extracted the "Hour" from the `Start_Time` column and created a new `Hour` field for time-of-day analysis.

- **Missing Values Handling:**  
  Identified columns with missing values (e.g., `Temperature(F)`, `Weather_Condition`).  
  Depending on the field, either:
  - Left missing values as-is for optional filtering later, or
  - Dropped rows only if critical fields (like location or time) were missing.

- **Column Selection:**  
  Selected only a subset of useful columns relevant to the analysis:
  - `ID`, `Start_Time`, `End_Time`, `State`, `City`, `Start_Lat`, `Start_Lng`, `Temperature(F)`, `Weather_Condition`, `Hour`.

- **Data Type Checking:**  
  Verified that numeric, categorical, and datetime fields had the appropriate types for analysis.

## 3.3 Result

After these steps, the dataset became:

- Cleaned of obvious inconsistencies.
- Structured in a tidy tabular format.
- Ready for grouping, summarizing, and visualization.

Each row cleanly represents one accident event with consistent types across all fields.

4. explain any tests you did to check data (e.g. using `pytest` to verify that no missing values are present in the tidied dataframes, verify that the resulting number of rows is reasonable)

5. explain any data enrichment steps

6. describe and explain meaningful summary statistics

7. present around 4-6 visualizations related to the data, explain trends and conclusions

You should have at least one interactive data widget.

You can include figures for example from an external notebook:
- https://quarto.org/docs/blog/posts/2023-03-17-jupyter-cell-embedding/ 
- https://quarto.org/docs/authoring/includes.html

8. at the end, display a graph of the git commit history

For team members of 2: 10 commits. Of 3: 15 commits. Of 4: 20 commits.

Your commits history elsewhere may be more dirty, but these 10-20 commits need to be clean and can be drawn as a graph.

Make sure your git graphs include author names, commit messages, date, git tags if any.

You can generate nice graphs of git commits with many tools. Among others, you could generate git-graphs using the following tools:

- in vscode: https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph
- https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs
- https://www.gitkraken.com/solutions/commit-graph

### Data storage options

Some options for data storage:

- Box link (free with Rutgers account)
- Dropbox
- Google Drive

The following companies have free data storage (up to ~5 GB) for 12 months. Be careful to make sure you're within the free limits!!!

- AWS S3 https://aws.amazon.com/s3/
- Google Cloud https://cloud.google.com/free
- Microsoft Azure https://azure.microsoft.com/en-us/free/students

