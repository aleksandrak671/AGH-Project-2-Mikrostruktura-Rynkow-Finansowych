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
- Descriptive statistics and comparison between companies (highlighting overdispersion)
- Cross-sectional averages revealing intraday seasonality (U-shape pattern)
- Removal of diurnal seasonality using the **Flexible Fourier Form (FFF)** method (`diurnalAdj` from the `ACDm` package), **estimated as a single model with dummy variables for days of the week** (`aggregation = "weekdays"`)
- Verification of deseasonalization effectiveness

### Part 2 – Price Durations
- Construction of price duration time series for two thresholds: $p_0 = 0.01$ PLN (1 grosz) and $p_0 = 0.05$ PLN (5 groszy)
- Descriptive statistics for a common threshold ($p_0 = 0.05$ PLN)
- Cross-sectional averages for both thresholds (10-minute intervals, visualized with a logarithmic scale)
- Comparison of trade liquidity vs. price activity

## Key Findings

- **Trade liquidity and price activity are distinct dimensions** deeply influenced by a stock's nominal price.
- **Company H** trades very frequently (high transaction liquidity), leading to faster price changes at the lowest threshold (1 gr). However, due to its low nominal price, generating a larger nominal move (5 gr) requires significant time and accumulation of smaller changes.
- **Company D** trades less frequently, but because 5 gr constitutes a minimal fraction of its high nominal price (400–500 PLN), it reaches this price threshold much faster than Company H.

## Tech Stack

- **R** with R Markdown (`.Rmd` → HTML report)
- Key packages: `tidyverse`, `lubridate`, `moments`, `ACDm`, `kableExtra`, `hms`

## Project Structure

```text
├── AGH-Project-2-Mikrostruktura-Rynkow-Finansowych.Rmd   # Main R Markdown source
├── spolkaD.csv             # Tick data – Company D
├── spolkaH.csv             # Tick data – Company H
└── README.md
