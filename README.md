# Copper Price Dataset

A public repository of historical copper price data from the Winding Wires Manufacturers' Association of India (WWMAI).

## Description

This repo contains copper price data extracted from official WWMAI price list circulars. The data tracks the indicative base price of 8 mm dia. Electrolytic CC Copper wire Rods along with all the components that contribute to the final price calculation.

## Data Structure

The repository is organized as follows:

```
copper-price-data/
│
├── data/
│   ├── processed/
│   │   └── copper_prices.csv   # Consolidated dataset in CSV format
│   │
│   └── raw/                    # Original PDF circulars
│       └── YYYY/               # Organized by year
│           └── MM-Month/       # Then by month
│               └── YYYY-MM-DD.pdf
│
└── scripts/                    # Utility scripts for processing
```

## CSV Data Format

The dataset (`data/processed/copper_prices.csv`) contains these fields:

| Field | Description |
|-------|-------------|
| date | Publication date of the price list |
| reference_number | Document reference number |
| copper_grade | Specification of the copper product |
| lme_price_usd_mt | London Metal Exchange price in USD per metric ton |
| premium_usd_mt | Premium for CC Copper Wire Rods in USD per MT |
| transaction_cost_usd_mt | Transaction costs in USD per MT |
| exchange_rate_inr_usd | Exchange rate (INR per USD) |
| multiplying_factor | Multiplying factor used by WWMAI |
| freight_handling_inr_kg | Freight and handling charges in INR per kg |
| base_price_inr_kg | Final calculated base price in INR per kg |
| valid_from | Start date of price validity |
| valid_to | End date of price validity |
| notes | Additional information |

## Usage

### Accessing the Data

The data can be used in various ways:

1. **Direct download**: Get the CSV file for use in your application
2. **Git clone**: Clone the entire repository to access both raw PDFs and processed data
   ```
   git clone https://github.com/iodize6399/wwmai-copper-data.git
   ```
3. **Staying updated**: Pull the latest changes periodically to get the most recent data

### Example Usage (Python)

```python
import pandas as pd

# Load the data
copper_data = pd.read_csv('data/processed/copper_prices.csv')

# Convert date columns to datetime
date_columns = ['date', 'valid_from', 'valid_to']
for col in date_columns:
    copper_data[col] = pd.to_datetime(copper_data[col])

# Analyze price trends
monthly_avg = copper_data.groupby(copper_data['date'].dt.strftime('%Y-%m'))[['base_price_inr_kg']].mean()
print(monthly_avg)
```

## Data Extraction Method

The data in this repository has been extracted from PDF documents using Optical Character Recognition (OCR) combined with Large Language Models (LLMs). The automated extraction process might occasionally introduce errors.

**Important:** Users are encouraged to verify any critical data against the original PDF files provided in the `data/raw/` directory. If you find any discrepancies between the CSV data and the source PDFs, please report them by [opening an issue](https://github.com/iodize6399/wwmai-copper-data/issues/new) on this repository.

## Updates

This dataset is updated regularly as new price lists are published. Each update includes:
- The original PDF source files
- Updates to the consolidated CSV

## License

This dataset is available under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

## Disclaimer

This repository is not officially affiliated with the Winding Wires Manufacturers' Association of India. The data is collected from publicly available circulars for research and informational purposes only. Use at your own risk.