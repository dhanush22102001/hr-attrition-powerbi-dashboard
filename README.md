# HR Attrition Dashboard — Power BI

A Power BI People Analytics report: attrition KPIs, department and tenure deep-dives, and exit-reason drivers, built on a star-schema model with DAX measures.

> **Data honesty:** the dataset is fictional (240 sample employees) created for portfolio demonstration. The modelling, DAX and report design are production-style.

## What the report shows

- **Overview page:** Headcount, Leavers, Attrition % and Avg Tenure KPI cards; attrition by department (Customer Support 29.2%, Sales 29.0% highest); attrition by tenure band (0–2 yrs at 30.6%)
- **Drivers page:** exit reasons (Career growth #1 with 19 exits), satisfaction and work-life-balance cuts, overtime %

## Model (star schema)

| Table | Role |
|---|---|
| `fact_employee.csv` | One row per employee: tenure, salary, satisfaction, work-life balance, performance, overtime, is_leaver flag, exit reason |
| `dim_department.csv` | Department dimension |
| `dim_role.csv` | Job-role dimension |

## Files

| File | Purpose |
|---|---|
| `data/*.csv` | Power BI-ready dataset (load via Get Data → CSV) |
| `dax/measures.dax` | Every DAX measure with formatting notes |
| `BUILD_GUIDE.md` | Step-by-step Power BI Desktop build: relationships, measures, both report pages, expected check values |
| `HR_Attrition_Dashboard.pbix` | The finished report (added after the Desktop build) |

## Build it yourself

Open `BUILD_GUIDE.md` and follow it in Power BI Desktop — about 20–30 minutes. Check values: Headcount 240 · Leavers 48 · Attrition 20.0%.

## Skills demonstrated

Power BI · DAX · Star-schema data modelling · Power Query type handling · HR Analytics · People Analytics · Data visualization
