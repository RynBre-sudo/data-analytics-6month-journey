# Week 2 Summary
**Dates:** 05/18/2026 - 05/24/2026
**Dataset:** Space Mission Launches (Kaggle)
**Total Time:** ~10-12 hours

## What I Did
- Committed all Week 1 work to GitHub with detailed messages
- Wrote Week 1 summary + updated GitHub README
- Continued SQL on ThoughtSpot (filtering + aggregate lessons)
- Created Google Docs SQL tracker
- Built deeper Python analysis (business questions)
- Created and saved 3 business insight visualizations
- Wrote first business insights document

## Errors I Fixed (Real Learning!)
1. NameError: 'df_clean' not defined → must reload + clean data in each new notebook
2. Variables don't persist across notebooks or kernel restarts → Run All Cells top to bottom
3. Saving charts → used plt.savefig() instead of snipping tool
4. Git "no changes added to commit" → files were already committed in an earlier commit
5. Untracked files cluttering git status → created .gitignore for checkpoints/venv

## SQL Lessons Completed (ThoughtSpot)
- LIKE operator (wildcard matching)
- IN operator (match multiple values)
- BETWEEN, IS NULL
- AND, OR, NOT (multiple conditions)
- Aggregate functions + GROUP BY
- HAVING (filter groups vs WHERE filters rows)

## Key Findings About the Dataset
- Launches peaked in the 1970s with 1,012 launches (only decade over 1,000)
- Volume declined to ~63 launches in the 2020s
- Top success rates: ULA (99.3%), Arianespace (96.4%), Boeing (96.3%)
- Surprise: NASA was NOT in the top 3 despite name recognition
- Launch costs dropped ~61% from 2011 ($146.6M) to 2020 ($56.7M)

## What Clicked
- SQL felt natural since I use it often at work.
- Asking "why?" about the data patterns (the analyst mindset)
- SQL filtering felt easy for the most part. 

## What Needs More Practice
- Still getting comfortable with Git Hub
- I am at a good spot for SQL

## Business Insights Document
- Created mission-launches-insights.md with embedded charts
- 3 key findings + questions for further investigation
- Documented data quality notes (78% missing price data)

## GitHub Activity
- Multiple commits with detailed messages
- Added .gitignore
- Embedded visualizations in insights doc

## Next Week
- SQL JOINs deep dive (ThoughtSpot Advanced SQL) - critical interview skill!
- Python + pandas depth (Corey Schafer series)
- Statistics refresher (Khan Academy)
- Excel pivot tables intro