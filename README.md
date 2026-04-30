# Project Name: Data Analysis & API Pipeline

## Overview
This repository contains the code and methodology for processing, enriching, and analyzing our dataset. The project features a robust data pipeline that integrates with an external API, optimizes execution through local caching, and performs comprehensive statistical analysis and modeling.

## Dataset
* **Description:** Data set is from hugging face. Here is the link:
https://huggingface.co/datasets/prometheus-eval/Feedback-Collection
* **Format:** Data is primarily processed and stored in CSV format.
* **Preprocessing Steps:** The pipeline handles missing values, standardizes numerical features, and performs necessary encodings (e.g., one-hot encoding) to prepare the data for downstream analysis.

## API Integration & Prerequisites
This codebase relies on an external API to process, classify, or enrich the dataset. 

⚠️ **IMPORTANT: Bring Your Own API Key**
To run the API pipeline, you must obtain your own API credentials. 
1.  Register with the API provider to get your key.
2.  Securely configure your key as an environment variable or via a `.env` file:
    ```bash
    export API_KEY="your_personal_api_key_here"
    ```
*(Note: Do not hardcode or commit your API key to version control!)*

## Optimization: CSV Caching 
To significantly reduce computation time and eliminate redundant API costs, the pipeline saves all intermediate API responses and processed data directly to a local CSV file.
* **Cost & Time Efficiency:** API calls are often the main bottleneck in both execution time and budget. By saving the processed dataset locally (`processed_data.csv`), subsequent analysis runs read directly from the disk. 
* **Rate Limit Protection:** This caching mechanism also ensures you don't exhaust your API rate limits during the exploratory data analysis (EDA) or model tuning phases.

## Analysis
The core analysis focuses on extracting insights and building models based on the processed dataset.
* **Methodology:**
1. Cleaned and formatted the csv
2. Calibration and test set formed 100 rows/1900 rows. Calibration had human label and llm label.
3. run through xgboost boosted tree regressor

## Getting Started
1.  Clone this repository to your local machine.
2.  Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3.  Configure your API key in the environment.
4.  Run the API fetching script to generate the initial CSV.
5.  Execute the analysis script/notebook on the locally saved data.
