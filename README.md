<p align="center">
  <img src="images/00_title_card.png" alt="Gurgaon Residential Real Estate Sales EDA" width="100%">
</p>

# Gurgaon Residential Real Estate Market Analysis

### 99acres • Python EDA • Residential Sales Market

> **From raw property listings to defensible market intelligence**

This project is a standalone Python Exploratory Data Analysis (EDA) of
Gurgaon's residential real-estate sales market, built from a raw 99acres
property-listing dataset.

The analysis is designed to demonstrate more than Python or
visualization skills. It documents the **analytical decisions required
to turn a mixed, messy real-estate listing source into a reliable
analytical dataset**, then uses that dataset to understand pricing
drivers, locality positioning, luxury-market characteristics and value
opportunities.

------------------------------------------------------------------------

## Why This Project Matters

Real-estate decisions are often reduced to one number: **listed property
price**.

That can be misleading.

A property's apparent value depends on factors such as:

-   locality and pricing power
-   property size
-   BHK and bathroom configuration
-   price per square foot
-   inventory concentration
-   premium-market positioning
-   the relationship between price and usable space

The central question of this project is therefore not simply:

> **"How expensive are properties in Gurgaon?"**

It is:

> **"What measurable factors are associated with property value, where
> does pricing power exist, and where can buyers find stronger
> space-to-price opportunities?"**

The EDA turns that question into a structured analytical journey from
**raw data → analytical decisions → evidence → market intelligence**.

------------------------------------------------------------------------

## Data Source

### Original Source

**Kaggle --- Indian Real Estate - 99acres.com**\
Published by **arvanshul**

🔗 **[View the original dataset on
Kaggle](https://www.kaggle.com/datasets/arvanshul/gurgaon-real-estate-99acres-com)**

The original source is important to this project because it is **not a
clean, ready-made analytical dataset**. It contains a broad set of
listing, property, location, pricing, amenity, society/building, contact
and scraping-related fields.

The uploaded source used for this analysis contains approximately:

-   **10,704 raw listings**
-   **67 raw columns**
-   **220+ Gurgaon localities**
-   Both **sales and rental listings**
-   Apartments, builder floors and independent houses
-   Property, pricing, area, BHK, bathroom, furnishing, locality and
    other listing attributes

The complexity of the source is part of the analytical challenge.

The objective was not to immediately start plotting. It was first to
understand **what the data actually represents, which fields are
analytically useful, which markets should be separated, and which
observations require investigation before they can be trusted.**

> **The source dataset is deliberately retained as the starting point of
> the analytical story: the final sales dataset was built through a
> sequence of decisions rather than supplied as a finished analytical
> table.**

------------------------------------------------------------------------

## Project Overview

The original 99acres source contains **both property sales and rental
listings**.

Because sale prices and monthly rents follow fundamentally different
pricing mechanisms, combining them would distort valuation
distributions, pricing comparisons and downstream insights.

The dataset was therefore separated into:

**Sales market → primary EDA focus**

**Rental market → retained separately, not mixed into sales valuation
analysis**

The residential sales dataset was then taken through a structured
preparation and exploratory-analysis process:

> **Raw Data → Inspect → Reduce → Standardize → Split → Repair →
> Engineer → Validate → Analyze → Decide**

The final analytical sales dataset contains **10,010 properties across
222 localities**.

------------------------------------------------------------------------

## Business Problem

Residential buyers and investors often compare properties using headline
price alone.

That creates several analytical blind spots:

-   A high-priced property may offer substantially more space.
-   A low-priced locality may still have poor price efficiency.
-   High listing volume does not automatically mean high-value
    positioning.
-   Premium pricing may be driven by location rather than property
    configuration.
-   Luxury properties can behave differently from the broader market.
-   Comparing properties of different sizes using total price alone can
    produce misleading conclusions.

This project therefore asks:

1.  **Which measurable property characteristics are most strongly
    associated with price?**
2.  **Which Gurgaon localities demonstrate stronger pricing power?**
3.  **Where does price-per-square-foot reveal premium or value
    positioning?**
4.  **How does the luxury segment differ from the broader residential
    market?**
5.  **Which localities provide stronger space-to-price efficiency?**

------------------------------------------------------------------------

## Analytical Objectives

### 01 --- Market Structure

Understand the composition of Gurgaon's residential sales market
through:

-   property configuration
-   BHK distribution
-   property size
-   pricing distribution
-   locality concentration
-   inventory patterns

### 02 --- Pricing Driver Analysis

Identify the measurable property attributes most strongly associated
with property price and evaluate the role of:

-   area
-   bathrooms
-   BHK
-   balconies

Correlation is used as an **association signal**, not as proof of
causation.

### 03 --- Locality Intelligence

Compare localities using:

-   listing concentration
-   median property price
-   median price per square foot
-   locality-level positioning

Minimum listing thresholds are used where appropriate so that very small
samples do not dominate comparisons.

### 04 --- Luxury Market Profiling

Profile the top 10% of properties as a distinct market segment and
compare them with the remaining 90% across:

-   price
-   area
-   price per square foot
-   bathrooms
-   bedrooms

### 05 --- Value Opportunity Identification

Move beyond "cheapest" versus "most expensive" and identify locations
where **price and space interact more efficiently**.

------------------------------------------------------------------------

## The Analytical Decision Framework

The most important part of this project is not the Python syntax.

It is the sequence of decisions made to protect analytical reliability.

``` text
BUSINESS QUESTION
       ↓
REDUCE NOISE
       ↓
SEPARATE MARKETS
       ↓
REPAIR DATA
       ↓
VALIDATE ANOMALIES
       ↓
ENGINEER METRICS
       ↓
ANALYZE PATTERNS
       ↓
INTERPRET EVIDENCE
       ↓
IDENTIFY OPPORTUNITY
```

### The key analytical decisions

  -----------------------------------------------------------------------
  Decision                What was done           Why it mattered
  ----------------------- ----------------------- -----------------------
  **Reduce**              Removed/reduced         Created a clearer
                          redundant, scraping and analytical schema
                          non-analytical fields   

  **Split**               Separated sales and     Prevented fundamentally
                          rental listings         different pricing
                                                  mechanisms from being
                                                  mixed

  **Repair**              Applied field-specific  Preserved business
                          missing-value treatment meaning instead of
                                                  using one blanket rule

  **Validate**            Investigated unusual    Avoided blindly
                          area and PPSF           deleting legitimate
                          observations before     high-value properties
                          filtering               

  **Engineer**            Created                 Made different-sized
                          price-per-square-foot   properties more
                          and analytical          comparable
                          groupings               

  **Aggregate carefully** Used locality           Reduced sensitivity to
                          thresholds and median   small samples and
                          PPSF                    extreme values

  **Analyze**             Compared drivers,       Converted cleaned data
                          localities, premiums    into market evidence
                          and luxury properties   

  **Decide**              Interpreted evidence    Connected EDA to
                          through buyer/value     practical
                          questions               decision-making
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## Data Preparation & Quality Decisions

Cleaning was treated as an **analytical process**, not a mechanical
preprocessing step.

### Missing Values

Different fields were handled according to their business meaning.

-   **PRICE** → median imputation because property prices are strongly
    skewed.
-   **AREA** → rows with missing area were removed because area is
    required to derive reliable PPSF.
-   **BEDROOM_NUM** → mode-based treatment.
-   **BALCONY_NUM** → treated as zero where appropriate.
-   **FLOOR_NUM** → median-based treatment.
-   **BROKERAGE** → zero treatment where absence represented no
    brokerage value.

The notebook validates the resulting sales dataset after treatment.

### Area Anomaly Investigation

Area was treated particularly carefully because it directly influences
valuation metrics.

The analysis investigated properties below multiple area thresholds and
separately inspected extreme high-area observations before defining a
validation range.

The final analytical rule constrained sales properties to:

> **250--50,000 sq.ft.**

This was not applied as an arbitrary first-pass filter. The workflow
was:

> **Detect → Investigate → Understand → Define Rule → Filter → Measure
> Impact**

### Price-per-Square-Foot Validation

PPSF was engineered as:

``` python
PRICE_SQFT = PRICE / AREA
```

The distribution was highly right-skewed, with a small number of extreme
observations.

The analysis therefore examined the distribution and lower-tail values
before defining a threshold. The final lower-bound rule used the **1st
percentile PPSF threshold of approximately ₹5,222/sq.ft.**

After the final anomaly treatment:

> **10,010 sales properties remained for the analytical EDA.**

------------------------------------------------------------------------

## Analytical Techniques

The project uses Python as the analytical environment:

-   **Pandas** --- data preparation, transformation, grouping and
    aggregation
-   **NumPy** --- numerical operations
-   **Matplotlib** --- analytical visualization
-   **Seaborn** --- statistical visualization

The important skill demonstrated is not simply tool usage, but the
ability to combine those tools with **business-aware analytical
reasoning**.

------------------------------------------------------------------------

## Selected Analytical Evidence

### Property Size & Price

Area emerged as the strongest measured structural signal among the
selected property attributes.

Correlation with price:

-   **Area:** \~0.48
-   **Bathrooms:** \~0.26
-   **BHK:** \~0.25
-   **Balconies:** \~0.11

These values indicate association within the analyzed dataset; they
should not be interpreted as causal effects.

### Locality Analysis

Locality comparisons use listing counts and median PPSF, with a minimum
listing threshold to avoid allowing tiny samples to dominate the
ranking.

This shifts the question from:

> "Which locality is the most expensive?"

toward:

> **"Which localities combine meaningful market presence with strong
> pricing power?"**

### Locality Efficiency

The analysis also examines the relationship between locality-level
pricing and property size.

This creates a more useful distinction between:

-   expensive because of premium positioning
-   expensive because properties are substantially larger
-   lower-priced with comparatively stronger space-to-price value

### Luxury Market

The top 10% of properties were profiled separately from the remaining
90%.

The luxury segment shows materially different characteristics across
price, property size, PPSF and configuration, supporting the view that
premium inventory should not simply be treated as a scaled-up version of
the broader market.

------------------------------------------------------------------------

## What the Analysis Revealed

The EDA produces several broader conclusions:

-   **Area is the strongest measured property-level price signal** among
    the selected numeric attributes.
-   **Location continues to create meaningful pricing premiums** beyond
    basic property configuration.
-   **High inventory and high pricing are not the same thing**; locality
    positioning requires both dimensions.
-   **PPSF provides a more comparable valuation lens** than headline
    price when property sizes differ.
-   **Luxury properties behave as a distinct market segment**, with
    materially different price, size and configuration profiles.
-   **Locality-level space-to-price analysis can reveal alternatives to
    the most expensive micro-markets.**

These findings are not presented as a predictive pricing model. They are
evidence from exploratory analysis designed to support **market
understanding and decision framing**.

------------------------------------------------------------------------

## From Data to Decision

The project ultimately changes how the real-estate question is framed.

Instead of:

> **"Which property is cheaper?"**

the analysis encourages questions such as:

> **What am I paying per square foot?**

> **Is the premium supported by location, size or configuration?**

> **Does a high-priced locality actually provide more usable space?**

> **Are there alternative localities with stronger space-to-price
> efficiency?**

> **Does the luxury segment behave differently enough to require a
> separate analytical lens?**

This is where the EDA moves from descriptive analysis toward **decision
support**.

------------------------------------------------------------------------

## Project Deliverables

The repository is intended to preserve the standalone Python EDA as a
complete analytical project.

``` text
gurgaon-99acres-residential-sales-eda/
│
├── README.md
│
├── notebook/
│   └── gurgaon_housing_analysis.ipynb
│
├── data/
│   └── README.md
│
├── deliverables/
│   └── Gurgaon_99acres_Sales_EDA_Notebook.pdf
│
├── images/
│   └── title-card / analytical visuals
│
└── docs/
    └── supporting methodology / notes
```

The original raw dataset should be accessed from the **Kaggle source
link above** rather than assumed to be redistributed with the
repository.

------------------------------------------------------------------------

## Tools & Skills

**Python** --- analytical workflow and exploratory analysis\
**Pandas** --- data cleaning, transformation, grouping and aggregation\
**NumPy** --- numerical analysis\
**Matplotlib / Seaborn** --- analytical visualization\
**Data Quality Analysis** --- missing-value treatment and anomaly
validation\
**Feature Engineering** --- PPSF and analytical segmentation\
**Statistical Reasoning** --- distribution analysis, correlation and
percentile-based thresholds\
**Business Analytics** --- locality positioning, value analysis and
market interpretation\
**Data Storytelling** --- translating analytical evidence into
decision-oriented conclusions\
**Git & GitHub** --- project documentation and portfolio presentation

------------------------------------------------------------------------

## Project Perspective

This project demonstrates an analytical approach that starts with the
**business question**, not the chart.

The journey is:

> **Business Problem → Data Context → Analytical Decisions → Evidence →
> Interpretation → Opportunity**

The strongest evidence of analytical maturity is therefore not that the
project uses Pandas or produces charts.

It is that the analysis shows:

-   why sales and rental markets had to be separated
-   why different missing-value strategies were necessary
-   why area required stricter validation
-   why anomalies were investigated before removal
-   why PPSF was engineered
-   why locality comparisons required minimum sample discipline
-   why correlation was treated as association rather than causation
-   and how the resulting evidence was translated into market and
    buyer-oriented questions

> **The goal was not simply to clean a real-estate dataset. It was to
> build a defensible analytical foundation for understanding price,
> locality and value.**

------------------------------------------------------------------------

## Author

**Debanjan Biswas**\
Data Analyst \| SQL \| Power BI \| Python

**LinkedIn:**
[linkedin.com/in/biswas-debanjan-2ab011148](https://www.linkedin.com/in/biswas-debanjan-2ab011148/)

------------------------------------------------------------------------

::: {align="center"}
### Raw Listings → Analytical Foundation → Market Intelligence → Decision Support

**Gurgaon Residential Real Estate Market Analysis**
:::
