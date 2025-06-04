# 🩺 Diabetes Risk Dashboard – Power BI Project

This project presents a data-driven dashboard built in **Power BI** using the **Pima Indians Diabetes Dataset**. The goal is to explore patterns and risk factors associated with diabetes using clear, interactive visualizations.

## 📊 Key Features

- **Outcome Distribution**: Bar chart comparing diabetic vs non-diabetic patients
- **Glucose vs BMI**: Scatter plot with Outcome-based coloring
- **Age Group Analysis**: Avg. glucose trends across age groups
- **Summary Table**: Min, Max, Median, and Average BMI by Outcome
- **Slicers**: Filter by Age Group, BMI, Glucose level, and Outcome

## 🧠 Insights

- High glucose levels correlate with increased diabetes risk
- Patients aged 40+ show higher prevalence
- BMI and glucose jointly indicate diabetes susceptibility

## 🛠 Tools Used

- **Power BI Desktop (Free version)**
- **DAX** for calculated columns and custom measures
- Cleaned CSV dataset (no preprocessing tools needed)

## Files

- `diabetes.csv` – Cleaned dataset
- `Diabetes_Dashboard.pbix` – Power BI dashboard file
- Screenshots of the dashboard visuals

##  Preview

![Dashboard Screenshot](images/diabetes_dashboard_preview.png)

##  About the Dataset

- Source: Pima Indians Diabetes Dataset
- 768 entries, 9 medical predictor variables + outcome
- Binary classification (1 = Diabetic, 0 = Non-diabetic)

##  diabetes-risk-dashboard-powerbi/
│
├── 📄 README.md
├── 📊 Diabetes_Dashboard.pbix
├── 📁 data/
│   └── diabetes.csv
│
├── 📁 images/
│   ├── dashboard_overview.png
│   ├── glucose_vs_bmi.png
│   └── outcome_distribution.png
│
├── 📁 dax/
│   └── measures.txt
│
├── 📁 docs/
│   └── project_summary.pdf 
│
└── 📁 
    ├── app.py
    └── requirements.txt

    ## dax/measures.txt 
    -- Total number of records
TotalPatients = COUNTROWS('diabetes')

-- Count of diabetic patients
DiabeticCount = CALCULATE(COUNTROWS('diabetes'), 'diabetes'[Outcome] = 1)

-- Median BMI by Outcome
MedianBMI = MEDIAN('diabetes'[BMI])

-- Age Group column
AgeGroup = 
SWITCH(TRUE(),
    'diabetes'[Age] < 20, "Under 20",
    'diabetes'[Age] < 30, "20-29",
    'diabetes'[Age] < 40, "30-39",
    'diabetes'[Age] < 50, "40-49",
    'diabetes'[Age] < 60, "50-59",
    "60+"
)

## app.py
import streamlit as st
import pandas as pd

st.set_page_config(page_title="Diabetes Risk Explorer", layout="wide")

df = pd.read_csv("diabetes.csv")

st.title("🩺 Diabetes Risk Dashboard (Streamlit)")
st.sidebar.header("Filters")
outcome_filter = st.sidebar.selectbox("Diabetes Outcome", options=[0, 1, "All"])

if outcome_filter != "All":
    df = df[df["Outcome"] == int(outcome_filter)]

st.write("### Data Preview", df.head())

st.write("### Glucose vs BMI Scatter Plot")
st.scatter_chart(df[["Glucose", "BMI"]])

## requirements.txt
streamlit
pandas

##  Let’s Connect!

I’m currently seeking opportunities in **Data Analytics** and **Healthcare BI** roles.  
Feel free to connect or reach out on [LinkedIn](https://www.linkedin.com/in/YOURUSERNAME)  

**#PowerBI #DataAnalytics #HealthcareData #DAX #DashboardDesign #OpenToWork**


