# Tableau Practice - Detailed Guide
## For Saturday's Tableau Work

**Time:** 1.5-2 hours
**Dataset:** mission_launches.csv (or your cleaned version)
**Goal:** 3 simple visualizations + 1 public link

---

## STEP 1: Save Your Cleaned Data First (5 min)

Before opening Tableau, save your cleaned dataset from Jupyter as a new CSV.

In Jupyter, add a cell:

```python
# Save cleaned data for Tableau
df_clean.to_csv('mission_launches_cleaned.csv', index=False)
print("Saved! File location:", )

import os
print(os.getcwd())  # Shows where the file was saved
```

Run it. Note the file path - you'll need to find this file later.

---

## STEP 2: Sign Up for Tableau Public (10 min)

1. Go to: https://public.tableau.com/
2. Click "Sign Up" (top right)
3. Create free account with your email
4. **Download Tableau Public Desktop** (the application)
   - Click "Create" or "Download" 
   - Install the .exe file
   - Open it after installation

**Note:** Tableau Public is free but everything you create is PUBLIC. That's fine for portfolio work.

---

## STEP 3: Open Tableau & Connect to Your Data (10 min)

1. **Open Tableau Public Desktop**
2. You'll see a start screen with "Connect" on the left
3. Under "To a File" → Click **"Text File"**
4. Navigate to your `mission_launches_cleaned.csv` file
5. Click "Open"

You should see:
- A "Data Source" tab at the bottom
- Your data appears in a grid
- Column names at the top with data type icons (# for number, Abc for text, calendar for date)

**Check your data types are correct:**
- Price should show **#** (number)
- Date should show **calendar icon** (date)
- Organisation should show **Abc** (text)

If any are wrong, click the icon to change it.

---

## STEP 4: Create Your First Sheet

Click **"Sheet 1"** at the bottom (next to "Data Source"). You'll see Tableau's main workspace.

### Understanding the Layout

**Left Side:**
- **Tables panel** - Lists all your columns
- **Dimensions** (top, blue) - Categories (text, dates, IDs)
- **Measures** (bottom, green) - Numbers you can calculate

**Top:**
- **Columns shelf** - What goes horizontally
- **Rows shelf** - What goes vertically

**Right side:**
- **Show Me panel** - Suggests chart types

---

## STEP 5: VIZ #1 - Bar Chart of Launches by Organization (20 min)

**Goal:** See which space organizations have launched the most rockets

1. **Drag `Organisation`** from left panel → drop on **Rows** shelf at top
2. **Drag `Number of Records`** (or `Organisation` again) from left panel → drop on **Columns** shelf
   - If using `Organisation`, change it to "Count" by clicking the green pill
3. You should see a horizontal bar chart!

**Make it look better:**

4. Click on the **sort icon** on the toolbar (looks like bars getting bigger) to sort by count
5. **Limit to top 10:**
   - Right-click on `Organisation` in Rows → Filter
   - Top tab → By Field → Top 10 by Count of Organisation
   - Click OK

**Add a title:**

6. Double-click "Sheet 1" at the top of your chart
7. Type: "Top 10 Space Organizations by Launches"

**Rename the sheet:**

8. Double-click "Sheet 1" tab at the bottom
9. Rename to: "Top Organizations"

---

## STEP 6: VIZ #2 - Line Chart of Launches Over Time (20 min)

**Create a new sheet:**

1. Click the **"New Sheet"** icon at the bottom (small page icon next to Sheet 1 tab)

**Build the chart:**

2. **Drag `Date`** → drop on **Columns** shelf
   - Tableau will probably default to YEAR. Good!
3. **Drag `Number of Records`** → drop on **Rows** shelf
   - This counts how many launches per year

You should see a line chart showing launches over time!

**Make it look better:**

4. Right-click on "YEAR(Date)" in Columns → Choose "Year" if not already
5. Hover over the line - tooltips show year + count

**Add color:**

6. Drag `Mission_Status` to the **Color** card (left side, "Marks" section)
7. Now you see launches by year, colored by success/failure

**Title and rename:**

8. Double-click title: "Space Launches Over Time by Mission Status"
9. Rename sheet: "Launches Over Time"

---

## STEP 7: VIZ #3 - Pie Chart of Mission Status (15 min)

**Create another new sheet:**

1. Click the **"New Sheet"** icon

**Build the chart:**

2. **Drag `Mission_Status`** → drop on **Rows** shelf
3. **Drag `Number of Records`** → drop on **Columns** shelf

You'll see a bar chart. Let's change it to a pie chart:

4. Look at the **Marks card** (left side)
5. Click the dropdown that says "Automatic" → Select **"Pie"**
6. The chart looks small/empty - we need to add the data:
7. **Drag `Mission_Status`** from left panel → drop on **Color** in Marks card
8. **Drag `Number of Records`** from left panel → drop on **Angle** in Marks card

**Make it bigger:**

9. Click "Size" in Marks card → Drag slider right
10. Or: In the menu bar, click **Format → Cell Size → Bigger**

**Add percentage labels:**

11. **Drag `Number of Records`** → drop on **Label** in Marks card
12. Right-click on it → Quick Table Calculation → Percent of Total

**Title and rename:**

13. Title: "Mission Success Rate"
14. Rename sheet: "Mission Status"

---

## STEP 8: Save Your Work (5 min)

1. Click **File** → **Save to Tableau Public As...**
2. Name it: "Week 1 - Space Mission Launches Analysis"
3. Tableau will ask you to sign in (use your account from Step 2)
4. Click Save

**This will:**
- Upload your workbook to Tableau Public (your portfolio)
- Give you a public URL you can share

**Important:** Tableau Public ONLY saves online (not locally). That's normal.

---

## STEP 9: Get Your Public Link (5 min)

1. After saving, Tableau opens your published workbook in your browser
2. **Copy the URL** from your browser
3. Save it somewhere (your GitHub README, notes file, etc.)

It will look like:
```
https://public.tableau.com/views/YourWorkbookName/Sheet1
```

This is your portfolio piece! Anyone can view it.

---

## STEP 10: Add to GitHub (10 min)

Add a file to your GitHub repo: `tableau-week1.md`

```markdown
# Week 1 - Tableau Visualizations

## Dataset
Space Mission Launches (Kaggle)

## Visualizations Created
1. **Top 10 Space Organizations** - Bar chart showing which orgs launched the most rockets
2. **Launches Over Time** - Line chart of launches by year, colored by success status
3. **Mission Success Rate** - Pie chart showing percentage of successful vs failed missions

## Tableau Public Link
[Insert your Tableau Public link here]

## Key Findings
- [What did you notice in the data?]
- [Any surprises?]
- [Most interesting visualization?]

## Time Spent
~2 hours
```

Commit and push to GitHub.

---

## TROUBLESHOOTING

### "I can't find my CSV file"
- In Tableau, click "More..." under "To a File"
- Browse to where you saved it (probably your Analytics/Month-1 folder)

### "My dates aren't showing as dates"
- Right-click the Date column in the Data Source view
- Change Data Type → Date or Date & Time

### "My chart looks wrong"
- Click the **"Show Me"** button (top right) for chart type suggestions
- Tableau will recommend chart types based on what you've dragged

### "I want to undo something"
- Ctrl+Z works! Use it often
- Or click the back arrow in the toolbar

### "The pie chart is tiny"
- Marks card → Size → Drag slider right
- Or use Format menu → Cell Size

---

## QUICK REFERENCE - Tableau Basics

| Action | How |
|--------|-----|
| Add field to chart | Drag from left panel to Rows/Columns/Marks |
| Change chart type | Click "Show Me" or use Marks card dropdown |
| Sort data | Click sort icon in toolbar |
| Filter data | Drag field to Filters card |
| Change color | Drag field to Color in Marks card |
| Add labels | Drag field to Label in Marks card |
| Calculate aggregation | Right-click pill → Measure → Sum/Count/Avg |

---

## YOUR GOAL TOMORROW

By end of Saturday, you should have:
- ✅ Tableau Public account
- ✅ 3 visualizations created
- ✅ Published to Tableau Public (saved online)
- ✅ Public link saved
- ✅ Added link to GitHub

**Time estimate:** 1.5-2 hours

**Don't worry about making them look beautiful.** Function over form. You can polish later.

---

## REMEMBER

This is a refresher, not perfection. Tableau has a lot of features. Today you just need:
- Drag fields to make charts
- Save your work online
- Get the public link

That's it. You're not building a masterpiece, just remembering how it works.

**Have fun with it!** 🚀

If you get stuck, take a screenshot and message me. I'll help you figure it out.
