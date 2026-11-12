# Food Delivery Data Analysis
### Kagnus Internship — Week 1: Dataset Understanding & Cleaning

## 1. Project Overview

This project focuses on understanding, inspecting, and preparing a food delivery dataset for future analysis.

The main objective of Week 1 is to examine the dataset's structure, identify data quality issues, investigate missing and unusual values, and apply only justified cleaning operations.

The project emphasizes data quality, transparency, and reproducibility. The original dataset is preserved, and cleaning decisions are documented rather than making assumptions about values whose meaning has not been confirmed.

## 2. Project Objectives

The main objectives of this project are:

- Understand the dataset's structure, dimensions, and variables.
- Identify missing values and examine their distribution.
- Check for duplicate records and duplicate identifiers.
- Inspect numerical and categorical variables.
- Investigate unusual values, inconsistent formats, and potential anomalies.
- Verify date and time formats before using them in calculations.
- Apply appropriate cleaning operations while preserving valid information.
- Document all identified issues and the decisions made.
- Export a separate cleaned dataset for future analysis.

## 3. Dataset Description

The dataset contains **45,584 records and 20 columns** related to food delivery operations.

Each row represents one delivery record.

The dataset includes information about:

- Delivery personnel, including age and ratings.
- Restaurant and delivery location coordinates.
- Order dates and order/pickup times.
- Weather conditions and road traffic density.
- Vehicle condition and type of vehicle.
- Order categories and multiple deliveries.
- Festival information and city classification.
- Total delivery time in minutes.

### Main Variables

| Category | Variables |
|---|---|
| Delivery information | ID, Delivery_person_ID |
| Personnel | Delivery_person_Age, Delivery_person_Ratings |
| Location | Restaurant_latitude, Restaurant_longitude, Delivery_location_latitude, Delivery_location_longitude |
| Date and time | Order_Date, Time_Orderd, Time_Order_picked |
| Conditions | Weather_conditions, Road_traffic_density |
| Vehicle | Vehicle_condition, Type_of_vehicle |
| Order details | Type_of_order, multiple_deliveries |
| Other information | Festival, City |
| Delivery duration | Time_taken (min) |

**Note:** An official data dictionary was not available during this stage. Therefore, undocumented codes and unusual values were not automatically reinterpreted.

## 4. Tools and Technologies

- **Python** — data inspection and cleaning.
- **Pandas** — data manipulation and analysis.
- **NumPy** — numerical operations, where needed.
- **Jupyter Notebook / Google Colab** — interactive development and documentation.
- **GitHub** — project version control and submission.

## 5. Data Understanding and Quality Checks

The initial inspection included:

- Checking the dataset's dimensions and column names.
- Reviewing data types and non-null counts.
- Calculating missing values and their percentages.
- Checking duplicate rows and duplicate IDs.
- Examining numerical statistics and categorical distributions.
- Inspecting date, time, and geographical coordinate fields.

### Main Findings

#### Missing Values

Several columns contain missing values, including:

- `Delivery_person_Age`
- `Delivery_person_Ratings`
- `Time_Orderd`
- `Weather_conditions`
- `Road_traffic_density`
- `multiple_deliveries`
- `Festival`
- `City`

Missing values were examined to understand their distribution and possible relationships. No automatic imputation was performed because the appropriate replacement values could not be established with sufficient confidence.

#### Duplicate Records

No fully duplicated rows were identified.

The `ID` column also contains no duplicated identifiers.

#### Date and Time

The order date values were successfully interpreted using the source date format.

The time columns contain different representations, including standard time strings, decimal-looking values, and values exceeding the usual 24-hour clock range.

These values require clarification from the dataset source before applying potentially incorrect conversions. Original time values were therefore preserved.

#### Numerical and Categorical Values

Numerical variables were examined for unusual minimums, maximums, and distributions.

Categorical variables were inspected for missing values, inconsistent labels, and unexpected categories.

Some values, such as delivery ratings of 6 and certain age or coordinate values, require confirmation before being classified as invalid.

#### Geographical Coordinates

Some restaurant coordinates contain zero values or negative latitude values.

These patterns were investigated and documented as potential data quality issues. However, no coordinate corrections were applied because the correct geographical values could not be established from the available information.

## 6. Cleaning Strategy and Decisions

The cleaning process followed a conservative approach:

1. Preserve the original dataset.
2. Investigate each identified issue before making changes.
3. Avoid deleting records solely because they contain unusual values.
4. Avoid replacing missing values without a justified method.
5. Preserve ambiguous values until additional information is available.
6. Document cleaning decisions and their reasons.
7. Export the cleaned dataset separately from the raw data.

A cleaning log is included in `docs/cleaning_log.csv`.

It records the issue, affected column, number of affected rows, action taken, and reason for the decision.

## 7. Project Structure

```text
food-delivery-data-analysis/
│
├── data/
│   ├── raw/
│   │   └── README.md
│   │
│   └── processed/
│       └── cleaned_food_delivery.csv
│
├── notebooks/
│   └── 01_data_understanding_and_cleaning.ipynb
│
├── docs/
│   └── cleaning_log.csv
│
├── README.md
└── requirements.txt
```

### Folder Description

- `data/raw/`: Information about the original dataset. The original file is kept separate and unchanged.
- `data/processed/`: Contains the cleaned dataset generated by the notebook.
- `notebooks/`: Contains the notebook documenting the inspection and cleaning process.
- `docs/`: Contains the cleaning log and documented decisions.
- `requirements.txt`: Lists the Python libraries required to run the project.
- `README.md`: Provides an overview of the project and instructions.

## 8. How to Run the Project

### Step 1 — Clone the Repository

```bash
git clone https://github.com/belguerouidouaa-db/food-delivery-data-analysis.git
```

### Step 2 — Navigate to the Project Folder

```bash
cd food-delivery-data-analysis
```

### Step 3 — Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4 — Prepare the Dataset

Place the original dataset inside:

```text
data/raw/
```

The original dataset is not included in the repository. Refer to `data/raw/README.md` for information about obtaining it.

### Step 5 — Run the Notebook

Open the following notebook using Jupyter Notebook or Google Colab:

```text
notebooks/01_data_understanding_and_cleaning.ipynb
```

Run the cells in order to reproduce the inspection and cleaning process.

The notebook generates the cleaned dataset in:

```text
data/processed/cleaned_food_delivery.csv
```

## 9. Limitations and Assumptions

Some data quality issues cannot be resolved confidently without additional documentation.

These include:

- The meaning and validity of certain numerical values.
- The correct interpretation of unusual time representations.
- The validity of zero and negative geographical coordinates.
- The meaning of some categorical labels.
- The reason behind missing values and gaps in the observed dates.

These limitations are documented rather than resolved through unsupported assumptions.

The cleaned dataset should therefore be understood as a carefully inspected and prepared version of the available data, not as proof that every underlying data issue has been resolved.

## 10. Conclusion

Week 1 established a foundation for future food delivery data analysis by examining the dataset, identifying data quality issues, and documenting cleaning decisions.

The project prioritizes preserving information, making justified decisions, and maintaining a reproducible workflow.

This preparation will support subsequent analysis while ensuring that future conclusions are based on a dataset whose limitations and quality issues are clearly understood.

---

**Project:** Food Delivery Data Analysis  
**Program:** Kagnus Internship  
**Milestone:** Week 1 — Dataset Understanding & Cleaning
