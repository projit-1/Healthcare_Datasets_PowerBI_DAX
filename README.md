Healthcare Analytics Dashboard - Power BI Project

## Project Overview

This project analyzes healthcare patient, hospital visit, and insurance claim data using Power BI. The goal is to transform raw healthcare data into meaningful insights that support decision-making for healthcare providers, hospital administrators, and insurance organizations.

The project follows a relational data model consisting of Patients, Visits, and Claims datasets and demonstrates data modeling, DAX calculations, KPI development, and dashboard creation.


## Business Objectives

The dashboard aims to answer the following business questions:

* How many patients are registered in the healthcare system?
* Which cities have the highest number of patients?
* What are the most common diagnoses?
* Which departments generate the highest treatment costs?
* What percentage of claims are approved?
* How many patients are considered high risk?
* Which insurance providers process claims most efficiently?
* What factors contribute to insurance fraud risk?

## Dataset Description

### 1. Patients Table

Contains demographic and health-related information about patients.

| Column            | Description               |
| ----------------- | ------------------------- |
| Patient_ID        | Unique patient identifier |
| First_Name        | Patient name              |
| Gender            | Male/Female               |
| Age               | Patient age               |
| City              | Patient location          |
| Blood_Group       | Blood group               |
| Chronic_Disease   | Existing chronic disease  |
| Insurance_Type    | Insurance category        |
| Registration_Date | Patient registration date |
| Risk_Score        | Health risk score (1-100) |


### 2. Visits Table

Contains hospital visit information.

| Column             | Description                |
| ------------------ | -------------------------- |
| Visit_ID           | Unique visit identifier    |
| Patient_ID         | Patient reference          |
| Visit_Date         | Visit date                 |
| Hospital_ID        | Hospital identifier        |
| Department         | Medical department         |
| Doctor_ID          | Doctor identifier          |
| Diagnosis          | Patient diagnosis          |
| Length_of_Stay     | Hospital stay duration     |
| Treatment_Cost     | Cost of treatment          |
| Outcome            | Treatment outcome          |
| Satisfaction_Score | Patient satisfaction score |

### 3. Claims Table

Contains insurance claim information.

| Column             | Description                 |
| ------------------ | --------------------------- |
| Claim_ID           | Unique claim identifier     |
| Visit_ID           | Visit reference             |
| Patient_ID         | Patient reference           |
| Claim_Date         | Claim submission date       |
| Insurance_Provider | Insurance company           |
| Claim_Amount       | Requested amount            |
| Approved_Amount    | Approved amount             |
| Claim_Status       | Approved, Pending, Rejected |
| Processing_Days    | Claim processing time       |
| Fraud_Flag         | Fraud indicator             |

## Data Model

Relationships:

Patients (1) → (Many) Visits

Visits (1) → (Many) Claims

Patients (1) → (Many) Claims

Star-schema principles were used to ensure efficient reporting and filtering across datasets.

## Key Performance Indicators (KPIs)

### Patient KPIs

* Total Patients
* Average Patient Age
* High-Risk Patients
* High-Risk Percentage
* Patients by Gender
* Patients by City

### Hospital KPIs

* Total Visits
* Average Length of Stay
* Average Satisfaction Score
* Treatment Cost
* Cost by Department

### Insurance KPIs

* Total Claims
* Average Claim Amount
* Approved Claims
* Rejected Claims
* Approval Rate
* Average Processing Days
* Fraud Rate

## DAX Measures

### Total Patients

```DAX
Total Patients =
COUNTROWS(patients)
```

### Average Claim Amount

```DAX
AVG_Claim_Amount =
AVERAGE(claims[Claim_Amount])
```

### High-Risk Patients

```DAX
High Risk Patients =
CALCULATE(
    COUNTROWS(patients),
    patients[Risk_Score] > 80
)
```

### High-Risk Percentage

```DAX
High Risk % =
DIVIDE(
    CALCULATE(
        COUNTROWS(patients),
        patients[Risk_Score] > 80
    ),
    COUNTROWS(patients)
)
```

### Claim Approval Rate

```DAX
Approval Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS(claims),
        claims[Claim_Status] = "Approved"
    ),
    COUNTROWS(claims)
)
```

---

## Dashboard Pages

### Executive Summary

Displays:

* Total Patients
* Total Visits
* Total Claims
* Approval Rate
* Fraud Rate

### Patient Analytics

Displays:

* Patients by Gender
* Patients by City
* Age Distribution
* High-Risk Patients
* Chronic Disease Analysis

### Hospital Operations

Displays:

* Visits by Department
* Average Length of Stay
* Satisfaction Score
* Treatment Cost Trends

### Insurance Analytics

Displays:

* Claims by Status
* Claim Approval Rate
* Processing Time
* Insurance Provider Performance

### Fraud Analysis

Displays:

* Fraud Rate
* Fraud Cases by Provider
* Fraud Trend Analysis


## Skills Demonstrated

* Data Cleaning
* Data Modeling
* Power Query
* DAX Measures
* Time Intelligence
* KPI Development
* Data Visualization
* Dashboard Design
* Healthcare Analytics
* Business Intelligence


## Tools Used

* Microsoft Power BI
* Power Query
* DAX
* CSV Data Sources
* Data Modeling

## Key Insights

* Identified high-risk patient populations.
* Evaluated patient satisfaction across departments.
* Analyzed treatment costs and hospital performance.
* Measured insurance claim approval efficiency.
* Monitored fraud indicators and claim processing performance.

## Author
Projit Mondol

