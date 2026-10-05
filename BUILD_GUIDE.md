# Build guide — HR Attrition Dashboard (.pbix)

Follow these clicks in **Power BI Desktop**. Dataset is fictional sample data (240 employees) — say so in the report footer, like a professional.

## 1. Get data
1. Open Power BI Desktop → **Get data → Text/CSV**
2. Load all three files from `data/`:
   - `fact_employee.csv`
   - `dim_department.csv`
   - `dim_role.csv`
3. In Power Query, check types: `is_leaver` = whole number, `monthly_salary_usd` / `annual_salary_usd` = currency/decimal, `tenure_years` = decimal. Close & Apply.

## 2. Model relationships (Model view)
- `dim_department[department_key]` → `fact_employee[department_key]` (1 to many, single direction)
- `dim_role[department_key]` → `fact_employee[department_key]` (1 to many, single direction)

## 3. Measures
1. **Home → Enter data** → create a table named `_Measures` (one column, no rows needed)
2. Create each measure from `dax/measures.dax` in `_Measures`
3. Apply the format notes at the bottom of that file (percentages 1 decimal, salary as USD)

Expected check values (whole dataset, no filters):
- Headcount **240** · Leavers **48** · Attrition % **20.0%** · Early Tenure Attrition % **30.6%**

## 4. Report pages

### Page 1 — Overview
- 4 KPI cards: Headcount, Leavers, Attrition %, Avg Tenure
- Bar chart: **Attrition % by department** (descending) — Customer Support 29.2% & Sales 29.0% on top
- Column chart: **Attrition % by tenure_band** (order: 0-2, 2-5, 5+)
- Slicers: department, gender, overtime
- Footer text box: "Fictional sample data (240 employees) for portfolio demonstration — HR Attrition Dashboard by Dhanush"

### Page 2 — Exit reasons & drivers
- Bar chart: Leavers by `exit_reason` (Career growth first, 19)
- Scatter or bar: Avg Job Satisfaction for leavers vs active (use is_leaver as legend)
- Bar: Attrition % by work_life_balance_1_5 score
- KPI: Overtime %

## 5. Save & publish to this repo
1. **File → Save as** → `HR_Attrition_Dashboard.pbix`
2. Upload the `.pbix` to this GitHub repo (Add file → Upload files) — GitHub shows "View raw"/download, which is what recruiters use
3. Take a screenshot of Page 1 (PNG) and add it to the repo as `dashboard-preview.png` — visuals sell the project
4. On your portfolio repo About description, use:
   `Power BI HR Attrition Dashboard: DAX measures, star-schema model and attrition insights on fictional HR data`

## Interview talking points
- Why a star schema (fact + dims) instead of one flat file
- Attrition % as DIVIDE(Leavers, Headcount) — safe against empty filters
- Early-tenure attrition (30.6%) as an onboarding/progression signal
- Career growth > compensation in exit reasons — progression paths before pay bands
