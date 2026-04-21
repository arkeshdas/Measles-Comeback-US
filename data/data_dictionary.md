# Data Dictionary

**Arkesh Das**

This file documents the datasets used in this project, where they came from, how they were combined, which columns were used, and which figures depend on which inputs. It also serves as the single place where all source links are compiled.

## Purpose

This project combines U.S. measles case data, vaccination coverage data, exemption data, births data, and population data to create final visualizations about measles incidence, vaccination coverage, and state-level outbreak patterns.

This file focuses on the datasets and relevant columns used in the final visualizations.

## Final Visualization Inputs

The following files were used in the final visualizations:

- `CDC-measles-by-year.csv`
- `global+EU-WHO-measles-by-year.xlsx`
- `WB_population_cleaned.csv`
- `NNDSS-2016-2023-state-measles-cases.csv`
- `2024-26-state-measles-cases.csv`
- `mmr-exemptions-state.csv`
- `childvax-us2.csv`
- `number-of-births-per-year.filtered/number-of-births-per-year.csv`
- `2025-state-populations.csv`

The following files were used in draft work only, not the final visualizations:

- `nis-child-us.csv`
- `childvax-us`

## Data Sources

### `CDC-measles-by-year.csv`

[Link](https://www.cdc.gov/measles/data-research/index.html#cdc_data_surveillance_section_5-yearly-measles-cases)

This is taken from the CDC website. If you scroll down to **"Yearly measles cases"**, you can click on **1985 to present** and download the data. This is U.S. national measles case data collected by the CDC.

#### Columns
- `filter`
- `year`
- `cases`

#### Columns used in this project
- `year`
- `cases`

#### Notes
- In the final visualization workflow, this file was filtered to years 1985-2025.
- This file was used for national U.S. measles case counts only.


### National Immunization Survey-Child

#### `nis-child-us.csv`

- [2017, 2013-2017](https://www.cdc.gov/mmwr/volumes/67/wr/mm6740a4.htm)
- [2010, 2006-2010](https://www.cdc.gov/mmwr/preview/mmwrhtml/mm6034a2.htm)
- [2013, 2009-2013](https://www.cdc.gov/mmwr/preview/mmwrhtml/mm6334a1.htm)
- [2006, 2002-2006](https://www.cdc.gov/mmwr/preview/mmwrhtml/mm5634a2.htm)
- [2000, 1994-2000](https://www.cdc.gov/mmwr/preview/mmwrhtml/mm5030a1.htm)
- [2005, 2001-2005](https://www.cdc.gov/mmwr/preview/mmwrhtml/mm5536a2.htm)

To determine vaccination participation in the U.S., I had to combine a bunch of different datasets. Essentially, this data started to be nationally collected in 1994. It was collected and reported in NIS-Child data reports. To get measles vaccine data from 1994-2017, I took the data reported in **Table 1** of each report and concatenated it into one CSV file.

**Note:** I only use this data file in my draft visualizations.

#### Notes
- This file was assembled manually from multiple CDC MMWR reports.
- It was not used in the final visualizations because the final visualizations rely on `childvax-us2.csv` instead.

### `childvax-us`

[Link](https://data.cdc.gov/Child-Vaccinations/Vaccination-Coverage-among-Young-Children-0-35-Mon/fhky-rtsk/explore/query/SELECT%0A%20%20%60vaccine%60%2C%0A%20%20%60dose%60%2C%0A%20%20%60geography_type%60%2C%0A%20%20%60geography%60%2C%0A%20%20%60year_season%60%2C%0A%20%20%60dimension_type%60%2C%0A%20%20%60dimension%60%2C%0A%20%20%60coverage_estimate%60%2C%0A%20%20%60_95_ci%60%2C%0A%20%20%60population_sample_size%60%0AWHERE%0A%20%20caseless_one_of%28%60vaccine%60%2C%20%22≥1%20Dose%20MMR%22%29%0A%20%20AND%20caseless_one_of%28%60geography_type%60%2C%20%22HHS%20Regions%2FNational%22%29%0A%20%20AND%20caseless_one_of%28%60geography%60%2C%20%22United%20States%22%29%0A%20%20AND%20caseless_one_of%28%60dimension%60%2C%20%2219%20Months%22%29%0AORDER%20BY%20%60year_season%60%20ASC%20NULL%20LAST/page/filter)

After 2017, a new platform was developed called ChildVax that can be used to slice and explore multiple years worth of datasets. For my draft visualizations, I could not figure out how to get 24-35 month data via ChildVax.

#### Notes
- This file was used in draft work only.
- It was not used in the final visualizations.


### `childvax-us2`

[Link](https://data.cdc.gov/Child-Vaccinations/Vaccination-Coverage-among-Young-Children-0-35-Mon/fhky-rtsk/explore/query/SELECT%0A%20%20%60vaccine%60%2C%0A%20%20%60dose%60%2C%0A%20%20%60geography_type%60%2C%0A%20%20%60geography%60%2C%0A%20%20%60year_season%60%2C%0A%20%20%60dimension_type%60%2C%0A%20%20%60dimension%60%2C%0A%20%20%60coverage_estimate%60%2C%0A%20%20%60_95_ci%60%2C%0A%20%20%60population_sample_size%60%0AWHERE%0A%20%20caseless_one_of%28%60vaccine%60%2C%20%22≥1%20Dose%20MMR%22%29%0A%20%20AND%20caseless_one_of%28%60geography%60%2C%20%22United%20States%22%29%0A%20%20AND%20caseless_one_of%28%60dimension%60%2C%20%2224%20Months%22%29/page/filter)

For my final visualizations, I decided to just use this filtered ChildVax data from 2011-2022. This is because there are no filters that directly correspond to the NIS-Child data from earlier.

#### Columns
- `Year`
- `MMR_rate`

#### Columns used in this project
- `Year`
- `MMR_rate`

#### Notes
- This is the U.S. vaccination coverage file used in the final visualizations.
- It was merged with births data by `Year`.


### `global+EU-WHO-measles-by-year.xlsx`

[Link](https://immunizationdata.who.int/global/wiise-detail-page/measles-reported-cases-and-incidence?CODE=Global+EUR&YEAR=)

This is WHO data for both global and European measles cases from 1980-2025.

**Note:** for 2025, the official numbers have not been released yet, so I modified the 2025 counts using these two reports:

- [europe](https://www.unicef.org/press-releases/measles-cases-dropped-europe-and-central-asia-2025-compared-previous-year-risk#:~:text=Measles%20cases%20dropped%20in%20Europe,way%20through%20under%2Dvaccinated%20communities)
- [world](https://bluedot.global/the-measles-stress-test-what-2025-taught-us-about-global-readiness/#:~:text=For%20similar%20reasons%2C%20both%20the,key%20insights%20to%20mitigate%20risk)

#### Columns / structure
This workbook is a wide-format table. Relevant columns include:
- `Country / Region`
- `Disease`
- year columns such as `2025`, `2024`, `2023`, `2022`, and earlier year columns extending back to 1980

The workbook also contains export metadata rows, such as:
- `Exported: 2026-23-3 13:26 UTC`

#### Columns used in this project
- `Country / Region`
- year columns from 1980-2025

#### Notes
- Only the rows for `European Region` and `Global` were used.
- The data was reshaped from wide format to long format using year columns.
- Case values were cleaned by removing commas and converting to numeric form.


### `number-of-births-per-year.filtered/`

[Link](https://ourworldindata.org/grapher/number-of-births-per-year?country=~USA&overlay=download-data)

**Data sources:** UN, World Population Prospects (2024), processed by Our World in Data

This data was downloaded from this website, but the data is obtained from the UN. I accessed the online tool and filtered the data to show only U.S. births. I then downloaded the zip file generated by this tool. The unzipped folder contains the data for births in the U.S. from 1950 to 2023, and then projections into 2100.

For my analysis, I only looked at the 1980s-2026 since that aligns with the other datasets, so some later years are projected.

#### File used
- `number-of-births-per-year.filtered/number-of-births-per-year.csv`

#### Columns
- `Entity`
- `Code`
- `Year`
- `Births, total`
- `Projected (Projected)`

#### Columns used in this project
- `Year`
- `Births, total`
- `Projected (Projected)`

#### Notes
- In the final visualization code, projected rows were removed by filtering where `Projected (Projected)` is missing.
- This file was merged with `childvax-us2.csv` by `Year`.


### `WB_population_cleaned.csv`

[Link](https://www.kaggle.com/datasets/ashrafkhetran/world-population-and-forecasting?resource=download)

**Data sources:** World Bank Data-Driven Analysis, Regional Trends, and Time-Series Forecasting

I downloaded this dataset from this website. I downloaded the data as is, and for my analysis, I wanted to look at the populations of the world, Europe, and the U.S. I like that this dataset has regions and countries, so I can filter and aggregate countries.

#### Columns
- `iso3`
- `country`
- `year`
- `population`

#### Columns used in this project
- `iso3`
- `country`
- `year`
- `population`

#### Notes
- This file was used to create population series for:
  - the United States
  - the world
  - the WHO European Region
- The WHO European Region population series was created by summing selected country populations by `year`.
- Existing 2025 rows for certain ISO3 codes were removed and replaced with manually entered 2025 values in the visualization code.
- These population series were merged with measles case data by `year` to calculate `cases_per_100k`.


### `2024-26-state-measles-cases.csv`

This is taken from the [CDC website](https://www.cdc.gov/measles/data-research/index.html#cdc_data_surveillance_section_5-yearly-measles-cases). It is a dataframe that concatenates the data from the CSV files that you can download from the **"Map of measles cases among U.S. residents"** for 2024, 2025, and 2026.

2026 data was accessed on April 16, 2026.

#### Columns
- `2024`
- `2025`
- `2026`
- `year`
- `Location`

#### Columns used in this project
- `2024`
- `2025`
- `2026`
- `Location`

#### Notes
- In the final workflow, `Location` was renamed to `state`.
- The `year` column in this raw file was not used in the final code.
- This file was reshaped from wide format to long format for years 2024-2026.
- It was merged with state population data to compute `cases_per_100k`.


### `NNDSS-2016-2023-state-measles-cases.csv`

[Link](https://wonder.cdc.gov/nndss-annual-summary.html)

**Data Source:** National Notifiable Diseases Surveillance System (NNDSS) Annual Summary Data

This data was obtained using this data request tool. I filtered by state, selected **"measles, total"** as the disease, selected all states, and exported as a CSV.

#### Columns
- `Notes`
- `Disease`
- `Disease Code`
- `Year`
- `Year Code`
- `States`
- `States Code`
- `Case Count`

#### Columns used in this project
- `Year`
- `States`
- `Case Count`

#### Notes
- This file was used for historical state-level measles data from 2016-2023.
- Non-state or non-comparable rows were excluded, including:
  - `United States`
  - `Territories`
  - `American Samoa`
  - `Guam`
  - `Puerto Rico`
  - `U.S. Virgin Islands`
  - `Non-U.S. Residents`
  - `New York City`
- `New York (excluding New York City)` was recoded to `New York`.
- This file was merged with state population data, then concatenated with 2024-2026 state case data.


### `mmr-exemptions-state.csv`

- [2019](https://www.cdc.gov/mmwr/volumes/68/wr/mm6841e1.htm#:~:text=According%20to%20a%20report%2C%20the%20following%20vaccination,children%20without%20an%20exemption%20were%20completely%20vaccinated.)
- [2020](https://www.cdc.gov/mmwr/volumes/70/wr/mm7003a2.htm#:~:text=According%20to%20a%20report%2C%20the%20national%20coverage,95%25%20The%20national%20exemption%20rate%20was%202.5%25.)
- [2021](https://www.cdc.gov/mmwr/volumes/71/wr/mm7116a1.htm)
- [2022](https://www.cdc.gov/mmwr/volumes/72/wr/mm7202a2.htm#:~:text=During%20the%202021–22%20school,a%20return%20to%20prepandemic%20coverage.)
- [2023](https://www.cdc.gov/mmwr/volumes/72/wr/mm7245a2.htm#:~:text=During%20the%202022–23%20school%20year%2C%20nationwide%20vaccination%20coverage%20among,in%20a%20majority%20of%20states.)
- [2024](https://www.cdc.gov/mmwr/volumes/73/wr/mm7341a3.htm)
- [2025](https://www.cdc.gov/schoolvaxview/data/index.html#:~:text=The%20number%20of%20kindergartners%20exempt,Measles%20Cases%20and%20Outbreaks%20%7C%20CDC.)

**Data Sources:** Vaccination Coverage for Selected Vaccines, Exemption Rates, and Provisional Enrollment Among Children in Kindergarten, United States reports from 2019-2025.

This dataframe selects the exemption rate and vaccination rate for the MMR vaccine from the 2019-2025 reports. These reports have been released annually since 2016, however they did not start reporting exemption rate until 2019. Therefore, I decided to only look at the 2019-2025 MMR participation and exemption rates per state.

#### Columns
- `State`
- `MMR_2019`
- `Exempt_2019`
- `MMR_2020`
- `Exempt_2020`
- `MMR_2021`
- `Exempt_2021`
- `MMR_2022`
- `Exempt_2022`
- `MMR_2023`
- `Exempt_2023`
- `MMR_2024`
- `Exempt_2024`
- `MMR_2025`
- `Exempt_2025`

#### Columns used in this project
- `State`
- `Exempt_2019`
- `Exempt_2020`
- `Exempt_2021`
- `Exempt_2022`
- `Exempt_2023`
- `Exempt_2024`
- `Exempt_2025`

#### Notes
- In the final code, only exemption columns were reshaped and used for the outbreak probability analysis.
- Vaccination rate columns are still preserved in the file.
- The file was reshaped from wide format to long format using state and year.


### `2025-state-populations.csv`

[Link](https://www2.census.gov/programs-surveys/popest/datasets/2020-2025/state/totals/NST-EST2025-ALLDATA.csv)

**Data source:** U.S. 2025 Census projections and change from the 2020 Census

This dataset contains the population of the U.S. as a whole, and each U.S. state in 2020, as well as projections for 2021, 2022, 2023, 2024, and 2025. The projections are official estimates calculated by the Census Bureau based on birth, death, and migration records.

#### Columns
This file contains many columns, including:
- `SUMLEV`
- `REGION`
- `DIVISION`
- `STATE`
- `NAME`
- `ESTIMATESBASE2020`
- `POPESTIMATE2020`
- `POPESTIMATE2021`
- `POPESTIMATE2022`
- `POPESTIMATE2023`
- `POPESTIMATE2024`
- `POPESTIMATE2025`
- and many additional change, migration, residual, group quarters, and rate columns

#### Columns used in this project
- `SUMLEV`
- `NAME`
- `POPESTIMATE2025`

#### Notes
- In the final workflow, this file was filtered to rows where `SUMLEV == "040"` to keep state-level rows only.
- `NAME` was renamed to `state`.
- `POPESTIMATE2025` was renamed to `population`.
- The same 2025 state population values were used to normalize historical and recent state measles cases into `cases_per_100k`.


## Data Processing and Integration

All merging and reshaping in the final workflow was done in Python. No saved merged analysis datasets were created. Instead, cleaned and merged tables were built in memory inside the visualization scripts.

### National incidence workflow
- `CDC-measles-by-year.csv` was filtered to U.S. annual case counts from 1985-2025.
- `global+EU-WHO-measles-by-year.xlsx` was filtered to `European Region` and `Global`, then reshaped from wide to long format using year columns.
- `WB_population_cleaned.csv` was filtered to create:
  - U.S. population by year
  - world population by year
  - WHO European Region population by year, created by summing selected countries
- These case datasets were merged with their corresponding population series by `year`.
- `cases_per_100k` was calculated for the U.S., WHO European Region, and world series.

### State-level incidence and exemption workflow
- `NNDSS-2016-2023-state-measles-cases.csv` was cleaned to keep state-level rows only.
- `2024-26-state-measles-cases.csv` was reshaped from wide to long format for years 2024-2026.
- `2025-state-populations.csv` was filtered to state rows and used to assign population values by state.
- Historical and recent state case datasets were normalized to `cases_per_100k` using state population.
- The historical and recent state case tables were concatenated row-wise into one state case series.
- `mmr-exemptions-state.csv` was reshaped from wide to long format using exemption columns and extracted year values.
- State exemption data was merged with state case data by `state` and `year`.

### Vaccination coverage and births workflow
- `childvax-us2.csv` provided annual U.S. MMR vaccination coverage.
- `number-of-births-per-year.filtered/number-of-births-per-year.csv` provided U.S. annual births.
- Projected births rows were removed in the final code.
- These two files were merged by `Year`.
- Annual estimated unvaccinated children and cumulative unvaccinated children were then calculated.


## Derived Variables

The following derived variables were created in the final analysis workflow.

### `cases_per_100k`
Calculated as:

```python
(cases / population) * 100000
```

Used for:

* U.S. national measles incidence
* WHO European Region measles incidence
* global measles incidence
* state-level measles incidence
* choropleth maps
* state-level outbreak analysis

### `outbreak`

Boolean indicator created from state-level incidence data:

```python
cases_per_100k > 0.1
```

Used for:

* exemption versus outbreak probability analysis

### `exemption_bin`

Categorical grouping of state exemption rates using bins:

* `0–2%`
* `2–4%`
* `4–6%`
* `6–8%`
* `8–10%`
* `10–15%`

Used for:

* grouped probability of outbreak by exemption level

### `unvaccinated_children`

Calculated as:

```python
Births, total * (1 - MMR_rate / 100)
```

Used for:

* annual estimated count of unvaccinated children in the U.S.

### `cumulative_unvaccinated_children`

Calculated as the cumulative sum of `unvaccinated_children`.

Used for:

* cumulative estimate of unvaccinated children over time


## Manual Adjustments and Cleaning Decisions

### Manual 2025 population additions

In the final national incidence code, manual 2025 population values were appended for:

* `USA`
* `WLD`
* countries used to construct the WHO European Region population series

These were used so that 2025 incidence values could be calculated consistently.

### WHO regional filtering

Only the following rows from `global+EU-WHO-measles-by-year.xlsx` were used:

* `European Region`
* `Global`

### State exclusions

For state-level case analysis, non-state or incomparable rows were excluded, including:

* `United States`
* `Territories`
* `American Samoa`
* `Guam`
* `Puerto Rico`
* `U.S. Virgin Islands`
* `Non-U.S. Residents`
* `New York City`

In the mapping workflow, a similar exclusion was applied, including:

* `Commonwealth of Northern Mariana Islands`

### New York handling

* `New York City` was excluded from state-level analyses and maps.
* `New York (excluding New York City)` was recoded as `New York`.

### Census state filtering

`2025-state-populations.csv` was filtered using `SUMLEV == "040"` so that only state-level rows were retained.

### Births projection filtering

In the births workflow, rows marked as projected were excluded before merging with vaccination coverage.


## Figures

### Figure 1

**Output file:** `fig1_measles_cases_per_100k.png`

#### Input files

* `CDC-measles-by-year.csv`
* `global+EU-WHO-measles-by-year.xlsx`
* `WB_population_cleaned.csv`

#### Main processing steps

* U.S., WHO European Region, and world measles cases were matched to population by `year`.
* The WHO file was reshaped from wide to long format.
* WHO European Region population was created by summing selected country populations.
* Manual 2025 population values were appended where needed.
* `cases_per_100k` was calculated for all three geographic series.

#### Main output concept

* Compares measles incidence over time across the United States, WHO European Region, and the world.
* Also includes a panel showing the change from 2024 to 2025.


### Figure 2

**Output file:** `fig2_exemption_outbreak_probability.png`

#### Input files

* `NNDSS-2016-2023-state-measles-cases.csv`
* `2024-26-state-measles-cases.csv`
* `2025-state-populations.csv`
* `mmr-exemptions-state.csv`

#### Main processing steps

* Historical and recent state case files were cleaned and combined.
* State case counts were normalized to `cases_per_100k`.
* Exemption data was reshaped from wide to long format.
* State exemption data was merged with state case data by `state` and `year`.
* `outbreak` was defined as `cases_per_100k > 0.1`.
* `exemption_bin` grouped exemption rates into categorical intervals.
* Outbreak probability was computed as the mean of the boolean outbreak indicator within each exemption bin.

#### Main output concept

* Shows the probability of measles outbreaks across bins of kindergarten exemption rates.


### Figure 3

**Output file:** `fig3_vax_unvaccinated_cumulative.png`

#### Input files

* `childvax-us2.csv`
* `number-of-births-per-year.filtered/number-of-births-per-year.csv`

#### Main processing steps

* Vaccination coverage was merged with U.S. births by `Year`.
* Projected birth rows were excluded.
* `unvaccinated_children` was calculated for each year.
* `cumulative_unvaccinated_children` was computed as a running total.

#### Main output concept

* Compares annual MMR vaccination coverage with the cumulative estimated number of unvaccinated children in the U.S.


### Figure 4

**Output files:** `fig4_measles_map_YYYY_per100k.png`

#### Input files

* `NNDSS-2016-2023-state-measles-cases.csv`
* `2024-26-state-measles-cases.csv`
* `2025-state-populations.csv`

#### Main processing steps

* Historical and recent state measles files were standardized and combined.
* State case counts were converted to `cases_per_100k`.
* State names were mapped to abbreviations for choropleth plotting.
* Separate choropleth maps were exported for each year from 2016-2026.

#### Main output concept

* Annual state-level choropleth maps of measles incidence per 100,000 people.


## Summary

This project uses a mixture of CDC, WHO, UN, Census, and other public data sources to analyze measles incidence and vaccination-related patterns across time and geography. The final workflow relies on Python-based filtering, reshaping, merging, and aggregation rather than on pre-saved merged datasets. This file is intended to document both the provenance of the source data and the specific role each dataset played in the final visualizations.

