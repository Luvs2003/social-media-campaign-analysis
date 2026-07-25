# Social Media Campaign Performance Analysis

End-to-end data analytics project analyzing social media campaign performance using Excel, SQL, and Power BI — from raw, messy data to actionable business insights.

## 📌 Project Overview

This project analyzes campaign-level social media data (reach, engagement, spend) across five platforms — Instagram, Facebook, LinkedIn, TikTok, and Twitter — to answer three core business questions:

1. Which **content type** drives the highest engagement?
2. What are the **best posting times** for engagement?
3. Which **platform delivers the best ROI** per dollar spent?

## 🛠️ Tools Used

- **Excel** — data cleaning and validation
- **MySQL** — data storage and analysis via SQL queries
- **Power BI** — interactive dashboard and visualization

## 🧹 Data Cleaning

The raw dataset (400 rows) had realistic data quality issues that needed to be resolved before analysis:

- **Inconsistent date formats** — three different formats (MM-DD-YYYY, DD/MM/YYYY, YYYY-MM-DD) mixed across rows, standardized to a single format
- **Missing values** — blank `clicks` and `comments` fields filled with `0`, based on the reasoning that no recorded event means no click/comment occurred
- **Duplicate rows** — 8 exact duplicates identified and removed
- **Inconsistent categorical values** — lowercase platform names (e.g. `instagram`) standardized to match the rest (`Instagram`)

## 🔍 SQL Analysis

Key techniques used in MySQL:

- `GROUP BY` + `HAVING COUNT(*) >= 5` — to filter out unreliable averages based on very small sample sizes (an early result was skewed by day/hour slots with only 1 post)
- `CASE WHEN` — to bucket exact posting hours into broader time windows (Morning / Afternoon / Evening / Night) for more statistically reliable comparisons
- Normalized metrics — engagement rate calculated as `(likes + comments + shares) / reach`, rather than raw counts, to fairly compare posts across different audience sizes
- ROI analysis — `engagement per dollar spent` calculated per platform to compare cost-efficiency, not just raw popularity

## 📊 Key Findings

| Finding | Insight |
|---|---|
| **Best content type** | Video content had the highest average engagement rate across all platforms |
| **Best posting time** | Monday evenings (5–8 PM) and Wednesday afternoons showed the strongest engagement, though the effect was modest rather than dominant |
| **Platform ROI** | TikTok delivered **~4x better engagement per dollar spent** than LinkedIn (1.46 vs. 0.34), despite similar total ad spend |

### Business takeaway
Total engagement alone can be misleading. When normalized for spend, TikTok was significantly more cost-efficient than platforms with similar or higher budgets — suggesting reallocating spend toward TikTok could improve overall campaign ROI, pending further testing at scale.

## 📁 Repository Contents

- `social_media_campaign_data.csv` — cleaned dataset
- SQL queries used for analysis
- Power BI dashboard (screenshots / `.pbix` file)

## 🎯 What I Learned

- Real-world data is never clean — handling inconsistent formats, missing values, and duplicates is often the majority of the actual work
- Small sample sizes can produce misleading averages if not filtered out
- The "right" metric depends on the business question — total volume and efficiency (per-dollar, per-user) can tell very different stories from the same data

---

*This project was built as a hands-on learning exercise while transitioning into data analytics from a commerce background.*
