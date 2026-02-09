# Financial Market Microstructure – Project 2

## Trade Durations & Price Durations Analysis

Analysis of intraday trade durations and price durations for two stocks listed on the Warsaw Stock Exchange (GPW), conducted as part of the **Financial Market Microstructure** course.

---

## Overview

This project examines high-frequency transaction data for two companies with contrasting characteristics:

| | **Company D** | **Company H** |
|---|---|---|
| Price range | 400–500 PLN | 7–9 PLN |
| Avg. daily transactions | ~910 | ~2 338 |
| Liquidity | Lower | Higher |

The analysis covers two main topics:

### Part 1 – Trade Durations
- Construction of trade duration time series (continuous trading phase: 9:00–16:50)
- Descriptive statistics and comparison between companies
- Cross-sectional averages revealing intraday seasonality (U-shape pattern)
- Removal of diurnal seasonality using **Flexible Fourier Form (FFF)** method (`diurnalAdj` from `ACDm` package), estimated separately for each day of the week
- Verification of deseasonalization effectiveness

### Part 2 – Price Durations
- Construction of price duration time series for two thresholds: $p_0 = 0.01$ PLN (1 grosz) and $p_0 = 0.05$ PLN (5 groszy)
- Descriptive statistics for a common threshold ($p_0 = 0.05$ PLN)
- Cross-sectional averages for both thresholds (10-minute intervals)
- Comparison of trade liquidity vs. price activity

## Key Findings

- **Company H** trades frequently (short trade durations) but price moves slowly (long price durations for the 5 gr threshold)
- **Company D** trades less frequently but generates faster and more frequent price changes
- **Trade liquidity and price activity are two distinct dimensions** — high transaction frequency does not imply high price volatility

## Tech Stack

- **R** with R Markdown (`.Rmd` → HTML report)
- Key packages: `tidyverse`, `lubridate`, `moments`, `ACDm`, `kableExtra`, `hms`

## Project Structure

```
├── AGH-Project-2-Mikrostruktura-Rynkow-Finansowych.Rmd   # Main R Markdown source
├── spolkaD.csv             # Tick data – Company D
├── spolkaH.csv             # Tick data – Company H
└── README.md
```

## How to Run

1. Place `spolkaD.csv` and `spolkaH.csv` in the same directory as the `.Rmd` file
2. Open the `.Rmd` file in RStudio
3. Click **Knit** → HTML report will be generated
