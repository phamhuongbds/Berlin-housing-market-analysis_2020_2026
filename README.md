# Berlin Housing Market 2020–2026: Prices, Rents and Rental Yields

A data/business analysis in Python (pandas + matplotlib) of Berlin resale listings, rental listings and a monthly district price panel.

**Notebook:** [`berlin_housing_analysis.ipynb`](berlin_housing_analysis.ipynb) — introduction, business questions, data preparation, analysis, conclusions.

## Project at a glance
![Project overview](figures/project_overview.png)

## Business questions
1. How did prices and rents change from 2020 to 2026, and what happened when mortgage rates rose?
2. Which districts are the most and least expensive, and how does price change with distance from the centre?
3. Where is the gross rental yield highest, and does it cover the mortgage rate?
4. How much more are flats with a better energy class, a newer building or a better condition worth?
5. Is it cheaper to rent or to buy, and did that change when mortgage rates rose?

## Key findings
- **Rents rose almost twice as fast as resale prices:** +43.5% vs. +23.0% between 2020 and 2025.
- **Prices barely reacted to the rate shock:** while the mortgage rate rose from 1.1% to 4.1%, resale prices dipped only about 5% and had fully recovered by April 2026.
- **Location dominates:** the most expensive district costs 3.1× the cheapest per m² (€6,155 vs. €1,967). Price falls about 60% from the centre to 10–15 km, then levels off.
- **Gross yields are thin:** 3.48%–3.97% by district, above today's 3.1% mortgage rate but below the 4.1% peak of 2023.
- **Features are priced in:** compared with neighbours in the same district and year, energy class H flats sell for about 20% less and A+ for about 50% more; flats needing renovation sell for 22% less.
- **Buying overtook renting in monthly cost:** in 2020–21 the loan payment for a flat was about 19% below the rent; since January 2022 it is higher (peak 1.42× the rent in 2023, 1.13× in April 2026). In 2025 buying and renting cost about the same in most districts (0.95×–1.12×).

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
