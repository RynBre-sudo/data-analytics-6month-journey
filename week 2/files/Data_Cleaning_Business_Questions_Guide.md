# Understanding df_clean + Data Cleaning + Business Questions
## A Plain English Guide

---

## PART 1: WHAT IS df_clean?

### The Simple Explanation

When you load a dataset, you create a variable called `df` (short for DataFrame).
A DataFrame is just a table - rows and columns, like a spreadsheet in Python.

```python
df = pd.read_csv('mission_launches.csv')
```

Think of `df` as your **original, untouched data.**

Then you create `df_clean`:

```python
df_clean = df.copy()
```

This makes an **exact copy** of your original data.

**Why copy it?**
- You never want to change your original data
- If you make a mistake cleaning, you can always start over from `df`
- It's like working on a photocopy instead of the original document

### The Analogy

Imagine you have an original signed contract (df).
You make a photocopy (df_clean).
You write notes, make corrections, highlight things on the photocopy.
The original is always safe if you need to start over.

### What df_clean Looks Like

Your mission_launches df_clean has:
- **Rows:** Each row = one space mission launch
- **Columns:** Date, Organisation, Location, Detail, Rocket_Status, Price, Mission_Status

```
Row 0: SpaceX | Aug 7 2020 | Falcon 9 | Success | $50M
Row 1: CASC   | Aug 6 2020 | Long March | Success | $29.75M
Row 2: SpaceX | Aug 4 2020 | Starship | Success | (no price)
...
```

---

## PART 2: DATA CLEANING - WHAT IT IS AND WHY

### What Is "Dirty" Data?

Real-world data is almost never perfect. It comes from different systems, different people entering data, different time periods. Problems include:

**1. Missing Values (Nulls)**
Some cells are just empty. Nobody entered anything.
```
Price: 50.0, 29.75, NaN, 65.0, NaN, NaN
```
NaN = "Not a Number" = blank/empty

**2. Wrong Data Types**
A column that should be a number is stored as text.
```
Price column: "50.0", "29.75", "65.0"  ← these are TEXT, not numbers!
```
You can't do math on text (that's why you got the box plot error!)

**3. Inconsistent Formats**
Same type of data stored different ways.
```
Date column:
"Fri Aug 07, 2020 05:12 UTC"  ← has time + timezone
"Wed Nov 04, 2015"            ← just date, no time
```

**4. Duplicates**
The same row appearing twice.
```
Row 5: SpaceX | Aug 7 2020 | Falcon 9 | Success | $50M
Row 5: SpaceX | Aug 7 2020 | Falcon 9 | Success | $50M  ← exact copy!
```

**5. Outliers**
Values that seem impossible or extreme.
```
Price: 50, 65, 29, 450, 62, 48, 5000  ← that 5000 seems suspicious!
```

**6. Inconsistent Text**
Same thing written different ways.
```
Organisation: "SpaceX", "SPACEX", "Space X", "spacex"  ← all the same company!
```

---

## PART 3: YOUR SPECIFIC DATA CLEANING JOURNEY

Here's exactly what you cleaned in mission_launches and WHY each step mattered:

### Step 1: Make a Copy
```python
df_clean = df.copy()
```
**Why:** Protects original data

---

### Step 2: Handle Missing Values
```python
print(df_clean.isnull().sum())
```
This tells you how many blanks are in each column.

For mission_launches you likely saw:
```
Price    3375  ← 3,375 missing prices!
```

**What to do with missing values depends on the situation:**

**Option A: Drop rows with missing values**
```python
df_clean = df_clean.dropna(subset=['Price'])
```
Use when: That column is critical for your analysis
Risk: Lose a lot of data (3,375 rows = 78% of your dataset!)

**Option B: Fill with a value**
```python
df_clean['Price'] = df_clean['Price'].fillna(0)
```
Use when: 0 makes logical sense (no price = free or unknown)
Risk: Changes your statistics (average price will be lower)

**Option C: Fill with the average**
```python
df_clean['Price'] = df_clean['Price'].fillna(df_clean['Price'].mean())
```
Use when: You need all rows but don't want to skew averages

**Option D: Leave them as NaN**
```python
# Do nothing - just be careful when analyzing
```
Use when: You want to keep all rows AND be honest about missing data
Best for: When only some analyses need that column

**For mission_launches:** Option D is best for Price.
Keep all 4,324 rows. When analyzing price, use `.dropna()` just for that analysis.

---

### Step 3: Fix Data Types
```python
# Fix dates (mixed formats + timezones)
df_clean['Date'] = pd.to_datetime(df_clean['Date'], format='mixed', utc=True)

# Fix price (stored as text)
df_clean['Price'] = pd.to_numeric(df_clean['Price'], errors='coerce')
```

**Why dates matter:**
Once Date is a proper datetime, you can:
```python
df_clean['Date'].dt.year    # Extract just the year
df_clean['Date'].dt.month   # Extract just the month
df_clean['Date'].dt.day     # Extract just the day
```
Without fixing it, these don't work!

**Why price matters:**
Once Price is a proper number, you can:
```python
df_clean['Price'].mean()    # Calculate average
df_clean['Price'].max()     # Find most expensive
df_clean['Price'].sum()     # Total all prices
```
Without fixing it, these give errors (as you discovered!)

---

### Step 4: Remove Duplicates
```python
print(f"Before: {len(df_clean)} rows")
df_clean = df_clean.drop_duplicates()
print(f"After: {len(df_clean)} rows")
```

If before = after, you had no duplicates. 

---

### Step 5: Add Derived Columns
Sometimes you CREATE new columns from existing ones:

```python
# Extract year from date (useful for grouping)
df_clean['Year'] = df_clean['Date'].dt.year

# Extract decade
df_clean['Decade'] = (df_clean['Date'].dt.year // 10 * 10).astype(str) + 's'
```

These aren't cleaning exactly - they're ENRICHING your data to make analysis easier.

---

### Step 6: Verify Your Cleaning

After cleaning, always check:
```python
# How does it look now?
print(df_clean.info())         # Data types
print(df_clean.isnull().sum()) # Missing values
print(df_clean.describe())     # Statistics
print(df_clean.head())         # First few rows
```

**Ask yourself:**
- Do data types look right? (float64 for numbers, datetime for dates)
- Are missing value counts what you expect?
- Do the statistics look reasonable? (no prices of $1 million when average is $130K)

---

## PART 4: BUSINESS QUESTIONS - WHAT ARE THEY?

### The Simple Explanation

A business question is just:
**"What do I want to learn from this data?"**

Not every question is a good business question. Here's the difference:

**Just a data question:**
"How many rows are in this dataset?"
→ Answer: 4,324. So what?

**A business question:**
"Which organizations have the best launch success rates?"
→ This tells you who the reliable launch providers are. That matters!

### How to Think About It

Good business questions have:
1. **A clear "so what?"** - Why does the answer matter?
2. **Actionable insight** - Could someone make a decision based on the answer?
3. **Something worth investigating** - Not obvious just from looking at column names

---

## PART 5: HOW TO CHOOSE BUSINESS QUESTIONS

### Step 1: Understand Your Dataset

Before asking questions, understand:
- What does each row represent? (One space launch)
- What columns do you have? (Date, Organisation, Price, Status, etc.)
- Who would care about this data? (Space agencies, investors, journalists)
- What decisions might they make?

### Step 2: Look at Your Columns

For mission_launches, columns suggest these themes:

**Organisation column suggests:**
- Which orgs launch the most? (Volume question)
- Which orgs are most reliable? (Quality question)
- Which orgs are growing? (Trend question)

**Date column suggests:**
- How has launch frequency changed over time? (Trend question)
- What years had the most/fewest launches? (Volume question)
- Are launches seasonal? (Pattern question)

**Price column suggests:**
- Are launches getting cheaper? (Trend question)
- Who offers the best value? (Comparison question)
- What's the range of prices? (Distribution question)

**Mission_Status column suggests:**
- What's the overall success rate? (Summary question)
- Has success rate improved over time? (Trend question)
- Which rocket types fail most? (Risk question)

### Step 3: The 3 Types of Business Questions

**Type 1: What happened? (Descriptive)**
- How many launches per year?
- What's the average price?
- Which org launches the most?

**Type 2: Why did it happen? (Diagnostic)**
- Did success rates improve after [year]?
- Are newer rockets cheaper than older ones?
- Do some orgs only launch certain types of missions?

**Type 3: What should we do? (Prescriptive)**
- Which launch provider should we use?
- Is the cost of launches trending in a good direction?
- Are launches becoming more reliable?

**Start with Type 1 (descriptive).** Once you understand what happened, Type 2 and 3 follow naturally.

---

## PART 6: CHOOSING THE RIGHT QUESTIONS

### For Your Mission Launches Dataset

**Best questions to focus on (and why):**

**✅ Question 1: How have launches changed over time?**
- Why good: Shows a trend, tells a story, historically interesting
- Visualize with: Line chart (launches per year)
- Business use: Space industry growth story

**✅ Question 2: Which organizations are most successful?**
- Why good: Directly useful (who do you trust with a rocket?)
- Visualize with: Bar chart (success rate by org)
- Business use: Vendor selection decision

**✅ Question 3: Are launch costs trending up or down?**
- Why good: Economic question, commercially relevant
- Visualize with: Line chart (avg price over time)
- Business use: Budget planning, market analysis

**✅ Question 4: What's the overall success vs failure rate?**
- Why good: Simple but important baseline
- Visualize with: Pie chart (already did this!)
- Business use: Risk assessment

---

**Questions to skip for now:**

**❌ "What is the exact location of every launch?"**
- Why skip: Too granular, no clear business insight
- The data exists, but the answer doesn't tell you much useful

**❌ "What does the Detail column say?"**
- Why skip: It's just the rocket name, hard to aggregate meaningfully
- Would take a lot of work for unclear payoff

**❌ "How many launches happened on Tuesdays?"**
- Why skip: No useful business application
- Interesting trivia, not insight

---

## PART 7: HOW TO FRAME YOUR FINDINGS

Once you have answers, write them like a business person, not a coder.

**Code output:**
```
Year
1957     2
1958     1
...
2020    40
2021    51
```

**Business finding:**
"Launch frequency has grown dramatically over 6 decades, from just 2 launches in 1957 to 51 in 2021—a 25x increase. The most significant growth came after 2010, coinciding with the entry of private companies like SpaceX."

See the difference? Same data, but the second version:
- Tells a story
- Provides context
- Mentions the "why" (private companies)
- Uses specific numbers

**This is what analysts get paid for.** Anyone can run the code. Fewer people can tell the story.

---

## PART 8: QUICK REFERENCE

### df_clean Cheat Sheet

| Code | What It Does |
|------|-------------|
| `df.copy()` | Create safe copy to work on |
| `df.info()` | Show column names, types, non-null counts |
| `df.describe()` | Statistics for numeric columns |
| `df.head(10)` | Show first 10 rows |
| `df.isnull().sum()` | Count missing values per column |
| `df.duplicated().sum()` | Count duplicate rows |
| `df.drop_duplicates()` | Remove duplicate rows |
| `df.dropna()` | Remove rows with any missing value |
| `df.dropna(subset=['col'])` | Remove rows where specific column is null |
| `df['col'].fillna(0)` | Replace nulls in column with 0 |
| `pd.to_datetime(df['col'])` | Convert column to datetime |
| `pd.to_numeric(df['col'])` | Convert column to number |
| `df['col'].dt.year` | Extract year from datetime column |
| `df['col'].dtype` | Check data type of one column |

### Business Question Checklist

Before choosing a question, ask:
- [ ] What does the answer tell me?
- [ ] Who would care about this answer?
- [ ] Could someone make a decision based on this?
- [ ] Do I have the data to answer it?
- [ ] Is it interesting enough to visualize?

If you answer yes to 3+ of these, it's a good business question.

---

## THE BOTTOM LINE

**df_clean:** A safe copy of your data where you make changes without risking the original.

**Data cleaning:** Finding and fixing problems (missing values, wrong types, inconsistencies) so your analysis doesn't break or mislead.

**Business questions:** Questions whose answers help someone make a decision or understand something important—not just trivia about the data.

**The analyst's job:**
1. Get data
2. Clean it so you can trust it
3. Ask smart questions
4. Turn answers into insights
5. Tell the story

You're learning all 5 steps right now. 💙
