# Data Mining: Energy Transition Forecasting

This project explores global climate and energy data and forecasts the transition from fossil fuels to renewable energy by country. The analysis is implemented in Jupyter notebooks and uses annual renewable/fossil energy shares, CO2 emissions, population, climate events, carbon prices, and temperature anomalies.

## Project overview

- **Exploratory analysis:** [`eda.ipynb`](./eda.ipynb)
- **Forecasting model:** [`Model.ipynb`](./Model.ipynb)
- **Forecast output:** [`CSV/renewable_fossil_forecast_2027_2035.csv`](./CSV/renewable_fossil_forecast_2027_2035.csv)
- **Historical scope:** 50 countries, 2000-2026
- **Forecast horizon:** 2027-2035

The forecasting notebook creates one-year and two-year lag features, trains several regression models, and performs a time-based validation using 2024-2026 as test years. Ridge regression achieved:

| Target | MAE | RMSE | R² |
|---|---:|---:|---:|
| Renewable share | 1.566 | 1.985 | 0.973 |
| Fossil share | 1.636 | 2.061 | 0.976 |

## Dataset files

| File | Description |
|---|---|
| [`CSV/energy_mix_yearly.csv`](./CSV/energy_mix_yearly.csv) | Annual coal, oil, gas, nuclear, hydro, solar, wind, renewable, and fossil shares |
| [`CSV/co2_emissions_yearly.csv`](./CSV/co2_emissions_yearly.csv) | Annual CO2 emissions, population, per-capita emissions, and emissions intensity |
| [`CSV/temperature_anomaly_monthly.csv`](./CSV/temperature_anomaly_monthly.csv) | Monthly temperature anomalies and atmospheric CO2 concentrations |
| [`CSV/carbon_prices_daily.csv`](./CSV/carbon_prices_daily.csv) | Daily carbon-market prices |
| [`CSV/climate_events.csv`](./CSV/climate_events.csv) | Major climate, weather, disaster, and policy events |
| [`CSV/merged.csv`](./CSV/merged.csv) | Combined source data used for analysis |
| [`CSV/renewable_fossil_forecast_2027_2035.csv`](./CSV/renewable_fossil_forecast_2027_2035.csv) | Country-level renewable and fossil forecasts from 2027 through 2035 |

## Methods

The modeling workflow includes:

1. Loading and merging the annual energy-mix and CO2 data.
2. Creating lag features for renewable, fossil, and individual fuel shares.
3. Encoding country information and standardizing numeric features.
4. Comparing a naive baseline with Ridge Regression, Gradient Boosting, and Random Forest.
5. Evaluating predictions with MAE, RMSE, and R².
6. Generating recursive forecasts for 2027-2035.
7. Visualizing the historical transition and model comparisons.

## Getting started

### 1. Clone the repository

```bash
git clone https://github.com/BammLNG/Data-Mining.git
cd Data-Mining
```

### 2. Create a Python environment

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.venv\Scripts\Activate.ps1
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install pandas numpy matplotlib scikit-learn jupyter
```

### 4. Run the notebooks

```bash
jupyter notebook
```

Open `eda.ipynb` for exploratory data analysis, then open `Model.ipynb` to train the models and generate forecasts.

The notebooks may also be opened in Google Colab. When running locally, keep the repository structure unchanged so the CSV files remain under the `CSV/` directory.

## Results

The [`Model.ipynb`](./Model.ipynb) notebook includes:

- Historical renewable and fossil energy trends
- Countries with the largest positive and negative changes
- Predicted-versus-actual plots
- Feature-importance analysis
- Four-model performance comparison
- Recursive 2027-2035 country forecasts

## Repository structure

```text
Data-Mining/
|-- eda.ipynb
|-- Model.ipynb
|-- README.md
`-- CSV/
    |-- carbon_prices_daily.csv
    |-- climate_events.csv
    |-- co2_emissions_yearly.csv
    |-- energy_mix_yearly.csv
    |-- merged.csv
    |-- renewable_fossil_forecast_2027_2035.csv
    `-- temperature_anomaly_monthly.csv
```