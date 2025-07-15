# Copper Price Dataset

A public repository of historical copper price data from the Winding Wires Manufacturers' Association of India (WWMAI).

## Description

This repo contains copper price data extracted from official WWMAI price list circulars. The data tracks the indicative base price of 8 mm dia. Electrolytic CC Copper wire Rods along with all the components that contribute to the final price calculation.

> **Note:** Data is currently published on a **semi‑weekly** cadence. See the [roadmap](#roadmap) below for daily and monthly circulars.

## Data Structure

The repository is organized as follows:

```
wwmai-copper-data/
└── data/
   ├── processed/
   │   └── copper_prices.csv   # Consolidated dataset in CSV format
   │
   └── raw/                    # Original PDF circulars
       └── YYYY/               # Organized by year
           └── MM-Month/       # Then by month
               └── file.pdf

```

## CSV Schema

The dataset (`data/processed/copper_prices.csv`) contains these fields:

| Field | Description |
|-------|-------------|
| date | Publication date of the price list |
| reference_number | Document reference number |
| lme_price_usd_mt | London Metal Exchange price in USD per metric ton |
| premium_usd_mt | Premium for CC Copper Wire Rods in USD per MT |
| transaction_cost_usd_mt | Transaction costs in USD per MT |
| exchange_rate_inr_usd | Exchange rate (INR per USD) |
| multiplying_factor | Multiplying factor used by WWMAI |
| freight_handling_inr_kg | Freight and handling charges in INR per kg |
| base_price_inr_kg | Final calculated base price in INR per kg |
| valid_from | Start date of price validity |
| valid_to | End date of price validity |

## Usage

### Accessing the Data

The data can be used in various ways:

1. **Direct download**: Get the CSV file for use in your application
2. **Git clone**: Clone the entire repository to access both raw PDFs and processed data
   ```
   git clone https://github.com/iodize6399/wwmai-copper-data.git
   ```
3. **Staying updated**: Pull the latest changes periodically to get the most recent data or [access the live dataset directly](https://raw.githubusercontent.com/iodize6399/wwmai-copper-data/refs/heads/main/data/processed/copper_prices.csv).

## Data Extraction Method
The data in this repository has been extracted from PDF documents using Optical Character Recognition (OCR) combined with Large Language Models (LLMs). The automated extraction process might occasionally introduce errors.

**Important:** Users are encouraged to verify any critical data against the original PDF files provided in the `data/raw/` directory. If you find any discrepancies between the CSV data and the source PDFs, please report them by [opening an issue](https://github.com/iodize6399/wwmai-copper-data/issues/new) on this repository. 

## Interactive Visualization
An interactive, auto-updating chart of the copper base price (INR/kg) over each validity interval is available on Datawrapper:

[View the chart →](https://www.datawrapper.de/_/ilR6g/)

<p align="left">
  <a href="https://www.datawrapper.de/_/ilR6g/" target="_blank" rel="noopener noreferrer">
    <img
      src="https://datawrapper.dwcdn.net/ilR6g/full.png"
      alt="Copper Base Price (INR/kg) — Validity Intervals"
      width="600"
      style="max-width: 100%; height: auto;"
    />
  </a>
</p>

The chart fetches the latest CSV from this repository on every load, so all new entries are reflected immediately.

## Roadmap

- **Semi‑weekly (current):** New circulars every 3–4 days, ingested and processed.  
- **Daily (planned):** Automate ingestion of daily circulars.  
- **Monthly (planned):** Automate ingestion of monthly circulars.  

## License

This dataset is available under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

## Disclaimer

This repository is not officially affiliated with the Winding Wires Manufacturers' Association of India. The data is collected from publicly available circulars for research and informational purposes only. **Use at your own risk.**