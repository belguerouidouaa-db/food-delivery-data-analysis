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
│   ├── 02_exploratory_data_analysis.ipynb
│   └── 03_visualization.ipynb
│
├── visualizations/
│   ├── initial_distance_vs_duration.png
│   ├── 01_delivery_duration_distribution.png
│   ├── 02_traffic_comparison.png
│   ├── 03_weather_comparison.png
│   ├── 04_distance_vs_duration.png
│   └── 05_vehicle_comparison.png
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

### Week 3 — Visualization and Interpretation

**Objective:** Transform the findings from Week 2 into clear and meaningful visualizations to communicate delivery-duration patterns and differences across operational factors.

Five visualizations were created using Matplotlib and Pandas, based on the cleaned dataset and calculations performed during the previous weeks.

**Visualizations created:**

**1. Delivery Duration Distribution — Histogram**

File: [`01_delivery_duration_distribution.png`](visualizations/01_delivery_duration_distribution.png)

- Displays the distribution of delivery durations across the dataset.
- Most delivery durations are concentrated approximately between 19 and 30 minutes.
- The distribution is positively (right) skewed, with fewer deliveries taking considerably longer.

**2. Traffic Comparison — Bar Chart**

File: [`02_traffic_comparison.png`](visualizations/02_traffic_comparison.png)

- Compares median delivery duration across traffic categories.
- Jam traffic has the highest median delivery duration (31 minutes), while Low traffic has the lowest (20 minutes).
- High and Medium traffic categories have similar median durations of approximately 27 minutes.

**3. Weather Comparison — Bar Chart**

File: [`03_weather_comparison.png`](visualizations/03_weather_comparison.png)

- Compares average delivery duration across weather conditions.
- Cloudy and Fog conditions show the highest average delivery durations, at approximately 28.9 minutes.
- Sunny conditions show the lowest average duration, at approximately 21.9 minutes.

**4. Distance vs. Delivery Duration — Scatter Plot**

File: [`04_distance_vs_duration.png`](visualizations/04_distance_vs_duration.png)

- Examines the relationship between calculated delivery distance and delivery duration.
- The Pearson correlation coefficient is approximately 0.3205, indicating a positive association between distance and delivery duration.
- Scenario B was used for coordinate handling: suspicious delivery-coordinate pairs and zero restaurant coordinates were excluded, while negative restaurant coordinates were converted to absolute values. This assumption was retained as a sensitivity-analysis approach rather than a verified geographical correction.

**5. Vehicle Comparison — Box Plot**

File: [`05_vehicle_comparison.png`](visualizations/05_vehicle_comparison.png)

- Compares delivery-duration distributions across vehicle categories using medians, interquartile ranges, whiskers, and outliers.
- Motorcycles and bicycles have median delivery durations of approximately 26 minutes, while scooters and electric scooters have medians of approximately 24 minutes.
- The bicycle category contains only 68 deliveries, compared with 26,429 motorcycle deliveries, so comparisons involving bicycles should be interpreted cautiously.

**Tools and techniques used:**

- **Pandas:** Data preparation, grouping, and aggregation.
- **NumPy:** Numerical calculations.
- **Matplotlib:** Creating and customizing visualizations.
- **Python:** Data manipulation, functions, and loops.

**Key notes and limitations:**

- All visualizations were generated using the cleaned dataset from Week 1 and the analytical findings from Week 2.
- The original Week 1 and Week 2 notebooks were preserved.
- Observed differences and relationships do not establish causation.
- Some categories have considerably smaller sample sizes than others.
- Distance results depend on the coordinate-handling assumptions used in Scenario B.

**Deliverables:**

- `notebooks/03_visualization.ipynb`
- Five exported PNG visualizations in the `visualizations/` folder.
- Written interpretations and limitations for each chart.

**Status:** Week 3 visualization and interpretation completed.

### Upcoming Milestone

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

