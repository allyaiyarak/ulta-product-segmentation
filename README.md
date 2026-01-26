# Ulta US Product Performance Segmentation (SQL + Tableau)

## Objective
Ulta Beauty wants to better understand which types of products resonate most with U.S. customers.
Using product-level engagement and satisfaction signals, this project segments Ulta’s e-commerce
assortment to identify:
- **Hero products** (high engagement + high satisfaction)
- **Hidden gems** (high satisfaction but low visibility)
- **Brand risks** (high visibility but low satisfaction)

## Dataset Used
Cosmetics e-commerce dataset (scraped product listings across multiple retailers).  
This analysis focuses on the subset where:
- `website = 'Ulta`
- `country = 'USA'`

Data fields used include: product category, price, rating, and number of ratings.

> Source: https://www.kaggle.com/datasets/devi5723/e-commerce-cosmetics-dataset
> Note: Ratings were validated to be on a consistent **1–5 scale** prior to segmentation.

## Tools / Technologies
- **SQL (SQLite)**: data cleaning, segmentation logic, aggregation
- **Tableau Public**: dashboard + storytelling visuals

## Segmentation Framework
**Engagement** (proxy = number of ratings):
- No engagement: `NULL` or `0`
- Low: `< 10`
- Medium: `10–50`
- High: `> 50`

**Satisfaction** (proxy = average rating):
- High rating: `>= 4.0`
- Medium rating: `3.0–3.9`
- Low rating: `< 3.0`
- No rating: `NULL`

## Project Workflow
1. **Scope the business problem** to Ulta (US)
2. **Validate data quality** (null checks, rating scale validation)
3. **Engineer segmentation labels** (engagement_level, rating_level)
4. **Build the segmentation matrix** (engagement × rating)
5. **Category drill-down** to identify where opportunities/risks cluster
6. **Dashboard build** in Tableau Public

## Key Results (Ulta US)
From the segmentation matrix:
- **High engagement + High rating:** 2,285 products (core “hero” assortment)
- **Hidden opportunity pool:** high-rated products with low/medium engagement (discoverability issue)
- **Brand risk:** a small number of high-engagement products with low ratings (needs review)

## Dashboard
- Tableau Public: [paste your dashboard link]
- Key visuals:
  - Engagement × Rating heatmap
  - Product distribution by engagement level
  - Category filter for drill-down

## Repository Contents
- `sql/` — sanity checks + segmentation queries
- `tableau/` — dashboard link + screenshots
- `notes/` — assumptions & threshold rationale

## How to Reproduce (Optional)
1. Download the dataset from Kaggle (link above)
2. Load into SQLite (DB Browser for SQLite)
3. Run queries in `sql/` in order
4. Export the final segmented table to CSV and connect in Tableau
