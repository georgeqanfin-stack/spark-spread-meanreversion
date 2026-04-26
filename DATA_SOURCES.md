# Data Sources

Download these files and place them in data/raw/ before running the notebooks.

## 1. German Day-Ahead Power (Germany.csv)
Source: Ember Climate
URL: https://ember-energy.org/data/european-wholesale-electricity-price-data/
Download: European wholesale electricity prices - hourly (ZIP)
Filter to Germany only when loading in notebook.

## 2. TTF Natural Gas (ttf_gas_raw.csv)
Source: Investing.com
URL: https://www.investing.com/commodities/dutch-ttf-gas-c1-futures-historical-data
Date range: Jan 2021 - present
Save as: data/raw/ttf_gas_raw.csv

## 3. EU ETS Carbon (carbon_ets_raw.csv)
Source: Investing.com
URL: https://www.investing.com/commodities/carbon-emissions-historical-data
Date range: Jan 2021 - Dec 2023
Save as: data/raw/carbon_ets_raw.csv

## 4. Extension files (2024 onwards)
TTF Gas 2024+:
URL: https://www.investing.com/commodities/dutch-ttf-gas-c1-futures-historical-data
Date range: Jan 2024 - present
Save as: data/raw/ttf_gas_2024.csv

Carbon 2024+:
URL: https://www.investing.com/commodities/carbon-emissions-historical-data
Date range: Jan 2024 - present
Save as: data/raw/carbon_2024.csv

## Notes
- Investing.com requires you to set the date range manually using the calendar picker
- All files should be saved as CSV in the data/raw/ folder
- The data/ folder is excluded from the repository via .gitignore
- Run notebooks in order: 01 through 05
