# EV Market Analysis – Electric Vehicle Population Dashboard (Tableau)

Analyzing 150,000+ registered electric vehicles to understand market composition, brand dominance, battery range trends, and clean-fuel eligibility, using Tableau.

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
├── images/
│   └── dashboard_preview.png         # Dashboard screenshot
├── README.md
└── .gitignore
```

## Data Preparation
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

## Key Metrics at a Glance
| Metric | Value |
|---|---|
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
📧 afsharaleena@gmail.com
🔗 [LinkedIn](https://www.linkedin.com/in/aleena-afshar) • [GitHub](https://github.com/aleena-afshar)
