# 🦠 COVID-19 Deaths Data Analysis

This project presents an in-depth analysis of global COVID-19 deaths using SQL and data analysis techniques. The goal is to extract insights about the spread and fatality of the virus across countries and over time.

---

## 🎯 Project Objectives

- Calculate total confirmed cases and deaths per country.
- Identify countries with the highest death rates.
- Analyze the trend of cases and deaths over time.
- Compare the impact across continents or regions.

---

## 🛠️ Tools & Technologies

- **SQL** (PostgreSQL / MySQL)
- **Excel** for data preparation
- **Power BI** or **Tableau** *(optional for visualizations)*

---

## 📊 Sample SQL Queries

Here are a few key queries used in the project:

```sql
-- Global totals of cases and deaths
SELECT SUM(new_cases) AS total_cases,
       SUM(new_deaths) AS total_deaths,
       SUM(new_deaths)/SUM(new_cases)*100 AS death_rate
FROM covid_deaths;


-- Top 10 countries by death rate
SELECT location, 
       SUM(new_deaths) / NULLIF(SUM(new_cases), 0) * 100 AS death_rate
FROM covid_deaths
GROUP BY location
ORDER BY death_rate DESC
LIMIT 10;
