# 🏦 Bank Loan Report — Excel Analytics Project

> **A comprehensive Excel-based analytical dashboard for monitoring, evaluating, and understanding a bank's loan portfolio performance through KPIs, trends, and Good vs. Bad loan classification.**

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Problem Statement](#-problem-statement)
- [Dataset Description](#-dataset-description)
- [Key Performance Indicators (KPIs)](#-key-performance-indicators-kpis)
- [Good Loan vs. Bad Loan Analysis](#-good-loan-vs-bad-loan-analysis)
- [Dashboards](#-dashboards)
- [Workbook Structure](#-workbook-structure)
- [Metrics & Calculations](#-metrics--calculations)
- [Tools & Techniques Used](#-tools--techniques-used)
- [File](#-file)
- [About the Developer](#-about-the-developer)

---

## 📖 Project Overview

The **Bank Loan Report** is a data analytics project built entirely in **Microsoft Excel**. It empowers bank analysts and decision-makers to:

- Track and evaluate **lending performance** across time
- Monitor the **health** of the loan portfolio
- Identify **emerging trends** to inform lending strategy
- Distinguish between **profitable (Good) and at-risk (Bad) loans**

The project processes real-world-style loan application data covering borrowers across multiple U.S. states, employment profiles, loan purposes, and repayment statuses — all from a single, well-structured Excel workbook.

---

## ❓ Problem Statement

> *"In order to monitor and assess our bank's lending activities and performance, we need to create a comprehensive Bank Loan Report. This report aims to provide insights into key loan-related metrics and their changes over time. The report will help us make data-driven decisions, track our loan portfolio's health, and identify trends that can inform our lending strategies."*

---

## 📊 Dataset Description

The raw data lives in the **`BANK LOAN DATA`** sheet and contains **25 columns** and **38,576 loan records** tracking every aspect of a loan application:

| Column | Description |
|---|---|
| `id` | Unique loan application identifier |
| `member_id` | Unique borrower identifier |
| `address_state` | U.S. state of the borrower |
| `application_type` | Individual or joint application |
| `emp_length` | Borrower's employment length |
| `emp_title` | Borrower's job title |
| `grade` | Loan grade assigned (A–G) |
| `sub_grade` | Sub-grade within the loan grade |
| `home_ownership` | Ownership status (RENT / OWN / MORTGAGE) |
| `issue_date` | Date the loan was issued |
| `loan_status` | Current status: *Fully Paid*, *Current*, or *Charged Off* |
| `Good v Bad Loan` | Derived classification: *Good Loan* or *Bad Loan* |
| `purpose` | Stated reason for the loan |
| `term` | Repayment term (36 or 60 months) |
| `verification_status` | Income verification status |
| `annual_income` | Borrower's annual income ($) |
| `dti` | Debt-to-Income ratio |
| `int_rate` | Interest rate on the loan |
| `installment` | Monthly installment amount ($) |
| `loan_amount` | Total loan amount disbursed ($) |
| `total_acc` | Total number of credit accounts |
| `total_payment` | Total amount received from borrower ($) |
| `last_credit_pull_date` | Date of last credit bureau pull |
| `last_payment_date` | Date of the most recent payment |
| `next_payment_date` | Scheduled next payment date |

### 📅 Data Scale
- **38,576** individual loan records
- Loan issuance dates span across **2021**, enabling month-over-month trend analysis
- Borrowers spread across **multiple U.S. states**

---

## 📈 Key Performance Indicators (KPIs)

The project tracks **5 core KPIs**, each monitored at three levels:

| KPI | All-Time Total | MTD (Month-to-Date) | MoM Change |
|---|:---:|:---:|:---:|
| 🗂️ **Total Loan Applications** | ✅ | ✅ | ✅ |
| 💰 **Total Funded Amount** | ✅ | ✅ | ✅ |
| 💵 **Total Amount Received** | ✅ | ✅ | ✅ |
| 📉 **Average Interest Rate** | ✅ | ✅ | ✅ |
| ⚖️ **Average Debt-to-Income (DTI)** | ✅ | ✅ | ✅ |

> **MoM Formula:**  
> `MoM Change (%) = (MTD Value − PMTD Value) / PMTD Value × 100`  
> Where **PMTD** = Previous Month-to-Date (e.g., November vs. December)

---

## ✅ Good Loan vs. Bad Loan Analysis

Loans are classified using the following business rule:

```
IF loan_status IN ("Fully Paid", "Current")  →  ✅ Good Loan
IF loan_status = "Charged Off"               →  ❌ Bad Loan
```

### Good Loan KPIs
| Metric | Description |
|---|---|
| 📊 Good Loan Application % | Share of applications classified as Good |
| 🗂️ Good Loan Applications | Count of fully paid + current loans |
| 💰 Good Loan Funded Amount | Total funds disbursed on good loans |
| 💵 Good Loan Total Received | Total repayments collected on good loans |

### Bad Loan KPIs
| Metric | Description |
|---|---|
| 📊 Bad Loan Application % | Share of applications classified as Bad |
| 🗂️ Bad Loan Applications | Count of charged-off loans |
| 💰 Bad Loan Funded Amount | Total funds disbursed on bad loans |
| 💵 Bad Loan Total Received | Partial repayments recovered on bad loans |

---

## 🖥️ Dashboards

The workbook contains **two interactive dashboards**:

### Dashboard 1 — Summary Dashboard
> **Sheet:** `SUMMARY DASHBOARD`

Focuses on high-level KPI cards and the Good vs. Bad loan breakdown. Gives executives a quick health-check of the loan book at a glance.

**Key visuals include:**
- KPI cards for Total Loan Applications, Funded Amount, Amount Received, Avg. Interest Rate, Avg. DTI
- MTD vs. PMTD KPI comparison tiles
- MoM % change indicators
- Good Loan vs. Bad Loan percentage breakdown

---

### Dashboard 2 — Overview Dashboard
> **Sheet:** `OVERVIEW DASHBOARD`

Provides deeper trend analysis and segmentation. Helps analysts identify patterns across time, geography, loan purpose, and borrower profile.

**Key visuals include:**
- **Monthly trend** of loan applications, funded amounts & repayments
- **State-wise** distribution of loan activity across the U.S.
- **Loan term** breakdown (36-month vs. 60-month)
- **Employment length** segmentation
- **Loan purpose** analysis (debt consolidation, credit card, home improvement, etc.)
- **Home ownership** analysis (RENT / OWN / MORTGAGE)

---

## 🗂️ Workbook Structure

```
Bank_Loan_Report.xlsx
│
├── 📋 BANK LOAN DATA          ← Raw loan-level data (25 columns, 38,576 records)
├── 🔧 design sheet            ← Pivot tables, GETPIVOTDATA formulas & KPI calculations
├── 📄 problem statement       ← Business requirements & KPI definitions
├── 📊 SUMMARY DASHBOARD       ← Executive KPI summary with Good/Bad loan split
└── 🗺️ OVERVIEW DASHBOARD      ← Trend, geographic & segmentation analysis
```

---

## 🧮 Metrics & Calculations

All KPI values are computed dynamically using **Excel Pivot Tables** and **`GETPIVOTDATA()`** formula references. This ensures every dashboard metric updates automatically when the underlying data changes.

### Example Formulas Used

```excel
-- Total Loan Applications (All-Time)
=GETPIVOTDATA("Count of id", $B$3)

-- MTD Loan Applications (December)
=GETPIVOTDATA("Count of id", $A$9, "Months (issue_date)", 12)

-- MoM Change in Funded Amount
=(GETPIVOTDATA("Sum of loan_amount",$A$9,"Months (issue_date)",12)
 - GETPIVOTDATA("Sum of loan_amount",$A$16,"Months (issue_date)",11))
 / GETPIVOTDATA("Sum of loan_amount",$A$16,"Months (issue_date)",11)

-- Good Loan Percentage
=GETPIVOTDATA("% of Total", $A$30, "Good v Bad Loan", "Good Loan")
```

---

## 🛠️ Tools & Techniques Used

| Tool / Feature | Usage |
|---|---|
| **Microsoft Excel** | Core platform for all data, analysis, and dashboards |
| **Pivot Tables** | Aggregating loan data by month, state, grade, purpose, etc. |
| **GETPIVOTDATA()** | Dynamic KPI extraction from pivot table results |
| **Conditional Logic (IF)** | Classifying loans as Good or Bad based on status |
| **MoM Calculations** | Month-over-Month variance tracking for all 5 KPIs |
| **Charts & Visualizations** | Line, bar, map, and donut charts across both dashboards |
| **Data Formatting** | Color-coded KPI tiles, custom number formats, icon sets |

---

## 🚀 How to Use

1. **Open** `Bank_Loan_Report.xlsx` in **Microsoft Excel 2016 or later**
2. Navigate to the **`SUMMARY DASHBOARD`** tab for high-level KPIs
3. Navigate to the **`OVERVIEW DASHBOARD`** tab for trend & segmentation analysis
4. To explore or modify raw data, go to the **`BANK LOAN DATA`** tab
5. Pivot tables and KPI formulas update **automatically** when data is refreshed

> ⚠️ **Note:** Enable macros and allow content if prompted, to ensure all pivot tables and linked formulas function correctly.

---

## 📂 File

| File | Size | Description |
|---|---|---|
| `Bank_Loan_Report.xlsx` | ~9.4 MB | Full workbook with 38,576 records, 5 sheets, and 2 dashboards |

---

## 🔮 Future Scope

- **Details Dashboard** — The problem statement outlines a third dashboard providing a consolidated, drill-through grid view of individual loan records. This can be added as a future enhancement to complete the full requirements.

---

## 👨‍💻 About the Developer

| | |
|---|---|
| **Name** | Ganesh Kurli |
| **Email** | [ganeshkurli845@gmail.com](mailto:ganeshkurli845@gmail.com) |

This project was designed and developed by **Ganesh Kurli** as a comprehensive Excel-based data analytics solution for bank loan portfolio management. The workbook demonstrates proficiency in data modelling, KPI design, Pivot Tables, dynamic formula engineering, and dashboard visualisation — all within Microsoft Excel.

---

<div align="center">

**Built with ❤️ by [Ganesh Kurli](mailto:ganeshkurli845@gmail.com) using Microsoft Excel**  
*Data-driven lending intelligence — from raw applications to executive dashboards.*

</div>

 ![image alt](

