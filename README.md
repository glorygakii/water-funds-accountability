# Climate-Smart Agriculture Analytics

A Python data science project analysing crop yield patterns against climate variables to guide agricultural planning in Sub-Saharan Africa.

## Project Overview

Maji Ndogo is a fictional region used as a simulated dataset by ExploreAI Academy, modelled on real agricultural challenges across Sub-Saharan Africa. This project analyses crop yield data against climate variables to identify patterns that could help farmers and agricultural planners make better decisions about what to grow, when to plant, and where to invest.

## Live Portfolio Page

View the full case study at: [glorygakii.com/projects/agriculture-pipeline.html](https://glorygakii.com/projects/agriculture-pipeline.html)

## Tools Used

- Python 3
- Pandas
- Matplotlib
- SQLAlchemy
- Jupyter Notebook
- Excel

## Screenshots

### Crop Yield & Climate Analysis
![Crop Yield & Climate Analysis](assets/python-analysis.png)

### Data Ingestion & Pipeline
![Data Pipeline](assets/python-pipeline.png)

### Excel Summary Output
![Excel Summary](assets/agriculture-excel.png)

## Notebooks

| Notebook | Description |
|----------|-------------|
| [P1 — Data Cleaning & Analysis](notebooks/P1_data_cleaning_analysis.ipynb) | Introduces the Maji Ndogo dataset; performs data cleanup and analysis covering crop preferences, fertile grounds, climate and geography, and data filtering |
| [P2 — Exploratory Data Analysis](notebooks/P2_EDA_analysis.ipynb) | Univariate and multivariate analysis across geographic, weather, and soil features; explores crop yield relationships across 8 crop types including coffee |
| [P3 — Data Pipeline & Validation](notebooks/P3_data_pipeline.ipynb) | Refactors code into a modular pipeline (ingestion, cleaning, corrections); validates the full dataset against weather station data using hypothesis testing |

## Pipeline Stages

1. **Data Ingestion** — SQLite database and web CSV sources
2. **Data Cleaning** — fixing column swaps, spelling errors, negative values
3. **Statistical Analysis** — correlation between climate variables and crop yields
4. **Visualisation** — Matplotlib charts
5. **Excel Export** — clean summary for non-technical stakeholders

## Key Python Techniques

- Modular pipeline design using functions and classes
- Multi-table SQL JOINs via SQLAlchemy
- Data cleaning and validation with Pandas
- Statistical correlation analysis across 8 crop types
- Matplotlib visualisations for data storytelling
- Excel export using openpyxl

## Core Pipeline Code

```python
def create_db_engine(db_path):
    """Creates and returns a SQLAlchemy database engine."""
    engine = create_engine(db_path)
    return engine

def query_data(engine, sql_query):
    """Queries the database and returns a DataFrame."""
    with engine.connect() as connection:
        df = pd.read_sql_query(text(sql_query), connection)
        return df

def read_from_web_CSV(URL):
    """Reads a CSV file from a web URL into a DataFrame."""
    df = pd.read_csv(URL)
    return df

# Run the full pipeline
field_df   = query_data(create_db_engine(config_params['db_path']),
                        config_params['sql_query'])
weather_df = read_from_web_CSV(config_params['weather_csv_path'])
```

## Key Findings

- Identified strong correlation between seasonal rainfall and crop yields across regions
- Flagged temperature anomaly years where yields dropped significantly
- Validated data integrity by cross-referencing field measurements against weather station records
- Produced a clean Excel summary accessible to agricultural extension officers
- Built a reproducible pipeline that can be rerun as new data becomes available

## Project Structure

```
climate-smart-agriculture/
├── notebooks/
│   ├── P1_data_cleaning_analysis.ipynb
│   ├── P2_EDA_analysis.ipynb
│   └── P3_data_pipeline.ipynb
├── data/
│   └── Maji_Ndogo_farm_survey_small.db
├── outputs/
│   └── agriculture_summary.xlsx
└── README.md
```

## Author

Glory Gakii Mbiti — Data Scientist and BI Analyst based in Nairobi, Kenya

- Portfolio: [glorygakii.com](https://glorygakii.com)
- LinkedIn: [linkedin.com/in/glorygakii](https://linkedin.com/in/glorygakii)
- Email: [gakiimbiti6@gmail.com](mailto:gakiimbiti6@gmail.com)
