# Week 1 Summary
**Dates:** 05/12/2026 - 05/15/2026
**Dataset:** Space Mission Launches (Kaggle)
**Total Time:** ~10 hours

## What I Did
- Set up Python environment (Jupyter, pandas, matplotlib)
- Created GitHub portfolio repo
- Loaded and explored mission_launches.csv
- Cleaned data: fixed dates, timezones, price data type
- Created 3 Python visualizations
- Created 3 Tableau visualizations

## Errors I Fixed (Real Learning!)
1. Mixed date formats → pd.to_datetime(format='mixed')
2. Mixed timezones → utc=True
3. matplotlib not installed → pip install matplotlib
4. Kernel restart lost variables → Run All Cells
5. Price stored as text → pd.to_numeric(errors='coerce')

## Key Findings About the Dataset
- 4,324 space mission launches in dataset
- Most launches are from CASC
- 2019 had the most launches
- Average launch price: ~$130 million
- Most launches are successful

## What Clicked
- Understanding the table fields and data types
- Selecting Pie chart did not automatically create a pie chart. It created a grid with circles.

## What Needs More Practice
- Understanding when to create certain tables/graphs
- Marks and Graphs

## Tableau Public Link
(https://public.tableau.com/app/profile/brandy.steals3189/viz/Week1-SpaceMissionLaunchesAnalysis/MissionStatus?publish=yes)

## Next Week
- Continue SQL (Mode chapters 6-10)
- Deeper Python analysis
- Start writing business insights