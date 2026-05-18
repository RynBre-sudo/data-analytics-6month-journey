# Week 2 Schedule
## Building on Your Week 1 Foundation

**Start Date:** Saturday
**End Date:** Following Sunday
**Total Time:** ~10-12 hours
**Pace:** Relaxed, enjoyable, no pressure

---

## WHAT YOU BUILT IN WEEK 1

Before we dive in, look at what you accomplished:
- ✅ Python environment running
- ✅ GitHub repo active
- ✅ Real dataset loaded + cleaned
- ✅ Fixed mixed dates, timezones, data types
- ✅ 3 Python visualizations
- ✅ 3 Tableau visualizations
- ✅ Real troubleshooting experience

**Week 2 builds directly on this.** You're not starting over—you're going deeper.

---

## WEEK 2 GOALS

By end of Week 2 you will have:
- ✅ GitHub updated with all Week 1 work + summary
- ✅ SQL refresher continued (Mode Analytics chapters 6-10)
- ✅ Deeper Python analysis of your dataset
- ✅ First real "business insights" written up
- ✅ Started thinking about your Month 1 project

---

## SATURDAY (2-3 hours)
### GitHub Catch-Up + Week 1 Summary

**This is your priority today.** Get everything committed and documented before moving forward.

### Part 1: GitHub Commit (45 min)

Open PowerShell and navigate to your folder:
```
cd C:\Users\blsst\Analytics\Month-1
```

Add all your files:
```
git add .
```

Commit with a detailed message:
```
git commit -m "Week 1 Complete: Data cleaning + Python + Tableau

COMPLETED:
- Loaded mission_launches.csv (4,324 rows, 8 columns)
- Fixed mixed date formats (format='mixed')
- Fixed mixed timezones (utc=True)
- Converted Price from string to float (pd.to_numeric)
- Created 3 Python visualizations (histogram, box plot, scatter)
- Created 3 Tableau visualizations (bar, line, pie)
- Published Tableau workbook

KEY LEARNINGS:
- Real-world data is messy (mixed formats, wrong types)
- How to read and fix error messages
- Matplotlib for Python charts
- Tableau basics (connect, drag, publish)

Time invested: ~10 hours"
```

Push to GitHub:
```
git push origin main
```

---

### Part 2: Week 1 Summary File (30 min)

Create a new file in Jupyter or your text editor:
Save as: `WEEK-1-SUMMARY.md` in your Analytics/Month-1 folder

```markdown
# Week 1 Summary
**Dates:** [Start date] - [End date]
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
- Most launches are from [what did you see?]
- [Year] had the most launches
- Average launch price: ~$130 million
- Most launches are successful

## What Clicked
- [What felt natural?]
- [What surprised you?]

## What Needs More Practice
- [What was confusing?]
- [What do you want to revisit?]

## Tableau Public Link
[Paste your link here if you have it]

## Next Week
- Continue SQL (Mode chapters 6-10)
- Deeper Python analysis
- Start writing business insights
```

Add + commit this file:
```
git add WEEK-1-SUMMARY.md
git commit -m "Add Week 1 summary"
git push origin main
```

---

### Part 3: Update GitHub README (30 min)

On GitHub.com, edit your main README.md to add Week 1 completion:

```markdown
## Progress Log

### Week 1 ✅ COMPLETE
**Focus:** Fundamentals setup + real data cleaning

**What I Built:**
- mission_launches.csv loaded and cleaned
- 3 Python visualizations
- 3 Tableau visualizations

**Key Skills Practiced:**
- pandas data cleaning
- matplotlib visualization
- Tableau basics
- Real-world error troubleshooting

**Time Invested:** ~10 hours

[See Week 1 Summary](WEEK-1-SUMMARY.md)

---

### Week 2 🔄 IN PROGRESS
**Focus:** SQL refresher + deeper analysis
```

**Saturday Deliverables:**
- ✅ All Week 1 work committed to GitHub
- ✅ Week 1 summary written
- ✅ README updated
- ✅ Clean, professional portfolio

---

## SUNDAY (1.5-2 hours)
### SQL Refresher - Continue Mode Analytics

**Where you left off:** Mode Analytics chapters 1-5
**Today's goal:** Chapters 6-8

**Go to:** https://mode.com/sql-tutorial/

### What Chapters 6-8 Cover:

**Chapter 6: JOINS**
This is one of the most important SQL skills.
A JOIN connects two tables together.

Example:
```sql
-- Get customer info + their orders
SELECT customers.name, orders.total
FROM customers
JOIN orders ON customers.id = orders.customer_id
```

**Chapter 7: Advanced JOINs (LEFT, RIGHT, FULL)**
- INNER JOIN: Only rows that match in BOTH tables
- LEFT JOIN: All rows from left table, matching from right
- RIGHT JOIN: All rows from right table, matching from left

**Chapter 8: UNION**
Stacks results from two queries on top of each other

### Your Task:
1. Read + do the exercises in Mode chapters 6-8
2. Take notes on JOINs (this is important for analyst work)
3. Try to write 3-5 practice queries yourself

**Note:** Mode's exercises use their sample database. That's fine - it's practicing the syntax that matters.

**Time: 1.5-2 hours**

---

## MONDAY (1.5 hours)
### Deeper Python Analysis

Now that your data is clean, let's ask real business questions.

**Open your Jupyter notebook** with the cleaned data, add new cells:

### Business Question 1: Which organizations are most successful?

```python
# Success rate by organization (top 10 orgs)
top_orgs = df_clean['Organisation'].value_counts().head(10).index

# Filter to top 10 orgs
top_org_data = df_clean[df_clean['Organisation'].isin(top_orgs)]

# Success rate per org
success_rate = top_org_data.groupby('Organisation')['Mission_Status'].apply(
    lambda x: (x == 'Success').sum() / len(x) * 100
).round(1).sort_values(ascending=False)

print("Success Rate by Organization (%):")
print(success_rate)
```

### Business Question 2: How have launches changed over decades?

```python
# Add decade column
df_clean['Decade'] = (df_clean['Date'].dt.year // 10 * 10).astype(str) + 's'

# Count by decade
decade_launches = df_clean.groupby('Decade').size()
print("\nLaunches by Decade:")
print(decade_launches)
```

### Business Question 3: Are launches getting cheaper?

```python
# Average price by year (only where price exists)
price_by_year = df_clean.groupby(df_clean['Date'].dt.year)['Price'].mean().dropna()
print("\nAverage Launch Price by Year (millions USD):")
print(price_by_year.tail(10))  # Last 10 years
```

**Write down what you find! These are your business insights.**

---

## TUESDAY (1.5 hours)
### Visualize Your Business Insights

Turn your Monday analysis into charts.

**In Jupyter, add visualization cells:**

### Chart 1: Success Rate by Organization

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(12, 6))
success_rate.sort_values().plot(kind='barh', color='steelblue')
plt.title('Mission Success Rate by Top 10 Organizations (%)')
plt.xlabel('Success Rate (%)')
plt.axvline(x=90, color='red', linestyle='--', label='90% threshold')
plt.legend()
plt.tight_layout()
plt.show()
```

### Chart 2: Launches by Decade

```python
plt.figure(figsize=(10, 5))
decade_launches.plot(kind='bar', color='orange', edgecolor='black')
plt.title('Space Launches by Decade')
plt.xlabel('Decade')
plt.ylabel('Number of Launches')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### Chart 3: Average Price Over Time

```python
plt.figure(figsize=(12, 5))
plt.plot(price_by_year.index, price_by_year.values, marker='o', linewidth=2)
plt.title('Average Rocket Launch Price Over Time')
plt.xlabel('Year')
plt.ylabel('Average Price (millions USD)')
plt.grid(True, alpha=0.3)
plt.tight_layout()
plt.show()
```

---

## WEDNESDAY (1 hour)
### Write Your Business Insights

This is the skill that separates good analysts from great ones—**turning data into a story**.

Create a new file: `mission-launches-insights.md`

```markdown
# Space Mission Launches - Business Insights
**Dataset:** 4,324 space missions
**Analysis by:** Brandy Steals
**Date:** [Today's date]

## Executive Summary
[2-3 sentences: What is this dataset? What are the most important findings?]

## Key Finding 1: Launch Volume Over Time
[What did you see? Are launches increasing? When was the peak?]

## Key Finding 2: Organization Performance
[Which orgs have the best success rates? Any surprises?]

## Key Finding 3: Launch Costs
[Are launches getting more or less expensive? What's the trend?]

## Interesting Observations
- [Something surprising you noticed]
- [Something that makes sense given what you know]
- [A question this data raises]

## Data Quality Notes
- Dataset had mixed date formats (fixed with format='mixed')
- Mixed timezones (standardized to UTC)
- Price column stored as string (converted to float)
- ~3,375 rows missing price data (78% of dataset)

## Tools Used
- Python (pandas, matplotlib)
- Tableau Public
```

Commit this to GitHub:
```
git add mission-launches-insights.md
git commit -m "Add business insights from mission launches analysis"
git push origin main
```

---

## THURSDAY (1 hour)
### Continue SQL - Mode Analytics

**Today's goal:** Chapters 9-10

**Chapter 9: SQL Aggregate Functions (Advanced)**
- COUNT, SUM, AVG, MIN, MAX refresher
- Using HAVING (like WHERE but for groups)
- Nested aggregates

Example:
```sql
-- Find organizations with more than 50 launches
SELECT Organisation, COUNT(*) as launch_count
FROM mission_launches
GROUP BY Organisation
HAVING COUNT(*) > 50
ORDER BY launch_count DESC
```

**Chapter 10: SQL Subqueries**
- A query inside a query
- Useful for complex filtering

Example:
```sql
-- Find launches by orgs with above-average success rates
SELECT *
FROM mission_launches
WHERE Organisation IN (
    SELECT Organisation
    FROM mission_launches
    WHERE Mission_Status = 'Success'
    GROUP BY Organisation
    HAVING COUNT(*) > 100
)
```

**Your task:**
1. Read chapters 9-10
2. Do the exercises
3. Write 3 practice queries in your notebook
4. Commit to GitHub

---

## FRIDAY (Optional - Light day)
### Review + Prep for Weekend

**Take it easy today.** Just review the week.

1. Look back at what you built
2. Update your notes
3. Any quick questions or stuck points → ask me
4. Think about: What do you want to do in Week 3?

---

## WEEKEND (Optional)
### Explore or Rest

**Option A: Rest**
- Take the weekend off
- You've earned it

**Option B: Explore**
- Try a second Kaggle dataset (healthcare or finance?)
- Build 1-2 more visualizations
- Or dig deeper into Mode SQL

**Option C: Tableau polish**
- Go back to your Tableau workbook
- Make your 3 charts look nicer
- Add titles, colors, tooltips

---

## WEEK 2 SUMMARY - WHAT YOU'LL HAVE BY NEXT SUNDAY

**GitHub:**
- ✅ All Week 1 work committed + documented
- ✅ Week 1 summary file
- ✅ Business insights document
- ✅ Advanced Python visualizations

**SQL:**
- ✅ Mode Analytics chapters 6-10 completed
- ✅ JOINs understood (important skill!)
- ✅ Practice queries written

**Python:**
- ✅ Business questions answered with data
- ✅ Insights visualized
- ✅ Analysis documented

**Skills Added:**
- SQL JOINs (major skill)
- SQL subqueries
- Groupby analysis in Python
- Business insight writing (turning data into story)

---

## TIME COMMITMENT

| Day | Time | Focus |
|-----|------|-------|
| Saturday | 2-3 hours | GitHub catch-up + Week 1 summary |
| Sunday | 1.5-2 hours | SQL chapters 6-8 |
| Monday | 1.5 hours | Deeper Python analysis |
| Tuesday | 1.5 hours | Visualize insights |
| Wednesday | 1 hour | Write business insights |
| Thursday | 1 hour | SQL chapters 9-10 |
| Friday | Optional | Review + rest |
| **Total** | **~10-12 hours** | **Solid Week 2** |

---

## IMPORTANT NOTES

**Don't skip the GitHub catch-up on Saturday.** It's tempting to jump to new stuff, but having clean, documented work matters for your portfolio.

**The business insights document is important.** This is what makes you different from someone who just runs code. You turn data into a story. That's what analysts get paid for.

**JOINs are critical.** Spend extra time on chapter 6-7 if needed. JOINs come up in almost every data analyst interview.

**No stress if you fall behind.** This is a flexible guide, not a strict schedule. Do what fits your week.

---

## COME BACK NEXT WEEKEND

When you check in at end of Week 2, tell me:
- What you built
- How the SQL felt (easier or harder than expected?)
- Did you enjoy the business insights part?
- What do you want to focus on in Week 3?

We'll plan Week 3 together. 💙

---

## YOU'RE DOING GREAT

Week 1 was setup + basics.
Week 2 is going deeper.

By end of Week 2, your GitHub will look like a real analyst portfolio.
And you'll know JOINs—which is one of the most used SQL skills in the field.

**One week at a time. You've got this.** 🚀
