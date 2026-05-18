# Data Analytics Journey - Complete Handoff Document
## Everything You Need to Continue in a New Conversation

---

## HOW TO USE THIS DOCUMENT

When you start a new conversation with Claude, say:
"I am continuing my 6-month data analytics journey. Here is my handoff document:"
Then paste this entire document OR upload it as a file.

---

## WHO I AM

**Name:** Brandy Steals
**Location:** Conway, PA (Baden, PA area)
**Current Job:** Senior Lead Engineer at FIS (Cranberry Township, PA)
**GitHub:** https://github.com/RynBre-sudo/data-analytics-6month-journey

**Professional Background:**
- 15+ years financial services (banking, fintech, PROFILE core banking system)
- 10+ years health insurance (Coventry Health Care, IDX/Intersystems system)
- 25+ years total software engineering experience
- Team lead managing 4 direct reports + offshore coordination
- Languages: MUMPS, PSL, Cache, Java, Python (learning)

**Current Situation:**
- FIS has had layoffs - situation uncertain but currently employed
- Job security for rest of 2025 (hopefully)
- Plan: Build data analytics skills as career backup/pivot
- **Mindset:** Non-urgent, calm learning journey. No anxiety. Steady pace.

---

## MY ANALYTICS BACKGROUND

**Already Have:**
- ✅ Google Data Analytics Certificate (Coursera, 2021 - completed all 8 courses + capstone)
- ✅ Python experience (built websites, deployed on GitHub)
- ✅ GitHub proficiency (active maintenance)
- ✅ SQL familiarity (use PROFILE's SQL at work daily)
- ✅ Excel basics (25 years finance experience)
- ✅ Business acumen (15+ years management)

**Currently Learning:**
- SQL refresher (Mode Analytics: https://mode.com/sql-tutorial/)
- Python data analysis (pandas, matplotlib)
- Tableau (just completed Week 1 visualizations)

---

## MY 6-MONTH PLAN OVERVIEW

**Goal:** Build a dual-industry data analytics portfolio
**Industries:** Financial Services (fintech/banking) + Health Insurance
**Specializations:** Customer Analytics + Business Intelligence
**Timeline:** 6 months (non-urgent, flexible)
**Time commitment:** ~10-12 hours/week (1.5 hrs weeknights + weekend)

**Why dual industry:**
- 15 years finance = fintech domain expertise
- 10 years health insurance = healthcare domain expertise
- Most analysts have ONE industry. I have TWO = rare, higher salary
- Target salary: $85K-$140K+ depending on timing

**Month-by-Month:**
- Month 1: Fundamentals refresh (SQL, Python, Tableau, Excel)
- Month 2: Customer Analytics specialization
- Month 3: Business Intelligence specialization
- Month 4: Integration + hybrid projects
- Month 5: Advanced deep dive (based on job market research)
- Month 6: Portfolio polish + future planning

---

## CURRENT PROGRESS

**Week:** Week 2 (just started)
**Month:** Month 1 (Fundamentals)

### Week 1 Completed ✅
- Python environment setup (Jupyter running on Windows)
- GitHub repo created: data-analytics-6month-journey
- Loaded + analyzed mission_launches.csv from Kaggle
- Fixed real-world data issues:
  - Mixed date formats → pd.to_datetime(format='mixed')
  - Mixed timezones → utc=True
  - Price stored as string → pd.to_numeric(errors='coerce')
  - matplotlib not installed → pip install matplotlib
- Created 3 Python visualizations (histogram, box plot, scatter)
- Created 3 Tableau visualizations (bar chart, line chart, pie chart)
- Published Tableau workbook to Tableau Public

### Week 2 In Progress 🔄
- Saturday: GitHub catch-up + Week 1 summary (in progress)
- Sunday onwards: SQL chapters + deeper Python analysis

---

## MY TOOLS & ENVIRONMENT

**Computer:** Windows PC (PowerShell terminal)
**Python:** Version 3.14.4
**Jupyter:** Running via `jupyter notebook` in PowerShell
**Work folder:** `C:\Users\blsst\Analytics\Month-1\`
**GitHub:** https://github.com/RynBre-sudo/data-analytics-6month-journey

**Installed packages:**
- pandas
- numpy
- matplotlib
- jupyter

**To start Jupyter:**
```
cd C:\Users\blsst\Analytics\Month-1
jupyter notebook
```

**Git commands:**
```
git add .
git commit -m "your message"
git pull origin main --no-rebase --no-edit
git push origin main
```
Note: Always pull before push to avoid conflicts!

---

## MY RESOURCES

### Primary Learning Resources:
- **SQL:** Mode Analytics Tutorial https://mode.com/sql-tutorial/ (follow top to bottom)
- **Python:** Corey Schafer YouTube https://www.youtube.com/@coreyschafer
- **Excel:** Alex The Analyst YouTube https://www.youtube.com/@AlexTheAnalyst
- **Tableau:** Alex The Analyst YouTube (Tableau playlist)
- **Statistics:** Khan Academy https://www.khanacademy.org/math/statistics-probability
- **Datasets:** Kaggle https://kaggle.com/datasets
- **SQL Reference:** W3Schools https://www.w3schools.com/sql/

**Note on Alex The Analyst:**
- Great for: Excel, Tableau, career advice, Python
- Skip: His MySQL videos (didn't resonate)
- Use for: Everything else

### Paid Courses (Planned for Month 2-3):
- Reforge Customer Analytics: $129
- Reforge Advanced Dashboarding: $129

### Skip:
- dataanalyst.com (affiliate site, not worth it)
- Random TikTok course promotions

---

## MY PORTFOLIO STRUCTURE

**GitHub repo:** data-analytics-6month-journey

**Planned structure:**
```
MONTH-1-FUNDAMENTALS/
├── sql-refresher/
├── python-refresher/ (mission_launches analysis)
├── tableau-refresher/
└── excel-refresher/

MONTH-2-CUSTOMER-ANALYTICS/
├── HEALTHCARE/ (insurance member churn + LTV)
└── FINTECH/ (bank customer churn)

MONTH-3-BUSINESS-INTELLIGENCE/
├── HEALTHCARE/ (insurance executive dashboard)
└── FINTECH/ (banking executive dashboard)

MONTH-4-INTEGRATION/
├── member-health-scorecard/
└── cohort-profitability/

MONTH-5-ADVANCED/ (based on job market research)
└── [chosen specialization]
```

**Target:** 14-18 polished projects by Month 6

---

## RESUME STATUS

**Current resume:** Brandy_Steals_Resume_2026.docx (already updated)

**What was added to resume:**
- Updated Professional Summary (mentions analytics transition)
- Added Python, Tableau, Power BI, Excel to Core Competencies
- Added Customer Analytics + Business Intelligence to competencies
- NEW SECTION: "Data Analytics Portfolio Development (In Progress)"
- NEW SECTION: "Certifications" with Google cert + Reforge in progress
- GitHub portfolio link added

**LinkedIn Status:**
- Headline should be updated to:
  "Data Analyst | Financial Services + Healthcare Insurance | Python • SQL • Tableau"
- Summary should mention transition + portfolio focus
- Certificate should be in Education section

**Resume update schedule:**
- End Month 1: Add 4 refresh projects
- End Month 2: Add CA projects (especially Healthcare LTV star project)
- End Month 3: Add BI projects
- End Month 4: Add integration projects
- End Month 5: Final version - job ready

---

## MY DATASETS

**Current dataset:** mission_launches.csv (Kaggle space launches)
- 4,324 rows, 8 columns
- Columns: Date, Organisation, Location, Detail, Rocket_Status, Price, Mission_Status
- Issues found + fixed: mixed dates, mixed timezones, Price stored as string
- Cleaned version: mission_launches_cleaned.csv

**Key data fixes learned:**
```python
# Fix mixed date formats + timezones
df_clean['Date'] = pd.to_datetime(df_clean['Date'], format='mixed', utc=True, errors='coerce')

# Fix numbers stored as text
df_clean['Price'] = pd.to_numeric(df_clean['Price'], errors='coerce')

# Always make a copy first
df_clean = df.copy()
```

**Future datasets (Month 2):**
- Healthcare: "Health Insurance Cross Sell" or "Medical Cost Personal Datasets" (Kaggle)
- Fintech: "Bank Customer Churn" (Kaggle)

---

## SQL PROGRESS

**Resource:** Mode Analytics https://mode.com/sql-tutorial/
**Status:** Completed chapters 1-5 (basics)
**Currently on:** Chapter 6 (GROUP BY: Group & Aggregate Data)
**Note:** Mode updated their site - chapter numbers may differ from old guides. Just follow top to bottom.

**Topics covered so far:**
- SELECT, FROM, WHERE, LIMIT
- Aggregate functions (COUNT, SUM, AVG, MIN, MAX)
- ORDER BY

**Topics coming up (Week 2):**
- GROUP BY + HAVING (current)
- Logical Operators (AND, OR, NOT)
- LIKE operator (pattern matching)
- IN operator (multiple values)
- JOINS (critical skill - comes up in every interview)

**SQL already familiar from work:** PROFILE system uses its own SQL dialect
- Basic queries feel easy
- Just refreshing syntax and learning analyst-specific patterns

---

## PYTHON PROGRESS

**Status:** Comfortable with basics, learning data analysis specifics

**What I can do:**
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load data
df = pd.read_csv('file.csv')
df_clean = df.copy()

# Explore
df.info()
df.describe()
df.head(10)
df.isnull().sum()
df.duplicated().sum()

# Clean
df_clean = df_clean.dropna(subset=['important_column'])
df_clean['col'] = df_clean['col'].fillna(0)
df_clean = df_clean.drop_duplicates()
df_clean['Date'] = pd.to_datetime(df_clean['Date'], format='mixed', utc=True, errors='coerce')
df_clean['Price'] = pd.to_numeric(df_clean['Price'], errors='coerce')

# Analyze
df_clean['Year'] = df_clean['Date'].dt.year
df_clean.groupby('Organisation')['Mission_Status'].value_counts()

# Visualize
plt.figure(figsize=(10, 5))
plt.hist(df_clean['Year'], bins=20, edgecolor='black')
plt.title('Title')
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.tight_layout()
plt.show()
```

**Errors encountered + fixed:**
1. Jupyter not found → pip install jupyter notebook
2. Mixed date formats → format='mixed'
3. Mixed timezones → utc=True
4. matplotlib not found → pip install matplotlib
5. Kernel restart loses variables → Run All Cells
6. Numbers stored as text → pd.to_numeric()

---

## TABLEAU PROGRESS

**Status:** Refreshed basics, 3 visualizations created

**What I built (Week 1):**
- Bar chart: Top 10 Organizations by launches
- Line chart: Launches over time by mission status
- Pie chart: Mission success rate

**Published to:** Tableau Public (account created)
**File saved locally:** Week 1 - Space Mission Launches Analysis.twb

**Tableau key lessons learned:**
- Use Extract (not Live) for Tableau Public uploads
- Drag fields to Rows/Columns/Marks to build charts
- "Show Me" button suggests chart types
- Ctrl+Z to undo

**Still to do in Week 2:**
- Add Tableau link to GitHub
- Build more visualizations as projects progress

---

## NOTES SYSTEM

**Recommendation:** Paper notebook (decided this is better for learning retention)
- Write concepts by hand = better memory
- Sketch out ideas, draw arrows
- Date each page + write topic at top
- Use GitHub/Google Docs for actual code snippets

---

## JOB MARKET STRATEGY

**Reconnaissance plan:**
- Month 3: Light browsing (30-45 min, 2-3x)
- Month 4: Active research (1 hour/week, Thursdays)
- End Month 4: Decide Month 5 specialization based on market signals
- Month 5: Build what market wants

**Networking (starts Month 2):**
- Monday: 1-2 LinkedIn connection requests (5 min)
- Tuesday: Comment on 1-2 industry posts (5 min)
- Thursday: Job market research (30-45 min)
- Total added time: 15-30 min/week

**Target companies:**
- Financial: Chase, Bank of America, Block, Stripe, Chime, SoFi
- Insurance: Aetna, Humana, UnitedHealth, Cigna, Oscar Health
- Both industries welcome (you have domain expertise in both)

**Target roles:**
- Senior Data Analyst
- Analytics Engineer
- BI Analyst
- Business Analyst (analytics focus)

**Target salary:**
- With dual industry expertise: $100K-$140K+
- If needed quickly: $85K-$110K

**FIS work impact - DOCUMENT THIS (private file):**
- Team size: 4 direct reports + offshore
- Years at FIS: 2013-present (12+ years)
- Capture: client retention numbers, revenue portfolio supports, any metrics
- This disappears when you leave - document now!

---

## WEEK 2 SCHEDULE (CURRENT WEEK)

**Saturday:** GitHub catch-up + Week 1 summary
**Sunday:** SQL chapters (GROUP BY, Logical Operators, LIKE, IN)
**Monday:** Deeper Python analysis (business questions)
**Tuesday:** Visualize insights
**Wednesday:** Write business insights document
**Thursday:** More SQL (JOINS - critical skill)
**Total:** ~10-12 hours

**Business questions to answer with mission_launches data:**
1. How have launches changed over time? (trend)
2. Which organizations are most successful? (reliability)
3. Are launch costs trending up or down? (economics)
4. What's the overall success rate? (risk)

---

## MONTH 1 REMAINING CHECKLIST

**Week 1:** ✅ Complete
**Week 2:** 🔄 In progress
**Week 3-4 (still to do):**
- [ ] Excel mini-module (pivot tables, VLOOKUP, SUMIF)
- [ ] More SQL (complete Mode tutorial)
- [ ] Deeper Python analysis
- [ ] Business insights documented
- [ ] All work committed to GitHub
- [ ] Month 1 summary written

---

## KEY CONCEPTS LEARNED

### df_clean Explained
- `df` = original data (never touch)
- `df_clean = df.copy()` = working copy (make all changes here)
- Like a photocopy - work on the copy, original stays safe

### Data Cleaning Steps
1. Make a copy (df_clean = df.copy())
2. Handle missing values (drop, fill, or leave)
3. Fix data types (dates, numbers stored as text)
4. Remove duplicates
5. Add derived columns (Year from Date, etc.)
6. Verify everything looks right

### Business Questions - How to Choose
Ask: "So what? Who would care about this answer?"
- Bad: "How many rows?" → Nobody cares
- Good: "Which orgs are most reliable?" → Launch buyers care!

Three types:
1. Descriptive: What happened?
2. Diagnostic: Why did it happen?
3. Prescriptive: What should we do?
Start with descriptive, then go deeper.

### Git Workflow (Windows/PowerShell)
```
cd C:\Users\blsst\Analytics\Month-1
git add .
git commit -m "your message"
git pull origin main --no-rebase --no-edit
git push origin main
```
Always pull before push!

---

## MONTHLY REVIEW PROCESS

At end of each month, start a NEW conversation and:
1. Upload this handoff document (updated)
2. Share GitHub links to projects
3. Tell Claude what went well + what was harder
4. Ask for Month 2 plan adjustments

---

## DOCUMENTS I HAVE

All saved in outputs from previous conversations:
1. **COMPLETE_PLAN_FINAL_v4.md** - Full 6-month plan with all adjustments
2. **QUICK_OVERVIEW_FINAL_v4.md** - One-page summary
3. **WEEK_2_SCHEDULE.md** - This week's detailed plan
4. **Data_Cleaning_Business_Questions_Guide.md** - Plain English guide
5. **Tableau_Practice_Guide.md** - Step by step Tableau instructions
6. **Monthly_Plan_Review_Guide.md** - How to review each month
7. **CALM_RESTART_GUIDE.md** - Mindset + non-urgent approach
8. **Brandy_Steals_Resume_2026_Updated.docx** - Resume with analytics added

---

## MY PERSONALITY + LEARNING STYLE NOTES

(For Claude to understand how to help me best)

- **Pace:** Non-urgent, calm, sustainable. No anxiety.
- **Time:** Evenings after 6pm, weekends flexible
- **Style:** Step by step instructions work best
- **When stuck:** Share screenshots of errors, I'll troubleshoot with you
- **SQL:** Already familiar from work (PROFILE system) - basics feel easy
- **Prefers:** Mode Analytics for SQL (tried Alex The Analyst MySQL - didn't resonate)
- **Notes:** Paper notebook for concepts, GitHub for code
- **Mindset:** This is building, not racing. Joy over fear.
- **Check-ins:** End of each month for review + next month planning
- **Adjustments:** Plan changes based on what's working and what isn't

---

## QUICK REFERENCE - COMMON COMMANDS

### Start Jupyter
```
cd C:\Users\blsst\Analytics\Month-1
jupyter notebook
```

### Standard Python Imports
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

### Load + Clean Data
```python
df = pd.read_csv('filename.csv')
df_clean = df.copy()
df_clean['Date'] = pd.to_datetime(df_clean['Date'], format='mixed', utc=True, errors='coerce')
df_clean['Price'] = pd.to_numeric(df_clean['Price'], errors='coerce')
df_clean = df_clean.drop_duplicates()
```

### Git Push Workflow
```
git add .
git commit -m "message"
git pull origin main --no-rebase --no-edit
git push origin main
```

### Install Missing Package
```
pip install package_name
```

### After Kernel Restart
- Always run cells from top to bottom
- Or: Kernel → Restart Kernel and Run All Cells

---

## ENCOURAGEMENT NOTE

You've already accomplished a lot:
- Set up a complete Python analytics environment
- Learned to troubleshoot real data errors
- Built 3 Python + 3 Tableau visualizations
- Published to Tableau Public
- Maintained a GitHub portfolio
- Started SQL refresher

You're not starting over in a new conversation.
You're continuing a journey that's already well underway.

**Steady. Calm. Sustainable. You've got this. 💙**
