<<<<<<< HEAD
# EV Market Analysis – Electric Vehicle Population Dashboard (Tableau)

Analyzing 150,000+ registered electric vehicles to understand market composition, brand dominance, battery range trends, and clean-fuel eligibility, using Tableau.
=======
# Retail Sales Analytics – Business Intelligence Dashboard (Tableau)

Analyzing retail sales, profit, and regional performance across the US Superstore business to identify where profitability is breaking down and support smarter purchasing, discounting, and inventory decisions using Tableau.
>>>>>>> 356b12d22055b1ce2c3e9ab2e58de98b47339925

## Table of Contents
- [Overview](#overview)
- [Business Problem](#business-problem)
- [Dataset](#dataset)
- [Tools & Technologies](#tools--technologies)
- [Project Structure](#project-structure)
- [Data Preparation](#data-preparation)
- [Key Metrics at a Glance](#key-metrics-at-a-glance)
- [Analysis & Key Findings](#analysis--key-findings)
- [Dashboard](#dashboard)
- [How to Run This Project](#how-to-run-this-project)
- [Results & Recommendations](#results--recommendations)
- [Future Work](#future-work)
- [Author & Contact](#author--contact)

## Overview
<<<<<<< HEAD
This project analyzes the Electric Vehicle Population dataset — 150,482 registered EVs, primarily in Washington State — to understand who's actually buying EVs, which manufacturers dominate the market, how battery range has evolved, and how many vehicles currently qualify for Clean Alternative Fuel Vehicle (CAFV) incentives. The result is an interactive Tableau dashboard that lets a stakeholder (a policymaker, dealership, or utility company) explore EV adoption trends by manufacturer, county, and model year.

## Business Problem
As EV adoption accelerates, government agencies, utility companies, and dealerships all need the same core answers: which manufacturers are winning, where are EVs concentrated geographically, is average battery range improving fast enough to ease range anxiety, and how many vehicles currently qualify for clean-fuel incentives versus how many are still "eligibility unknown." This project turns a flat 150K-row registration file into a dashboard that answers all four questions at a glance.

## Dataset
- **Source:** Electric Vehicle Population Data (`data/ev_population_dataset.xlsx`)
- **Records:** 150,482 individual vehicle registrations
- **Coverage:** Primarily Washington State (150,141 of 150,482 records), with a small number of out-of-state registrations
- **Model Years:** 1997–2024
- **Manufacturers represented:** 37

**Key columns used:**
| Column | Description |
|---|---|
| Make / Model / Model Year | Vehicle identity |
| Electric Vehicle Type | Battery Electric (BEV) vs Plug-in Hybrid (PHEV) |
| Electric Range | Manufacturer-rated range in miles |
| CAFV Eligibility | Clean Alternative Fuel Vehicle incentive eligibility status |
| County / City / State | Registration location |
| Base MSRP | Manufacturer's suggested retail price (where available) |

## Tools & Technologies
- **Tableau Desktop** — data modeling, calculated fields, dashboard build
- **Excel (.xlsx)** — source data format

## Project Structure
```
ev-market-analysis-tableau/
├── data/
│   └── ev_population_dataset.xlsx    # Raw source data (150K+ EV registrations)
├── dashboards/
│   └── ev_market_dashboard.twbx      # Tableau packaged workbook
=======
This project evaluates Superstore's sales and profitability performance across regions, states, categories, sub-categories, and customers between 2014 and 2017. Using Tableau, the raw transactional data was transformed into an interactive dashboard that surfaces not just *how much* the business is selling, but *where it's actually making money* — and where high sales volume is quietly masking a loss.

The dashboard is built to be usable by a non-technical stakeholder: someone in leadership should be able to open it, filter by region or category, and walk away with a clear answer to "where should we focus next quarter."

## Business Problem
Superstore's total revenue has grown every year in the dataset — but profit has not scaled at the same rate. A category or region can look successful on a top-line sales report while actually eroding margin once discounts, returns, and cost-to-serve are factored in. Leadership needed answers to three things:

1. Which categories and sub-categories are genuinely profitable, versus which ones just generate volume?
2. Is the company's discounting strategy helping close sales, or actively destroying margin?
3. Which regions and states need a pricing/operations review because sales aren't converting into profit?

This project was built to answer those three questions with data instead of assumption.

## Dataset
- **Source:** Sample Superstore dataset (`data/superstore_dataset.xls`)
- **Sheets:** `Orders`, `Returns`, `People`
- **Size:** 9,994 order-line records
- **Coverage:** 793 unique customers · 49 states · 4 regions · 3 categories · 17 sub-categories
- **Timeframe:** 2014–2017

**Key columns used from the `Orders` sheet:**
| Column | Description |
|---|---|
| Order ID / Order Date / Ship Date | Order-level identifiers and timing |
| Customer ID / Customer Name / Segment | Who placed the order |
| Region / State / City | Where the order shipped |
| Category / Sub-Category / Product Name | What was sold |
| Sales / Quantity / Discount / Profit | The core numbers this analysis is built on |

## Tools & Technologies
- **Tableau Desktop** — data modeling, calculated fields, dashboard build
- **Excel (.xls)** — source data format

## Project Structure
```
retail-sales-analytics-tableau/
├── data/
│   └── superstore_dataset.xls        # Raw source data (Orders, Returns, People)
├── dashboards/
│   └── retail_sales_dashboard.twbx   # Tableau packaged workbook
>>>>>>> 356b12d22055b1ce2c3e9ab2e58de98b47339925
├── images/
│   └── dashboard_preview.png         # Dashboard screenshot
├── README.md
└── .gitignore
```

## Data Preparation
<<<<<<< HEAD
- Verified data types on Model Year (integer), Electric Range and Base MSRP (numeric), and Make/Model/County (dimension/string).
- Confirmed Electric Range contains a mix of real values and 0/blank entries for vehicles the manufacturer hadn't reported range on at time of registration — these were excluded when calculating average range to avoid skewing it downward.
- Built five calculated fields to drive the dashboard's KPI cards and charts:

| Calculated Field | Purpose |
|---|---|
| Total_Companies | Count of distinct manufacturers (Make) in the dataset |
| Total_Vehicles | Total registered EV count |
| Total_BEV_Vehicles | Count filtered to Battery Electric Vehicles only |
| Total_PHEV_Vehicles | Count filtered to Plug-in Hybrid Electric Vehicles only |
| Average_EV_Range | Mean Electric Range, excluding unreported (0) values |
=======
Before analysis, the following was done in Tableau directly on the connected data source:

- Verified data types on Order Date / Ship Date (date), Sales / Profit / Discount (numeric), and Region / Category / Sub-Category (dimension/string).
- Checked for and confirmed no null values in the core measures (Sales, Profit, Quantity, Discount).
- Built six calculated fields to support deeper analysis beyond the raw columns:

| Calculated Field | Formula | Purpose |
|---|---|---|
| Profit Margin % | `[Profit] / [Sales] * 100` | Normalize profitability across categories of different sizes |
| Profitability Status | `IF [Profit] > 0 THEN "Profitable" ELSE "Loss Making" END` | Quickly flag losing product lines |
| Discount Tier | No / Low (≤20%) / Medium (≤50%) / High Discount | Bucket orders to test discount impact |
| Sales per Unit | `[Sales] / [Quantity]` | Normalize sales at the unit level |
| Profit per Unit | `[Profit] / [Quantity]` | Normalize profit at the unit level |
| Order Value Tier | High Value (Sales ≥ 500) vs Regular | Separate large orders from routine ones |
>>>>>>> 356b12d22055b1ce2c3e9ab2e58de98b47339925

## Key Metrics at a Glance
| Metric | Value |
|---|---|
<<<<<<< HEAD
| Total Registered Vehicles | 150,482 |
| Total Manufacturers | 37 |
| Battery Electric Vehicles (BEV) | 116,807 (77.6%) |
| Plug-in Hybrid Vehicles (PHEV) | 33,675 (22.4%) |
| Average Electric Range (reported vehicles) | 126.4 miles |
| CAFV-Eligible Vehicles | 62,951 |

## Analysis & Key Findings

**Market Share by Manufacturer**
| Make | Registered Vehicles |
|---|---|
| Tesla | 68,983 (45.8%) |
| Nissan | 13,497 |
| Chevrolet | 12,026 |
| Ford | 7,614 |
| BMW | 6,439 |

Tesla alone accounts for nearly **46% of every registered EV** in the dataset — more than the next five manufacturers combined. This is a market with one dominant player, not a fragmented one.

**Top Individual Models**
Tesla Model Y (28,502) and Model 3 (27,709) are the two single best-selling EVs in the dataset, followed by the Nissan Leaf (13,187). Tesla holds 4 of the top 6 individual models.

**BEV vs PHEV Split**
77.6% of registered vehicles are full Battery Electric Vehicles versus 22.4% Plug-in Hybrids — the market has moved decisively toward full-electric rather than hybrid transition vehicles.

**CAFV Eligibility**
- Eligible: 62,951 vehicles (41.8%)
- Not eligible (low battery range): 17,833 vehicles (11.9%)
- Eligibility unknown / not yet researched: 69,698 vehicles (**46.3%**)

Nearly half the dataset has an *unknown* CAFV status rather than a confirmed yes/no — this is a data-completeness gap as much as a market finding, and it limits how confidently incentive eligibility can be reported.

**Geographic Concentration**
King County alone accounts for 79,075 vehicles — **over half the entire dataset** — followed by Snohomish (17,307) and Pierce (11,542). EV adoption in this dataset is heavily concentrated around the Seattle metro area rather than spread evenly across the state.

**Adoption Growth by Model Year**
Registrations climbed sharply from 4,934 in 2015 to 37,079 in 2023 — a more than 7x increase over eight years, with the steepest jump between 2021 and 2023.

## Dashboard
The **EV Market Intelligence Dashboard** combines the following worksheets into one interactive view:

- **KPI Cards** — Total Companies, Total Vehicles, Total BEV Vehicles, Total PHEV Vehicles, Average EV Range
- **% of BEV and PHEV Vehicles** — proportion breakdown chart
- **Top 10 Companies** — manufacturer ranking by registered vehicle count
- **Country-wise Vehicle Count** — geographic distribution view
- **AFV Eligibility** — breakdown of CAFV eligibility status
- **Average EV Range** — range trend view
- **Companies Details** — detail table for drill-down by manufacturer

![Dashboard Preview](images/dashboard_preview.png)

> **Note:** the image above is a low-resolution thumbnail auto-extracted from the Tableau file's internal metadata, not a real screenshot. Export a proper one before publishing — see [How to Run This Project](#how-to-run-this-project) for the exact steps.

## How to Run This Project
1. Clone the repository
   ```bash
   git clone https://github.com/aleena-afshar/ev-market-analysis-tableau.git
   ```
2. Open `dashboards/ev_market_dashboard.twbx` in Tableau Desktop (or Tableau Reader / Tableau Public) to explore the interactive dashboard.
3. Reference `data/ev_population_dataset.xlsx` if you want to trace any calculated field back to the raw source data.

To replace the placeholder dashboard image with a real one: open the dashboard tab in Tableau Desktop → **Dashboard → Export Image** → save as `dashboard_preview.png` → replace the file in `images/` → `git add`, `commit`, and `push` the change.

## Results & Recommendations
1. **Tesla's ~46% market share** makes it the single most important manufacturer to track for policy and infrastructure planning — charging network decisions built around "average" EV specs should be weighted toward Tesla's actual range and charging standard.
2. **Close the CAFV eligibility data gap** — with 46.3% of vehicles marked "eligibility unknown," any incentive program relying on this data is working with an incomplete picture of true eligible volume.
3. **Prioritize charging infrastructure investment in King, Snohomish, and Pierce counties**, where over 74% of registered EVs are concentrated.
4. **Range anxiety concerns are easing** — the 126-mile average reported range, combined with rapid year-over-year adoption growth, suggests range is no longer the primary adoption barrier it once was.

## Future Work
- Bring in Base MSRP more fully (currently reported for only ~2.3% of records) to analyze the relationship between price and adoption.
- Add a time-series view of average range by model year to quantify how fast battery technology is actually improving.
- Cross-reference county-level adoption with population and income data to identify under-served areas for infrastructure investment.
- Investigate the CAFV "eligibility unknown" segment to see if it correlates with older model years or specific manufacturers.

## Author & Contact
**Aleena Afshar**
Data Analyst
=======
| Total Sales | $2,297,201 |
| Total Profit | $286,397 |
| Overall Profit Margin | 12.5% |
| Total Orders | 5,009 |
| Total Customers | 793 |
| Average Order Value | $458.61 |
| Standard Class Share of Orders | ~60% |

## Analysis & Key Findings

**By Category**
| Category | Sales | Profit | Margin % |
|---|---|---|---|
| Technology | $836,154 | $145,455 | 17.40% |
| Furniture | $742,000 | $18,451 | 2.49% |
| Office Supplies | $719,047 | $122,491 | 17.04% |

Furniture generates almost as much revenue as Technology but converts almost none of it to profit — this is the single biggest profitability gap in the dataset.

**By Sub-Category**
- Most profitable: Copiers ($55.6K), Phones ($44.5K), Accessories ($41.9K), Paper ($34.1K), Binders ($30.2K)
- Losing money outright: Tables (**-$17.7K**), Bookcases (**-$3.5K**), Supplies (**-$1.2K**)

**By Region**
| Region | Sales | Profit | Margin % |
|---|---|---|---|
| West | $725,458 | $108,418 | 14.94% |
| East | $678,781 | $91,523 | 13.48% |
| Central | $501,240 | $39,706 | 7.92% |
| South | $391,722 | $46,749 | 11.93% |

The Central region has the lowest margin of any region despite solid sales volume — a strong signal that pricing or discount policy is different (worse) there compared to West and East.

**By State**
- Top states by revenue: California ($457.7K), New York ($310.9K), Texas ($170.2K)
- Loss-making states: **Texas (-$25.7K)**, Ohio (-$17.0K), Pennsylvania (-$15.6K), Illinois (-$12.6K), North Carolina (-$7.5K)
- Texas is the standout red flag: a top-5 state by revenue, but the single largest loss-maker in the entire dataset.

**Discounting Impact**
- Correlation between Discount and Profit: **-0.22**
- Higher discount tiers are consistently associated with lower profitability — discounting is not a neutral lever in this business, it's actively working against margin in the higher tiers.

**Yearly Trend**
| Year | Sales |
|---|---|
| 2014 | $484,247 |
| 2015 | $470,533 |
| 2016 | $609,206 |
| 2017 | $733,215 |

Sales dipped slightly in 2015, then grew 51% from 2015 to 2017 — meaning the profitability problem has been growing alongside revenue, not shrinking.

## Dashboard
The **Superstore Performance Dashboard** was built from 19 individual worksheets combined into one interactive view, including:

- **KPI Cards** — Total Sales, Total Profit, Total Customers, Average Profit Margin
- **Sales Trend Over Time** — monthly/yearly line chart
- **Category Performance / Profit by Category** — bar charts comparing the three categories
- **State-wise Profitability** — a filled map showing profit by state, immediately surfacing the Texas/Ohio/Pennsylvania problem visually
- **Sales by Region** — regional comparison
- **Discount vs. Profit** — scatter plot testing the discount hypothesis
- **Top 10 Customers by Sales** — ranked bar chart
- **Profitability Status / High Value Order / Sales by Ship Mode** — supporting breakdown views

![Dashboard Preview](images/dashboard_preview.png)

## How to Run This Project
1. Clone the repository
   ```bash
   git clone https://github.com/aleena-afshar/retail-sales-analytics-tableau.git
   ```
2. Open `dashboards/retail_sales_dashboard.twbx` in Tableau Desktop (or Tableau Reader / Tableau Public) to explore the interactive dashboard — filter by region, category, or year to reproduce any of the findings above.
3. Reference `data/superstore_dataset.xls` if you want to trace any calculated field back to the raw source data.

## Results & Recommendations
1. **Re-evaluate the Furniture category**, specifically Tables and Bookcases — through supplier renegotiation, pricing changes, or a hard cap on discounting for these sub-categories.
2. **Introduce discount tiering rules** rather than uniform discounting, since the data shows margin erosion increases with discount depth.
3. **Audit pricing and cost-to-serve in Texas, Ohio, Pennsylvania, and Illinois** — these states have real sales volume but are losing money, which points to a market-specific problem rather than a product problem.
4. **Protect and grow investment in Technology and Office Supplies** — the two categories already proven to convert sales into profit reliably.

## Future Work
- Incorporate the `Returns` sheet to quantify how much of the Furniture loss is return-driven versus purely a margin/pricing issue.
- Add customer segment (Consumer / Corporate / Home Office) as a dimension to check whether the profitability problem is segment-specific.
- Publish the workbook to Tableau Public for a live, shareable dashboard link.
- Extend the discount analysis with a statistical significance test rather than correlation alone.

## Author & Contact
**Aleena Afshar**
Aspiring Data Analyst
>>>>>>> 356b12d22055b1ce2c3e9ab2e58de98b47339925
📧 afsharaleena@gmail.com
🔗 [LinkedIn](https://www.linkedin.com/in/aleena-afshar) • [GitHub](https://github.com/aleena-afshar)
