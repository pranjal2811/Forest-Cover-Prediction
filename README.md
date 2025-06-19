Algerian Forest Fires Analysis


Introduction

This project focuses on analyzing the Algerian Forest Fires dataset to understand the factors contributing to forest fires and to classify fire incidents. Forest fires are a significant environmental and ecological concern, causing extensive damage to ecosystems, properties, and human lives. This repository contains a Python-based data analysis notebook that performs data cleaning, preprocessing, and exploratory data analysis (EDA) to derive insights into fire occurrences in two distinct regions of Algeria.

Objective
The primary objectives of this project are:

To load and preprocess the Algerian Forest Fires dataset, ensuring data quality and readiness for analysis.

To perform detailed data cleaning, including handling missing values and converting data types.

To create a 'Region' column to distinguish between the two geographical areas covered in the dataset.

To conduct exploratory data analysis (EDA) to understand the distribution of fire incidents and the correlation between various meteorological and fire weather index (FWI) components and fire classes.

To transform the 'Classes' column into a numerical format for potential future modeling.

To generate a clean dataset suitable for further machine learning applications.

Implementation Steps
My analysis for this project involved the following steps, as executed in the provided Jupyter notebook:

Data Loading and Initial Inspection:

The dataset Algerian_forest_fires_dataset_UPDATE (3).csv was loaded into a Pandas DataFrame, specifying header=1 due to the file structure.

Initial inspection using df.shape revealed 246 entries and 14 columns.

df.info() showed that all columns were initially of object dtype, and identified missing values in month, year, Temperature, RH, Ws, Rain, FFMC, DMC, DC, ISI, BUI, FWI, and Classes.

df[df.isnull().any(axis=1)] confirmed specific rows with missing data, including a row at index 122 ("Sidi-Bel Abbes Region Dataset") which serves as a separator for regions.

Region Assignment:

A new column Region was created and populated based on the dataset's internal structure:

Rows from index 0 to 122 (inclusive) were assigned Region = 1 (Bejaia Region).

Rows from index 122 onwards were assigned Region = 2 (Sidi-Bel Abbes Region).

The Region column's data type was cast to int.

Data Cleaning and Preprocessing:

Rows containing any NaN values were dropped using df.dropna().reset_index(drop=True), reducing the dataset size to 244 entries.

The header row (at new index 122) which contained day, month, year, etc. as string values was identified using df.iloc[[122]] and subsequently dropped using df.drop(122).reset_index(drop=True). This resulted in a clean dataset of 243 entries.

Column names were stripped of leading/trailing whitespace using df.columns.str.strip().

day, month, year, Temperature, RH, and Ws columns were converted from object to int type.

Other Fire Weather Index (FWI) components (Rain, FFMC, DMC, DC, ISI, BUI, FWI) were converted from object to float type, excluding Classes.

The Classes column, which contained values like 'fire' and 'not fire' (with some leading/trailing spaces), was cleaned by stripping whitespace (df.Classes.str.strip()).

Target Variable Encoding:

The Classes column was transformed into a numerical target variable:

'not fire' was encoded as 0.

'fire' was encoded as 1.

This conversion facilitates its use in machine learning models.

Cleaned Data Export:

The processed DataFrame was saved to a new CSV file named cleanalgerianforest_fire.csv for future use, without including the DataFrame index.

Results
The data cleaning and preprocessing steps resulted in a refined dataset ready for in-depth analysis and modeling. Key quantitative outcomes include:

Initial Data Dimensions: The original dataset contained 246 rows and 14 columns.

Final Cleaned Data Dimensions: After extensive cleaning, the dataset was reduced to 243 rows and 15 columns (including the newly engineered 'Region' column).

Missing Values Handled: All missing values identified in the raw data were successfully addressed through dropping rows or type conversions.

Fire Incident Distribution (Pre-Encoding):

Before encoding, the Classes column had the following counts:

'fire': 137 incidents

'not fire': 106 incidents

Fire Incident Distribution (Post-Encoding):

After encoding 'not fire' as 0 and 'fire' as 1:

Class 1 (fire): 137 incidents

Class 0 (not fire): 106 incidents

Data Type Conversion: All relevant columns were successfully converted to appropriate numerical (int or float) types, except for Classes which became int (0 or 1).

Region Segmentation: The dataset was successfully segmented into two distinct regions, '1' and '2', allowing for region-specific analysis.

This project successfully transformed raw, messy data into a clean, structured format, ready for further statistical analysis or the development of predictive models to forecast forest fires in the Algerian regions.

Contact Information
For any questions, discussions, or potential collaborations on this project, please feel free to connect:

Name: Pranjal Joshi

Email: pranjaljoshi2811@gmail.com

GitHub: https://github.com/pranjal2811

LinkedIn: https://www.linkedin.com/in/pranjaljoshi2811
