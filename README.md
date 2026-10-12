# Berlin Housing Market 2020–2026: Prices, Rents and Rental Yields

## 1. Introduction

**Context.** After the Covid-19 pandemic, the war in Ukraine, and the energy crisis, inflation in Europe rose sharply. To bring it down, the ECB raised interest rates from mid-2022, and mortgages became much more expensive. In this dataset, the average mortgage rate rises from 1.16% in December 2020 to 4.1% in mid-2023 and then eases to 3.8% in April 2026, while rents keep rising. [*Germany: Mortgage credit interest*](https://www.theglobaleconomy.com/Germany/mortgage_interest_rate/). Anyone deciding where to rent, buy or invest in Berlin needs to know what the data shows: how prices and rents moved, where, and what drives the differences.

**Goal.** Answer five business questions for people who rent, buy, or invest in Berlin, using real-looking listing data.

**Data.** [*Berlin Real Estate: Sales & Rentals 2020-2026*](https://www.kaggle.com/datasets/sergionefedov/berlin-real-estate-sales-and-rentals-2020-2026) on Kaggle (Sergio Nefedov). I use three of its files:

| File | What one row is | Used for |
|---|---|---|
| `kiez_prices_monthly.csv` | one district (Ortsteil) in one month | trends over time |
| `secondary_sales.csv` | one resale listing | resale prices |
| `rentals.csv` | one rental listing | rents |

**Tools.** Python, pandas, matplotlib.

**How to read this notebook.** Each question follows the same pattern: *Question → Chart or table → "Further analysis"*. Prices are **asking prices from listings** and medians are used throughout, because medians are not distorted by a few extreme listings.

## Project at a glance
The whole project on one page: where the data comes from, how it is prepared, the five questions answered, and what the reader gets at the end.
![Project overview](figures/project_overview.png)

## Key findings
- **Rents rose almost twice as fast as resale prices:** +43.5% vs. +23.0% between 2020 and 2025.
- **Prices barely reacted to the rate shock:** while the mortgage rate rose from 1.1% to 4.1%, resale prices dipped only about 5% and had fully recovered by April 2026.
- **Location dominates:** the most expensive district costs 3.1× the cheapest per m² (€6,155 vs. €1,967). Price falls about 60% from the centre to 10–15 km, then levels off.
- **Gross yields are thin:** 3.48%–3.97% by district, above today's 3.1% mortgage rate but below the 4.1% peak of 2023.
- **Features are priced in:** compared with neighbours in the same district and year, energy class H flats sell for about 20% less and A+ for about 50% more; flats needing renovation sell for 22% less.
- **Buying overtook renting in monthly cost:** in 2020–21 the loan payment for a flat was about 19% below the rent; since January 2022 it is higher (peak 1.42× the rent in 2023, 1.13× in April 2026). In 2025 buying and renting cost about the same in most districts (0.95×–1.12×).

## 2. Business questions

| # | Business question | Who cares | Decision it supports |
|---|---|---|---|
| **Q1** | How did prices and rents change from 2020 to 2026, and what happened when mortgage rates rose? | Everyone | Timing; rent or buy |
| **Q2** | Which districts are the most and least expensive, and how does price change with distance from the centre? | Buyers, renters | Where to look |
| **Q3** | Where is the gross rental yield highest, and does it cover the mortgage rate? | Investors | Where to buy to let |
| **Q4** | How much more are flats with a better energy class, a newer building or a better condition worth? | Owners, investors, buyers | Which features justify a higher price |
| **Q5** | Is it cheaper to rent or to buy, and did that change when mortgage rates rose? | Renters, buyers | Rent or buy |

## 3. Data preparation
### 3.1 Load only what is needed
The files have many columns. For these five questions I keep a small set of them. *To run this notebook, put the three CSV files in a folder called `data/` next to it.*

### 3.2 Quality checks
Before analysing, I check whether the data is complete and unique.

![Prices and rents vs. mortgage rate](figures/q1_trends.png)
![Gross rental yield by district](figures/q3_yield.png)
![Buying vs. renting](figures/q5_buy_vs_rent.png)

## Data
[Berlin Real Estate: Sales & Rentals 2020-2026](https://www.kaggle.com/datasets/sergionefedov/berlin-real-estate-sales-and-rentals-2020-2026) (Kaggle, Sergio Nefedov). Three of the five files are used. The data is **not** included in this repository; download it and place the CSVs in `data/` (see `data/README.txt`).

## How to run
```bash
pip install -r requirements.txt
jupyter notebook berlin_housing_analysis.ipynb
```
Run all cells from top to bottom. Charts are also saved to `figures/`.

## Skills demonstrated
Data cleaning and quality checks · exploratory analysis with pandas (`groupby`, medians, indices, binning) · comparing like with like (price relative to the same district and year) · financial metric design (gross rental yield vs. mortgage rate, loan payment vs. rent with explicit assumptions) · clear data visualisation · business storytelling ("So what?" per question) · stating limitations honestly.

## Limitations
- Listing (asking) prices, not transaction prices.
- The dataset looks artificially generated (some patterns are unusually regular), so findings describe this dataset, not the real Berlin market.
- Associations, not causal effects; feature effects overlap (e.g. new buildings also have better energy classes).
- Yields are gross, computed from medians, and not adjusted for flat size or age.
- The buy-vs-rent comparison is simplified (80% loan, 2% repayment; excludes purchase costs, maintenance and equity build-up).
