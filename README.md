# Food Delivery Data Analysis

## Kagnus Internship Project

This project focuses on analyzing a food delivery dataset to understand delivery performance, investigate data quality, and explore operational factors associated with delivery duration.

The project is organized into four weekly milestones, with each stage building on the previous one. It emphasizes data accuracy, transparent analytical decisions, reproducibility, and clear communication of findings.

## Project Objectives

- Understand the dataset structure, variables, and data quality.
- Prepare a reliable dataset while preserving the original data.
- Explore delivery duration and its relationship with operational factors.
- Identify meaningful patterns and potential areas for further investigation.
- Communicate findings through data visualizations and evidence-based recommendations.

## Dataset Overview

The project uses the food delivery dataset provided through the Kagnus internship.

The dataset contains **45,584 records and 20 columns**, covering delivery information such as:

- Delivery person characteristics and ratings.
- Restaurant and delivery location coordinates.
- Order and pickup times.
- Weather and road traffic conditions.
- Vehicle type and condition.
- Multiple deliveries and festival indicators.
- Total delivery duration.

The target variable for the exploratory analysis is `Time_taken (min)`, which represents the recorded delivery duration in minutes.

The original dataset is preserved. The cleaned version is stored separately in `data/processed/`.

## Tools and Technologies

- **Python** – Main programming language.
- **Pandas** – Data manipulation and analysis.
- **NumPy** – Numerical operations.
- **Matplotlib** – Data visualization.
- **Seaborn** – Statistical visualization.
- **Jupyter Notebook / Google Colab** – Development environment.
- **Git and GitHub** – Version control and project documentation.

## Project Structure

```text
food-delivery-data-analysis/
│
├── data/
│   ├── raw/
│   │   └── README.md
│   └── processed/
│       └── cleaned_food_delivery.csv
│
├── notebooks/
│   ├── 01_data_understanding_and_cleaning.ipynb
│   └── 02_exploratory_data_analysis.ipynb
│
├── visualizations/
│   └── initial_distance_vs_duration.png
│
├── docs/
│   └── cleaning_log.csv
│
├── README.md
└── requirements.txt
```

## Weekly Progress

### Week 1 — Dataset Understanding and Cleaning

**Objective:** Understand the dataset, identify data quality issues, and prepare a separate cleaned dataset for subsequent analysis.

Work completed:

- Inspected the dataset structure, columns, data types, and descriptive statistics.
- Investigated missing values, duplicate records, inconsistent categories, and unusual numerical values.
- Examined potential anomalies in coordinate and rating fields.
- Applied only justified cleaning operations and documented relevant decisions in a cleaning log.
- Preserved the original dataset and exported the processed version.

**Key data quality observations:**

- Missing values were identified across several columns, including delivery person age, ratings, order time, weather, traffic density, and city.
- No duplicate IDs or fully duplicated records were identified.
- Fifty-three delivery ratings had a value of 6, outside the expected 1–5 scale. These values were investigated rather than automatically removed.
- Unusual coordinate values and category variations were documented without making unsupported assumptions.

**Output:** `notebooks/01_data_understanding_and_cleaning.ipynb`

### Week 2 — Exploratory Data Analysis (EDA)

**Objective:** Explore delivery duration and investigate its relationship with selected operational factors.

Work completed:

- Calculated descriptive statistics to establish a baseline for delivery duration.
- Examined the delivery-time distribution using histograms and boxplots.
- Compared delivery duration across traffic, weather, vehicle type, and multiple-delivery categories.
- Grouped delivery ratings into broader categories to make comparisons easier to interpret.
- Investigated the relationship between geographical distance and delivery duration using the Haversine formula, correlation analysis, and an initial scatter plot.
- Compared alternative coordinate-filtering scenarios to understand how coordinate assumptions influence the distance analysis.
- Conducted a sensitivity comparison to evaluate the effect of excluding the 53 rating values of 6.

**Initial delivery-duration baseline:**

| Metric | Result |
|---|---:|
| Number of records | 45,584 |
| Mean | 26.29 minutes |
| Median | 26 minutes |
| Minimum | 10 minutes |
| Maximum | 54 minutes |
| Standard deviation | 9.38 minutes |
| First quartile (Q1) | 19 minutes |
| Third quartile (Q3) | 32 minutes |

**Selected preliminary observations:**

- Orders in the `Jam` traffic category had the highest average delivery duration (31.18 minutes), while `Low` traffic had the lowest (21.27 minutes).
- Cloudy and foggy weather categories had the highest average delivery durations, at approximately 28.9 minutes.
- Motorcycle deliveries had an average duration of 27.61 minutes, compared with approximately 24.5 minutes for scooter and electric scooter deliveries.
- Delivery duration increased across the multiple-delivery categories: the average ranged from 22.88 minutes for zero multiple deliveries to 47.82 minutes for three.
- The rating-group comparison showed longer average delivery durations in the lower-rating group than in the higher-rating group. This is an association, not evidence of causation.

These observations are exploratory and should be interpreted alongside group sizes, missing values, and the limitations of the dataset.

**Output:** `notebooks/02_exploratory_data_analysis.ipynb`

**Initial distance visualization:** `visualizations/initial_distance_vs_duration.png`

### Upcoming Milestones

- **Week 3 — Data Visualization:** Develop and refine the final visualizations to communicate the most important patterns.
- **Week 4 — Final Analysis and Reporting:** Consolidate findings, develop evidence-based recommendations, and prepare the final project report.

## Running the Project

1. Clone or download this repository.
2. Install the required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Ensure that the cleaned dataset is available at:

   `data/processed/cleaned_food_delivery.csv`

4. Open the required notebook using Jupyter Notebook, JupyterLab, or Google Colab.
5. Execute the notebook cells in order.

The original dataset is not included in the repository unless redistribution is permitted. Refer to `data/raw/README.md` for its source and access information.

## Assumptions and Limitations

- The dataset does not include an official data dictionary, so undocumented variable meanings and encodings are not assumed.
- Some missing values and unusual observations are retained where their correction or removal cannot be justified.
- The coordinate-based distance analysis uses alternative filtering scenarios because the meaning of certain coordinate values could not be confirmed.
- Correlation and grouped comparisons identify associations and patterns; they do not establish causal relationships.
- Results depend on the available records and their data quality.

## Repository

[Food Delivery Data Analysis — GitHub](https://github.com/belguerouidoua-db/food-delivery-data-analysis)

