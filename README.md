# WA-Housing-Model-2021-analysis

## Project Overview
This repository contains the end-to-end data engineering, exploratory analysis, and predictive modelling phases of the **WA Housing Model Project**. The objective is to quantify and predict housing stress levels across Western Australian suburbs by analysing the relationship between household income, mortgage repayments, and rental costs using 2021 Census data.

This analysis is the foundational component of a three-repository portfolio project:
1. **`WA-Housing-Model-2021-analysis` (Current Repo):** Data ETL, Geospatial Wrangling, and Machine Learning.
2. **`WA-Housing-Model-2021-service`:** A Flask API microservice that serves the trained Random Forest model.
3. **`WA-Housing-Model-2021-dashboard`:** An interactive Streamlit dashboard for real-time scenario simulation.

*Note: The analysis and findings documented in this repository are based on a data snapshot from the **2021 ABS Census**, processed on **14 February 2026**.*

## Tech Stack
* **Data Processing:** [Pandas](http://pandas.pydata.org) (Feature engineering, mid-point imputation, and data cleaning)
* **Geospatial:** [GeoPandas](https://geopandas.org) (Spatial joins and GDA2020/EPSG:7844 Coordinate Reference Systems)
* **Machine Learning:** [Scikit-Learn](https://scikit-learn.org) (Random Forest Regressor, Lasso Regression, and Standardisation)
* **Serialization:** [Joblib](https://joblib.readthedocs.io) (Exporting production-ready model binaries)
* **Analysis:** [Jupyter Notebooks](https://jupyter.org) for transparent, modular data science workflows

## Methodology
The core objective is to calculate and predict a **Housing Stress Index**, defined by the percentage of a suburb's population where housing costs (rent or mortgage) exceed 30% of gross household income. 

The project is documented across four modular notebooks:
1.  **[00_dictionary_creation.ipynb](./notebooks/00_dictionary_creation.ipynb):** Mapping census categorical ranges to numerical mid-points.
2.  **[01_data_cleaning.ipynb](./notebooks/01_data_cleaning.ipynb):** Aggregating raw G-series tables and performing spatial joins.
3.  **[02_statistical_eda.ipynb](./notebooks/02_statistical_eda.ipynb):** Identifying correlations and economic drivers.
4.  **[03_regression_modelling.ipynb](./notebooks/03_regression_modelling.ipynb):** Training and validating the Random Forest model (98% R²).

## Getting Started (Reproducibility)
To run this analysis locally, ensure you have Python 3.11+ installed:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/GaryUWA/WA-Housing-Model-2021-analysis.git
    cd WA-Housing-Model-2021-analysis
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv .venv
    source .venv/scripts/activate # Windows
    # source .venv/bin/activate # macOS/Linux
    ```

3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Data Acquisition:**
    Due to file size constraints, raw data is not included in this repository. To reproduce the results, download the following and place them in their respective folders:

    **A. Tabular Data (`data/raw/`):**
    Download the **2021 Census G-Series** for Western Australia (Suburbs and Localities) from the [ABS DataPacks portal](https://www.abs.gov.au/census/find-census-data/datapacks). Ensure the following files are present:
    * `G01`, `G02`, `G33`, `G38`, `G40`
    * `G46A` and `G46B` (Both parts are required)
    * `G54A` and `G54B` (Both parts are required)

    **B. Spatial Data (`data/spatial/`):**
    Download the **ASGS Edition 3 SAL boundaries** from the [ABS Digital Boundary Files page](https://www.abs.gov.au/statistics/standards/australian-statistical-geography-standard-asgs-edition-3/jul2021-jun2026/access-and-downloads/digital-boundary-files#downloads-for-gda2020-digital-boundary-files). 
    * Select the link: **Suburbs and Localities - 2021 - Shapefile** (under the GDA2020 header).
    * Extract all associated files (`.shp`, `.shx`, `.dbf`, `.prj`, etc.) into the `data/spatial/` directory.

5.  **Run the Analysis:**
    Execute the notebooks in numerical order to generate the processed datasets and the final model binaries located in the `models/` folder.

## Model Export & Production
The final Random Forest model and its corresponding scaler are exported as `.joblib` files. These artifacts are designed to be consumed by the **WA Housing Service (Flask API)** to provide real-time predictions for the final dashboard application.

## Disclaimer
This project is for **educational and portfolio purposes only**. While it utilises official data from the [Australian Bureau of Statistics (ABS)](https://www.abs.gov.au/), the "Housing Stress Index" and subsequent predictions are independent calculations. This analysis should not be used for real-estate investment, financial advice, or government policy decisions. Development was AI-assisted by Gemini for framework scaffolding, rapid development, and debugging; no sensitive information from the ABS datasets were shared with the AI during this process.

## Attribute & License
This project is licensed under the [MIT License](./LICENSE)

## Author
* **Zain Zabidi** - Data Science Graduate (UWA)