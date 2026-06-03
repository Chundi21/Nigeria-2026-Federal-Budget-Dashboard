# Nigeria 2026 Federal Budget Dashboard

This is an interactive 4-page Power BI report analyzing ₦51.59 trillion in Nigeria's 2026 federal budget allocations across 56 Ministries, Departments, and Agencies (MDAs), with drill-down by sector, ministry, and individual budget line item.


## Overview
Nigeria's federal budget is public data, but in its raw form, it is a document most citizens, journalists, and policymakers struggle to interrogate meaningfully. This project transforms the 2026 appropriation data into a navigable Power BI dashboard that makes sector priorities, ministry-level allocations, and line item breakdowns immediately legible.
The analysis covers three critical sectors in depth: the Security, Healthcare, and Education sectors, alongside a general overview of the full ₦51.59 trillion envelope.


## Objectives
- Source and structure Nigeria's 2026 federal budget appropriation data
- Build a 4-page Power BI report with consistent navigation and drill-down across MDAs
- Surface allocation priorities, sector shares, and capital vs recurrent breakdowns
- Produce a dashboard that a policy analyst, journalist, or civil servant could navigate without training


## Tech Stack
| Microsoft Power BI | Dashboard development |
| Power Query (M) | Data cleaning and transformation |
| DAX | Measures and calculated columns |
| Excel / CSV | Source data preparation |


## Data
- **Source:** Nigeria 2026 Federal Appropriation Bill (publicly available)
- **Total Budget:** ₦51.59 trillion
- **Coverage:** 56 MDAs
- **Sectors analyzed:** Security, Healthcare, Education, General Overview


## Dashboard Structure
**Page 1 — General Overview**
- Total budget: ₦51.59 trillion
- Recurrent vs Capital expenditure split
- Top 10 MDAs by allocation
- Sector share of total budget

**Page 2 — Security Sector**
- Total security allocation and share of the national budget
- Breakdown across defence, police, intelligence, and paramilitary MDAs
- Capital vs recurrent split within security

**Page 3 — Healthcare Sector**
- Federal Ministry of Health allocation by programme
- Primary care, tertiary hospitals, NHIS, disease control breakdown
- Capital vs recurrent in health spend

**Page 4 — Education Sector**
- Federal Ministry of Education + UBEC + TETFund allocations
- Breakdown by education level
- Capital vs recurrent split


## Key DAX Measures

```dax
Total Budget = SUM('Budget'[Amount])

Sector Share % =
DIVIDE(
    CALCULATE(SUM('Budget'[Amount]), ALLSELECTED('Budget'[Sector])),
    CALCULATE(SUM('Budget'[Amount]), ALL('Budget'))
)

CapEx Total =
CALCULATE(SUM('Budget'[Amount]), 'Budget'[Expenditure_Type] = "Capital")

RecEx Total =
CALCULATE(SUM('Budget'[Amount]), 'Budget'[Expenditure_Type] = "Recurrent")

CapEx Ratio = DIVIDE([CapEx Total], [RecEx Total])
```


## Key Findings
**Security dominates discretionary spending.** Security received one of the largest single-sector allocations, reflecting ongoing internal security challenges across multiple theatres.

**Healthcare capital allocation is thin.** A significant share of the health budget goes to recurrent costs, primarily salaries, leaving limited room for infrastructure and programme delivery.

**Education faces the same structural problem.** Personnel costs consume the majority of the education budget, with TETFund bearing most capital spend for tertiary institutions.

**Capital vs recurrent imbalance is systemic.** Across all three sectors, recurrent expenditure consistently overshadows capital spend, limiting investment in long-term capacity regardless of headline allocation numbers.


## What I Learned
- Government budget data is rarely clean, the ministry names are inconsistent, and sector classifications require judgment calls
- DAX measures are significantly more powerful than calculated columns for anything involving ratios or cross-filter context
- Defining the four sectors as an analytical frame before touching Power BI made every design decision easier
