# Food Delivery Data Analysis — Week 1

This repository contains the Week 1 dataset-understanding and cleaning work.

## Structure

- `data/raw/`: original source dataset (place `Food delivery Dataset.csv` here; do not modify it)
- `data/processed/cleaned_food_delivery.csv`: cleaned export
- `notebooks/01_data_understanding_and_cleaning.ipynb`: documented analysis and cleaning workflow
- `docs/cleaning_log.csv`: issues, actions, and justifications

## Run the notebook

1. Install dependencies with `pip install -r requirements.txt`.
2. Put the original CSV in `data/raw/`.
3. Open the notebook and run all cells from top to bottom.

The workflow preserves missing and suspicious values unless a correction can be justified. Only the verified `Order_Date` format is standardized.
