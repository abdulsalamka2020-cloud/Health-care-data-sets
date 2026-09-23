# Healthcare Data Analysis Dashboard (Excel)
![](https://github.com/abdulsalamka2020-cloud/Health-care-data-sets/blob/main/Healthcare%20excel%20sheets%20folder/2483dec64055ddcf8baa5e2760543d48.jpg)

An interactive Excel dashboard that analyses hospital billing and admission records for **54,966 patients** (2019 – 2024). The workbook turns a raw patient dataset into two navigable dashboards, **Billing** and **Admission**, built entirely with Excel tables, pivot tables, pivot charts and slicers.

![Billing Dashboard](/billing_dashboard.png)

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Tools Applied](#tools-applied)
3. [Workbook Structure](#workbook-structure)
4. [Dataset Description](#dataset-description)
5. [Data Preparation](#data-preparation)
6. [How the Dashboard Was Built](#how-the-dashboard-was-built)
7. [Dashboard 1: Billing Analysis](#dashboard-1-billing-analysis)
8. [Dashboard 2: Admission Analysis](#dashboard-2-admission-analysis)
9. [Problem Statements and Answers](#problem-statements-and-answers)
10. [Key Insights and Interpretation](#key-insights-and-interpretation)
11. [Recommendations](#recommendations)
12. [Limitations](#limitations)
13. [Files in this Repository](#files-in-this-repository)

---

## Project Overview

Hospitals generate a large volume of data on who is admitted, why, for how long, and how much it costs. This project analyses that data to answer practical questions such as:

- Where does the hospital earn the most revenue, and from whom?
- Which conditions and patient groups need the most attention?
- When are admissions highest, and how are patients being admitted?

The result is a two-page dashboard with buttons for moving between pages and slicers for filtering the whole report by year, gender, condition and more.

## Tools Applied

- **Microsoft Excel**
  - Data cleaning and formatting
  - Excel Tables
  - Calculated column (Length of Stay)
  - Pivot Tables
  - Pivot Charts
  - Slicers (with report connections)
  - Shapes and hyperlinks for navigation

---

## Workbook Structure

The workbook contains five sheets. Each one has a specific role in the workflow, from raw data to finished dashboard.

| Sheet | Purpose |
|---|---|
| **healthcare dataset** | The cleaned raw data, formatted as an Excel Table. This is the single source for everything else. |
| **PIVOT SHEET** | All pivot tables. Each table answers one problem statement (e.g. revenue by condition, admissions by month). |
| **CHART SHEET** | The pivot charts created from the pivot tables. Each chart is formatted here first, then moved to a dashboard. |
| **BILLING** | Dashboard 1: financial analysis (revenue, billing amounts, insurance, medication). |
| **ADMISSION** | Dashboard 2: patient and admission analysis (volume, admission types, conditions, blood types, length of stay). |

### Navigation buttons

The teal panel on the left side of each dashboard has three buttons. Each button is a shape with a **hyperlink** to a sheet in the workbook (Insert → Link → Place in This Document):

| Button | Linked sheet | What it opens |
|---|---|---|
| **Billing** | `BILLING` | The billing analysis dashboard |
| **Admission** | `ADMISSION` | The admission analysis dashboard |
| **Datasets** | `healthcare dataset` | The raw data table behind the dashboards |

This makes the workbook behave like an application. A viewer can move between pages and go back to the raw data without hunting through sheet tabs.

![Dataset sheet](/dataset_sheet.png)

---

## Dataset Description

The dataset has **54,966 patient records** and **15 columns** (14 original fields plus 1 calculated field).

| Column | Description | Type |
|---|---|---|
| **Name** | Patient's name | Text |
| **Age** | Patient's age in years at admission | Number |
| **Gender** | Male or Female | Category |
| **Blood Type** | One of eight groups: A+, A−, B+, B−, AB+, AB−, O+, O− | Category |
| **Medical Condition** | Diagnosed condition: Arthritis, Asthma, Cancer, Diabetes, Hypertension, Obesity | Category |
| **Date of Admission** | Date the patient was admitted | Date |
| **Doctor** | Doctor in charge of the patient | Text |
| **Insurance Provider** | Aetna, Blue Cross, Cigna, Medicare, UnitedHealthcare | Category |
| **Billing Amount** | Amount billed for the stay (formatted in ₦) | Currency |
| **Room Number** | Room the patient was assigned | Number |
| **Admission Type** | Elective (planned), Emergency (unplanned, life-threatening), Urgent (needs prompt care but not immediately life-threatening) | Category |
| **Discharge Date** | Date the patient left the hospital | Date |
| **Medication** | Drug prescribed: Aspirin, Ibuprofen, Lipitor, Paracetamol, Penicillin | Category |
| **Test Results** | Normal, Abnormal or Inconclusive | Category |
| **Length of Stay** | Number of days in hospital (calculated, see below) | Number |

---

## Data Preparation

1. **Converted the range to an Excel Table** (Ctrl + T). This gives filter buttons, banded rows and, importantly, pivot tables that automatically include new rows.
2. **Formatted Billing Amount as currency** (₦) so all money values display consistently.
3. **Created a new column, Length of Stay**, calculated as:

   `Length of Stay = Discharge Date − Date of Admission`

   This gives the number of days each patient stayed. The average across all patients is **15.68 days**.
4. **Checked date and category columns** for consistent formatting so they group correctly in pivot tables (for example, dates grouped into months and years).

---

## How the Dashboard Was Built

The dashboard was built in four steps, moving from raw data to the finished report.

**Step 1: Pivot Tables (PIVOT SHEET).**
One pivot table was created for each problem statement. For example, Medical Condition in Rows and Sum of Billing Amount in Values answers "which condition generates the highest revenue?". Counts, sums and averages were used depending on the question.

**Step 2: Pivot Charts (CHART SHEET).**
Each pivot table was turned into a pivot chart (line, column, bar, donut or pie, depending on the data). Charts were formatted with clear titles, currency axes and a consistent colour scheme.

![Chart sheet](/chart_sheet.png)

**Step 3: Dashboards (BILLING and ADMISSION).**
The finished charts were copied to the two dashboard sheets and arranged under a row of headline **KPI cards**. Each dashboard has its own theme colour (teal), title banner and navigation panel.

**Step 4: Slicers.**
Six slicers (Year, Admission Type, Gender, Insurance Provider, Medical Condition and Blood Type) were added and connected to every pivot table through **Report Connections**. Clicking a slicer button, for example "2023" or "Female", updates all the charts and KPI cards at the same time.

---

## Dashboard 1: Billing Analysis

**Sheet:** `BILLING`  |  **Focus:** money coming in, and where it comes from.

![Billing Dashboard](/billing_dashboard.png)

### KPI cards

| KPI | Value | What it means |
|---|---|---|
| **Total no. of patients** | 54,966 | Number of patient records (admissions) in the dataset |
| **Total Billing Amount** | ₦1,404,068,339.23 | Total revenue billed across all admissions |
| **Average Billing Amount** | ₦25,544.31 | Average bill per patient (total billing ÷ patients) |
| **Average Amount of Medication** | ₦280,813,667.85 | Average revenue per medication type (total billing ÷ the 5 medications) |

### Charts

**1. Revenue Trend over the Month (line chart).**
Shows total billing for each month, January to December. Revenue is not steady. It falls sharply in **February**, which is the lowest point, recovers by March, and reaches its highest levels around **July and August**. It dips again in the later months. This helps the hospital plan for quiet and busy periods.

**2. Total Revenue Generated by Each Medical Condition (bar chart).**
Compares the revenue each condition brings in. **Diabetes** is highest, followed closely by **Obesity** and **Arthritis**. **Cancer** is lowest. The gap between conditions is fairly small in the overall picture (the axis starts at ₦225M, which makes differences look larger).

**3. Insurance per Billing Amount (column chart).**
Shows how much each insurer contributes. **Cigna** contributes the most, followed by **Medicare** and **Blue Cross**, with **Aetna** contributing the least. This tells the hospital which insurer relationships matter most financially.

**4. Total Revenue per Drug Type (column chart).**
Shows revenue linked to each of the five medications, so the hospital can see which drugs drive the most billing. **Ibuprofen** generated the highest revenue.

### Slicers

Year, Admission Type, Gender, Insurance Provider, Medical Condition and Blood Type. Any combination can be selected to drill down, for example "Emergency admissions of Diabetes patients under Cigna in 2022".

---

## Dashboard 2: Admission Analysis

**Sheet:** `ADMISSION`  |  **Focus:** patients, admission patterns and clinical outcomes.

![Admission Dashboard](/admission_dashboard.png)

### KPI cards

| KPI | Value | What it means |
|---|---|---|
| **No. of Abnormal Results** | 18,437 | Patients whose test result was "Abnormal" (about one third of all patients) |
| **Highest Blood Type** | A− | The blood group with the most patients |
| **Total Patients** | 54,966 | Total admissions in the dataset |
| **Average Length of Stay** | 15.68 days | Average number of days between admission and discharge |

### Charts

**1. Number of Admissions per Month (line chart).**
Counts admissions for each month. Months are sorted from highest to lowest, so the line slopes downward. **August** has the most admissions (about 4,780) and **February** has the fewest (about 4,210). February being lowest also matches the drop in revenue on the billing dashboard.

**2. Number of Admission Types (donut chart).**
Shows the share of Elective, Emergency and Urgent admissions. The three types are close to one third each, with **Elective** the most common. This means the hospital has to be ready for planned and unplanned patients in almost equal numbers.

**3. Number of Medical Conditions (bar chart).**
Counts patients per condition. **Arthritis** and **Diabetes** each have about 9,200 patients and are the most common, while **Asthma** has the fewest.

**4. Gender Distribution (pie chart).**
Male patients number 27,496 and female patients 27,470, which is an almost perfect 50/50 split.

**5. Number of Blood Types (column chart, on the CHART SHEET).**
Counts patients by blood group. **A−** is highest (about 4,225) and **AB+** is lowest (about 4,020).

### Slicers

Same six slicers as the billing dashboard, so the two pages can be filtered the same way.

---

## Problem Statements and Answers

| # | Question | Answer |
|---|---|---|
| 1 | Which condition generates the highest revenue? | **Diabetes** |
| 2 | Which age group visits the hospital most? | **Age 38** was the single most frequent age |
| 3 | Which insurance provider contributes the most financially? | **Cigna** |
| 4 | Which admission type is most common? | **Elective** |
| 5 | Which condition keeps patients in hospital the longest? | **Asthma** |
| 6 | Most prescribed medication? | **Lipitor** |
| 7 | Which medication generates the highest revenue? | **Ibuprofen** |
| 8 | Condition with the highest abnormal test results? | **Arthritis** |
| 9 | Which gender is admitted through Emergency the most? | **Female** |
| 10 | Which month had the highest number of admissions? | **August** |
| 11 | Most common blood type? | **A−** |

---

## Key Insights and Interpretation

Each finding below says what the data shows, then what it could mean. The "what it could mean" parts are **hypotheses** to be tested, not proven causes.

**1. Diabetes generates the most revenue.**
*Observation:* Diabetes has the highest total billing, with Obesity and Arthritis close behind.
*Interpretation:* Total revenue depends on both how many patients a condition has and how much each patient is billed. Diabetes is also one of the two most common conditions (about 9,200 patients), so its revenue is driven partly by volume. A useful next step is to compare average bill per patient by condition to see whether it is also more expensive to treat.

**2. Age 38 is the most frequent patient age.**
*Observation:* More patients are aged 38 than any other single age.
*Interpretation:* This shows that working-age adults are a major share of patients. Because the analysis used single ages, grouping ages into bands (for example 18–30, 31–45, 46–60, 60+) would give a clearer picture of which age group uses the hospital most.

**3. Cigna contributes the most financially.**
*Observation:* Cigna has the highest billing total, Aetna the lowest.
*Interpretation:* Insurer totals are fairly close, so no single insurer dominates. Still, Cigna is the most important relationship for the hospital's cash flow, and delays in Cigna payments would affect income the most.

**4. Elective is the most common admission type, but the split is nearly even.**
*Observation:* Elective, Emergency and Urgent admissions are each close to one third.
*Interpretation:* A large share of admissions are planned, so scheduling can smooth out demand, but about two thirds are unplanned, so the hospital needs spare capacity all the time.

**5. Asthma patients stay the longest.**
*Observation:* Asthma has the longest average length of stay, compared with the overall average of 15.68 days.
*Interpretation:* This could be due to monitoring to prevent repeat attacks or to severity of cases. It is worth reviewing whether asthma care pathways can be shortened safely.

**6. Lipitor is the most prescribed medication, but Ibuprofen earns the most.**
*Observation:* The most-prescribed drug is not the one that generates the most revenue.
*Interpretation:* Revenue depends on price and billing as well as frequency. Stock decisions should consider both the demand (how often prescribed) and the revenue (how much it brings in).

**7. Arthritis has the most abnormal test results.**
*Observation:* Arthritis leads on abnormal results, which fits with it being one of the most common conditions.
*Interpretation:* The number of abnormal results should also be looked at as a percentage of each condition's patients, so conditions with more patients don't automatically look worse.

**8. More females than males are admitted through Emergency.**
*Observation:* Female patients are the larger group among Emergency admissions.
*Interpretation:* Overall, male and female patient counts are almost equal (27,496 vs 27,470), so this difference comes from admission type and not from more females in the dataset. The data shows what happened, not why, and it should not be read as females being more prone to disease.

**9. August is the busiest month and February the quietest.**
*Observation:* August has the most admissions (about 4,780) and February the fewest (about 4,210). Revenue follows a similar pattern, with a sharp February drop.
*Interpretation:* Staffing, bed capacity and stock can be planned around this seasonal pattern.

**10. A− is the most common blood type.**
*Observation:* A− leads with about 4,225 patients, and AB+ is lowest with about 4,020.
*Interpretation:* The gap between blood types is small (the chart axis starts at 3,900, which exaggerates it). Also, these are the blood groups of **patients**, not of transfusion demand or donors, so blood bank stocking should be based on transfusion records.

---

## Recommendations

1. **Give extra attention to Diabetes and Arthritis.** They are the most common conditions and among the top revenue earners. Dedicated clinics, follow-up programmes and appropriate facilities would improve care, and the hospital could consider bill discounts or payment plans for long-term patients.
2. **Stock Lipitor and Ibuprofen well.** Lipitor is prescribed most often and Ibuprofen earns the most, so shortages would hurt both care and revenue.
3. **Prepare for seasonal peaks.** Plan staff rosters, beds and supplies around the busy period (around July and August) and use the quieter months (like February) for maintenance, training and elective scheduling.
4. **Keep strong relationships with the top insurers**, especially Cigna and Medicare, and follow up on claims promptly.
5. **Run patient education sessions** on lifestyle and prevention for the main conditions, for all genders.
6. **Review the length of stay for Asthma** to see if outpatient follow-up or better discharge planning could reduce long stays.
7. **Keep blood stock in line with actual transfusion demand**, using the lab's transfusion records, with A− well supplied as the most common patient blood type.

---

## Limitations

- The dataset appears to be **synthetic or simulated** (for example, near-equal gender and admission-type splits, and very small differences between conditions and insurers), so findings should be treated as a demonstration of analysis skills and not as real clinical conclusions.
- Several charts have **axes that do not start at zero**, which makes small differences look bigger than they are. Exact figures should be read from the pivot tables.
- The data does not include location, diagnosis severity or treatment details, so reasons behind patterns can only be suggested, not confirmed.

---

## Files in this Repository

| File / Folder | Description |
|---|---|
| `Healthcare excel sheets folder/healthcare_dataset.xlsx` | The full Excel workbook with the dataset, pivot tables, charts and dashboards |
| `images/billing_dashboard.png` | Screenshot of the Billing dashboard |
| `images/admission_dashboard.png` | Screenshot of the Admission dashboard |
| `images/dataset_sheet.png` | Screenshot of the cleaned dataset sheet |
| `images/chart_sheet.png` | Screenshot of the charts used to build the dashboards |
| `README.md` | Project documentation |

**Download the workbook:** [healthcare_dataset.xlsx](https://github.com/abdulsalamka2020-cloud/Health-care-data-sets/blob/main/Healthcare%20excel%20sheets%20folder/healthcare_dataset.xlsx)

---

*Prepared by Abdulsalam, IOTB Tech Fellowship, Data Analytics track.*

