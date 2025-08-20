# 🚦 Road Accident Analysis – Power BI Dashboard

This project explores UK road accident data to identify **trends, hotspots, and high-risk areas**. The dashboard enables stakeholders to track **year-over-year performance**, understand **regional accident patterns**, and take **data-driven safety actions**.

![Dashboard Preview](https://raw.githubusercontent.com/Analyzewithasim/road_accident_analysis_PowerBI/main/Road%20Accident%20Analysis_page-0001.jpg)
---

## 📊 Objective

To help the road safety and transport analytics team:
- Compare **Current vs. Previous Year (YTD)** accident and casualty trends
- Identify **top high-risk areas** using visual maps and filters
- Spot **monthly patterns and seasonal spikes**
- Analyze accident severity by **vehicle type, road type, and light conditions**

---

## 🛠 Tools & Skills Used

- **Power BI** (Data Modeling, DAX, Visualization)
- **DAX Measures** (Time Intelligence, YoY, TOTALYTD, SAMEPERIODLASTYEAR)
- **Data Cleaning** (Power Query)
- **Calendar Table Creation**
- **Custom Visuals** (Maps, Donuts, Line & Bar Charts)

---

## 🧹 Data Preparation

- Replaced incorrect values (e.g., `Fetal` → `Fatal` in `Accident_Severity`)
- Removed null or invalid date rows
- Created a custom **Calendar Table**:
```DAX
Calendar = CALENDAR(MIN(Data[Accident Date]), MAX(Data[Accident Date]))
Year = YEAR('Calendar'[Date])
Month = FORMAT('Calendar'[Date], "mmm")
Month Number = MONTH('Calendar'[Date])
```

## 🔢 Key DAX Measures
```
Casualties (Current vs Previous Year):
CY Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]), 'Calendar'[Date])
PY Casualties = CALCULATE(SUM(Data[Number_of_Casualties]), SAMEPERIODLASTYEAR('Calendar'[Date]))
YoY Casualties = ([CY Casualties] - [PY Casualties]) / [PY Casualties]
```
Accidents Count (Current vs Previous Year):
```
CY Accidents Count = TOTALYTD(COUNT(Data[Accident_Index]), 'Calendar'[Date])
PY Accidents = CALCULATE(COUNT(Data[Accident_Index]), SAMEPERIODLASTYEAR('Calendar'[Date]))
YoY Accidents = ([CY Accidents Count] - [PY Accidents]) / [PY Accidents]
```
## 📈 Dashboard Features

- **KPI Cards**: CY vs PY Casualties, Accidents, Fatalities, Serious & Slight Casualties
- **Line Chart**: Monthly casualty trends (2021 vs 2022)
- **Map Visual**: Casualties by region to detect hotspots
- **Donut Charts**: Urban vs Rural, Light Conditions breakdown
- **Bar Chart**: Casualties by Road Type
- **Icons / Bars**: Casualties by Vehicle Type

## 🔍 Key Insights

✅ Fatal casualties reduced by 33%, indicating improved safety efforts
✅ Urban areas accounted for 62% of total casualties
✅ Single carriageways recorded the highest number of accidents
✅ Seasonal spikes during July–August, highlighting campaign opportunities

## 📌 Business Impact

This dashboard helped road safety authorities:

- Focus enforcement in urban hotspots
- Allocate funding for road upgrades
- Launch targeted awareness campaigns before seasonal peaks
- Support data-backed policy decisions to improve public safety

## 🙌 Let's Connect

If you're working on safety analytics, transport data, or just love Power BI — let's connect!

🔗 **LinkedIn** – [Connect with me professionally](https://www.linkedin.com/in/analyzewithasim/)

📧 **Email** - asim.analystdata@gmail.com

**Instagram**: [Follow me for daily tips and updates](https://www.instagram.com/asim_pardeshi/)
